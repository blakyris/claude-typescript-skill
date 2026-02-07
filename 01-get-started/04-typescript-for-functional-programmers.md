# TypeScript for Functional Programmers

TypeScript began its life as an attempt to bring traditional object-oriented types to JavaScript so that the programmers at Microsoft could bring traditional object-oriented programs to the web. As it has developed, TypeScript's type system has evolved to model code written by native JavaScripters. The resulting system is powerful, interesting and messy.

This introduction is designed for working Haskell or ML programmers who want to learn TypeScript. It describes how the type system of TypeScript differs from Haskell's type system. It also describes unique features of TypeScript's type system that arise from its modelling of JavaScript code.

## Prerequisites

In this introduction, I assume you know the following:

- How to program in JavaScript, the good parts.
- - Type syntax of a C-descended language.
 
  - ## Concepts not in Haskell
 
  - ### Built-in types
 
  - JavaScript defines 8 built-in types: Number, String, BigInt, Boolean, Symbol, Null, Undefined, Object.
 
  - TypeScript has corresponding primitive types for the built-in types: `number`, `string`, `bigint`, `boolean`, `symbol`, `null`, `undefined`, `object`.
 
  - ### Gradual typing
 
  - TypeScript uses the type `any` whenever it can't tell what the type of an expression should be. Compared to Dynamic, calling `any` a type is an overstatement. It just turns off the type checker wherever it appears.
 
  - ### Structural typing
 
  - Structural typing is a familiar concept to most functional programmers, although Haskell and most MLs are not structurally typed. Its basic form is pretty simple: named types just give a name to a type; for assignability purposes there's no difference between type aliases and interface types.
 
  - ### Unions
 
  - In TypeScript, union types are untagged. In other words, they are not discriminated unions like `data` in Haskell. However, you can often discriminate types in a union using built-in tags or other properties.
 
  - ### Intersections
 
  - TypeScript also has intersections. `Combined` has two properties, `a` and `b`, just as if they had been written as one object literal type.
 
  - ### Unit types
 
  - Unit types are subtypes of primitive types that contain exactly one primitive value. For example, the string `"foo"` has the type `"foo"`.
 
  - ## Concepts similar to Haskell
 
  - ### Contextual typing
 
  - TypeScript has some obvious places where it can infer types, like variable declarations. But it also infers types in a few other places that you may not expect.
 
  - ### Type aliases
 
  - Type aliases are mere aliases, just like `type` in Haskell. The compiler will attempt to use the alias name wherever it was used in the source code, but does not always succeed.
 
  - ### Discriminated Unions
 
  - The closest equivalent to `data` is a union of types with discriminant properties, normally called discriminated unions in TypeScript.
 
  - ### Type Parameters
 
  - Like most C-descended languages, TypeScript requires declaration of type parameters. Type parameters can also be constrained to a type, which behaves a bit like type class constraints.
 
  - ### Higher-kinded types
 
  - TypeScript does not have higher kinded types.
 
  - ### Point-free programming
 
  - Point-free programming is possible in JavaScript, but can be verbose. In TypeScript, type inference often fails for point-free programs.
 
  - ### Module system
 
  - JavaScript's modern module syntax is a bit like Haskell's, except that any file with `import` or `export` is implicitly a module.
 
  - ### readonly and const
 
  - In JavaScript, mutability is the default, although it allows variable declarations with `const` to declare that the reference is immutable. TypeScript additionally has a `readonly` modifier for properties.
 
  - ## Next Steps
 
  - - Read the full Handbook from start to finish
    - - Explore the Playground examples
