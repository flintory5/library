# Architecture Decision Records (ADRs) and Standards

This directory contains the documented architectural standards, patterns, and technology choices for projects.

## Purpose

The primary goal of these documents is to provide a clear, consistent, and maintainable guide for designing and building software. They serve as a reference for developers and AI assistants (like GitHub Copilot) to ensure alignment with established best practices and preferences.

## How to Use These Standards

1.  **Consult Before Designing:** Before starting new features or services, review the relevant documents (e.g., `architectural_patterns.md`, `languages_frameworks.md`) to understand the preferred approaches.
2.  **Follow During Development:** Adhere to the guidelines outlined in `coding_style.md`, `security.md`, and `testing_strategy.md` during implementation.
3.  **Reference for Tooling:** Use the specified tools and configurations for linting, formatting, testing, deployment (`deployment.md`), and security (`security.md`).
4.  **AI Assistant Guidance:** These documents provide context for AI assistants. Refer the assistant to these files when asking for design or implementation help (e.g., "Based on the standards in the `/architecture` directory, design...").
5.  **Keep Updated:** These are living documents. As technology evolves or decisions change, update the relevant files. Consider using a lightweight ADR (Architecture Decision Record) process for significant changes.

---

## Architectural Patterns

*   **Microservices:** Decompose applications into small, independent services.
*   **Serverless:** Utilize managed services (like AWS Lambda, Fargate, SQS, DynamoDB) to minimize infrastructure management.
*   **Event-Driven Architecture (EDA):** Design systems around the production, detection, consumption of, and reaction to events.
*   **Model-View-Controller (MVC):** Can be useful for structuring applications, particularly web applications, but be mindful of potential complexity. Avoid overly rigid implementations.

### Discouraged Patterns

*   **Monoliths:** Avoid building large, single-deployment applications. Prefer decomposition from the start or have a clear strategy for future decomposition.

### Code Structure within Services/Applications

*   **Layered Architecture:** Structure code logically into distinct layers, typically:
    *   **Presentation/API Layer:** Handles incoming requests (HTTP, events) and outgoing responses.
    *   **Application/Service Layer:** Orchestrates use cases, contains application logic.
    *   **Domain Layer:** Contains core business logic, entities, value objects, and domain events.
    *   **Infrastructure Layer:** Deals with external concerns like databases, external APIs, message queues, file systems.

### Frontend State Management

State management choice depends on the complexity of the frontend application and the chosen framework. Start simple and introduce more complex solutions as needed.

*   **General Recommendation:** Consider framework-specific built-in solutions first.
*   **React/Next.js:**
    *   Start with React Context API for simple state sharing.
    *   For more complex global state, consider Zustand (simpler) or Redux Toolkit (more powerful, better for very large/complex state).
*   **Vue.js:**
    *   Use Pinia (current official recommendation).
    *   Vuex is an option for existing projects but Pinia is preferred for new ones.
*   **Emerging Patterns:** Keep an eye on Signals, which are gaining traction in various frameworks.

---

## Coding Style

### Guiding Principle

**Simplicity and Readability:** Code should be written in a clear, straightforward manner. Prioritize making the code easy for others (and your future self) to understand quickly. Avoid unnecessary complexity or overly clever solutions.

### Linting and Formatting

Consistent code style is enforced using standard tooling.

*   **TypeScript/JavaScript:**
    *   **Formatter:** Prettier (Use default settings or establish a `.prettierrc` file).
    *   **Linter:** ESLint (Configure with recommended rulesets like `eslint:recommended`, `plugin:@typescript-eslint/recommended`, and integrate with Prettier using `eslint-config-prettier`).
*   **Python:**
    *   **Formatter:** Black (Use default settings).
    *   **Linter:** Flake8 (Use default settings or establish a `.flake8` configuration file).

### Naming Conventions

*   **Variables & Functions:**
    *   TypeScript/JavaScript: `camelCase`
    *   Python: `snake_case`
*   **Classes & Types:**
    *   TypeScript/JavaScript/Python: `PascalCase`
*   **Constants:**
    *   TypeScript/JavaScript/Python: `UPPER_SNAKE_CASE`

### Comments and Documentation

