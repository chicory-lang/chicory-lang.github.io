---
title: "JSX"
description: ""
draft: false
# weight: 100
toc: true
---

Chicory integrates JSX for declarative UI description.

```chicory
const MyComponent = ({name, count}) =>
  <div>
    <h1>{name}</h1>
    <p>Count: {(count).toString()}</p>
    <p>Double: {(count * 2).toString()}</p>
  </div>

<MyComponent name="Chicory" count={10} />
```

*   **JSX Elements**: Start with an opening tag `<TagName>` and end with a closing tag `</TagName>`. Self-closing tags are also supported `<TagName />`.
*   **JSX Attributes**:  Attributes are defined within the opening tag, like `name="Chicory"` or `count={10}`. Attribute values can be:
    *   Literal strings and numbers: `"value"` or `123`
    *   Expressions: `{if (true) "Yes" else "No"}`
*   **JSX Children**: Content within JSX tags can be:
    *   Plain Text
    *   Expressions
    *   Other JSX elements
* JSX expressions in Chicory compile to JSX. This allows Chicory to be used for frameworks like React, Preact, and Solid.
