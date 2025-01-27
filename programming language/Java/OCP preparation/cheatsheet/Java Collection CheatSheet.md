
### Java Collections Cheat Sheet for Java 17 OCP

---

#### 1. Collection Framework Overview

- Collection Interface: Root of the collection hierarchy.
- List: Ordered, allows duplicates. (`ArrayList`, `LinkedList`)
- Set: Unordered, no duplicates. (`HashSet`, `TreeSet`, `LinkedHashSet`)
- Queue: Ordered, typically used for FIFO operations. (`PriorityQueue`, `LinkedList`)
- Deque: Double-ended queue, allows insertion/removal from both ends. (`ArrayDeque`)
- Map: Key-Value pairs, no duplicate keys. (`HashMap`, `TreeMap`, `LinkedHashMap`)

---

#### 2. List Interface

- ArrayList: Resizable array implementation.
    
    - Operations: `add()`, `get()`, `set()`, `remove()`, `size()`, `clear()`
    - Example: `List<String> list = new ArrayList<>();`
- LinkedList: Doubly linked list implementation.
    
    - Operations: `addFirst()`, `addLast()`, `removeFirst()`, `removeLast()`
    - Example: `List<Integer> list = new LinkedList<>();`
- Vector: Synchronized version of `ArrayList`. Rarely used.
    
- Stack: LIFO (Last In, First Out) implementation.
    
    - Example: `Stack<Integer> stack = new Stack<>();`

---

#### 3. Set Interface

- HashSet: Unordered, no duplicates.
    - Example: `Set<String> set = new HashSet<>();`
- LinkedHashSet: Maintains insertion order.
    - Example: `Set<Integer> set = new LinkedHashSet<>();`
- TreeSet: Sorted set (ascending by default).
    - Example: `Set<Double> set = new TreeSet<>();`

---

#### 4. Queue Interface

- PriorityQueue: Queue where elements are ordered by priority.
    - Example: `Queue<String> queue = new PriorityQueue<>();`
- LinkedList: Implements both `List` and `Queue` interfaces.
    - Example: `Queue<Integer> queue = new LinkedList<>();`
- Deque (Double Ended Queue):
    - ArrayDeque: No capacity limitations like `LinkedList`.
    - Example: `Deque<String> deque = new ArrayDeque<>();`

---

#### 5. Map Interface

- HashMap: No order, allows null keys and values.
    - Example: `Map<String, Integer> map = new HashMap<>();`
- LinkedHashMap: Maintains insertion order.
    - Example: `Map<String, String> map = new LinkedHashMap<>();`
- TreeMap: Sorted map by keys.
    - Example: `Map<Integer, String> map = new TreeMap<>();`

---

#### 6. Common Collection Methods

- add(E): Adds element to a collection.
- remove(E): Removes specific element.
- size(): Returns the number of elements.
- contains(E): Checks if the collection contains an element.
- clear(): Removes all elements from the collection.
- isEmpty(): Checks if the collection is empty.
- forEach(): Performs action on each element (since Java 8).
- stream(): Converts collection to a stream (since Java 8).

---

#### 7. Common Collection Operations (Java 17)

- Sorting:
    
    - `Collections.sort(list)`: Sorts `List` (uses `Comparable` or `Comparator`).
    - `TreeSet`: Automatically sorted.
- Iterating:
    
    - For-Each Loop: `for (String item : list) {...}`
    - Iterator: `Iterator<E> iterator = collection.iterator(); while (iterator.hasNext()) {...}`
    - Lambda: `list.forEach(item -> System.out.println(item));`
- Conversion Between Collections:
    
    - List to Set: `Set<T> set = new HashSet<>(list);`
    - Set to List: `List<T> list = new ArrayList<>(set);`
    - Collection to Stream: `Stream<T> stream = collection.stream();`
    - Stream to Collection: `List<T> list = stream.collect(Collectors.toList());`

---

#### 8. Collection Utilities (Java 17)

- `Collections.synchronizedList(list)`: Synchronized access to a list.
- `Collections.reverse(list)`: Reverses the order of elements.
- `Collections.sort(list)`: Sorts a list.
- `Collections.unmodifiableList(list)`: Creates an unmodifiable list.
- `Collections.max(collection)`: Finds the maximum element.
- `Collections.min(collection)`: Finds the minimum element.

---

#### 9. New Features in Java 17

- Set.of(): Immutable set creation.
    - Example: `Set<String> set = Set.of("A", "B", "C");`
- List.of(): Immutable list creation.
    - Example: `List<Integer> list = List.of(1, 2, 3);`
- Map.of(): Immutable map creation.
    - Example: `Map<String, Integer> map = Map.of("key1", 1, "key2", 2);`
- toArray(): Converts a collection to an array.
    - Example: `T[] array = list.toArray(new T[0]);`

---

#### 10. Performance Considerations

- ArrayList: Best for random access, worst for insertion/removal at the start.
- LinkedList: Best for insertion/removal at ends, slow random access.
- HashSet: O(1) for add/remove, poor ordering.
- TreeSet: O(log n) for add/remove, keeps elements sorted.
- PriorityQueue: O(log n) for add/remove, useful for priority tasks.

---

#### 11. Best Practices

- Avoid: Using `Vector` or `Stack` (use `ArrayList` and `Deque` instead).
- Use: `LinkedHashMap` for maintaining insertion order.
- Immutable Collections: Use `List.of()`, `Set.of()`, and `Map.of()` for immutable collections.

---

#### 12. Key Takeaways

- Thread-Safety: Use `Collections.synchronizedX()` for thread safety.
- Performance: Choose the right collection type based on usage pattern.
- Immutability: Prefer immutable collections for safety and efficiency.
- Lambda Expressions: Leverage lambdas with `forEach`, `filter`, and other Stream operations.

---

This cheat sheet should serve as a quick reference for mastering the Java Collection Framework in Java 17, covering all essential types, methods, and best practices needed for the OCP exam.