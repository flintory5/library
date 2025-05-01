# Coding Style

## Guiding Principle

**Simplicity and Readability:** Code should be written in a clear, straightforward manner. Prioritize making the code easy for others (and your future self) to understand quickly. Avoid unnecessary complexity or overly clever solutions.

## Linting and Formatting

Consistent code style is enforced using standard tooling.

*   **TypeScript/JavaScript:**
    *   **Formatter:** Prettier (Use default settings or establish a `.prettierrc` file).
    *   **Linter:** ESLint (Configure with recommended rulesets like `eslint:recommended`, `plugin:@typescript-eslint/recommended`, and integrate with Prettier using `eslint-config-prettier`).
*   **Python:**
    *   **Formatter:** Black (Use default settings).
    *   **Linter:** Flake8 (Use default settings or establish a `.flake8` configuration file).

## Naming Conventions

*   **Variables & Functions:**
    *   TypeScript/JavaScript: `camelCase`
    *   Python: `snake_case`
*   **Classes & Types:**
    *   TypeScript/JavaScript/Python: `PascalCase`
*   **Constants:**
    *   TypeScript/JavaScript/Python: `UPPER_SNAKE_CASE`

## Comments and Documentation

*   **TypeScript:** Use TSDoc comments (`/** ... */`) for documenting exported functions, classes, methods, and types. Add inline comments (`//`) for complex or non-obvious logic blocks.
*   **JavaScript:** Use JSDoc comments (`/** ... */`) similarly to TSDoc.
*   **Python:** Use standard docstrings (`""" ... """`) for modules, classes, functions, and methods. Use inline comments (`#`) for complex logic.
