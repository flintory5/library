# Languages and Frameworks

## Backend Development

### Preferred Languages

1.  **TypeScript (Node.js):** Primary choice for backend development.
2.  **JavaScript (Node.js):** Secondary choice if TypeScript is not feasible for a specific task.
3.  **Python:** Fallback option if neither TypeScript nor JavaScript are suitable.

### Preferred Frameworks/Libraries

*   **Node.js (TypeScript/JavaScript):** Express.js
*   **Python:** Flask

## Frontend Development

### Preferred Languages

*   **TypeScript:** Primary choice for frontend development.
*   **JavaScript:** Secondary choice.

### Preferred Frameworks/Libraries

1.  **Next.js:** Primary choice.
2.  **Vue.js:** Secondary choice.
3.  **React:** Tertiary choice.

## Databases

Database choice should be driven by the specific problem and data structure requirements.

*   **Relational:**
    *   PostgreSQL (Preferred)
    *   AWS Aurora
*   **Non-Relational (Key-Value/Document):**
    *   AWS DynamoDB
*   **Graph:**
    *   Neo4j

## Other Technologies

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