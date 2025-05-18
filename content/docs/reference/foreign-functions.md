---
title: "Foreign Function Interface (FFI)"
description: ""
draft: false
# weight: 100
toc: true
---

# Introduction

Chicory is designed to be a safe and maintainable language, but it also recognizes the need to interact with the vast ecosystem of existing JavaScript libraries and browser APIs. The Foreign Function Interface (FFI) is the mechanism that allows Chicory code to call JavaScript functions and access JavaScript objects in a type-safe way.

By defining clear type signatures for external JavaScript code, Chicory can ensure that these interactions uphold its safety guarantees, bridging Chicory's statically-typed world with the dynamic nature of JavaScript.

## Binding to Global Variables

Often, you'll need to interact with objects available in the global JavaScript scope, such as `window`, `document`, or `console` in a browser environment. Chicory uses the `global` keyword for this.

You declare the global variable and provide a type signature for the parts of it you intend to use, typically using a record type.

**Syntax:**

```chicory
global <globalName> as <TypeSignature>
```

**Example:**

To safely use `console.log` from Chicory, you can define its type:

```chicory
global console as {
  log: (string) => void,        // Log a string (console.log will only accept a single string if typed like this)
  warn: (T) => void             // Log any value (using generics)
}

// Now you can call it:
console.log("Hello from Chicory!")
console.warn(123)
console.warn("also accepts strings")
```

In this example:
*   `console` is the name of the global JavaScript object.
*   The `as` keyword is followed by a record type defining the expected shape of `console`.
*   `log: (string) => void` specifies that `console` has a `log` method which takes a `string` argument and returns nothing (`void`).
*   `warn: (T) => void` shows a generic function, indicating `console.warn` can take an argument of any type `T`.

## Binding to External Modules

To use functions or values exported from JavaScript modules (e.g., NPM packages), Chicory provides the `bind ... from` syntax. This is similar to ES6 imports.

**Syntax:**

```chicory
bind { <exportName> as <TypeSignature>, ... } from "<module-path>"
```

You can bind multiple exports from the same module within a single `bind` block.

**Example:**

Let's say you want to use the `useState` hook from React:

```chicory
bind {
  useState as (T) => [T, (T) => void]
} from "react"

// This makes `useState` available in your Chicory code
// with the specified type signature.
// const [count, setCount] = useState(0)
```

In this example:
*   `useState` is the name of the function being imported from the "preact/hooks" module.
*   `as (T) => [T, (T) => void]` defines the type of `useState`.
    *   It's a generic function taking an `initialState` of type `T`.
    *   It returns a tuple:
        1.  The current state, also of type `T`.
        2.  A setter function that takes a `newState` of type `T` and returns `void`.
*   `from "react"` specifies the module from which to import.
