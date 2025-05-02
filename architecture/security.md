# Security Standards

## Authentication and Authorization

*   **Preferred Method:** OAuth 2.0 / OpenID Connect (OIDC).
    *   Experience with Auth0.
    *   Consider managed services like AWS Cognito or other identity providers.
*   **JSON Web Tokens (JWTs):** Can be considered for session management or inter-service communication, especially in microservice architectures. Ensure proper implementation (e.g., short expiry, secure signing keys, potentially refresh tokens).
*   **Authorization:** Implement Role-Based Access Control (RBAC) or attribute-based access control (ABAC) based on application needs. Enforce the principle of least privilege.

## Secrets Management

*   **Tool:** Use Doppler for managing all sensitive information (API keys, database credentials, certificates, etc.).
*   **Avoid:** Do not commit secrets directly into source control. Avoid storing secrets in plain text environment variables where possible; use injected secrets from Doppler.

## Data Encryption

*   **Encryption in Transit:** All network communication must use TLS 1.2 or higher.
*   **Encryption at Rest:**
    *   **Default:** Utilize built-in encryption features provided by the database (e.g., PostgreSQL TDE, AWS RDS encryption, DynamoDB encryption).
    *   **Requirement:** Confirm specific encryption requirements based on data sensitivity for each project. Consider application-level encryption or specific KMS usage if needed.

## CI/CD Security Scanning

Integrate automated security scanning into the CI/CD pipeline:

*   **Static Application Security Testing (SAST):** Scan source code for potential vulnerabilities.
*   **Software Composition Analysis (SCA):** Scan dependencies for known vulnerabilities (e.g., using `npm audit`, Snyk, or similar tools integrated into the pipeline).
*   **Dynamic Application Security Testing (DAST):** (Optional, depending on setup) Scan running applications in test environments.
*   **Secrets Scanning:** Integrate tools to prevent accidental commits of secrets.

## General Best Practices

*   **OWASP Top 10:** Adhere to principles and mitigations outlined in the latest OWASP Top 10 list.
*   **Input Validation:** Validate and sanitize all input from external sources (users, APIs, etc.) on the server-side.
*   **Rate Limiting:** Implement rate limiting on APIs and sensitive endpoints to prevent abuse and denial-of-service attacks.
*   **Principle of Least Privilege:** Grant users and services only the permissions necessary to perform their intended functions.
*   **Dependency Updates:** Regularly update dependencies to patch known vulnerabilities.

## API Security

*   **Authentication/Authorization:** Secure all API endpoints appropriately (see above).
*   **Input Validation:** Enforce strict input validation using schemas (e.g., JSON Schema, OpenAPI Specification validation).
*   **Rate Limiting:** Apply specific rate limits to API endpoints.
*   **HTTPS:** All API traffic must be over HTTPS (TLS).