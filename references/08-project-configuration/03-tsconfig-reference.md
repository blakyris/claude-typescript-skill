## Compiler Options

##### Top Level

1.  `files,`
2.  `extends,`
3.  `include,`
4.  `exclude and`
5.  `references`

#### `"compilerOptions"`

##### Type Checking

1.  `allowUnreachableCode,`
2.  `allowUnusedLabels,`
3.  `alwaysStrict,`
4.  `exactOptionalPropertyTypes,`
5.  `noFallthroughCasesInSwitch,`
6.  `noImplicitAny,`
7.  `noImplicitOverride,`
8.  `noImplicitReturns,`
9.  `noImplicitThis,`
10.  `noPropertyAccessFromIndexSignature,`
11.  `noUncheckedIndexedAccess,`
12.  `noUnusedLocals,`
13.  `noUnusedParameters,`
14.  `strict,`
15.  `strictBindCallApply,`
16.  `strictBuiltinIteratorReturn,`
17.  `strictFunctionTypes,`
18.  `strictNullChecks,`
19.  `strictPropertyInitialization and`
20.  `useUnknownInCatchVariables`

##### Modules

1.  `allowArbitraryExtensions,`
2.  `allowImportingTsExtensions,`
3.  `allowUmdGlobalAccess,`
4.  `baseUrl,`
5.  `customConditions,`
6.  `module,`
7.  `moduleResolution,`
8.  `moduleSuffixes,`
9.  `noResolve,`
10.  `noUncheckedSideEffectImports,`
11.  `paths,`
12.  `resolveJsonModule,`
13.  `resolvePackageJsonExports,`
14.  `resolvePackageJsonImports,`
15.  `rewriteRelativeImportExtensions,`
16.  `rootDir,`
17.  `rootDirs,`
18.  `typeRoots and`
19.  `types`

##### Emit

1.  `declaration,`
2.  `declarationDir,`
3.  `declarationMap,`
4.  `downlevelIteration,`
5.  `emitBOM,`
6.  `emitDeclarationOnly,`
7.  `importHelpers,`
8.  `inlineSourceMap,`
9.  `inlineSources,`
10.  `mapRoot,`
11.  `newLine,`
12.  `noEmit,`
13.  `noEmitHelpers,`
14.  `noEmitOnError,`
15.  `outDir,`
16.  `outFile,`
17.  `preserveConstEnums,`
18.  `removeComments,`
19.  `sourceMap,`
20.  `sourceRoot and`
21.  `stripInternal`

##### JavaScript Support

1.  `allowJs,`
2.  `checkJs and`
3.  `maxNodeModuleJsDepth`

##### Editor Support

1.  `disableSizeLimit and`
2.  `plugins`

##### Interop Constraints

1.  `allowSyntheticDefaultImports,`
2.  `erasableSyntaxOnly,`
3.  `esModuleInterop,`
4.  `forceConsistentCasingInFileNames,`
5.  `isolatedDeclarations,`
6.  `isolatedModules,`
7.  `preserveSymlinks and`
8.  `verbatimModuleSyntax`

##### Backwards Compatibility

1.  `charset,`
2.  `importsNotUsedAsValues,`
3.  `keyofStringsOnly,`
4.  `noImplicitUseStrict,`
5.  `noStrictGenericChecks,`
6.  `out,`
7.  `preserveValueImports,`
8.  `suppressExcessPropertyErrors and`
9.  `suppressImplicitAnyIndexErrors`

##### Language and Environment

1.  `emitDecoratorMetadata,`
2.  `experimentalDecorators,`
3.  `jsx,`
4.  `jsxFactory,`
5.  `jsxFragmentFactory,`
6.  `jsxImportSource,`
7.  `lib,`
8.  `libReplacement,`
9.  `moduleDetection,`
10.  `noLib,`
11.  `reactNamespace,`
12.  `target and`
13.  `useDefineForClassFields`

##### Compiler Diagnostics

1.  `diagnostics,`
2.  `explainFiles,`
3.  `extendedDiagnostics,`
4.  `generateCpuProfile,`
5.  `generateTrace,`
6.  `listEmittedFiles,`
7.  `listFiles,`
8.  `noCheck and`
9.  `traceResolution`

##### Projects

1.  `composite,`
2.  `disableReferencedProjectLoad,`
3.  `disableSolutionSearching,`
4.  `disableSourceOfProjectReferenceRedirect,`
5.  `incremental and`
6.  `tsBuildInfoFile`

##### Output Formatting

1.  `noErrorTruncation,`
2.  `preserveWatchOutput and`
3.  `pretty`

##### Completeness

1.  `skipDefaultLibCheck and`
2.  `skipLibCheck`

##### Command Line

##### Watch Options

