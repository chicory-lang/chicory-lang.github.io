---
title: "Variables"
description: "Chicory's variable assignments and type system"
draft: false
weight: 100
toc: true
---

## Assignments

There are two ways to assign values to variables in Chicory:

```chicory
let varName     = "value"
const constName = "value"
```

Like Javascript, Chicory uses `let` to declare **mutable**  variables and `const` to declare **immutable** constants.


## Types

Chicory is statically typed and supports several built-in and composite data types.

### Primitive Types

*   `number`: Represents numerical values (integers and floating-point numbers).
    ```chicory
    let count: number = 123
    let price: number = 99.99
    ```
*   `string`: Represents textual data.
    ```chicory
    let greeting: string = "Hello, world!"
    ```
*   `boolean`: Represents truth values (`true` or `false`).
    ```chicory
    let isActive: boolean = true
    ```
*   `array`: Represents a list of values of the same type.
    ```chicory
    let numbers: array<number> = [1, 2, 3, 4, 5]
    let names: array<string> = ["Alice", "Bob", "Charlie"]
    ```

[TODO: Decide on this:]
The obvious missing type is `object`. Chicory does not have a built-in `object` type, because in Javascript, objects are arbitrary collections of key-value pairs that can change at runtime. Chicory uses `records` to represent objects (see below).

### Records

Record types are similar to objects or structs in other languages, defining a collection of named fields with associated types.

```chicory
type Person = {
    name: string,
    age: number,
    city: string,
}

let john: Person = { name: "John Doe", age: 30, city: "New York" }
```

*   Record types are defined using curly braces `{}`.
*   Each field within a record is defined as `fieldName: Type`.
*   Fields are separated by commas `,`.

### Tuples

Tuple types represent ordered lists of values, where each element can have a different type (in contrast to the array primitive).

```chicory
type Coordinates = [number, number]
type UserInfo = [string, number, boolean]

let point: Coordinates = [10, 20]
let user: UserInfo = ["Alice", 25, true]
```

*   Tuple types are defined using square brackets `[]`.
*   Each element in a tuple can be a `primitiveType` or a defined `IDENTIFIER` (type name).
*   Elements are separated by commas `,`.


### Algebraic Data Types (ADTs)

ADTs allow you to define types that can be one of several distinct options.

```chicory
type SimpleADT = Option1 | Option2

type MaybeName =
    | Name(string)
    | None

type Result =
    | Ok(SimpleADT)
    | Err({ error: string })
```

*   The list of options for an ADT is separated by `|`, including an optional leading `|`.
*   Options may be defined as:
    *   A simple identifier (e.g., `Option1`).
    *   An identifier with a parameter of a primitive type (e.g., `Name(string)`).
    *   An identifier with a parameter defined as a record-like structure (e.g., `Err({ error: string })`).
    *   The parameter can also be another defined type, including other ADTs (e.g., `Ok(SimpleADT)`).
