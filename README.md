# Biome Formatter & Linter: General Guide

Biome is a modern tool for formatting, linting, and organizing code in JavaScript, TypeScript, JSON, and more. It helps keep codebases clean, consistent, and easy to read by automatically enforcing style and quality rules.

---

## JavaScript Formatter Options (with Examples)

quoteStyle
- **Explanation:** Choose the type of quotes for strings.
- **Possible values:**
  - "double": Use double quotes for all strings.
    - Example: "Hello, world!"
  - "single": Use single quotes for all strings.
    - Example: 'Hello, world!'

quoteProperties
- **Explanation:** Decide when to quote object keys.
- **Possible values:**
  - "asNeeded": Only quote keys if required by JavaScript (e.g., if the key has spaces or special characters).
    - Example: { name: "John" }
  - "always": Always quote all object keys.
    - Example: { "name": "John" }
  - "consistent": If any key needs quotes, quote all keys.
    - Example: { "name": "John", "age": 30 }
  - "preserve": Keep the original quoting style from your code.
    - Example: { name: "John" } or { "name": "John" } (as in your code)

arrowParentheses
- **Explanation:** Control if arrow functions always use parentheses.
- **Possible values:**
  - "always": Always use parentheses, even for a single argument.
    - Example: (x) => x
  - "asNeeded": Omit parentheses when there is only one argument.
    - Example: x => x

trailingCommas
- **Explanation:** Add trailing commas in arrays, objects, etc.
- **Possible values:**
  - "all": Add trailing commas everywhere possible.
    - Example: [1, 2, 3,]
  - "es5": Add trailing commas only where valid in ES5 (objects, arrays, not function params).
    - Example: [1, 2, 3]
  - "none": Never add trailing commas.
    - Example: [1, 2, 3]

bracketSpacing
- **Explanation:** Add or remove spaces inside object brackets.
- **Possible values:**
  - true: Add spaces.
    - Example: { name: "John" }
  - false: No spaces.
    - Example: {name:"John"}

semicolons
- **Explanation:** Control when semicolons are added.
- **Possible values:**
  - "always": Always add semicolons.
    - Example: let x = 1;
  - "asNeeded": Only add semicolons when required by JavaScript.
    - Example: let x = 1
  - "never": Never add semicolons.
    - Example: let x = 1

indentWidth
- **Explanation:** Set the number of spaces or tabs for indentation.
- **Possible values:**
  - 2: Two spaces for each indentation level.
    - Example:
      function foo() {
        return 42;
      }
  - 4: Four spaces for each indentation level.
    - Example:
        function foo() {
            return 42;
        }

bracketSameLine
- **Explanation:** Place closing brackets on the same line as the last property or on a new line.
- **Possible values:**
  - true: Closing bracket on the same line.
    - Example:
      <Component
        prop1="foo"
        prop2="bar" />
  - false: Closing bracket on a new line.
    - Example:
      <Component
        prop1="foo"
        prop2="bar"
      />

indentStyle
- **Explanation:** Use spaces or tabs for indentation.
- **Possible values:**
  - "space": Use spaces for indentation.
    - Example: (4 spaces for each indent)
  - "tab": Use tab characters for indentation.
    - Example: (tab character for each indent)

lineEnding
- **Explanation:** Choose the type of line ending for files.
- **Possible values:**
  - "lf": Use Unix-style line endings (\n).
    - Example: Line ends with \n
  - "crlf": Use Windows-style line endings (\r\n).
    - Example: Line ends with \r\n

formatWithErrors
- **Explanation:** Format code even if there are syntax errors.
- **Possible values:**
  - true: Biome will format code even if there are syntax errors.
  - false: Biome will not format code if there are syntax errors.

lineWidth
- **Explanation:** Set the maximum number of characters per line before wrapping.
- **Possible values:**
  - 80: Maximum number of characters per line before wrapping.
  - 100: Maximum number of characters per line before wrapping.

---

## JSON Formatter Options

trailingCommas
- **Explanation:** Controls whether trailing commas are added in arrays and objects in JSON files.
- **Possible values:**
  - "none": No trailing commas are added.
    - Example: { "a": 1, "b": 2 }

indentStyle
- **Explanation:** Sets the type of indentation for JSON files.
- **Possible values:**
  - "space": Use spaces for indentation.
    - Example:
      {
          "a": 1
      }
  - "tab": Use tab characters for indentation.
    - Example:
      {
      	"a": 1
      }

indentWidth
- **Explanation:** Sets the number of spaces or tabs for each indentation level in JSON files.
- **Possible values:**
  - 2: Two spaces per indent level.
    - Example:
      {
        "a": 1
      }
  - 4: Four spaces per indent level.
    - Example:
      {
          "a": 1
      }

lineEnding
- **Explanation:** Sets the type of line ending for JSON files.
- **Possible values:**
  - "lf": Use Unix-style line endings (\n).
    - Example: Line ends with \n
  - "crlf": Use Windows-style line endings (\r\n).
    - Example: Line ends with \r\n

---

## Linting & Organizing Imports
- Linter: Biome can enforce code quality and style rules, such as preventing redeclaration of variables, enforcing recommended best practices, and more.
- Organize Imports: Biome can automatically sort and organize your import statements.

---

## Why Use Biome?
- Keeps code style consistent across teams and projects
- Reduces code review friction
- Makes code easier to read and maintain
- Works with JavaScript, TypeScript, JSON, and more

---

> **Tip:** You can configure Biome in a `biome.json` file at the root of your project. Adjust the options to match your team's style preferences!
