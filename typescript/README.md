# Typescript Guidelines

This document covers the guidelines for best practices when using Typescript.

## Table of Contents-

- [1. Typings](#1-typings)
  - [1.1. Functions](#11-functions)
  - [1.2. Variables](#12-variables)
- [2. Naming Conventions](#2-naming-conventions)
- [3. Declaring Types](#3-declaring-types)
- [4. Exporting Types](#4-exporting-types)
- [5. Types to Avoid](#5-types-to-avoid)
- [6. Access Modifiers](#6-access-modifiers)
- [7. Readonly](#7-readonly)
- [8. Arrays](#8-arrays)
- [9. Enums](#9-enums)
- [10. Interfaces vs Types](#10-interfaces-vs-types)

## 1. Typings

When using typescript, always use typings for functions and variables. This is to ensure that we are using the correct types and to avoid any type errors.

### 1.1. Functions

- Functions should have a return type and a parameter type.
- The function signature should be properly defined in its type. If the function does not return anything, use `void` as the return type.

### 1.2. Variables

- Primitive variables need not have an explicitly defined type. The typescript compiler will infer the type automatically.
- If the variable is complex (non-primitive), the type should be defined explicitly.

### 2. Naming Conventions

Typescript shares the same [naming conventions](/general/README.md#2-naming-conventions) as Javascript.

### 3. Declaring Types

- Always declare types/interfaces in a separate file if they are being imported by multiple files.
- If the type is being used only in a single file, declare it in the same file at the top.

### 4. Exporting Types

Do not export types/functions unless you need to use them across multiple files.

### 5. Types to Avoid

- Avoid using `any` or 'Object' type as much as possible. If you are using `any` or `Object`, you are losing the benefits of using typescript.
- If you are using `any` in a function, you should be able to explain why you are using it. Prefer to use `unknown` when necessary.

### 6. Access Modifiers

Keep your code as strict as possible, so keep all functions and properties `private` unless they
have to be `protected` or `public`.

Explicitly define whether your `constructor` functions are for internal or external interfaces.

```ts
// bad
constructor() {
  //...
}
// good
public constructor() {
  //...
}
```

### 7. Readonly

In order to be as strict as possible, every property should be set to readonly unless it should be
writable.

### 8. Arrays

Always prefer `ReadonlyArray` over a regular `Array` unless it must be possible to modify the Array.

### 9. Enums

Prefer to use `const enum` over regular `enum` unless you need to use the enum at runtime.

### 10. Interfaces vs Types

- Types and interfaces are very similar, but they [serve different purposes](https://www.typescriptlang.org/play#example/types-vs-interfaces). Use `interfaces` for
defining objects and `types` for defining primitives, unions, and tuples.

- Prefer to use `interface` over `type` unless you need to use a union or tuple type.
