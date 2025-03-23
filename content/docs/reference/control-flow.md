---
title: "Control Flow"
description: ""
draft: false
# weight: 100
toc: true
---

## If Expressions

Conditional execution is handled with `if` expressions. Unlike Javascript, `if` is an **expression**, not a statement. This means that it can be used in places where a value is expected, for example in variable assignments.

```chicory
const answer = if (airSpeedVelocity > 10 && unladen) {
    "African"
}
else if (unladen) {
    "European"
}
else {
    "I don't know that!"
}

const accent = if (hasGrail) "French" else "English"
```

*   The `condition` must be an expression that evaluates to a boolean value.
*   The `else` branch is optional, but in expression context, it's generally expected for a consistent type.
*   `else if` chains are created by nesting `if` expressions in the `else` branch.
*   The `{ ... }` block is optional and only required if the block contains multiple statements. This allows more terse ternary-like syntax.

## Match Expressions

`match` expressions are used for pattern matching, particularly useful for working with ADTs.

*   Patterns are tried in order. When a pattern matches, the corresponding expression is evaluated, and that's the result of the `match` expression.
* Patterns must be exhaustive, meaning they must cover all possible values of the expression.
* An identifier will destructure out the value in that place (implicitly matching anything).
* The `_` pattern matches anything, but is not destructured. It is useful for the default case.
* Like `if`, the `{ ... }` braces are optional and only required if the block contains multiple statements. But the `{ ... }` must evaluate to a value.

A simple case where pattern matching is useful is where primitve typed values can be matched against literals.

```chicory
let force = match (name) {
    "Skywalker" => Strong
    "Palpatine" => Strong
    _ => Weak
}
```

**Note**: You can't use a variable in a match expression because of the ambiguity of whether assignment or comparison is happening.

`match` takes an expression that may return an ADT. Using ADTs with pattern matching is a very productive (ahem) _pattern_, especially because it supports straightforward destructuring of values out of the ADT.

```chicory
// a is a `string[]`, indexing into it returns an `Option<string>`
let message = match (a[1000]) {
    Some("Hello") => "The value was 'Hello'"
    Some(v) => "The value was not 'Hello'"
    None => "There was no value"
}
```

Records and Tuples can be destructured (up to one level), including in ADTs.

```chicory
let something = match (["str", -1, true]) {
    [_, 1, _] => "foo"
    [x, y, false] => "bar"
    ["str", y, _] => "baz"
}
```

**Note**: Right now, using `match` on a record doesn't make a lot of sense in chicory, since there is no way to require specific keys to have specific values (destrucutring matches anything). This is an area for further exploration. 
