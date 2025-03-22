---
title: "Why I Made a Language to Be JavaScript's Nanny"
description: "Chicory is no Mary Poppins"
summary: "Typescript is not the destination, it's a milestone along the way to a safer Javascript with fewer footguns and more guardrails."
date: 2025-03-22T16:27:22+02:00
date: 2025-03-22T16:27:22+02:00
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

We love JavaScript. It's the lingua franca of the web, powering everything from interactive UIs to backend services. It's flexible, dynamic, and has an absolutely enormous ecosystem. But let's be honest, sometimes JavaScript feels less like a helpful tool and more like a wild child in need of supervision.

Like a rambunctious child left unsupervised, JavaScript has its… quirks. `null`, `undefined`, implicit globals, the mysteries of `this`, and the ever-present specter of runtime errors lurking in the shadows. TypeScript stepped in like a well-meaning oldest sibling, trying to instill some order and discipline. And it's done a remarkable job bringing type safety to the party.

But what if, instead of just adding rules *on top* of the existing structure, we could rebuild from the ground up? What if we could create a language that retains the *joy* of JavaScript – its expressiveness and ecosystem – but makes the parents feel a little more at ease about their progeny.

That's the idea behind **Chicory**, a new programming language I'm building to be JavaScript's nanny. Chicory is Mary Poppins meets Hindley-Milner, arriving with a spoonful of strongly-typed sugar and a firm but fair approach to language design.

**Chicory isn't just about web UIs. It's about bringing sanity and safety to the entire JavaScript ecosystem.** Here's how Chicory is aiming to be the nanny JavaScript desperately needs (if not the one it deserves):

* **"A Nanny Should Always Be Firm, But Kind": Strict Type Safety via Hindley-Milner Inference.** Chicory is built on a foundation of rock-solid type safety, powered by the elegance of Hindley-Milner type inference. This isn't just about catching errors at compile time – it's about *designing* a language where errors are harder to make in the first place. Less verbose type annotations, more robust code. It's practically magic… or, you know, good type theory.
* **"No More Naughty Corners!": Removing JavaScript Footguns.** Like a good nanny who sets clear boundaries, Chicory eliminates problematic JavaScript features. `null` and `undefined` are banished to the naughty step, replaced with a cleaner optional type system. `with`? Sent to bed without supper. Chicory aims to be carefully curated, keeping the good parts of JavaScript and leaving the Bad Parts™  out altogether.
* **"A Few of My Favorite Things": Familiar Syntax Plus Some New Tricks.** Chicory isn't just about what it *removes*. It’s also about what it *adds* to make your developer experience delightful. Think of it as adding a little "brown paper packages tied up with strings" to your coding day:
  * **Chicory looks like JSX:** It feels incredibly familiar to write Chicory because the syntax is nearly identical to JSX. Automatic type inference means you're not annotating everything. So there's barely anything to learn.
  * **Match Expressions:** "So long, farewell, auf wiedersehen, goodbye" to messy `if/else if` chains. Match expressions bring clarity and elegance to complex conditional logic.
  * **`if` as an Expression:** No more nested ternary operators. `if` is now an expression, making your code flow more naturally.
* **"Let's Start at the Very Beginning": Seamless JavaScript Interop.** Chicory understands that you can't just throw out the entire JavaScript ecosystem. That's why it’s designed with excellent interoperability in mind. **You can import existing JavaScript libraries and code directly into Chicory.** So, you can start using Chicory in your projects incrementally, leveraging the vast JS landscape while gradually adopting a safer and more robust language (you'll need to write binding annotations when importing into Chicory).
* **"Practically Perfect in Every Way": Compiles to JSX (and beyond).** Chicory's familiar syntax, interop story and the fact that it compiles to JSX make adoption easy. The fact that it provides runtime guarantees makes it simply supercalifragilisticexpialidocious.

Sound like your cup of ~~tea~~ ~~java~~ ~~coffee~~ _chicory_? Give a star and/or contribute at https://github.com/chicory-lang/compiler
