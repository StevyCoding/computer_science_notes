The `keyof` operator in TypeScript is used to get the union of keys from an object type. Here’s an example of how it can be used:

```ts
interface User {
  name: string;
  age: number;
  location: string;
}

type UserKeys = keyof User; // "name" | "age" | "location"
const key: UserKeys = 'name';
```

In this example, `UserKeys` is a type that represents the union of keys from the `User` interface, which is `"name"` | `"age"` | `"location"`. And a constant named `key` with the type `UserKeys` is declared with the value `"name"`.