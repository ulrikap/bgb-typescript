---
theme: seriph
layout: cover
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: Brain Gains Bonanza - Typescript
mdc: true
---

# Typescript Super Bonanza

---

# Why use Typescript?

Some of my reasons
<v-clicks>

- Typescript introduces order in an otherwise large and dangerous world of untyped javascript.
- It does not exist at runtime, which means that there is no performance overhead (except when building)
- Allows for better cooperation and allows developers to express intent more clearly with their work
- Improved developer experience

</v-clicks>

---

# What is Typescript?

Typescript is a superset of Javascript. This means that any valid Javascript is valid Typescript.

It is a structural type system

```ts
// A structural type system means that any type that can match the structure of another type will be considered valid
type NOK = string;
type SEK = string;

const myFunction = (arg: NOK) => arg;

const nok: NOK = "string";
const sek: SEK = "string";

// Both are valid!
myFunction(sek);
myFunction(nok);
```

<v-click>

If a type is shaped like a duck, it's a duck. <br/>

</v-click>

<v-click>

If a goose has all the same attributes as a duck, then it also is a duck.

</v-click>

<v-click>

<img src="https://static-00.iconduck.com/assets.00/duck-emoji-1831x2048-uk40l929.png" alt="A duck" style="width:40px;"/>

</v-click>

---

# Basic syntax

A little overview

```ts {1-7|9-11|12-13|15-17|18-24}
// basic types
number
string
boolean
null
undefined
void

// these can all be defined as array types by simply adding a []
number[]

// tuples are arrays with known members
[number, number]

// Defines the shape of any type
type t = string

// Defines the shape of an object
interface t {
  name: string
}
```

---

# Basic syntax

Some operators

```ts {1-3|4-9|10-12}
// | pipe operator, used for creating unions

type MyUnion = "Ulrik" | "Palmstrøm"; // values will be either 'Ulrik' or 'Palmstrøm'

// & ampersand operator, used for creating intersection types

type MyInvalidIntersection = "Ulrik" & "Palmstrøm"; // not valid, cannot intersect these two types

type MyValidIntersection = { id: string } & { name: string }; // { id: string; name: string }

// function types
type MyFunction = (argument: string) => number;
```

These can be combined to create pretty powerful types when it comes to managing code complexity

Speaking about complexity ...

---

# Advanced syntax

Some typescript features can be pretty mind boggling to understand

```ts {1-2|4-9|10-21}
// type assertions
const test = "Ulrik" as unknown as number; // should be illegal, but its allowed. This string is now a number

// satisfies and "as const" operator
const array = [
  "daily banking",
  "cards",
  "mortgages",
] as const satisfies readonly string[];

// template literal types, this one is kinda neat. You can define the structure of a string

type Url = `https://${string}.${string}`;

const url1: Url = "https://google.com";

const url2: Url = "test"; // Error: Type 'test' is not assignable to type 'https://${string}.${string}'.
```

---

# Advanced syntax

```ts {1-10|11-16|17-25}
// keyof and lookup types
type MyTest = {
  keyOne: 1;
  keytwo: 1;
  keyThree: 1;
  keyFour: 1;
};
type Test = keyof MyTest; // keyOne | keytwo | keyThree | keyFour

// typeof operator - pluck the type from a value
const myNiceObject = {
  id: 123,
  name: "Ulrik",
};
const SomeType = typeof myNiceObject;

// Overwriting global namespaces
declare global {
  namespace NodeJS {
    interface ProcessEnv {
      MY_SECRET_ENV_VARIABLE: string;
    }
  }
}
```

---
transition: slide-up
level: 2
---

# Generics

Keep type safety, but introduce flexibility

```ts {1-2|4-5|6-9|11-13}
const testFunction = (arg) => arg; // Input and output will be typed as any, as the function has no knowledge of the type
testFunction("my string"); // Type returns as any

const testFunctionWithGeneric = <T>(arg: T): T => arg; // We now preserve type safety!
testFunctionWithGeneric("my string"); // Type returns as "my string"

// conditional types
type MyType = 1 | 2 | 3 extends 1 ? 1 : never; // will return never, why?
type MyType<T> = T extends 1 ? T : never; // will return 1 if called as MyType<1 | 2 | 3>, why?

// mapped types
type Readonly<T> = { readonly [K in keyof T]: T[K] };
```

---

# Let's do some challenges!

### Find a partner (or two)

### Clone this repo

https://github.com/type-challenges/type-challenges

### From root, run

- `nvm install 18`
- `nvm use 18`

(install pnpm if you don't have it: `npm install -g pnpm`)

- `pnpm install`
- `pnpm generate`

and then ...

---

# Challenge 1

---

# Challenge 2

---

# Challenge 3

---

# Challenge 4

---

# Challenge 5
