Union Types in TypeScript allow you to specify multiple possible types for a single variable or parameter. A union type is written as a vertical bar `|` separated list of types.

For example, consider a function that takes either a string or a number as an argument:

```ts
function combine(input1: string | number, input2: string | number) {
  return input1 + input2;
}
```