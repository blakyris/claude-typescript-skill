---
name: typescript
description: Deep TypeScript expertise powered by official documentation. Use when answering TypeScript questions, writing TypeScript code, debugging type errors, configuring tsconfig, or helping with TypeScript migration.
allowed-tools: Read, Grep, Glob
---

You have access to comprehensive TypeScript reference documentation in the `references/` directory. **Always consult the relevant reference files before answering TypeScript questions** — do not rely solely on your training data.

## Reference Map

Use this map to find the right file for each topic. All paths are relative to `references/`.

### Type System Fundamentals
- **Basics & everyday types**: `02-handbook/02-the-basics.md`, `02-handbook/03-everyday-types.md`
- **Narrowing & type guards**: `02-handbook/04-narrowing.md`
- **Type inference**: `03-reference/15-type-inference.md`
- **Type compatibility**: `03-reference/12-type-compatibility.md`

### Functions & Objects
- **Functions**: `02-handbook/05-functions.md`
- **Object types**: `02-handbook/06-objects.md`

### Generics
- **Generics**: `02-handbook/08-generics.md`

### Advanced Type Manipulation
- **Overview**: `02-handbook/07-types-from-types.md`
- **keyof types**: `02-handbook/09-keyof-types.md`
- **typeof types**: `02-handbook/10-typeof-types.md`
- **Indexed access types**: `02-handbook/11-indexed-access-types.md`
- **Conditional types**: `02-handbook/12-conditional-types.md`
- **Mapped types**: `02-handbook/13-mapped-types.md`
- **Template literal types**: `02-handbook/14-template-literal-types.md`

### Classes
- **Classes**: `02-handbook/15-classes.md`

### Modules
- **Modules (handbook)**: `02-handbook/16-modules.md`
- **Module system theory**: `04-modules-reference/02-theory.md`
- **Choosing compiler options for modules**: `04-modules-reference/03-choosing-compiler-options.md`
- **Module reference**: `04-modules-reference/04-reference.md`
- **ESM/CJS interop**: `04-modules-reference/05-esm-cjs-interop.md`
- **Namespaces**: `03-reference/08-namespaces.md`

### Utility Types
- **Built-in utility types**: `03-reference/01-utility-types.md`

### Enums, Decorators, JSX
- **Enums**: `03-reference/04-enums.md`
- **Decorators**: `03-reference/02-decorators.md`
- **JSX/TSX**: `03-reference/06-jsx.md`

### Other Reference
- **Declaration merging**: `03-reference/03-declaration-merging.md`
- **Iterators & generators**: `03-reference/05-iterators-and-generators.md`
- **Mixins**: `03-reference/07-mixins.md`
- **Symbols**: `03-reference/10-symbols.md`
- **Triple-slash directives**: `03-reference/11-triple-slash-directives.md`
- **Variable declarations**: `03-reference/16-variable-declarations.md`

### Declaration Files
- **Introduction**: `06-declaration-files/01-intro.md`
- **Reference**: `06-declaration-files/02-reference.md`
- **Library structures**: `06-declaration-files/03-library-structures.md`
- **Module .d.ts**: `06-declaration-files/04-modules-d-ts.md`
- **Module plugin**: `06-declaration-files/05-module-plugin.md`
- **Module class**: `06-declaration-files/06-module-class.md`
- **Module function**: `06-declaration-files/07-module-function.md`
- **Global .d.ts**: `06-declaration-files/08-global-d-ts.md`
- **Global-modifying module**: `06-declaration-files/09-global-modifying-module-d-ts.md`
- **Do's and don'ts**: `06-declaration-files/10-do-s-and-don-ts.md`
- **Deep dive**: `06-declaration-files/11-deep-dive.md`
- **Publishing**: `06-declaration-files/12-publishing.md`
- **Consumption**: `06-declaration-files/13-consumption.md`

### Project Configuration (tsconfig)
- **tsconfig.json**: `08-project-configuration/01-tsconfig-json.md`
- **tsconfig reference**: `08-project-configuration/03-tsconfig-reference.md`
- **Compiler options**: `08-project-configuration/04-compiler-options.md`
- **Project references**: `08-project-configuration/05-project-references.md`
- **Build tool integration**: `08-project-configuration/06-integrating-with-build-tools.md`
- **Watch mode**: `08-project-configuration/07-configuring-watch.md`

### JavaScript Interop
- **Intro to JS with TS**: `07-javascript/01-intro-to-js-ts.md`
- **Type-checking JS files**: `07-javascript/02-type-checking-javascript-files.md`
- **JSDoc reference**: `07-javascript/03-jsdoc-reference.md`
- **Generating .d.ts from JS**: `07-javascript/04-dts-from-js.md`

### Migration & Tutorials
- **Migrating from JavaScript**: `05-tutorials/04migrating-from-javascript.md`
- **DOM manipulation**: `05-tutorials/03-dom-manipulation.md`
- **Using with Babel**: `05-tutorials/05-babel-with-typescript.md`

## Guidelines

1. **Read before answering**: When a user asks about a TypeScript topic, read the relevant reference file(s) before responding. Do not guess.
2. **Cite specifics**: Reference exact syntax, constraints, and examples from the documentation.
3. **Prefer idiomatic patterns**: Recommend patterns that align with the official handbook's guidance.
4. **Combine references when needed**: Many questions span multiple topics (e.g., generics + conditional types). Read all relevant files.
5. **Stay current**: The reference files represent the official TypeScript documentation. Prefer them over your training data when there is a conflict.
