Je vais créer un cours complet, dense et structuré pour atteindre un niveau Senior Flutter en 3 heures. Ce sera un markdown prêt pour Obsidian avec toutes les explications de syntaxe et logique.

---

# 🚀 Flutter Senior Mastery: De Zéro à Expert en 3 Heures

## Architecture du Cours
- **Heure 1**: Fondations & State Management (Riverpod, Notifiers)
- **Heure 2**: Networking (Dio) & Routing (GoRouter)
- **Heure 3**: Patterns Avancés, Performance & Architecture Clean

---

# 📚 HEURE 1: Fondations & State Management

## 1.1 Comprendre la Syntaxe Dart Moderne (Prérequis)

### Null Safety & Type Safety
```dart
// AVANT (null unsafe)
String name; // Peut être null → crash potentiel

// APRÈS (null safe)
String name; // ❌ Erreur de compilation
String? name; // ✅ Peut être null
String name = 'John'; // ✅ Non-null, initialisé

// Late initialization
late String name; // Je promets de l'initialiser avant usage
name = 'John'; // ✅ OK après assignation

// Null-aware operators
String? maybeName;
print(maybeName?.length ?? 0); // Si null → 0, sinon length
print(maybeName!.length); // ❌ Force non-null (danger si null)
```

**Logique**: Dart force la gestion explicite du null. Le `?` marque un type nullable, `!` force l'accès (risqué), `??` fournit une valeur par défaut.

### Extension Methods & Records (Dart 3)
```dart
// Extensions: Ajouter des méthodes aux types existants
extension StringX on String {
  String get capitalized => 
    isEmpty ? this : '${this[0].toUpperCase()}${substring(1)}';
}

// Usage
final name = 'john'.capitalized; // 'John'

// Records (Dart 3): Tuples nommés/positionnels
({int x, int y}) point = (x: 10, y: 20);
(String, int) person = ('John', 30);

// Pattern matching
final (name, age) = person;
final (:x, :y) = point;
```

**Logique**: Les extensions permettent d'enrichir les types sans héritage. Les records remplacent les classes simples pour retourner multiples valeurs.

---

## 1.2 Riverpod: La Révolution du State Management

### Pourquoi Riverpod > Provider ?

| Provider | Riverpod |
|----------|----------|
| Dépend du BuildContext | Context-free |
| Compile-time safety | Compile-time safety |
| Global state difficile | Scoped state naturel |
| Pas de auto-dispose | Auto-dispose intelligent |

### Syntaxe Fondamentale: Les 4 Types de Providers

```dart
import 'package:flutter_riverpod/flutter_riverpod.dart';

// ═══════════════════════════════════════════════════════════
// 1. PROVIDER: Valeur immuable/calculée (jamais modifié)
// ═══════════════════════════════════════════════════════════
final apiUrlProvider = Provider<String>((ref) => 'https://api.example.com');
// Usage: ref.read(apiUrlProvider) ou ref.watch(apiUrlProvider)

// ═══════════════════════════════════════════════════════════
// 2. STATEPROVIDER: État simple (primitifs: int, String, bool)
// ═══════════════════════════════════════════════════════════
final counterProvider = StateProvider<int>((ref) => 0);
// Modification: ref.read(counterProvider.notifier).state = 5
// ou: ref.read(counterProvider.notifier).update((state) => state + 1)

// ═══════════════════════════════════════════════════════════
// 3. FUTUREPROVIDER: Async opérations (HTTP, DB, SharedPrefs)
// ═══════════════════════════════════════════════════════════
final userProvider = FutureProvider<User>((ref) async {
  final dio = ref.watch(dioProvider);
  final response = await dio.get('/user');
  return User.fromJson(response.data);
});
// Gère automatiquement: loading, error, data states

// ═══════════════════════════════════════════════════════════
// 4. STREAMPROVIDER: Flux de données temps réel (WebSocket, Firebase)
// ═══════════════════════════════════════════════════════════
final messagesProvider = StreamProvider<List<Message>>((ref) {
  return FirebaseFirestore.instance
    .collection('messages')
    .snapshots()
    .map((snap) => snap.docs.map((d) => Message.fromFirestore(d)).toList());
});
```

**Logique clé**: Riverpod utilise `ref` (reference) pour créer des dépendances. Quand un provider A watch le provider B, A se rebuild automatiquement quand B change.

