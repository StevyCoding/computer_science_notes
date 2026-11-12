```markdown
# TypeScript Type Validation with `satisfies` 🧐

TypeScript developers often face a dilemma: ensuring an expression matches a specific type while preserving the most specific type for inference.

## Example: Color Palette 🎨

Consider this color palette:

```typescript
// Each property can be a string or an RGB tuple.
const palette = {
  red: [255, 0, 0],
  green: '#00ff00',
  bleu: [0, 0, 255],
  //  ~~~~ sacrebleu - we've made a typo!
};
```

We want to use array methods on `red` and string methods on `green`.

```typescript
const redComponent = palette.red.at(0);
const greenNormalized = palette.green.toUpperCase();
```

Notice the typo with `bleu` – we should have written `blue`. We could use a type annotation, but that would lose information about each property.

```typescript
type Colors = 'red' | 'green' | 'blue';
type RGB = [red: number, green: number, blue: number];

type Palette = Record<Colors, string | RGB>;

const palette: Palette = {
  red: [255, 0, 0],
  green: '#00ff00',
  bleu: [0, 0, 255],
  //  ~~~~ The typo is now correctly detected
};
```

However, this introduces an undesirable error – `palette.red` could be a string.

## Using the `satisfies` Operator 🚀

The `satisfies` operator allows us to validate that the type of an expression matches a specific type, without changing the resulting type of that expression.

For example, we can validate that all the properties of `palette` are compatible with `string | number[]`:

```typescript
type Colors = 'red' | 'green' | 'blue';
type RGB = [red: number, green: number, blue: number];

const palette = {
  red: [255, 0, 0],
  green: '#00ff00',
  bleu: [0, 0, 255],
  //  ~~~~ The typo is now caught!
} satisfies Record<Colors, string | RGB>;
```

Both methods remain accessible:

```typescript
const redComponent = palette.red.at(0);
const greenNormalized = palette.green.toUpperCase();
```
```