In TypeScript, namespaces are used to organize and share code across multiple files. Namespaces allow you to group related functionality into a single unit and prevent naming conflicts.

Here’s an example of how you can use namespaces in TypeScript:

```ts
// myNamespace.ts
namespace MyNamespace {
  export function doSomething() {
    console.log('Doing something...');
  }
}

// main.ts
/// <reference path="myNamespace.ts" />
MyNamespace.doSomething(); // Output: "Doing something..."
```

In this example, we use the `namespace` keyword in the “myNamespace.ts” file to define a namespace “MyNamespace”. Within the namespace, we export a function “doSomething”.