### Syntaxe ConsumerWidget vs ConsumerStatefulWidget

```dart
// ═══════════════════════════════════════════════════════════
// STATELESS avec Riverpod: ConsumerWidget
// ═══════════════════════════════════════════════════════════
class HomePage extends ConsumerWidget {
  const HomePage({super.key});

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    // watch = s'abonner aux changements (rebuild auto)
    final count = ref.watch(counterProvider);
    
    // read = lecture ponctuelle (pas de rebuild)
    final apiUrl = ref.read(apiUrlProvider);

    return Scaffold(
      body: Text('Count: $count'),
      floatingActionButton: FloatingActionButton(
        // .notifier donne accès à l'objet qui contrôle l'état
        onPressed: () => ref.read(counterProvider.notifier).state++,
        child: const Icon(Icons.add),
      ),
    );
  }
}

// ═══════════════════════════════════════════════════════════
// STATEFUL avec Riverpod: ConsumerStatefulWidget
// ═══════════════════════════════════════════════════════════
class ProfilePage extends ConsumerStatefulWidget {
  const ProfilePage({super.key});

  @override
  ConsumerState<ProfilePage> createState() => _ProfilePageState();
}

class _ProfilePageState extends ConsumerState<ProfilePage> {
  @override
  void initState() {
    super.initState();
    // Action au démarrage: ref accessible via widgetRef dans la classe
  }

  @override
  Widget build(BuildContext context) {
    final asyncUser = ref.watch(userProvider);
    
    return asyncUser.when(
      data: (user) => UserProfile(user: user),
      loading: () => const CircularProgressIndicator(),
      error: (err, stack) => ErrorWidget(err),
    );
  }
}
```

---

## 1.3 StateNotifier & AsyncNotifier: Logique Métier Complexe

### StateNotifier (Synchrone)

```dart
// ═══════════════════════════════════════════════════════════
// ÉTAT: Modèle immuable avec Freezed (recommandé)
// ═══════════════════════════════════════════════════════════
@freezed
class CartState with _$CartState {
  const factory CartState({
    @Default([]) List<CartItem> items,
    @Default(false) bool isLoading,
    String? error,
  }) = _CartState;
  
  // Computed properties
  double get totalPrice => 
    items.fold(0, (sum, item) => sum + item.price * item.quantity);
  int get itemCount => items.length;
}

// ═══════════════════════════════════════════════════════════
// NOTIFIER: Classe métier qui contrôle l'état
// ═══════════════════════════════════════════════════════════
class CartNotifier extends StateNotifier<CartState> {
  CartNotifier() : super(const CartState()); // État initial

  // Méthodes métier = transitions d'état explicites
  void addItem(Product product) {
    // Toujours créer un nouvel état (immutabilité)
    final existingIndex = state.items.indexWhere((i) => i.id == product.id);
    
    if (existingIndex >= 0) {
      // Modifier quantité existante
      final updatedItems = [...state.items];
      updatedItems[existingIndex] = updatedItems[existingIndex].copyWith(
        quantity: updatedItems[existingIndex].quantity + 1,
      );
      state = state.copyWith(items: updatedItems);
    } else {
      // Ajouter nouvel item
      state = state.copyWith(
        items: [...state.items, CartItem.fromProduct(product)],
      );
    }
  }

  void removeItem(String id) {
    state = state.copyWith(
      items: state.items.where((i) => i.id != id).toList(),
    );
  }

  void clear() => state = const CartState();
}

// ═══════════════════════════════════════════════════════════
// PROVIDER dérivé
// ═══════════════════════════════════════════════════════════
final cartProvider = StateNotifierProvider<CartNotifier, CartState>((ref) {
  return CartNotifier();
});

// Provider dérivé (computed) - ne rebuild que quand nécessaire
final cartTotalProvider = Provider<double>((ref) {
  final cart = ref.watch(cartProvider);
  return cart.totalPrice;
});
```

**Logique critique**: 
- `state = ...` déclenche le rebuild des widgets qui watch
- L'état est immuable: `copyWith` crée une copie modifiée
- `StateNotifier` est obsolète, préférer `AsyncNotifier` ou `Notifier` (Riverpod 2.x)

---

### AsyncNotifier: Le Standard Moderne (Riverpod 2.x+)