1.  `assumeChangesOnlyAffectDirectDependencies`

#### `"watchOptions"`

##### watchOptions

1.  `watchFile,`
2.  `watchDirectory,`
3.  `fallbackPolling,`
4.  `synchronousWatchDirectory,`
5.  `excludeDirectories and`
6.  `excludeFiles`

#### `"typeAcquisition"`

##### typeAcquisition

1.  `enable,`
2.  `include,`
3.  `exclude and`
4.  `disableFilenameBasedTypeAcquisition`

### Root Fields

Starting up are the root options in the TSConfig - these options relate to how your TypeScript or JavaScript project is set up.

### # Files - `files`

Specifies an allowlist of files to include in the program. An error occurs if any of the files can’t be found.

```json
{
  "compilerOptions": {},
  "files": [
    "core.ts",
    "sys.ts",
    "types.ts",
    "scanner.ts",
    "parser.ts",
    "utilities.ts",
    "binder.ts",
    "checker.ts",
    "tsc.ts"
  ]
}
```

This is useful when you only have a small number of files and don’t need to use a glob to reference many files. If you need that then use `include`.

-   Default:
    
    `false`
    
-   Related:
    -   `include`
        
    -   `exclude`
        
-   Released:
    
    1.5
    

### # Extends - `extends`

The value of `extends` is a string which contains a path to another configuration file to inherit from. The path may use Node.js style resolution.

The configuration from the base file are loaded first, then overridden by those in the inheriting config file. All relative paths found in the configuration file will be resolved relative to the configuration file they originated in.

It’s worth noting that `files`, `include`, and `exclude` from the inheriting config file _overwrite_ those from the base config file, and that circularity between configuration files is not allowed.

Currently, the only top-level property that is excluded from inheritance is `references`.

##### Example

`configs/base.json`:

```json
{
  "compilerOptions": {
    "noImplicitAny": true,
    "strictNullChecks": true
  }
}
```

`tsconfig.json`:

```json
{
  "extends": "./configs/base",
  "files": ["main.ts", "supplemental.ts"]
}
```

`tsconfig.nostrictnull.json`:

```json
{
  "extends": "./tsconfig",
  "compilerOptions": {
    "strictNullChecks": false
  }
}
```

Properties with relative paths found in the configuration file, which aren’t excluded from inheritance, will be resolved relative to the configuration file they originated in.

-   Default:
    
    `false`
    
-   Released:
    
    2.1
    

### # Include - `include`

Specifies an array of filenames or patterns to include in the program. These filenames are resolved relative to the directory containing the `tsconfig.json` file.

```json
{
  "include": ["src/**/*", "tests/**/*"]
}
```

Which would include:

```
.
├── scripts                ⨯
│   ├── lint.ts            ⨯
│   ├── update_deps.ts     ⨯
│   └── utils.ts           ⨯
├── src                    ✓
│   ├── client             ✓
│   │    ├── index.ts      ✓
│   │    └── utils.ts      ✓
│   ├── server             ✓
│   │    └── index.ts      ✓
├── tests                  ✓
│   ├── app.test.ts        ✓
│   ├── utils.ts           ✓
│   └── tests.d.ts         ✓
├── package.json
├── tsconfig.json
└── yarn.lock
```

`include` and `exclude` support wildcard characters to make glob patterns:

-   `*` matches zero or more characters (excluding directory separators)
-   `?` matches any one character (excluding directory separators)
-   `**/` matches any directory nested to any level

If the last path segment in a pattern does not contain a file extension or wildcard character, then it is treated as a directory, and files with supported extensions inside that directory are included (e.g. `.ts`, `.tsx`, and `.d.ts` by default, with `.js` and `.jsx` if `allowJs` is set to true).

-   Default:
    
    `[]` if `files` is specified; `**/*` otherwise.
    
-   Related:
    -   `files`
        
    -   `exclude`
        
-   Released:
    
    2.0
    

### # Exclude - `exclude`

Specifies an array of filenames or patterns that should be skipped when resolving `include`.

**Important**: `exclude` _only_ changes which files are included as a result of the `include` setting. A file specified by `exclude` can still become part of your codebase due to an `import` statement in your code, a `types` inclusion, a `/// <reference` directive, or being specified in the `files` list.

It is not a mechanism that **prevents** a file from being included in the codebase - it simply changes what the `include` setting finds.

-   Default:
    
    node\_modules bower\_components jspm\_packages `outDir`
    
-   Related:
    -   `include`
        
    -   `files`
        
-   Released:
    
    2.0
    

### # References - `references`

Project references are a way to structure your TypeScript programs into smaller pieces. Using Project References can greatly improve build and editor interaction times, enforce logical separation between components, and organize your code in new and improved ways.

You can read more about how references works in the Project References section of the handbook