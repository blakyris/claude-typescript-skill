## The `typeof` type operator

JavaScript already has a `typeof` operator you can use in an _expression_ context:

```typescript
// Prints "string"
console.log(typeof "Hello world");
```

TypeScript adds a `typeof` operator you can use in a _type_ context to refer to the _type_ of a variable or property:

```typescript
let s = "hello";
let n: typeof s;
     let n: string
```

This isn’t very useful for basic types, but combined with other type operators, you can use `typeof` to conveniently express many patterns. For an example, let’s start by looking at the predefined type `ReturnType<T>`. It takes a _function type_ and produces its return type:

```typescript
type Predicate = (x: unknown) => boolean;
type K = ReturnType<Predicate>;
      type K = boolean
```

If we try to use `ReturnType` on a function name, we see an instructive error:

```typescript
function f() {
  return { x: 10, y: 3 };
}
type P = ReturnType<f>;
'f' refers to a value, but is being used as a type here. Did you mean 'typeof f'?2749'f' refers to a value, but is being used as a type here. Did you mean 'typeof f'?
```

Remember that _values_ and _types_ aren’t the same thing. To refer to the _type_ that the _value `f`_ has, we use `typeof`:

```typescript
function f() {
  return { x: 10, y: 3 };
}
type P = ReturnType<typeof f>;
      type P = {
   x: number;
   y: number; }
```

### Limitations

TypeScript intentionally limits the sorts of expressions you can use `typeof` on.

Specifically, it’s only legal to use `typeof` on identifiers (i.e. variable names) or their properties. This helps avoid the confusing trap of writing code you think is executing, but isn’t:

```typescript
// Meant to use = ReturnType<typeof msgbox>
let shouldContinue: typeof msgbox("Are you sure you want to continue?");
',' expected.
```