*   **TypeScript:** Use TSDoc comments (`/** ... */`) for documenting exported functions, classes, methods, and types. Add inline comments (`//`) for complex or non-obvious logic blocks.
*   **JavaScript:** Use JSDoc comments (`/** ... */`) similarly to TSDoc.
*   **Python:** Use standard docstrings (`""" ... """`) for modules, classes, functions, and methods. Use inline comments (`#`) for complex logic.

---

## Deployment Strategy

### CI/CD

*   **Preferred Tools:**
    *   GitHub Actions (if repository is on GitHub).
    *   GitLab CI (if repository is on GitLab).
*   **Pipeline Goals:** Automate testing, building, and deployment processes.

### Deployment Targets

*   **Primary:** AWS Lambda for serverless functions.
*   **Containers:**
    *   AWS ECS (Preferred for simplicity/cost).
    *   AWS EKS (If Kubernetes is required).
*   **Cloud Provider:** AWS is the preferred cloud environment.

### Deployment Strategies

*   **Default:** Blue/Green deployments.
*   **Flexibility:** The optimal strategy may depend on the specific release and application context. Confirm the strategy during release planning.
*   **Other Considerations:** Canary releases or Rolling updates might be suitable in specific scenarios.

### Infrastructure Management

*   **Approach:** Infrastructure as Code (IaC) is mandatory.
*   **Preferred Tools:**
    1.  Terraform
    2.  AWS CloudFormation (if Terraform is not suitable or for specific AWS integrations).
    3.  Pulumi (Fallback option).
*   **Avoid:** Manual infrastructure setup through consoles or CLIs for production environments.

### Monitoring, Logging, and Alerting

*   **AWS Environments:** Utilize AWS CloudWatch (Logs, Metrics, Alarms).
*   **Other Environments:** Use Prometheus for metrics collection and Grafana for visualization and alerting.
*   **Error Tracking:** Consider dedicated error tracking services (e.g., Sentry) for application-level errors.

---

## Languages and Frameworks

### Backend Development

#### Preferred Languages

1.  **TypeScript (Node.js):** Primary choice for backend development.
2.  **JavaScript (Node.js):** Secondary choice if TypeScript is not feasible for a specific task.
3.  **Python:** Fallback option if neither TypeScript nor JavaScript are suitable.

#### Preferred Frameworks/Libraries

*   **Node.js (TypeScript/JavaScript):** Express.js
*   **Python:** Flask

### Frontend Development

#### Preferred Languages

*   **TypeScript:** Primary choice for frontend development.
*   **JavaScript:** Secondary choice.

#### Preferred Frameworks/Libraries

1.  **Next.js:** Primary choice.
2.  **Vue.js:** Secondary choice.
3.  **React:** Tertiary choice.

### Databases

Database choice should be driven by the specific problem and data structure requirements.

*   **Relational:**
    *   PostgreSQL (Preferred)
    *   AWS Aurora
*   **Non-Relational (Key-Value/Document):**
    *   AWS DynamoDB
*   **Graph:**
    *   Neo4j

### Other Technologies

*   **Message Queues:** AWS SQS
*   **Caching:** Redis
*   **Cloud Provider:** AWS
*   **Containerization:**
    *   AWS ECS (Elastic Container Service) - Preferred for simplicity and cost.
    *   AWS EKS (Elastic Kubernetes Service) - Use if Kubernetes orchestration is specifically required.
*   **API Styles:**
    *   GraphQL (Preferred)
    *   REST (Viable alternative, especially for simpler needs or cost considerations)
    *   **Note:** The best choice depends on the specific project scale and requirements. Please confirm during the design phase.

---

## Security Standards

### Authentication and Authorization

*   **Preferred Method:** OAuth 2.0 / OpenID Connect (OIDC).
    *   Experience with Auth0.
    *   Consider managed services like AWS Cognito or other identity providers.
*   **JSON Web Tokens (JWTs):** Can be considered for session management or inter-service communication, especially in microservice architectures. Ensure proper implementation (e.g., short expiry, secure signing keys, potentially refresh tokens).
*   **Authorization:** Implement Role-Based Access Control (RBAC) or attribute-based access control (ABAC) based on application needs. Enforce the principle of least privilege.

### Secrets Management

