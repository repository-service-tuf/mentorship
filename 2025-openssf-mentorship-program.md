# 2025 OpenSSF Mentorship Program

Dates: June 2-August 29

# Repository Service for TUF (RSTUF)

## Purpose

The purpose of this project is to enhance the ([Repository Service for TUF RSTUF](https://openssf.org/projects/repository-service-for-tuf/)) implementation by tackling critical areas that would significantly improve its functionality, scalability, and ease of adoption. RSTUF is designed to manage content distribution efficiently using the TUF ([The Update Framework](https://theupdateframework.io/)), but it currently has areas where improvements in delegation flexibility, performance, testing, and documentation are needed. This project will allow RSTUF to handle larger and more complex scenarios, while providing an improved experience for both developers and adopters.

## Goal

**Enable succinct hash-bin delegations within custom delegations**: Enhance the flexibility of RSTUF’s delegation model to allow for more fine-grained delegation control.

**Improve performance on the online role bumping process**: Optimize the process of updating large numbers of delegated roles to improve scalability, especially in environments where there are many roles to manage.

**Enhance the developer experience by improving functional tests**: Improve the effectiveness, reusability, and performance of the functional tests that ensure RSTUF’s features work across releases.

**Improve documentation to facilitate easier adoption**: Enhance the user-facing documentation to make it clearer, more comprehensive, and more accessible for new adopters, thus accelerating the onboarding process.

## Desired Outcomes & Deliverables (up to 3 mentees)

1. **New feature: Support Succinct hash-bin delegations (TAP 15\) on existing custom delegations**

    **Context**: Currently, RSTUF supports two delegation designs:

   * **Succinct hash-bin delegations**: These are based on a fixed size and create a delegation from the `Targets` role to bins-xxxx (e.g., `bins-00`, `bins-01`, etc.). This allows for organizing and storing artifacts in a way that aligns with a hash-based path, which is particularly useful for large artifact collections.

   * **Custom delegations**: Users can define custom roles like `Targets → project-a`, `Targets → project-b`, etc., allowing for more control over the path and the artifacts it handles.

   **Project goal**: The project aims to enable **custom delegations** to also support **succinct hash-bin delegation**. This would allow users to define roles such as `project-a-bins-xxxx`, where the user can create custom paths but still benefit from the hash-bin organization for better scalability and organization.

      **Deliverables**:

   * A new feature that adds succinct hash-bin delegation capabilities to custom roles.

   * Clear documentation and usage examples for this new functionality.

   * Tests to ensure the new delegation model works smoothly with custom roles.

---

2. **Performance improvement: Improve performance on bumping online roles**

    **Context**: RSTUF uses **online keys** stored in services like Key Management System (KMS) or Vault to sign metadata, primarily for the **Timestamp** and **Snapshot** roles. Additionally, when using succinct hash-bin delegations, the number of roles can become extremely large — in some cases, reaching up to **16k** or more roles. When these roles need to be updated simultaneously, performance can degrade.

   The issue arises because updating a large number of roles concurrently can overwhelm the system, resulting in slow updates and potential failures. This is particularly problematic in systems that rely on rapid updates, such as security updates or automated build systems.

   **Project goal**: This project aims to enhance the performance of RSTUF by optimizing the bumping process, ensuring that updates to a large number of delegated roles can occur more efficiently, without sacrificing security or reliability.

    **Deliverables**:

   * Performance improvements to reduce the overhead of updating a large number of roles.

   * Benchmark tests to compare the performance before and after optimizations.

   * Documentation of the improvements made and how they impact system performance.

---

3. **Improve development experience: Functional Tests**

   **Context**: **Functional Tests** are critical to ensuring that RSTUF's features work as expected across different versions. However, these tests can often be slow, hard to maintain, or difficult to scale, especially as the codebase grows.

   One of the key pain points is the **reusability** of tests. Often, developers find themselves rewriting similar test code or struggling with tests that are difficult to maintain due to their complexity.

   **Project goal**: This project aims to [refactor the functional tests in RSTUF](https://repository-service-tuf.readthedocs.io/en/stable/devel/development.html#functional-tests-using-behavior-development-driven-bdd) to increase reusability, improve performance, and make the tests easier to maintain. The ultimate goal is to improve the development experience for both contributors and users of RSTUF by providing better, more reliable tests.

    **Deliverables**:

   * Refactor existing functional tests to improve their performance and maintainability.

   * Enhance reusability by reducing redundancy in test code.

   * Implement modern testing techniques (e.g., BDD, GitHub Actions) for better usability and integration.

---

4. **RSTUF Docs: Improvement for adopters**

   **Context**: The documentation for [RSTUF is hosted on **ReadTheDocs**](https://repository-service-tuf.readthedocs.io/), but as the project has evolved, the documentation has not kept up with the changes, particularly in areas that are most relevant to adopters (i.e., new users trying to integrate RSTUF into their systems).

    A common complaint from adopters is the steep learning curve in understanding how to set up and configure RSTUF, as well as how to troubleshoot common issues. Improving the documentation will not only help new users adopt RSTUF more quickly but also provide a better overall user experience.

   **Project goal**: The aim of this project is to improve RSTUF’s documentation by adding clear, concise instructions and examples for new adopters, as well as better explanations of key concepts and workflows.

    **Deliverables**:

   * Improved user guides, setup instructions, and troubleshooting tips.

   * Example use cases and tutorials that cover real-world scenarios.

   * A more structured documentation site that helps users find information quickly.

## Relevant Knowledge & Recommended Skills

1. **New feature: Support Succinct hash-bin delegations**

* **Skills**: Testing frameworks, Containerization (Docker) Delegation systems.
* **Technologies**: Python, Celery, FastAPI. 

2. **Performance improvement: Improve performance on bumping online roles**

* **Skills**: Algorithm optimization, AsyncIO, Profiling tools, Benchmarking, Performance tuning.
* **Technologies**: Python

3. **Improve development experience: Functional Tests**

* **Skills**: BDD (Behavior-Driven Development), Containerization, Test-driven development (TDD).
* **Technologies**: Python, Shell Scripting, GitHub Actions,.

4. **RSTUF Docs: Improvement for adopters**

* **Skills**: English, Documentation best practices, Writing clear instructions, User-focused documentation.
* **Technologies**: Sphinx, Readthedocs, Python

## Mentors

Kairo de Araujo ([kairo@dearaujo.nl](mailto:kairo@dearaujo.nl))
