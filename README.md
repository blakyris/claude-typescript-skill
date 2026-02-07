```
     ┌────────────────────────────────────┐
     │                                    │
     │        ████████╗███████╗           │
     │        ╚══██╔══╝██╔════╝           │
     │           ██║   ███████╗           │
     │           ██║   ╚════██║           │
     │           ██║   ███████║           │
     │           ╚═╝   ╚══════╝           │
     │                                    │
     │          S K I L L  F O R          │
     │        C L A U D E  C O D E        │
     │                                    │
     └────────────────────────────────────┘
```

> Give Claude deep TypeScript expertise, grounded in official documentation — not just training data.

This [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code/skills) equips Claude with  complete TypeScript knowledge as searchable reference material.

---

## Why use a skill?

Claude already knows TypeScript. But large language models can confuse version-specific details, invent type signatures, or miss subtle constraints. This skill fixes that by giving Claude the actual source of truth to read on demand.

---

## Installation

Clone this repo into your Claude Code skills directory:

```bash
# Global install (available in all projects)
git clone git@github.com:blakyris/claude-typescript-skill.git ~/.claude/skills/typescript

# Or project-level install
git clone git@github.com:blakyris/claude-typescript-skill.git .claude/skills/typescript
```

That's it. Claude Code will automatically discover and activate the skill when TypeScript topics come up.

---

## What's included

The `references/` directory contains the complete official TypeScript documentation, organized into 8 sections:

```
references/
├── 01-getting-started/      # TypeScript from scratch, 5-minute intros
├── 02-handbook/              # Core handbook (types, narrowing, generics, classes...)
├── 03-reference/             # Utility types, enums, decorators, JSX, and more
├── 04-modules-reference/     # Module system theory, ESM/CJS interop
├── 05-tutorials/             # DOM manipulation, Babel, migration guides
├── 06-declaration-files/     # Writing and publishing .d.ts files
├── 07-javascript/            # JS interop, type-checking JS, JSDoc
└── 08-project-configuration/ # tsconfig.json, compiler options, project references
```

---

## Topics covered

- **Type system fundamentals** — primitives, unions, intersections, literal types, narrowing, type guards
- **Generics** — constraints, inference, generic classes and interfaces
- **Advanced types** — conditional types, mapped types, template literal types, `keyof`, `typeof`, indexed access
- **Utility types** — `Partial`, `Required`, `Readonly`, `Pick`, `Omit`, `Record`, `Extract`, `Exclude`, and more
- **Functions & objects** — overloads, call signatures, index signatures, type predicates
- **Classes** — visibility modifiers, abstract classes, generics, `implements` vs `extends`
- **Modules** — ESM/CJS interop, module resolution, namespaces
- **Declaration files** — authoring, publishing, and consuming `.d.ts` files
- **Project configuration** — `tsconfig.json`, compiler options, project references, build tool integration
- **JavaScript interop** — type-checking JS files, JSDoc annotations, generating declarations from JS
- **Enums, decorators, JSX/TSX, mixins, iterators, symbols**