*   **Tool:** Use Doppler for managing all sensitive information (API keys, database credentials, certificates, etc.).
*   **Avoid:** Do not commit secrets directly into source control. Avoid storing secrets in plain text environment variables where possible; use injected secrets from Doppler.

### Data Encryption

*   **Encryption in Transit:** All network communication must use TLS 1.2 or higher.
*   **Encryption at Rest:**
    *   **Default:** Utilize built-in encryption features provided by the database (e.g., PostgreSQL TDE, AWS RDS encryption, DynamoDB encryption).
    *   **Requirement:** Confirm specific encryption requirements based on data sensitivity for each project. Consider application-level encryption or specific KMS usage if needed.

### CI/CD Security Scanning

Integrate automated security scanning into the CI/CD pipeline:

*   **Static Application Security Testing (SAST):** Scan source code for potential vulnerabilities.
*   **Software Composition Analysis (SCA):** Scan dependencies for known vulnerabilities (e.g., using `npm audit`, Snyk, or similar tools integrated into the pipeline).
*   **Dynamic Application Security Testing (DAST):** (Optional, depending on setup) Scan running applications in test environments.
*   **Secrets Scanning:** Integrate tools to prevent accidental commits of secrets.

### General Best Practices

*   **OWASP Top 10:** Adhere to principles and mitigations outlined in the latest OWASP Top 10 list.
*   **Input Validation:** Validate and sanitize all input from external sources (users, APIs, etc.) on the server-side.
*   **Rate Limiting:** Implement rate limiting on APIs and sensitive endpoints to prevent abuse and denial-of-service attacks.
*   **Principle of Least Privilege:** Grant users and services only the permissions necessary to perform their intended functions.
*   **Dependency Updates:** Regularly update dependencies to patch known vulnerabilities.

### API Security

*   **Authentication/Authorization:** Secure all API endpoints appropriately (see above).
*   **Input Validation:** Enforce strict input validation using schemas (e.g., JSON Schema, OpenAPI Specification validation).
*   **Rate Limiting:** Apply specific rate limits to API endpoints.
*   **HTTPS:** All API traffic must be over HTTPS (TLS).

---

## Testing Strategy

### Guiding Principles

*   **Test Pyramid:** Adhere to the testing pyramid principle: focus on a large base of fast unit tests, a smaller layer of integration tests, and a minimal set of end-to-end (E2E) tests.
*   **Test-Driven Development (TDD):** Write tests before writing the implementation code where practical. This helps ensure testability and drives design.
*   **Test Quality:** Aim for tests that are clear, concise, and provide meaningful feedback. Consider mutation testing to assess the effectiveness of the test suite in catching bugs.

### Test Types and Scope

*   **Unit Tests:** Test individual functions, methods, or classes in isolation. Dependencies should be mocked or stubbed.
*   **Integration Tests:** Test the interaction between multiple components or services (e.g., service layer interacting with a database repository, API endpoint calling a service). May involve real dependencies in controlled environments or sophisticated test doubles.
*   **End-to-End (E2E) Tests:** Test complete user flows through the application, typically via the UI or API layer. Use sparingly due to their slower execution time and brittleness.

### Preferred Frameworks and Libraries

*   **Backend (Node.js - TypeScript/JavaScript):** Mocha (with Chai for assertions and Sinon for mocks/stubs, or Jest as an alternative all-in-one).
*   **Backend (Python):** Pytest (with `pytest-mock` for mocking).
*   **Frontend/E2E:** Playwright.

### Code Coverage

*   **Target:** Aim for a minimum of 85% line coverage across unit and integration tests. Coverage is a guide, not a strict rule; focus on testing critical paths and complex logic effectively.

### Handling Dependencies

*   **Primary Approach:** Use mocking and stubbing extensively, especially for unit tests, to isolate the code under test.
*   **Integration Tests:** May use test containers (e.g., via Docker) or dedicated test databases/environments where necessary, but prefer mocks if interactions are simple.

### Test File Location

*   **Structure:** Place test files in a separate top-level `tests` or framework-specific directory (e.g., `__tests__` for Jest, potentially a `tests/` directory structured mirroring the `src/` directory for Pytest/Mocha).
*   **Naming:** Follow framework conventions (e.g., `*.test.ts`, `*.spec.ts`, `test_*.py`).