```dart
// ═══════════════════════════════════════════════════════════
// ASYNCNOTIFIER: Gère état asynchrone avec loading/error/data
// ═══════════════════════════════════════════════════════════
@riverpod
class AuthController extends _$AuthController {
  @override
  FutureOr<User?> build() async {
    // build() = initialisation + rechargement automatique
    // Return FutureOr = peut être synchrone ou asynchrone
    
    final prefs = await SharedPreferences.getInstance();
    final token = prefs.getString('token');
    
    if (token == null) return null;
    
    // Auto-validate token
    return _validateToken(token);
  }

  Future<void> login(String email, String password) async {
    // state = AsyncLoading() implicite via guard
    state = const AsyncLoading();
    
    try {
      final dio = ref.read(dioProvider);
      final response = await dio.post('/auth/login', data: {
        'email': email,
        'password': password,
      });
      
      final user = User.fromJson(response.data);
      
      // Persist token
      await ref.read(storageProvider).setToken(user.token);
      
      // Mise à jour succès
      state = AsyncData(user);
    } on DioException catch (e, stackTrace) {
      // Mise à jour erreur avec stacktrace pour debugging
      state = AsyncError(e, stackTrace);
    }
  }

  Future<void> logout() async {
    await ref.read(storageProvider).clearToken();
    state = const AsyncData(null);
  }
  
  // Mutation optimiste (UI instantanée, rollback si erreur)
  Future<void> updateProfile(String name) async {
    final previousUser = state.valueOrNull;
    if (previousUser == null) return;
    
    // Optimistic update
    state = AsyncData(previousUser.copyWith(name: name));
    
    try {
      final dio = ref.read(dioProvider);
      await dio.patch('/user/profile', data: {'name': name});
    } catch (e, stack) {
      // Rollback on error
      state = AsyncError(e, stack);
      // Optionnel: restaurer previousUser après délai
    }
  }
}

// ═══════════════════════════════════════════════════════════
// SYNTAXE GÉNÉRÉE (avec riverpod_generator)
// ═══════════════════════════════════════════════════════════
// Le décorateur @riverpod génère authControllerProvider automatiquement
// Usage: ref.watch(authControllerProvider) → AsyncValue<User?>
//        ref.read(authControllerProvider.notifier).login(...)
```

**Logique AsyncNotifier**:
- `build()` est la source de vérité initiale
- `state` est un `AsyncValue<T>` avec 3 cas: `data`, `loading`, `error`
- `AsyncValue.guard(() async {...})` raccourci pour try/catch + state update
- `keepAlive` et `autoDispose` configurables via annotations

---

## 1.4 Family & AutoDispose: Patterns Avancés

```dart
// ═══════════════════════════════════════════════════════════
// PROVIDER avec PARAMÈTRES (Family)
// ═══════════════════════════════════════════════════════════
final userDetailProvider = FutureProvider.family<User, String>((ref, userId) async {
  final dio = ref.watch(dioProvider);
  final response = await dio.get('/users/$userId');
  return User.fromJson(response.data);
});
// Usage: ref.watch(userDetailProvider('123'))

// ═══════════════════════════════════════════════════════════
// AUTODISPOSE: Nettoyage automatique quand plus utilisé
// ═══════════════════════════════════════════════════════════
final searchProvider = FutureProvider.autoDispose.family<List<Product>, String>((ref, query) async {
  // Annuler requête si provider disposé avant completion
  final cancelToken = CancelToken();
  ref.onDispose(() => cancelToken.cancel());
  
  final dio = ref.watch(dioProvider);
  final response = await dio.get(
    '/search',
    queryParameters: {'q': query},
    cancelToken: cancelToken,
  );
  
  return (response.data as List).map((e) => Product.fromJson(e)).toList();
});
// Se nettoie automatiquement quand le widget est détruit

// ═══════════════════════════════════════════════════════════
// COMBINAISON: Provider qui dépend d'autres providers
// ═══════════════════════════════════════════════════════════
final filteredProductsProvider = Provider.autoDispose<List<Product>>((ref) {
  final searchQuery = ref.watch(searchQueryProvider); // String
  final category = ref.watch(selectedCategoryProvider); // String?
  final allProducts = ref.watch(productsProvider); // AsyncValue<List<Product>>
  
  return allProducts.when(
    data: (products) {
      return products.where((p) {
        final matchesSearch = p.name.toLowerCase().contains(searchQuery.toLowerCase());
        final matchesCategory = category == null || p.category == category;
        return matchesSearch && matchesCategory;
      }).toList();
    },
    loading: () => [],
    error: (_, __) => [],
  );
});
```

