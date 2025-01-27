In TypeScript, you can achieve constructor overloading by using multiple constructor definitions with different parameter lists in a single class. Given below is the example where we have multiple definitions for the constructor:

```ts
class Point {
  // Overloads
  constructor(x: number, y: string);
  constructor(s: string);
  constructor(xs: any, y?: any) {
    // TBD
  }
}
```

Note that, similar to function overloading, we only have one implementation of the consructor and it’s the only the signature that is overloaded.