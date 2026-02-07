# The Basics

Each and every value in JavaScript has a set of behaviors you can observe from running different operations.

## Static type-checking

A type is the concept of describing which values can be passed to a function and which will crash. JavaScript only truly provides dynamic typing - running the code to see what happens.

The alternative is to use a static type system to make predictions about what the code is expected to do before it runs.

Static type systems describe the shapes and behaviors of what our values will be when we run our programs. A type-checker like TypeScript uses that information and tells us when things might be going off the rails.

## Non-exception Failures

JavaScript gives us different behavior and returns the value `undefined` when accessing a property that doesn't exist on an object.

In TypeScript, the following code would produce an error:

```typescript
const user = {
  name: "Daniel",
  age: 26,
};

user.location;  // Error: Property 'location' does not exist
```

While sometimes that implies a trade-off in what you can express, the intent is to catch legitimate bugs in our programs.

## Types for Tooling

TypeScript can catch bugs when we make mistakes in our code. That's great, but TypeScript can also prevent us from making those mistakes in the first place.

The type-checker has information to check things like whether we're accessing the right properties on variables and other properties. Once it has that information, it can also start suggesting which properties you might want to use.

TypeScript can deliver "quick fixes" to automatically fix errors, refactorings to easily re-organize code, and useful navigation features for jumping to definitions of a variable, or finding all references to a given variable.

## tsc, the TypeScript compiler

First we'll need to grab it via npm:

```shell
npm install -g typescript
```

This installs the TypeScript Compiler `tsc` globally.

### Your first TypeScript program

Create `hello.ts`:

```typescript
// Greets the world.
console.log("Hello world!");
```

Now let's type-check it by running the command `tsc`:

```shell
tsc hello.ts
```

This will output a `hello.js` file next to your `hello.ts` file.

### Type-checking

Let's rewrite `hello.ts` with a function that has a type-checking error:

```typescript
function greet(person, date) {
  console.log(`Hello ${person}, today is ${date}!`);
}

greet("Brendan");  // Error: Expected 2 arguments, but got 1.
```

If we run `tsc hello.ts`, TypeScript will give us an error on the command line.

### Emitting with Errors

One thing to note is that TypeScript will still emit a JavaScript file even when there are type errors. This is based on one of TypeScript's core values: much of the time, you will know better than TypeScript.

You can use the `noEmitOnError` compiler option to prevent this:

```shell
tsc --noEmitOnError hello.ts
```

## Explicit Types

Let's add type annotations to our function:

```typescript
function greet(person: string, date: Date) {
  console.log(`Hello ${person}, today is ${date.toDateString()}!`);
}
```

What we did was add type annotations on `person` and `date` to describe what types of values `greet` can be called with.

### Type Inference

In many cases, TypeScript can even just infer (or "figure out") the types for us even if we omit them:

```typescript
let msg = "hello there!";
// TypeScript infers that msg has type 'string'
```

## Erased Types

Type annotations aren't part of JavaScript, so there really aren't any browsers or other runtimes that can just run TypeScript unmodified.

TypeScript needs a compiler to strip out or transform any TypeScript-specific code so that you can run it. Type annotations are completely erased.

Important: Type annotations never change the runtime behavior of your program.

## Downleveling

TypeScript has the ability to rewrite code from newer versions of ECMAScript to older ones. This process of moving from a newer version to an older one is sometimes called downleveling.

By default TypeScript targets ES5, an extremely old version of ECMAScript. You can choose something more recent by using the `target` option:

```shell
tsc --target es2015 hello.ts
```

## Strictness

Different users come to TypeScript looking for different things in a type-checker. TypeScript provides strictness settings that turn static type-checking from a switch into something closer to a dial.

The `strict` flag in the CLI, or `"strict": true` in a `tsconfig.json` toggles all strictness settings on simultaneously.

### noImplicitAny

The `noImplicitAny` flag will issue an error on any variables whose type is implicitly inferred as `any`. This encourages you to be more explicit about your types.

### strictNullChecks

By default, values like `null` and `undefined` are assignable to any other type. This can make writing some code easier, but forgetting to handle `null` and `undefined` is the cause of countless bugs.

The `strictNullChecks` flag makes handling `null` and `undefined` more explicit, and spares us from worrying about whether we forgot to handle them.