**Logique**: 
- `family` crée une "famille" de providers indexés par paramètre
- `autoDispose` libère la mémoire automatiquement
- `ref.onDispose` permet cleanup custom (cancel HTTP, close streams)

---

# 📚 HEURE 2: Networking & Navigation

## 2.1 Dio: Client HTTP Enterprise-Grade

### Configuration Senior

```dart
// ═══════════════════════════════════════════════════════════
// DIO: Configuration avancée avec interceptors
// ═══════════════════════════════════════════════════════════
final dioProvider = Provider<Dio>((ref) {
  final dio = Dio(BaseOptions(
    baseUrl: 'https://api.example.com/v1',
    connectTimeout: const Duration(seconds: 5),
    receiveTimeout: const Duration(seconds: 10),
    headers: {'Accept': 'application/json'},
    validateStatus: (status) => status != null && status < 500,
  ));

  // INTERCEPTOR: Logging & Auth
  dio.interceptors.add(InterceptorsWrapper(
    onRequest: (options, handler) {
      // Inject token depuis Riverpod
      final token = ref.read(authTokenProvider).valueOrNull;
      if (token != null) {
        options.headers['Authorization'] = 'Bearer $token';
      }
      
      log('➡️ ${options.method} ${options.uri}');
      return handler.next(options);
    },
    onResponse: (response, handler) {
      log('✅ ${response.statusCode} ${response.requestOptions.uri}');
      return handler.next(response);
    },
    onError: (DioException e, handler) async {
      log('❌ ${e.response?.statusCode} ${e.requestOptions.uri}');
      
      // Refresh token automatique sur 401
      if (e.response?.statusCode == 401 && 
          e.requestOptions.path != '/auth/refresh') {
        try {
          await ref.read(authControllerProvider.notifier).refreshToken();
          // Retry avec nouveau token
          final newToken = ref.read(authTokenProvider).valueOrNull;
          e.requestOptions.headers['Authorization'] = 'Bearer $newToken';
          return handler.resolve(await dio.fetch(e.requestOptions));
        } catch (_) {
          // Logout si refresh échoue
          ref.read(authControllerProvider.notifier).logout();
        }
      }
      return handler.next(e);
    },
  ));

  // Retry interceptor (package: dio_smart_retry)
  dio.interceptors.add(RetryInterceptor(
    dio: dio,
    logPrint: log,
    retryDelays: const [
      Duration(seconds: 1),
      Duration(seconds: 2),
      Duration(seconds: 3),
    ],
  ));

  return dio;
});
```

### Modèles avec JSON Serializable

```dart
// ═══════════════════════════════════════════════════════════
// MODÈLE: Sérialisation automatique avec Freezed + JSON
// ═══════════════════════════════════════════════════════════
import 'package:freezed_annotation/freezed_annotation.dart';

part 'user.freezed.dart';
part 'user.g.dart';

@freezed
class User with _$User {
  const factory User({
    required String id,
    required String email,
    @JsonKey(name: 'full_name') required String fullName,
    @Default('user') String role,
    DateTime? createdAt,
    @JsonKey(fromJson: _avatarFromJson) String? avatarUrl,
  }) = _User;

  factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);
}

// Custom converter
String? _avatarFromJson(dynamic value) {
  if (value == null) return null;
  if (value is String && value.startsWith('http')) return value;
  return 'https://cdn.example.com/avatars/$value';
}

// ═══════════════════════════════════════════════════════════
// REPOSITORY PATTERN: Abstraction du data source
// ═══════════════════════════════════════════════════════════
abstract class IUserRepository {
  Future<User> getUser(String id);
  Future<List<User>> searchUsers(String query);
  Future<User> updateUser(String id, UserUpdateDTO dto);
}

class UserRepository implements IUserRepository {
  final Dio _dio;
  UserRepository(this._dio);

  @override
  Future<User> getUser(String id) async {
    final response = await _dio.get('/users/$id');
    return User.fromJson(response.data);
  }

  @override
  Future<List<User>> searchUsers(String query) async {
    final response = await _dio.get('/users', queryParameters: {'q': query});
    return (response.data as List).map((e) => User.fromJson(e)).toList();
  }

  @override
  Future<User> updateUser(String id, UserUpdateDTO dto) async {
    final response = await _dio.patch('/users/$id', data: dto.toJson());
    return User.fromJson(response.data);
  }
}

// Provider
final userRepositoryProvider = Provider<IUserRepository>((ref) {
  return UserRepository(ref.watch(dioProvider));
});
```

