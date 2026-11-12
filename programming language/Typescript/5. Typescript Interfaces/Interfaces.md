Interfaces in TypeScript provide a way to define a contract for a type, which includes a set of properties, methods, and events. They are used to enforce a structure for an object, class, or function argument. Interfaces are not transpiled to JavaScript and are only used by TypeScript at compile-time for type-checking purposes. 🧐

Here’s an example of defining and using an interface in TypeScript:

```typescript
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: 'John Doe',
  age: 30,
};
``` 👍