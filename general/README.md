# General Coding Guidelines

This document covers the general coding guidelines

## Table of Contents

- [1. Code Syntax](#1-code-syntax)
- [2. Naming Conventions](#2-naming-conventions)
  - [2.1. English Language](#21-english-language)
  - [2.2. Casing](#22-casing)
    - [2.2.1. Classes, Interfaces, Types and Generics](#221-classes-interfaces-types-and-generics)
    - [2.2.2. Functions, properties, arguments and variables](#222-functions-properties-arguments-and-variables)
    - [2.2.3. Properties with a getter and/or setter](#223-properties-with-a-getter-andor-setter)
    - [2.2.4. Globally used constants](#224-globally-used-constants)
    - [2.2.5. Abbreviations and Acronyms](#225-abbreviations-and-acronyms)
  - [2.3. File names](#23-file-names)
    - [2.3.1. File extensions](#231-file-extensions)
    - [2.3.2. .js](#232-js)
    - [2.3.3. .ts](#233-ts)
    - [2.3.4. .jsx](#234-jsx)
    - [2.3.5. .tsx](#235-tsx)
    - [2.3.6. .vue](#236-vue)
  - [2.4. S-I-D](#24-s-i-d)
  - [2.5. Avoid contractions](#25-avoid-contractions)
  - [2.6. Avoid context duplication](#26-avoid-context-duplication)
  - [2.7. Reflect the expected result](#27-reflect-the-expected-result)
  - [2.8. Abbreviations](#28-abbreviations)
  - [2.9. A/HC/LC Pattern](#29-ahclc-pattern)
  - [2.10. Plural / Singular](#210-plural--singular)
    - [2.10.1. Classes, Interfaces, Types and Enums](#2101-classes-interfaces-types-and-enums)
    - [2.10.2. Arrays](#2102-arrays)
    - [2.10.3. Folders](#2103-folders)
    - [2.10.4. Functions](#2104-functions)
    - [2.10.5. Classes, variables, properties, etc](#2105-classes-variables-properties-etc)
    - [2.10.6. Getters and setters](#2106-getters-and-setters)
    - [2.10.7. Booleans](#2107-booleans)
    - [2.10.8. Handlers and callbacks](#2108-handlers-and-callbacks)
    - [2.10.9. Always Affirmative](#2109-always-affirmative)
    - [2.10.10. Prefixes](#21010-prefixes)
    - [2.10.11. TypeScript Generics](#21011-typescript-generics)
    - [2.10.12. Interfaces and type aliases](#21012-interfaces-and-type-aliases)
- [3. Refactoring](#3-refactoring)
- [4. Coding](#4-coding)
  - [4.1. Functions](#41-functions)
    - [4.1.1. Pure functions](#411-pure-functions)
    - [4.1.2. Arrow functions](#412-arrow-functions)
  - [4.2. Separate Logic From Configuration](#42-separate-logic-from-configuration)
  - [4.3. Do not repeat yourself (DRY)](#43-do-not-repeat-yourself-dry)
  - [4.4. Do not use Magic Numbers](#44-do-not-use-magic-numbers)
  - [4.5. Default in a switch](#45-default-in-a-switch)
- [5. Formatting](#5-formatting)
- [6. Comments](#6-comments)
  - [6.1. Documentation comments](#61-documentation-comments)
  - [6.2. Regular Expressions](#62-regular-expressions)
  - [6.3. Commented out code](#63-commented-out-code)
  - [6.4. TODO](#64-todo)

## 1. Code Syntax

Use soft tabs with two spaces. You need to configure your editor for this.

**✅ Good:**

```js
const obj = {
  prop: "value",
  prop2: "value2",
  prop3: "value3",
}
```

```css
.foo {
  color: red;
}
```

```html
<div>
  <p>Hello World</p>
</div>
```

**❌ Bad:**

```js
const obj = {
    prop: "value",
    prop2: "value2",
    prop3: "value3",
}
```

```css
.foo {
    color: red;
}
```

```html
<div>
    <p>Hello World</p>
</div>
```

## 2. Naming Conventions

There are only two hard things in Computer Science: cache invalidation and naming things.

### 2.1. English Language

Always use `English` language when naming variables, functions, classes, etc. Make sure to use correct spelling and grammar.

```js
/* Bad */
const primerNombre = 'Gustavo'
const amigos = ['Kate', 'John']
/* Good */
const firstName = 'Gustavo'
const friends = ['Kate', 'John']
```

> Tip: Install a spell checker in your IDE to avoid typos.
> [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)

### 2.2. Casing

#### 2.2.1. Classes, Interfaces, Types and Generics

**PascalCase** Every individual word start with an upper case character, no underscores, no dashes.

#### 2.2.2. Functions, properties, arguments and variables

**camelCase** Starts with a lower case character, every following individual word start with an
upper case character, no underscores, no dashes.

#### 2.2.3. Properties with a getter and/or setter

When a private property has a public getter and/or setter, it's recommended to prefix the private
property with an underscore (`_`) to prevent naming conflicts.

> Note that prefixing a property name with an underscore is not allowed by the ESLint configuration.
> So in order to do this you need to disable this linting rule for this line.

```ts
// eslint-disable-next-line @typescript-eslint/naming-convention
private _isActive: boolean = false;
public get isActive(): boolean {
  return this._isActive;
}
```

#### 2.2.4. Globally used constants

**SNAKE_UPPER_CASE** Only use upper case characters, individual words must be separated with an
underscore.

#### 2.2.5. Abbreviations and Acronyms

Abbreviations and acronyms should be treated as words, which means only the first character will be
capitalized for camelCase and PascalCase.

```ts
const jsonApiSdkUrl = new JsonApiSdkUrl();
```

### 2.3. File names

If a file contains only one class, type or object, or when there is one main class, type or object
with some helper classes, types or objects, the file should have the same name, in `kebab-case`,
as that (main) class, type or object. If a file contains a class, but only an instance of that class
is exported, the file should have the same name as the class.

If a file holds multiple classes, types and/or objects, and they are all more or less equal in
importance, the file should have a name that describes all the classes, types and/or objects,
written in `kebab-case`.

#### 2.3.1. File extensions

#### 2.3.2. .js

> JavaScript only

#### 2.3.3. .ts

> TypeScript only

#### 2.3.4. .jsx

> JavaScript with JSX syntax. If a file has the `.jsx` extension, it must contain JSX code.

#### 2.3.5. .tsx

> TypeScript with JSX syntax. If a file has the `.tsx` extension, it must contain JSX code.

#### 2.3.6. .vue

> Vue single file components

### 2.4. S-I-D

A name must be _short_, _intuitive_ and _descriptive_:

- **Short**. A name must not take long to type and, therefore, remember;
- **Intuitive**. A name must read naturally, as close to the common speech as possible;
- **Descriptive**. A name must reflect what it does/possesses in the most efficient way.

```js
/* Bad */
const a = 5 // "a" could mean anything
const isPaginatable = a > 10 // "Paginatable" sounds extremely unnatural
const shouldPaginatize = a > 10 // Made up verbs are so much fun!
/* Good */
const postCount = 5
const hasPagination = postCount > 10
const shouldPaginate = postCount > 10 // alternatively
```

### 2.5. Avoid contractions

Do **NOT** use contractions. They contribute to nothing but decreased readability of the code. Finding a short, descriptive name may be hard, but contraction is not an excuse for not doing so.

```js
/* Bad */
const onItmClk = () => {}
/* Good */
const onItemClick = () => {}
```

### 2.6. Avoid context duplication

A name should not duplicate the context in which it is defined. Always remove the context from a name if that doesn't decrease its readability.

```js
class MenuItem {
  /* Method name duplicates the context (which is "MenuItem") */
  handleMenuItemClick = (event) => { ... }
  /* Reads nicely as `MenuItem.handleClick()` */
  handleClick = (event) => { ... }
}
```

### 2.7. Reflect the expected result

A name should reflect the expected result.

```jsx
/* Bad */
const isEnabled = itemCount > 3
return <Button disabled={!isEnabled} />
/* Good */
const isDisabled = itemCount <= 3
return <Button disabled={isDisabled} />
```

### 2.8. Abbreviations

Avoid them as a general rule. For example, `calculateOptimalValue()` is a better method name than
`calcOptVal()`. Being clear is more important than minimizing keystrokes. If you don't abbreviate,
developers won't have to remember whether you shortened a word like _qualified_ to `qual` or `qlfd`.

Abbreviations that are part of the HTML, CSS and/or JavaScript API are allowed, like:

- `url` for Uniform Resource Locator
- `uri` for Uniform Resource Identifier
- `src` for source
- `dom` for Document Object Model
- `img` for image

You should only use these abbreviations within the same context. So only use `img` if you refer to
an HTML Image Tag. (`<img>`)

We have standardized on a few abbreviations that are allowed to use:

- `app` for application
- `args` for arguments
- `auto` for automatic, as in `autoLayout`
- `bin` for binary
- `cta` for "Call to action". It's the part of the application that the user needs to click in order
  to take the action you want them to take.
- `fps` for frames per second
- `id` for identifier. Please note that 'd' should be written in lowercase when used in combination
  with another word, like `userId`.
- `info` for information, as in `GridRowInfo`
- `init` for initialize
- `lib` for library
- `max` for maximum, as in `maxHeight`
- `min` for minimum, as in `minWidth`
- `param` or `params` for parameter or parameters respectively
- `prop` or `props` for property or properties respectively
- `ref` for reference
- `temp` for temporary
- `ui` for user interface
- `util` or `utils` for utility or utilities, as in `StringUtils`

```js
// bad
prevButton.addEventListener('click', onPrevClick);
// good
previousButton.addEventListener('click', onPreviousClick);
```

```js
// bad
buttons.forEach((elm) => {
  //...
});
// better
buttons.forEach((element) => {
  // prettier should add brackets by default
  //...
});
// best
buttons.forEach((button) => {
  //...
});
```

### 2.9. A/HC/LC Pattern

There is a useful pattern to follow when naming functions:

```txt
prefix? + action (A) + high context (HC) + low context? (LC)
```

Take a look at how this pattern may be applied in the table below.

| Name                   | Prefix   | Action (A) | High context (HC) | Low context (LC) |
| ---------------------- | -------- | ---------- | ----------------- | ---------------- |
| `getUser`              |          | `get`      | `User`            |                  |
| `getUserMessages`      |          | `get`      | `User`            | `Messages`       |
| `handleClickOutside`   |          | `handle`   | `Click`           | `Outside`        |
| `shouldDisplayMessage` | `should` | `Display`  | `Message`         |                  |

> **Note:** The order of context affects the meaning of a variable. For example, `shouldUpdateComponent` means _you_ are about to update a component, while `shouldComponentUpdate` tells you that _component_ will update on itself, and you are but controlling when it should be updated.
> In other words, **high context emphasizes the meaning of a variable**.

### 2.10. Plural / Singular

#### 2.10.1. Classes, Interfaces, Types and Enums

Should always have a **singular** name, unless the object is only used to hold other values and
these other value are more important then the object itself, like `Props`, `Settings` or `Options`.
For example: `MyComponentProps`, `ProductionSettings` or `CalendarOptions`.

#### 2.10.2. Arrays

Or other kind of lists should have a plural name or end with `List` or `Collection`, like
`userList`.

#### 2.10.3. Folders

If a folder holds multiple files, but all related to one main type, it should have a singular name.
If it holds multiple main files of a type, it should have a plural name.

For example, the folder `page` contains a single page, with maybe some helper files. The folder
`pages` contains multiple pages.

#### 2.10.4. Functions

Prefer using a verb as a name to indicate it will do something. Like `render`, `open` or `getData`.

#### 2.10.5. Classes, variables, properties, etc

All non-functions should have a noun as a name, not a verb.

#### 2.10.6. Getters and setters

Although getters and setters are technically functions, they are used as if they are properties.
Therefore, their name should be a noun.

> Some frameworks support `computed` properties. They work like getters, so their name should be a
> noun as well.

#### 2.10.7. Booleans

Should start with `is`, `has`, `will` or `should`. Like `isValid` or `hasValues`.

#### 2.10.8. Handlers and callbacks

To indicate that a function or property is used as a callback or handler you can start the name with
`on`, like: `onClick`, `onLoadComplete`, `onResize`. Do not postfix the name with `handler` since
this is redundant when there is already an `on`.

Also note that a name of only `on` + `event name` might not be descriptive enough, depending on the
context. Using a more descriptive name is recommended.

```js
// bad
function complete() {
  //...
}
// bad
function handleComplete() {
  //...
}
// bad
function completeHander() {
  //...
}
// bad
function onCompleteHander() {
  //...
}
// good
function onComplete() {
  //...
}
// better
function onImageLoadComplete() {
  //...
}
```

#### 2.10.9. Always Affirmative

Avoid negations. _“Don’t ever not avoid negative logic”_. Prefer `isShown` over `isHidden` or
`isEnabled` over `isDisabled`. Do not use names like `notEditable`.

#### 2.10.10. Prefixes

We are not using prefixes for any name. Interfaces should follow the exact naming rules as classes,
and should not use the `I` or any other pre- or postfix.

#### 2.10.11. TypeScript Generics

If the usages of the generic is obvious, then naming that generic `T` is sufficient. As long as the
usage is clear you can use `U`, `V` etc. for any following generic.

If the usage is not obvious, you should use a more descriptive name. The same naming rules as for
classes will apply then.

```ts
// bad, prefix generics with T
class Response<TResponseData> {
  public data: TResponseData;
}
// good, use common abbreviations like T(ype), K(ey), V(alue), P(roperty) etc.
type Partial<T> = { [P in keyof T]?: T[P] };
// better, add more semantic context by extending the type
type ResponseData = Record<string, unknown>;
class Response<T extends ResponseData> {
  public data: T;
}
```

#### 2.10.12. Interfaces and type aliases

Depending on the use case there is a choice to implement an
[interface or type alias](https://github.com/typescript-cheatsheets/react#useful-table-for-types-vs-interfaces),
but be aware using types impacts
[compilation performance](https://ncjamieson.com/prefer-interfaces/).

```ts
// bad, you should not prefix interfaces with I
interface IResponse {
  //...
}
// bad, prefix types with T
type TResponse = {
  //...
};
// good, no prefix
interface Response {
  //...
}
// good, no prefix
type Response = {
  //...
};
```

## 3. Refactoring

- When refactoring code, leave the code better than you found it. Refactoring is a great opportunity to clean up code, without changing its behavior.

- Refactoring should only be done when the current functionality of the code works as expected. We must make sure that the new changes will not break the current functionality.

## 4. Coding

Every function or class should do **one thing** (and do it good). If it needs to do more than one
thing, split it up. Keep your files, classes and functions small. It’s okay to have a file with just
a single line. Modularity is key.

### 4.1. Functions

#### 4.1.1. Pure functions

Prefer writing pure functions, which means they do not manipulate the input arguments or
reference/manipulate global state. This makes your code better scalable and testable.

#### 4.1.2. Arrow functions

Prefer to use arrow functions when `this` should be bound to the outside context, and not to the
function itself. Arrow functions do not have their own context, so it will lexically go up a scope,
and use the value of `this` in the scope in which it was defined.

```js
const human = {
  message: 'Hello, World!',
  say() {
    setTimeout(() => {
      console.log(this.message);
    }, 1000);
  }
};
```

Also arrow functions are good in case of inline callbacks, which are most often found in `map`,
`filter`, `reduce` methods in order to improve code readability.

```js
[1, 2, 3]
  .map((x) => x * 5)
  .filter((x) => x < 10)
```

Prefer to use keyword `function` to create functions in cases:

- Function is at top level
- Function contains complex logic
- If there are no advantages to using the arrow function

Benefits of using the keyword `function` instead of arrow function:

- Function is not anonymous and has a name, so you get a better stack trace in case of an error
- [Hoisting](https://ui.dev/ultimate-guide-to-execution-contexts-hoisting-scopes-and-closures-in-javascript/)
  allows a function to be used before it is declared, so the order is not important

Example of creating a function using the `function` keyword:

```js
function secondsToDurationFormat(value: number): string {
  const days = Math.floor((value / 86400) % 365);
  const hours = Math.floor((value / 3600) % 24);
  const minutes = Math.floor((value / 60) % 60);
  const seconds = Math.floor(value % 60);
  return `P${days}DT${hours}H${minutes}M${seconds}S`;
};
```

### 4.2. Separate Logic From Configuration

Write code that is reusable, scalable and testable.

### 4.3. Do not repeat yourself (DRY)

- Do not copy code to another place.
- Avoid using the same string twice in a project.
- Move shared logic to a shared place.
- Make sure you do not have to adapt changes in multiple places.

### 4.4. Do not use Magic Numbers

See <https://en.wikipedia.org/wiki/Magic_number_(programming>)

### 4.5. Default in a switch

Every `switch` must have a `default`. If there is no need to handle the `default`, either throw an
`Error` or add a comment that the default is explicitly ignored.

```js
switch (state) {
  case 1: {
    // ....
    break;
  }
  case 2: {
    // ....
    break;
  }
  default: {
    throw new Error(`Unhandled value for state '${state}'`);
  }
}
```

_throw an error for things that should not occur_

```js
switch (state) {
  case 1: {
    // ....
    break;
  }
  case 2: {
    // ....
    break;
  }
  default: {
    // do nothing
    break;
  }
}
```

_add a comment that the default is explicit ignored_

Adding the comment makes it clear the developer did not forget to implement the default.

## 5. Formatting

All code within a project should have the same formatting. To enforce that we use
[Prettier](https://prettier.io/).

## 6. Comments

### 6.1. Documentation comments

Reconsider if your code really needs comments. Code should be self explaining. Don't add comments
that already tell what code does (by just repeating) or that are needed in order for the code to
make any sense. Code that needs such comments is probably bad. Instead, it is recommended to write
the intention of the code.

If you're new to a project or piece of code, when going over it, and trying to understand it, add
explanatory comments on things that took you some time to figure out.

If someone else asks during a code review why something is done a certain way, see if you can answer
it with a code comment instead of a reply in the review tool (when applicable).

### 6.2. Regular Expressions

Since regular expressions can be hard to read, they should have a comment that indicate what they
do. Especially when they are complex.

### 6.3. Commented out code

Don't leave commented out code into project. You can always find it back in the version control
system. If for some reason you want to keep commented out code in the project, add a comment
explaining why it is commented out.

### 6.4. TODO

If something needs to be changed or refactored later, add a `// TODO` comment to indicate what the
issue is.

> Tip: Install a TODO finder plugin in your IDE to find all TODOs.
> [TODO Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)