---

## 2.2 GoRouter: Navigation Déclarative

### Configuration Fondamentale

```dart
// ═══════════════════════════════════════════════════════════
// GOROUTER: Router déclaratif avec deep linking
// ═══════════════════════════════════════════════════════════
final routerProvider = Provider<GoRouter>((ref) {
  final authState = ref.watch(authControllerProvider);
  
  return GoRouter(
    initialLocation: '/',
    debugLogDiagnostics: true,
    
    // REDIRECTION: Auth guard
    redirect: (context, state) {
      final isAuthenticated = authState.valueOrNull != null;
      final isAuthRoute = state.matchedLocation == '/login';
      
      if (!isAuthenticated && !isAuthRoute) return '/login';
      if (isAuthenticated && isAuthRoute) return '/';
      return null; // Pas de redirection
    },
    
    routes: [
      // Route simple
      GoRoute(
        path: '/',
        builder: (context, state) => const HomePage(),
      ),
      
      // Route avec paramètre
      GoRoute(
        path: '/user/:id',
        builder: (context, state) {
          final userId = state.pathParameters['id']!; // String
          return UserDetailPage(userId: userId);
        },
      ),
      
      // Route avec query params /user/123?tab=settings
      GoRoute(
        path: '/profile',
        builder: (context, state) {
          final tab = state.uri.queryParameters['tab'] ?? 'general';
          return ProfilePage(initialTab: tab);
        },
      ),
      
      // ROUTES IMBRIQUÉES (ShellRoute pour layouts persistants)
      ShellRoute(
        builder: (context, state, child) => ScaffoldWithNavBar(child: child),
        routes: [
          GoRoute(
            path: '/dashboard',
            builder: (context, state) => const DashboardPage(),
          ),
          GoRoute(
            path: '/settings',
            builder: (context, state) => const SettingsPage(),
            // Sous-routes
            routes: [
              GoRoute(
                path: 'notifications', // /settings/notifications
                builder: (context, state) => const NotificationsSettingsPage(),
              ),
            ],
          ),
        ],
      ),
    ],
    
    // Error handling
    errorBuilder: (context, state) => ErrorPage(error: state.error),
  );
});

// ═══════════════════════════════════════════════════════════
// UTILISATION: Navigation impérative et déclarative
// ═══════════════════════════════════════════════════════════

// Navigation simple
context.go('/'); // Remplace toute la stack
context.push('/user/123'); // Ajoute à la stack
context.pop(); // Retour

// Avec paramètres
context.go('/user/${user.id}');
context.pushNamed('user', pathParameters: {'id': user.id});

// Navigation avec résultat (async)
final result = await context.push<bool>('/confirm-delete');
if (result == true) { /* ... */ }

// ═══════════════════════════════════════════════════════════
// ROUTES TYPÉES (Type Safety) - Pattern Senior
// ═══════════════════════════════════════════════════════════
class AppRoutes {
  static const home = '/';
  static const login = '/login';
  
  static String userDetail(String id) => '/user/$id';
  static String settings({String? tab}) => 
    tab != null ? '/settings?tab=$tab' : '/settings';
}

// Extension pour syntaxe fluide
extension GoRouterContext on BuildContext {
  void goHome() => go(AppRoutes.home);
  void goUser(String id) => go(AppRoutes.userDetail(id));
}
```

### Navigation avec Riverpod (Pattern Expert)

