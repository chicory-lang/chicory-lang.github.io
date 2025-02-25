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

```chicory
let force = match (name) {
    "Skywalker" => Strong,
    "Palpatine" => Strong,
    _ => Weak
}

// a is a `string[]`, indexing into it returns an `Option<string>`
let message = match (a[1000]) {
    Some("Hello") => "The value was 'Hello'",
    Some(v) => v,
    None => "There was no value"
}
```

*   The `expression` is evaluated, and its value is matched against the patterns.
*   Patterns are tried in order. When a pattern matches, the corresponding expression is evaluated, and that's the result of the `match` expression.
*   Patterns must be exhaustive, meaning they must cover all possible values of the expression.
*   The `_` pattern matches anything, and is useful for a default case.
*   Like `if`, the `{ ... }` block is optional and only required if the block contains multiple statements.
*   Records and Tuples can be destructured (up to one level), including in ADTs
*   Primitve typed values can be matched against literals (but not against identifiers, because of the ambiguity of whether assignment or comparison is happening)
*   **Match Patterns**:
    *   `IDENTIFIER`: Matches a specific ADT option without parameters (Bare ADT Match Pattern).
    *   `IDENTIFIER(IDENTIFIER)`: Matches an ADT option with a parameter, binding the parameter to the identifier (ADT with Parameter Match Pattern).
    *   `IDENTIFIER(literal)`: Matches an ADT option with a parameter that is a specific literal value (ADT with Literal Match Pattern).
    *   `_`: Wildcard pattern, matches anything (Wildcard Match Pattern).
    *   `literal`: Matches a specific literal value (Literal Match Pattern).
