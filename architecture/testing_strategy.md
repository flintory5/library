# Testing Strategy

## Guiding Principles

*   **Test Pyramid:** Adhere to the testing pyramid principle: focus on a large base of fast unit tests, a smaller layer of integration tests, and a minimal set of end-to-end (E2E) tests.
*   **Test-Driven Development (TDD):** Write tests before writing the implementation code where practical. This helps ensure testability and drives design.
*   **Test Quality:** Aim for tests that are clear, concise, and provide meaningful feedback. Consider mutation testing to assess the effectiveness of the test suite in catching bugs.

## Test Types and Scope

*   **Unit Tests:** Test individual functions, methods, or classes in isolation. Dependencies should be mocked or stubbed.
*   **Integration Tests:** Test the interaction between multiple components or services (e.g., service layer interacting with a database repository, API endpoint calling a service). May involve real dependencies in controlled environments or sophisticated test doubles.
*   **End-to-End (E2E) Tests:** Test complete user flows through the application, typically via the UI or API layer. Use sparingly due to their slower execution time and brittleness.

## Preferred Frameworks and Libraries

*   **Backend (Node.js - TypeScript/JavaScript):** Mocha (with Chai for assertions and Sinon for mocks/stubs, or Jest as an alternative all-in-one).
*   **Backend (Python):** Pytest (with `pytest-mock` for mocking).
*   **Frontend/E2E:** Playwright.

## Code Coverage

*   **Target:** Aim for a minimum of 85% line coverage across unit and integration tests. Coverage is a guide, not a strict rule; focus on testing critical paths and complex logic effectively.

## Handling Dependencies

*   **Primary Approach:** Use mocking and stubbing extensively, especially for unit tests, to isolate the code under test.
*   **Integration Tests:** May use test containers (e.g., via Docker) or dedicated test databases/environments where necessary, but prefer mocks if interactions are simple.

## Test File Location

*   **Structure:** Place test files in a separate top-level `tests` or framework-specific directory (e.g., `__tests__` for Jest, potentially a `tests/` directory structured mirroring the `src/` directory for Pytest/Mocha).
*   **Naming:** Follow framework conventions (e.g., `*.test.ts`, `*.spec.ts`, `test_*.py`).