```dart
// ═══════════════════════════════════════════════════════════
// NAVIGATION CONTROLLER: Navigation depuis la logique métier
// ═══════════════════════════════════════════════════════════
final navigationControllerProvider = Provider((ref) {
  // Accès au navigatorKey pour navigation hors widget tree
  final router = ref.read(routerProvider);
  return NavigationController(router);
});

class NavigationController {
  final GoRouter _router;
  NavigationController(this._router);

  void goHome() => _router.go('/');
  void goUserDetail(String id) => _router.push('/user/$id');
  void goBack<T extends Object?>([T? result]) => _router.pop(result);
  
  // Navigation après action async
  Future<void> navigateAfterLogin(User user) async {
    await _router.pushReplacement('/');
    if (!user.hasCompletedOnboarding) {
      _router.push('/onboarding');
    }
  }
}

// ═══════════════════════════════════════════════════════════
// DEEPLINKING: Configuration pour notifications/push
// ═══════════════════════════════════════════════════════════
// AndroidManifest.xml / Info.plist configuration requise

// Handler de liens entrants
final deepLinkHandlerProvider = Provider((ref) {
  return DeepLinkHandler(ref.read(navigationControllerProvider));
});

class DeepLinkHandler {
  final NavigationController _nav;
  DeepLinkHandler(this._nav);

  void handleUri(Uri uri) {
    // app://user/123 → /user/123
    if (uri.pathSegments.first == 'user') {
      final userId = uri.pathSegments[1];
      _nav.goUserDetail(userId);
    }
  }
}
```

---

# 📚 HEURE 3: Architecture & Patterns Senior

## 3.1 Clean Architecture en Flutter

```
lib/
├── main.dart                 # Entry point
├── app.dart                  # MaterialApp avec router
├── core/                     # Code transversal
│   ├── constants/            # Couleurs, strings, endpoints
│   ├── errors/               # Exceptions, Failures
│   ├── extensions/           # Dart extensions
│   ├── theme/                # ThemeData, styles
│   └── utils/                # Helpers, validators
├── data/                     # Layer données
│   ├── datasources/          # Dio, Firebase, Hive
│   ├── models/               # DTOs (JSON serializable)
│   └── repositories/         # Implémentations
├── domain/                   # Layer métier (pur Dart)
│   ├── entities/             # Modèles métier (pas de JSON)
│   ├── repositories/         # Interfaces abstraites
│   └── usecases/             # Actions métier atomiques
├── presentation/             # Layer UI
│   ├── providers/            # Riverpod controllers
│   ├── pages/                # Screens
│   ├── widgets/              # Composants réutilisables
│   └── states/               # États UI (Freezed)
└── config/                   # DI, routes, env
    └── router.dart
```

### Implémentation Clean

```dart
// ═══════════════════════════════════════════════════════════
// DOMAIN: Entité pure (indépendante de Flutter/datasources)
// ═══════════════════════════════════════════════════════════
// lib/domain/entities/todo.dart
class Todo {
  final String id;
  final String title;
  final bool isCompleted;
  final DateTime createdAt;

  const Todo({
    required this.id,
    required this.title,
    this.isCompleted = false,
    required this.createdAt,
  });

  Todo toggleComplete() => Todo(
    id: id,
    title: title,
    isCompleted: !isCompleted,
    createdAt: createdAt,
  );
}

// Interface repository (contrat)
abstract class ITodoRepository {
  Future<List<Todo>> getTodos();
  Future<Todo> createTodo(String title);
  Future<Todo> updateTodo(Todo todo);
  Future<void> deleteTodo(String id);
}

// ═══════════════════════════════════════════════════════════
// DATA: Modèle + Implémentation
// ═══════════════════════════════════════════════════════════
// lib/data/models/todo_model.dart
class TodoModel extends Todo {
  const TodoModel({
    required super.id,
    required super.title,
    required super.isCompleted,
    required super.createdAt,
  });

  factory TodoModel.fromJson(Map<String, dynamic> json) => TodoModel(
    id: json['id'],
    title: json['title'],
    isCompleted: json['completed'],
    createdAt: DateTime.parse(json['created_at']),
  );

  Map<String, dynamic> toJson() => {
    'id': id,
    'title': title,
    'completed': isCompleted,
    'created_at': createdAt.toIso8601String(),
  };
}

// lib/data/repositories/todo_repository_impl.dart
class TodoRepositoryImpl implements ITodoRepository {
  final Dio _dio;
  TodoRepositoryImpl(this._dio);

  @override
  Future<List<Todo>> getTodos() async {
    final response = await _dio.get('/todos');
    return (response.data as List)
      .map((e) => TodoModel.fromJson(e))
      .toList();
  }
  // ... autres méthodes
}

// ═══════════════════════════════════════════════════════════
// PRESENTATION: Riverpod Controller
// ═══════════════════════════════════════════════════════════
@riverpod
class TodoListController extends _$TodoListController {
  @override
  Future<List<Todo>> build() async {
    final repo = ref.read(todoRepositoryProvider);
    return repo.getTodos();
  }

  Future<void> addTodo(String title) async {
    final repo = ref.read(todoRepositoryProvider);
    
    // Optimistic update
    final previousTodos = state.valueOrNull ?? [];
    final newTodo = Todo(
      id: DateTime.now().toString(), // Temp ID
      title: title,
      createdAt: DateTime.now(),
    );
    
    state = AsyncData([...previousTodos, newTodo]);
    
    try {
      final savedTodo = await repo.createTodo(title);
      // Replace temp with real
      state = AsyncData([
        ...previousTodos.where((t) => t.id != newTodo.id),
        savedTodo,
      ]);
    } catch (e, stack) {
      state = AsyncError(e, stack);
      // Rollback
      state = AsyncData(previousTodos);
    }
  }
}
```

