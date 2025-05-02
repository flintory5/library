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

## Contents

This directory contains detailed documentation on various aspects of our architecture and development practices.

### [Architectural Patterns](architectural_patterns.md)
Preferred high-level architectural patterns (e.g., microservices, serverless) and code structuring approaches.

### [Coding Style](coding_style.md)
Guidelines for code formatting, linting, naming conventions, and commenting.

### [Deployment](deployment.md)
Standards for CI/CD, infrastructure management (IaC), deployment targets, and monitoring.

### [Languages and Frameworks](languages_frameworks.md)
Preferred programming languages, frameworks, databases, and other core technologies.

### [Security](security.md)
Requirements for authentication, authorization, secrets management, encryption, and secure coding practices.

### [Testing Strategy](testing_strategy.md)
Approach to unit, integration, and E2E testing, including preferred tools and coverage expectations.