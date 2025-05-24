# Biome Formatter & Linter: General Guide

Biome is a modern tool for formatting, linting, and organizing code in JavaScript, TypeScript, JSON, and more. It helps keep codebases clean, consistent, and easy to read by automatically enforcing style and quality rules.

## Index
- [Biome Formatter & Linter: General Guide](#biome-formatter--linter-general-guide)
  - [Index](#index)
  - [Why Use Biome?](#why-use-biome)
  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Biome Usage Overview](#biome-usage-overview)
    - [JavaScript Formatter Options](#javascript-formatter-options)
    - [JSON Formatter Options](#json-formatter-options)
  - [More information](#more-information)

## Why Use Biome?

- ✨ Keeps code style consistent across teams and projects
- 🔍 Reduces code review friction
- 📖 Makes code easier to read and maintain
- 🛠️ Works with JavaScript, TypeScript, JSON, and more

## Installation

To install Biome, run:
```powershell
npm install --save-dev --save-exact @biomejs/biome
```
- This pins the exact version for consistency across your team.
- You can also use [standalone executables](https://biomejs.dev/guides/manual-installation) if you don't want to use Node.js.

## Configuration

To set up Biome, create a `biome.json` file at the root of your project. This file holds all your configuration options for formatting, linting, and organizing imports.

To generate a config file, run:
```powershell
npx @biomejs/biome init
```
- You can add the `--jsonc` flag to the init command if you want your config file to support comments (the file will be named `biome.jsonc`). This is useful for adding explanations or notes directly in your configuration.

Example `biome.json`:
```json
{
  "$schema": "https://biomejs.dev/schemas/1.9.4/schema.json",
  "formatter": { "enabled": true },
  "linter": { "enabled": true, "rules": { "recommended": true } },
  "javascript": {
    "formatter": {
      "quoteStyle": "double",
      "arrowParentheses": "always",
      "trailingCommas": "all",
      "bracketSpacing": true,
      "semicolons": "always",
      "indentWidth": 4
    }
  },
  "json": {
    "formatter": {
      "trailingCommas": "none",
      "indentStyle": "space",
      "indentWidth": 4
    }
  }
}
```

Adjust the options to match your team's style preferences. You can set different rules for JavaScript, JSON, and other supported languages.

Add Biome scripts to your `package.json` for easy formatting and linting:
```json
"scripts": {
  "lint": "biome lint .",
  "format": "biome format ."
}
```

Use the Biome VS Code extension for real-time feedback and auto-formatting:
- 💻 Install the [Biome VS Code extension](https://marketplace.visualstudio.com/items?itemName=biomejs.biome) from the VS Code Marketplace for instant feedback and auto-formatting as you type or save files.
- ⚡ The extension will automatically detect your `biome.json` and apply your settings.
- 🏃‍♂️ You can run formatting and linting commands directly from the command palette or on file save.

> [!TIP]
> The VS Code extension makes it easy to keep your codebase consistent and error-free, with instant feedback as you work.

## Biome Usage Overview

This section provides practical guidance on how to use Biome for formatting, linting, and maintaining code quality in your projects. You'll find explanations and examples for the most important configuration options, making it easy to apply Biome's features to your workflow.

Biome is a modern tool for formatting, linting, and organizing code in JavaScript, TypeScript, JSON, and more. It helps keep codebases clean, consistent, and easy to read by automatically enforcing style and quality rules.

### JavaScript Formatter Options

quoteStyle
- **Explanation:** Choose the type of quotes for strings.
- **Possible values:**
  - `"double"`: Use double quotes for all strings.
    - Example:
      ```js
      "Hello, world!"
      ```
  - `"single"`: Use single quotes for all strings.
    - Example:
      ```js
      'Hello, world!'
      ```

quoteProperties
- **Explanation:** Decide when to quote object keys.
- **Possible values:**
  - `"asNeeded"`: Only quote keys if required by JavaScript (e.g., if the key has spaces or special characters).
    - Example:
      ```js
      { name: "John" }
      ```
  - `"always"`: Always quote all object keys.
    - Example:
      ```js
      { "name": "John" }
      ```
  - `"consistent"`: If any key needs quotes, quote all keys.
    - Example:
      ```js
      { "name": "John", "age": 30 }
      ```
  - `"preserve"`: Keep the original quoting style from your code.
    - Example:
      ```js
      { name: "John" } // or { "name": "John" }
      ```

arrowParentheses
- **Explanation:** Control if arrow functions always use parentheses.
- **Possible values:**
  - `"always"`: Always use parentheses, even for a single argument.
    - Example:
      ```js
      (x) => x
      ```
  - `"asNeeded"`: Omit parentheses when there is only one argument.
    - Example:
      ```js
      x => x
      ```

trailingCommas
- **Explanation:** Add trailing commas in arrays, objects, etc.
- **Possible values:**
  - `"all"`: Add trailing commas everywhere possible.
    - Example:
      ```js
      [1, 2, 3,]
      ```
  - `"es5"`: Add trailing commas only where valid in ES5 (objects, arrays, not function params).
    - Example:
      ```js
      [1, 2, 3]
      ```
  - `"none"`: Never add trailing commas.
    - Example:
      ```js
      [1, 2, 3]
      ```

bracketSpacing
- **Explanation:** Add or remove spaces inside object brackets.
- **Possible values:**
  - `true`: Add spaces.
    - Example:
      ```js
      { name: "John" }
      ```
  - `false`: No spaces.
    - Example:
      ```js
      {name:"John"}
      ```

semicolons
- **Explanation:** Control when semicolons are added.
- **Possible values:**
  - `"always"`: Always add semicolons.
    - Example:
      ```js
      let x = 1;
      ```
  - `"asNeeded"`: Only add semicolons when required by JavaScript.
    - Example:
      ```js
      let x = 1
      ```
  - `"never"`: Never add semicolons.
    - Example:
      ```js
      let x = 1
      ```

indentWidth
- **Explanation:** Set the number of spaces or tabs for indentation.
- **Possible values:**
  - `2`: Two spaces for each indentation level.
    - Example:
      ```js
      function foo() {
        return 42;
      }
      ```
  - `4`: Four spaces for each indentation level.
    - Example:
      ```js
      function foo() {
          return 42;
      }
      ```

bracketSameLine
- **Explanation:** Place closing brackets on the same line as the last property or on a new line.
- **Possible values:**
  - `true`: Closing bracket on the same line.
    - Example:
      ```jsx
      <Component
        prop1="foo"
        prop2="bar" />
      ```
  - `false`: Closing bracket on a new line.
    - Example:
      ```jsx
      <Component
        prop1="foo"
        prop2="bar"
      />
      ```

indentStyle
- **Explanation:** Use spaces or tabs for indentation.
- **Possible values:**
  - `"space"`: Use spaces for indentation.
    - Example:
      ```js
      // Four spaces for each indent
      function greet() {
          console.log("Hello");
      }
      ```
  - `"tab"`: Use tab characters for indentation.
    - Example:
      ```js
      // Tab character for each indent
      function greet() {
      	console.log("Hello");
      }
      ```

lineEnding
- **Explanation:** Choose the type of line ending for files.
- **Possible values:**
  - `"lf"`: Use Unix-style line endings (\n).
    - Example: Line ends with \n
  - `"crlf"`: Use Windows-style line endings (\r\n).
    - Example: Line ends with \r\n

formatWithErrors
- **Explanation:** Format code even if there are syntax errors.
- **Possible values:**
  - `true`: Biome will format code even if there are syntax errors.
  - `false`: Biome will not format code if there are syntax errors.

lineWidth
- **Explanation:** Set the maximum number of characters per line before wrapping.
- **Possible values:**
  - `80`: Maximum number of characters per line before wrapping.
  - `100`: Maximum number of characters per line before wrapping.

### JSON Formatter Options

trailingCommas
- **Explanation:** Controls whether trailing commas are added in arrays and objects in JSON files.
- **Possible values:**
  - `"none"`: No trailing commas are added.
    - Example:
      ```json
      { "a": 1, "b": 2 }
      ```

indentStyle
- **Explanation:** Sets the type of indentation for JSON files.
- **Possible values:**
  - `"space"`: Use spaces for indentation.
    - Example:
      ```json
      {
          "a": 1
      }
      ```
  - `"tab"`: Use tab characters for indentation.
    - Example:
      ```json
      {
      	"a": 1
      }
      ```

indentWidth
- **Explanation:** Sets the number of spaces or tabs for each indentation level in JSON files.
- **Possible values:**
  - `2`: Two spaces per indent level.
    - Example:
      ```json
      {
        "a": 1
      }
      ```
  - `4`: Four spaces per indent level.
    - Example:
      ```json
      {
          "a": 1
      }
      ```

lineEnding
- **Explanation:** Sets the type of line ending for JSON files.
- **Possible values:**
  - `"lf"`: Use Unix-style line endings (\n).
    - Example: Line ends with \n
  - `"crlf"`: Use Windows-style line endings (\r\n).
    - Example: Line ends with \r\n

## More information

For more information, see the [official Biome documentation](https://biomejs.dev/)
