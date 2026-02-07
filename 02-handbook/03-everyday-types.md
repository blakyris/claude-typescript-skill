# Everyday Types

In this chapter, we'll cover some of the most common types of values you'll find in JavaScript code, and explain the corresponding ways to describe those types in TypeScript.

## The primitives: string, number, and boolean

JavaScript has three very commonly used primitives: `string`, `number`, and `boolean`. Each has a corresponding type in TypeScript.

- `string` represents string values like "Hello, world"
- - `number` is for numbers like 42. JavaScript does not have a special runtime value for integers, so there's no equivalent to int or float
  - - `boolean` is for the two values `true` and `false`
   
    - Always use `string`, `number`, or `boolean` for types (lowercase). The capitalized versions `String`, `Number`, and `Boolean` are legal but refer to some special built-in types that will very rarely appear in your code.
   
    - ## Arrays
   
    - To specify the type of an array like `[1, 2, 3]`, you can use the syntax `number[]`; this syntax works for any type (e.g. `string[]` is an array of strings).
   
    - You may also see this written as `Array<number>`, which means the same thing.
   
    - ## any
   
    - TypeScript has a special type `any` that you can use whenever you don't want a particular value to cause typechecking errors.
   
    - When a value is of type `any`, you can access any properties of it, call it like a function, assign it to (or from) a value of any type, or pretty much anything else that's syntactically legal.
   
    - The `any` type is useful when you don't want to write out a long type just to convince TypeScript that a particular line of code is okay. Use the compiler flag `noImplicitAny` to flag any implicit `any` as an error.
   
    - ## Type Annotations on Variables
   
    - When you declare a variable using `const`, `var`, or `let`, you can optionally add a type annotation to explicitly specify the type of the variable:
   
    - ```typescript
      let myName: string = "Alice";
      ```

      TypeScript doesn't use "types on the left"-style declarations like `int x = 0;` Type annotations will always go after the thing being typed.

      In most cases, though, this isn't needed. Wherever possible, TypeScript tries to automatically infer the types in your code.

      ## Functions

      ### Parameter Type Annotations

      When you declare a function, you can add type annotations after each parameter to declare what types of parameters the function accepts:

      ```typescript
      function greet(name: string) {
        console.log("Hello, " + name.toUpperCase() + "!!");
      }
      ```

      When a parameter has a type annotation, arguments to that function will be checked.

      ### Return Type Annotations

      You can also add return type annotations. Return type annotations appear after the parameter list:

      ```typescript
      function getFavoriteNumber(): number {
        return 26;
      }
      ```

      Much like variable type annotations, you usually don't need a return type annotation because TypeScript will infer the function's return type based on its return statements.

      ### Anonymous Functions

      Anonymous functions are a little bit different from function declarations. When a function appears in a place where TypeScript can determine how it's going to be called, the parameters of that function are automatically given types. This process is called contextual typing.

      ## Object Types

      Apart from primitives, the most common sort of type you'll encounter is an object type. To define an object type, we simply list its properties and their types:

      ```typescript
      function printCoord(pt: { x: number; y: number }) {
        console.log("The coordinate's x value is " + pt.x);
        console.log("The coordinate's y value is " + pt.y);
      }

      printCoord({ x: 3, y: 7 });
      ```

      ### Optional Properties

      Object types can also specify that some or all of their properties are optional. To do this, add a `?` after the property name:

      ```typescript
      function printName(obj: { first: string; last?: string }) {
        // ...
      }
      ```

      ## Union Types

      A union type is a type formed from two or more other types, representing values that may be any one of those types.

      ### Defining a Union Type

      ```typescript
      function printId(id: number | string) {
        console.log("Your ID is: " + id);
      }
      ```

      ### Working with Union Types

      TypeScript will only allow an operation if it is valid for every member of the union. If you have a value of a union type, how do you work with it?

      The solution is to narrow the union with code. Narrowing occurs when TypeScript can deduce a more specific type for a value based on the structure of the code:

      ```typescript
      function printId(id: number | string) {
        if (typeof id === "string") {
          console.log(id.toUpperCase());
        } else {
          console.log(id);
        }
      }
      ```

      ## Type Aliases

      A type alias is a name for any type. The syntax for a type alias is:

      ```typescript
      type Point = {
        x: number;
        y: number;
      };

      function printCoord(pt: Point) {
        console.log("The coordinate's x value is " + pt.x);
        console.log("The coordinate's y value is " + pt.y);
      }

      printCoord({ x: 100, y: 100 });
      ```

      You can actually use a type alias to give a name to any type at all, not just an object type.

      ## Interfaces

      An interface declaration is another way to name an object type:

      ```typescript
      interface Point {
        x: number;
        y: number;
      }

      function printCoord(pt: Point) {
        console.log("The coordinate's x value is " + pt.x);
        console.log("The coordinate's y value is " + pt.y);
      }

      printCoord({ x: 100, y: 100 });
      ```

      ### Differences Between Type Aliases and Interfaces

      - A type cannot be re-opened to add new properties, but an interface which is always extendable
      - - Type aliases may not participate in declaration merging, but interfaces can
        - - Interfaces may only be used to declare the shapes of objects, not rename primitives
          - - For the most part, you can choose based on personal preference
           
            - ## Type Assertions
           
            - Sometimes you will have information about the type of a value that TypeScript can't know about. In this situation, you can use a type assertion to specify a more specific type:
           
            - ```typescript
              const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
              ```

              You can also use the angle-bracket syntax (except if the code is in a `.tsx` file):

              ```typescript
              const myCanvas = <HTMLCanvasElement>document.getElementById("main_canvas");
              ```

              Because type assertions are removed at compile-time, there is no runtime checking associated with a type assertion.

              ## Literal Types

              In addition to the general types `string` and `number`, we can refer to specific strings and numbers in type positions.

              By combining literals into unions, you can express a much more useful concept - for example, functions that only accept a certain set of known values:

              ```typescript
              function printText(s: string, alignment: "left" | "right" | "center") {
                // ...
              }
              ```

              ## null and undefined

              JavaScript has two primitive values used to signal absent or uninitialized value: `null` and `undefined`. TypeScript has two corresponding types by the same names.

              How these types behave depends on whether you have the `strictNullChecks` option on.

              ### strictNullChecks on

              With `strictNullChecks` on, when a value is `null` or `undefined`, you will need to test for those values before using methods or properties on that value.

              ### Non-null Assertion Operator (Postfix !)

              TypeScript also has a special syntax for removing `null` and `undefined` from a type without doing any explicit checking. Writing `!` after any expression is effectively a type assertion that the value isn't `null` or `undefined`:

              ```typescript
              function liveDangerously(x?: number | null) {
                console.log(x!.toFixed());
              }
              ```

              ## Enums

              Enums are a feature added to JavaScript by TypeScript which allows for describing a value which could be one of a set of possible named constants.
