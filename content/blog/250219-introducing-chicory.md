---
title: "Remove Footguns, Add Guardrails"
description: "Replace Javascript"
summary: "Chicory is a new programming language that compiles to JavaScript, designed specifically for JS/TS developers to find familiar with the goal of removing common pitfalls ('footguns') like null/undefined while adding safety features such as static typing with automatic type-inference."
date: 2025-02-19T16:27:22+02:00
date: 2025-02-19T16:27:22+02:00
draft: false
# weight: 50
categories: []
tags: []
contributors: []
pinned: false
homepage: false
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  robots: "" # custom robot tags (optional)
---

There are a ton of ["compiles to JS"](https://github.com/jashkenas/coffeescript/wiki/List-of-languages-that-compile-to-JS) languages. Seriously, tons! So why bother with a new JS-like language? If you want to use a language you're familiar with and transpile to JS, Chicory is not for you. But if you're a JS/TS developer, then Chicory is aimed at you.

> Chicory removes footguns and adds guardrails

JS is great. But JS comes with a lot of baggage, and we can do better even with the same runtime. So how is Chicory better?

## Removes Footguns

The first thing Chicory does is removes footguns from JS (and TS). There is no `null`, `undefined` or `any`. There is no more type coercion, so there is also no more `===` equality check. Fortunately `===` has become pretty standard. But these issues are so embedded in JS-land that falsiness checks are routinely used to handle `null` and `undefined`. Of course, if your value happened to be set, but was `0` or `false`, you just fired a footgun.

JS can't destroy backwards compatibility. So it's nigh impossible to remove features from the language. In addition, the TC39 committee also means that the language tends to grow. So instead of having a well-designed language, JS (and TS) is growing into an ever large and increasingly complex language. And hey, there was a lot of room to grow from its humble beginnings.

Chicory's design is a work-in-progress. It's not production ready, and you can expect breaking changes. But the objective is for a small, well-designed and robust language rather than a language with every feature anyone can imagine.

## Adds Guardrails

The biggest change Chicory intends to bring to the table is static typing with automatic type-inference, so that type annotations are often not required. Static type checking means that will never have your code crash because you tried to index into `null` or `undefined`. If you've ever used ReScript, Rust, or Elm, Chicory brings that promise to a language that is extremely familiar to JS developers.

Along with static type-checking, Algebraic Data Types and pattern matching make for a pleasant developer experience. These are new introductions to a JS developer, but they are familiar enough in syntax that the shift from `switch` (or even `if`) to `match` should be an easy one.

## Conclusion

Typescript is easy to move to from JS and has, unsurprisingly seen wide adoption, but it doesn't have the guarantees that a static type system could offer. Rust has guarantees that we want in Chicory, but Rust is a big language with a steep learning curve. Elm has the guarantees we want and it's a small language, but it's a big jump for most JS developers. The ideal would be to write in a language that looks like it might be JS, but with the guardrails of Elm and Rust.

Chicory is a lot of promises right now: not the `async` kind. There's a lot of work to be done implementing and refining the grammar, the compiler, the type-checker, and all the tooling that surrounds it. And that's just to prove out the concept.

If you want to be involved, submit an issue or a PR! If your business wants to sponsor development, contact us.
