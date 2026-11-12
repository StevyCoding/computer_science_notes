Recursive types in TypeScript are a way to define a type that references itself. Recursive types are used to define complex data structures, such as trees or linked lists, where a value can contain one or more values of the same type. 🌳

For example, the following is a recursive type that represents a linked list:

```typescript
type LinkedList<T> = {
  value: T;
  next: LinkedList<T> | null;
};
```

Let's break down this example:

```typescript
type LinkedList<T> = {
  value: T;
  next: LinkedList<T> | null;
};
```

In this example, the `LinkedList` type is defined as a type that extends `T` and contains a property `next` of the same type `LinkedList<T>`. This allows us to create a linked list where each node contains a value of type `T` and a reference to the next node, which is also a `LinkedList<T>`. This creates a circular structure. 🔄

You can create an instance like this:

```typescript
let list: LinkedList<number> = {
  value: 1,
  next: { value: 2, next: { value: 3, next: null } },
};
```

This demonstrates a linked list with three nodes: 1, 2, and 3. The `next` property points to the subsequent nodes in the list. The final node's `next` property is set to `null` to indicate the end of the list. 🔚