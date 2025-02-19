---
title: "Beyond TypeScript"
description: "The Search for a Successor"
summary: "Typescript is not the destination, it's a milestone along the way to a safer Javascript with fewer footguns and more guardrails."
date: 2025-02-18T16:27:22+02:00
date: 2025-02-18T16:27:22+02:00
draft: false
weight: 50
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

TypeScript has done wonders for the JavaScript ecosystem. Gradual typing meant that where I used to write buggy code and not know, now I often know. I started coding in the 90s, I remember when jquery hit the scene, and I remember when React was new and would never be able to compete with Angular (lol).

I loved using [Coffeescript](https://coffeescript.org/) after a foray into Rails. But it doesn't feel like new programming languages were popping up every other day back then, like it does today. Of late, I keep getting to look at new languages and think about all the tradeoffs that come with them. One of the obvious waves (of which React was certainly a part) is the rise of functional styles (and, with, composition over inheritance the decline of OOP).

So I've done a bit of Rust, and, on the frontend, been thoroughly enjoying [Rescript](https://rescript-lang.org/). And while TypeScript is a massive step forward, it's clear to me that it's not the _end_ of the road. There's still room – and, I'd argue, a _need_ – for alternative languages that compile to JavaScript. And crucially, coffeescript shows us that their value extends beyond immediate widespread adoption.

## The Limitations of TypeScript

TypeScript carries too much JS baggage. Here's why alternatives are _necessary_:

1.  **Gradual Typing:** TypeScript's greatest strength is also a potential weakness. Its "gradual typing" system allows you to mix typed and untyped code. This is fantastic for migrating existing projects, but it creates escape hatches. It's easy to end up with parts of your codebase that are effectively _untyped_, undermining the overall safety guarantees.

2.  **`null` and `undefined`:** The "billion-dollar mistake" persists in TypeScript. TypeScript tracks these, which is nice. But it adds `any` for some ungodly reason. Behind this problem is actually that JS panics. So what if we just _eliminated_ `throw` and `catch`, `null`, `undefined` and `any`, and replaced them with the safer `Option` and `Result` types, forcing explicit handling `None` and `Err`?

3.  **"Truthy" and "Falsy" Values:** JavaScript's loose equality and implicit type coercions (e.g., `0 == false`, `"" == false`) are notorious sources of bugs. Right now, my Typescript code is littered with checks for undefined and null because somehow a couple of function calls in, it could be either (or an actual value). At least the type-checker warns me, but it's still a pain.

4.  **Object References:** JavaScript's mutable objects and references can lead to subtle bugs, hard-to-track state changes, and surprising equality comparisons. TypeScript helps, but doesn't solve the problem.

## The Value of Niche Languages (Beyond Adoption): A Lesson from CoffeeScript

Even if a new language like doesn't immediately achieve TypeScript-level adoption, it still holds significant value. We can see a clear precedent for this in the history of JavaScript itself, specifically with the example of [**CoffeeScript**](https://coffeescript.org/).

CoffeeScript, while never becoming as ubiquitous as JavaScript, had a _profound_ impact on the evolution of the language. It introduced cleaner syntax, and new features like arrow functions, destructuring, better falsiness checks, and even classes and cool ideas like "nullish coalescing" and optional chaining. These ideas, initially niche within the CoffeeScript community, were eventually adopted into the ECMAScript standard (ES6 and beyond). CoffeeScript _pushed_ JavaScript forward, even though many developers never directly wrote CoffeeScript code.

The existence of [Elm](https://elm-lang.org/), [Purescript](https://www.purescript.org/), [Fable](https://fable.io/) (F#), [Rescript](https://rescript-lang.org/) (and [ReasonML](https://reasonml.github.io/)), and [Clojurescript]() (have I missed any?) shows that there's a hunger for a stricter kind of functional JS. The existence of [Civet](https://civet.dev/) shows that there's interest in experimenting with alternative syntax and new language features in js-land.

## Conclusion: A Call for Experimentation

Typescript showed us that js could be the foundation of an industrial-strength language (maybe). But there is clearly a desire for more than gradual types.

> Typescript is not the destination. It's a milestone along the way to a safer Javascript with fewer footguns and more guardrails

Two things that I've taken from Rust & Rescript that I would like to see in JS are `pattern matching` and `expressions`. So among other things, I would like to experiment with a language that supports `match` (and ADTs) and treats `if` and `match` as expressions. I intend to experiment with these ideas in a new language. For now, I'm calling it [**Chicory** (caffeine-free javascript: 🐣)](https://github.com/chicory-lang/chicory).