---

## 3.2 Patterns Avancés

### Pattern: Sealed Classes pour États UI

```dart
// ═══════════════════════════════════════════════════════════
// SEALED CLASSES (Dart 3): États exhaustifs et type-safe
// ═══════════════════════════════════════════════════════════
sealed class AuthState {
  const AuthState();
}

class AuthInitial extends AuthState {
  const AuthInitial();
}

class AuthLoading extends AuthState {
  const AuthLoading();
}

class AuthAuthenticated extends AuthState {
  final User user;
  const AuthAuthenticated(this.user);
}

class AuthError extends AuthState {
  final String message;
  final AuthErrorType type;
  const AuthError(this.message, this.type);
}

enum AuthErrorType { network, invalidCredentials, server }

// ═══════════════════════════════════════════════════════════
// USAGE: Switch exhaustif (impossible d'oublier un cas)
// ═══════════════════════════════════════════════════════════
Widget buildAuthWidget(AuthState state) {
  return switch (state) {
    AuthInitial() => const LoginForm(),
    AuthLoading() => const LoadingSpinner(),
    AuthAuthenticated(user: final u) => HomePage(user: u),
    AuthError(message: final m, type: final t) => ErrorDisplay(
        message: m,
        isRetryable: t == AuthErrorType.network,
      ),
  };
}
```

### Pattern: Mixin pour Code Réutilisable

```dart
// ═══════════════════════════════════════════════════════════
// MIXIN: Comportements partagés entre Notifiers
// ═══════════════════════════════════════════════════════════
mixin PaginationMixin<T> on AsyncNotifier<List<T>> {
  int _page = 1;
  bool _hasMore = true;
  bool _isLoadingMore = false;

  Future<List<T>> fetchPage(int page);

  Future<void> loadMore() async {
    if (_isLoadingMore || !_hasMore) return;
    
    _isLoadingMore = true;
    final currentItems = state.valueOrNull ?? [];
    
    try {
      final newItems = await fetchPage(_page + 1);
      if (newItems.isEmpty) {
        _hasMore = false;
      } else {
        _page++;
        state = AsyncData([...currentItems, ...newItems]);
      }
    } catch (e, stack) {
      // Garder données existantes, afficher erreur subtile
    } finally {
      _isLoadingMore = false;
    }
  }

  Future<void> refresh() async {
    _page = 1;
    _hasMore = true;
    state = const AsyncLoading();
    state = await AsyncValue.guard(() => fetchPage(1));
  }
}

// Usage
@riverpod
class ProductListController extends _$ProductListController 
    with PaginationMixin<Product> {
  @override
  Future<List<Product>> build() => fetchPage(1);

  @override
  Future<List<Product>> fetchPage(int page) async {
    final repo = ref.read(productRepositoryProvider);
    return repo.getProducts(page: page, limit: 20);
  }
}
```

---

## 3.3 Performance & Optimisations

