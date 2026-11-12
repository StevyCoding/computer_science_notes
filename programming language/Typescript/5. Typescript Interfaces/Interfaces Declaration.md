An `interface` in TypeScript is a blueprint for creating objects with a specific structure. It defines a set of properties, methods, and events that a class or object must implement. The interface serves as a contract between objects and classes, enforcing a structure in your code. 

Here is an example of an interface declaration in TypeScript:

```typescript
interface Person {
  firstName: string;
  lastName: string;
  age?: number;

  getFullName(): string;
}
```

In this example, the `Person` interface defines four properties: `firstName`, `lastName`, `age`, and a method `getFullName()`. The `age` property is optional, indicated by the `?` symbol. Any class or object that implements the `Person` interface must have these properties and method. 🚀