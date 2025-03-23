---
title: "Introducing Chicory"
description: "A type-safe, functional-friendly Javascript replacement"
draft: false
# weight: 100
toc: true
---

Meet **Chicory**, a programming language aiming to make web development safe and maintable while still being familiar. Chicory is designed with modern web development in mind. It draws inspiration from languages like TypeScript, Rust, and Elm, while forging its own path towards a better developer experience. Ideally, Chicory is just a better Javascript: the good parts with the warts burnt away.

## Why Chicory?

* **Static Typing:** Chicory's core principle is static typing. By catching errors *before* your code runs, your code will never crash.
* **Designed with the Web in Mind:** Chicory's built-in support for JSX makes building user interfaces feel natural. You write components using familiar syntax, boosted by the power and safety of a robust type system. While web development is the initial focus, Chicory's design isn't limited to the browser.
* **Functional Influences:** Chicory incorporates functional programming concepts, like Algebraic Data Types (ADTs) and pattern matching. These features enable more predictable and often more concise code.

## A Taste of Chicory

Here's a small example demonstrating JSX and pattern matching in Chicory, using Preact:

```chicory
import { useState } from "bindings/preact"

type User =
    | Anonymous
    | LoggedIn(string)

const App = () => {
    const [user, setUser] = useState(Anonymous)

    match (user) {
        Anonymous => <h1>{"Welcome, Guest!"}</h1>
        LoggedIn(name) => <h1>{"Hello, " + name + "!"}</h1>
    }
}

export { App }
```

This snippet showcases how Chicory combines familiar JSX with the power of pattern matching on ADTs. The `match` expression elegantly handles different user states, ensuring all possibilities are covered. This is just a glimpse of what's possible.

## Chicory vs. Other Languages

Chicory sits in an interesting space:

* **Chicory vs JavaScript:** Chicory's syntax is extremely similar to that of Javascript. But Chicory offers the significant advantage of compile-time type checking, aiming to eliminate many common runtime errors.
* **Chicory vs TypeScript:** Both add static typing to the JavaScript world, but Chicory is designed to be more strict, prioritizing strong type guarantees. TypeScript focuses on gradual adoption and close JavaScript interoperability. Any valid Javascript is valid Typescript. But Chicory, while similar, is a distinct language.
* **Chicory vs Elm:** Both prioritize safety through static typing. Elm achieves this with a purely functional approach. Chicory aims for similar safety but with a syntax that might feel more familiar to JavaScript/TypeScript developers.

## The Road Ahead

It's early days for Chicory. Right now, its development is focused on creating a solid foundation for building robust and maintainable web applications. If you want a reliable alternative to JS/TS that is equally approachable but comes with stronger guarantees, watch this space.