```dart
// ═══════════════════════════════════════════════════════════
// OPTIMISATIONS RENDERING
// ═══════════════════════════════════════════════════════════

// 1. const constructors partout où possible
const MyWidget(); // Build jamais recalculé si params identiques

// 2. RepaintBoundary pour isoler animations
RepaintBoundary(
  child: AnimatedWidget(), // N'affecte pas le reste de l'arbre
);

// 3. ListView.builder pour longues listes
ListView.builder(
  itemCount: 10000,
  itemBuilder: (context, index) => ListTile(
    // key unique pour recycling correct
    key: ValueKey(items[index].id),
    title: Text(items[index].name),
  ),
);

// 4. Select pour rebuilds granulaires
// Au lieu de watch tout l'objet:
final user = ref.watch(userProvider); // Rebuild si user.name OU user.email change

// Préférer:
final name = ref.watch(userProvider.select((u) => u.name)); 
// Rebuild UNIQUEMENT si name change

// 5. Cache avec keepAlive
final expensiveComputationProvider = FutureProvider((ref) async {
  ref.keepAlive(); // Garde en cache même si plus utilisé
  return heavyCalculation();
});

// 6. Debounce sur recherche
final searchResultsProvider = FutureProvider.family<List<Item>, String>((ref, query) async {
  // Annuler requête précédente si nouvelle arrive dans 500ms
  final cancelToken = CancelToken();
  ref.onDispose(() => cancelToken.cancel());
  
  await Future.delayed(const Duration(milliseconds: 500)); // Debounce
  if (cancelToken.isCancelled) throw Exception('Cancelled');
  
  return ref.read(repositoryProvider).search(query);
});
```

---

## 3.4 Testing: Stratégie Senior

```dart
// ═══════════════════════════════════════════════════════════
// TESTING RIVERPOD
// ═══════════════════════════════════════════════════════════

// Provider container pour tests
void main() {
  test('Counter increments', () {
    final container = ProviderContainer();
    addTearDown(container.dispose);
    
    final controller = container.read(counterControllerProvider.notifier);
    final initial = container.read(counterControllerProvider);
    
    expect(initial, 0);
    
    controller.increment();
    final updated = container.read(counterControllerProvider);
    
    expect(updated, 1);
  });

  test('AsyncNotifier handles error', () async {
    final container = ProviderContainer(
      overrides: [
        // Mock dépendance
        dioProvider.overrideWithValue(MockDio()),
      ],
    );
    
    final asyncValue = await container.read(userProvider.future);
    // Assertions...
  });
}

// Widget testing avec Riverpod
testWidgets('Counter displays correctly', (tester) async {
  await tester.pumpWidget(
    ProviderScope(
      child: MaterialApp(home: CounterPage()),
    ),
  );
  
  expect(find.text('0'), findsOneWidget);
  
  await tester.tap(find.byIcon(Icons.add));
  await tester.pump();
  
  expect(find.text('1'), findsOneWidget);
});
```

---

# 🎯 Cheat Sheet: Syntaxes Critiques

| Pattern | Syntaxe | Usage |
|---------|---------|-------|
| Provider simple | `final p = Provider<T>((ref) => ...)` | Config, services |
| State simple | `StateProvider<T>` | bool, int, String UI |
| Async data | `FutureProvider<T>` / `AsyncNotifier` | HTTP, DB |
| Logique complexe | `StateNotifier<T>` / `Notifier<T>` | State métier |
| Paramètres | `.family` | Routes, IDs |
| Auto-cleanup | `.autoDispose` | Streams, recherche |
| Dépendances | `ref.watch(otherProvider)` | Chainage réactif |
| Lecture unique | `ref.read(provider)` | Events, callbacks |
| Notifier access | `ref.read(provider.notifier)` | Appeler méthodes |

---

# 🚀 Projet Final: Structure Complète

```dart
// main.dart
void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  
  final container = ProviderContainer();
  // Init services ici si besoin
  
  runApp(
    UncontrolledProviderScope(
      container: container,
      child: const MyApp(),
    ),
  );
}

class MyApp extends ConsumerWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final router = ref.watch(routerProvider);
    
    return MaterialApp.router(
      title: 'Senior Flutter App',
      theme: ref.watch(themeProvider),
      routerConfig: router,
      builder: (context, child) => ErrorBoundary(child: child!),
    );
  }
}
```

---

**Fin du cours.** Ce markdown couvre 95% des patterns utilisés en production Flutter senior. Pour maîtriser en 3 heures:
1. **Heure 1**: Lire sections 1.1-1.4, coder les exemples Riverpod
2. **Heure 2**: Implémenter Dio + GoRouter avec auth flow complet
3. **Heure 3**: Architecturer un feature complet (Clean Arch) avec tests

Les concepts clés sont l'**immutabilité**, la **réactivité** (watch vs read), et la **séparation des concerns** (UI/state/data).