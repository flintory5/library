# Architectural Patterns

## Preferred High-Level Patterns

*   **Microservices:** Decompose applications into small, independent services.
*   **Serverless:** Utilize managed services (like AWS Lambda, Fargate, SQS, DynamoDB) to minimize infrastructure management.
*   **Event-Driven Architecture (EDA):** Design systems around the production, detection, consumption of, and reaction to events.
*   **Model-View-Controller (MVC):** Can be useful for structuring applications, particularly web applications, but be mindful of potential complexity. Avoid overly rigid implementations.

## Discouraged Patterns

*   **Monoliths:** Avoid building large, single-deployment applications. Prefer decomposition from the start or have a clear strategy for future decomposition.

## Code Structure within Services/Applications

*   **Layered Architecture:** Structure code logically into distinct layers, typically:
    *   **Presentation/API Layer:** Handles incoming requests (HTTP, events) and outgoing responses.
    *   **Application/Service Layer:** Orchestrates use cases, contains application logic.
    *   **Domain Layer:** Contains core business logic, entities, value objects, and domain events.
    *   **Infrastructure Layer:** Deals with external concerns like databases, external APIs, message queues, file systems.

## Frontend State Management

State management choice depends on the complexity of the frontend application and the chosen framework. Start simple and introduce more complex solutions as needed.

*   **General Recommendation:** Consider framework-specific built-in solutions first.
*   **React/Next.js:**
    *   Start with React Context API for simple state sharing.
    *   For more complex global state, consider Zustand (simpler) or Redux Toolkit (more powerful, better for very large/complex state).
*   **Vue.js:**
    *   Use Pinia (current official recommendation).
    *   Vuex is an option for existing projects but Pinia is preferred for new ones.
*   **Emerging Patterns:** Keep an eye on Signals, which are gaining traction in various frameworks.