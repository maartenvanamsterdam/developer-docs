# React Foundations

## [3 JSX Rules](https://react.dev/learn/writing-markup-with-jsx#the-rules-of-jsx) JavaScript XML and 1 Pro-Tip!

### 1. Return a Single Root Element

To return multiple elements from a component, wrap them with a single parent tag.

Example:

```
<div>
  <h1>Hello</h1>
  <p>World</p>
</div>
```

---

### 2. Close All Tags

JSX requires tags to be explicitly closed.

Examples:

- Self-closing tags:

  ```
  <img />
  ```

- Wrapping tags:

  ```
  <li>List item</li>
  ```

---

### 3. camelCase Most Things

JSX turns into JavaScript, and attributes written in JSX become keys of JavaScript objects.

Examples:

```
className
onClick
backgroundColor
```

Avoid:

- dashes in attribute names
- reserved words like `class`

---

### Pro-Tip: Use a JSX Converter

## [Converter](https://transform.tools/html-to-jsx)
