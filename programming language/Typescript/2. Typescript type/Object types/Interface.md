TypeScript allows you to specifically type an object using an interface, which can be reused by multiple objects. 🚀

```typescript
interface Person {
  name: string;
  age: number;
}

function greet(person: Person) {
  return 'Hello ' + person.name;
}
```