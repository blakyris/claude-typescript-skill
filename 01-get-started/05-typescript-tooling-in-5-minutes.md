# TypeScript Tooling in 5 minutes

Let's get started by building a simple web application with TypeScript.

## Installing TypeScript

There are two main ways to add TypeScript to your project:

- Via npm (the Node.js package manager)
- - By installing TypeScript's Visual Studio plugins
 
  - For npm users:
 
  - ```shell
    > npm install -g typescript
    ```

    ## Building your first TypeScript file

    In your editor, type the following JavaScript code in `greeter.ts`:

    ```typescript
    function greeter(person) {
      return "Hello, " + person;
    }

    let user = "Jane User";

    document.body.textContent = greeter(user);
    ```

    ## Compiling your code

    We used a `.ts` extension, but this code is just JavaScript. You could have copy/pasted this straight out of an existing JavaScript app.

    At the command line, run the TypeScript compiler:

    ```shell
    tsc greeter.ts
    ```

    The result will be a file `greeter.js` which contains the same JavaScript that you fed in.

    Now we can start taking advantage of some of the new tools TypeScript offers. Add a `: string` type annotation to the 'person' function parameter as shown here:

    ```typescript
    function greeter(person: string) {
      return "Hello, " + person;
    }

    let user = "Jane User";

    document.body.textContent = greeter(user);
    ```

    ## Type annotations

    Type annotations in TypeScript are lightweight ways to record the intended contract of the function or variable. In this case, we intend the greeter function to be called with a single string parameter.

    We can try changing the call greeter to pass an array instead:

    ```typescript
    function greeter(person: string) {
      return "Hello, " + person;
    }

    let user = [0, 1, 2];

    document.body.textContent = greeter(user);
    // Error: Argument of type 'number[]' is not assignable to parameter of type 'string'.
    ```

    ## Interfaces

    Let's develop our sample further. Here we use an interface that describes objects that have a `firstName` and `lastName` field.

    ```typescript
    interface Person {
      firstName: string;
      lastName: string;
    }

    function greeter(person: Person) {
      return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = { firstName: "Jane", lastName: "User" };

    document.body.textContent = greeter(user);
    ```

    ## Classes

    Finally, let's extend the example one last time with classes. TypeScript supports new features in JavaScript, like support for class-based object-oriented programming.

    ```typescript
    class Student {
      fullName: string;
      constructor(
        public firstName: string,
        public middleInitial: string,
        public lastName: string
      ) {
        this.fullName = firstName + " " + middleInitial + " " + lastName;
      }
    }

    interface Person {
      firstName: string;
      lastName: string;
    }

    function greeter(person: Person) {
      return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Jane", "M.", "User");

    document.body.textContent = greeter(user);
    ```

    ## Running your TypeScript web app

    Now type the following in `greeter.html`:

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <title>TypeScript Greeter</title>
      </head>
      <body>
        <script src="greeter.js"></script>
      </body>
    </html>
    ```

    Open `greeter.html` in the browser to run your first simple TypeScript web application!
