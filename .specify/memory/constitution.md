<!-- Sync Impact Report
Version: 1.0.0 (Initial Ratification)
Modified Principles: Established initial principles (TDD, Tech Stack, Clean Code, ADRs, Context7)
Added Sections: Technology Stack, Quality Gates
Templates requiring updates: ✅ None
-->
# AI Chatbot Constitution

## Core Principles

### I. Test-Driven Development (TDD)
**Write tests first.**
Adhere strictly to the TDD approach. Tests must be written and fail before implementation begins. This ensures testability and clear requirements.

### II. Modern Python Environment
**Use Python 3.14 with `uv`.**
The project is standardized on Python 3.14, utilizing the `uv` package manager for dependency management and virtual environments.

### III. Clean Code
**Keep code clean and easy to read.**
Code maintainability is paramount. Write code that is self-explanatory where possible, and easy for others to understand.

### IV. Architectural Decision Records (ADR)
**Document important decisions.**
Use ADRs to document significant architectural choices, ensuring context and rationale are preserved.

### V. Context7 First
**Use Context7 for documentation.**
Always use the Context7 MCP server tool to look up documentation before implementation. Specifically, before writing code for 'openai agents sdk', verify usage via Context7.

## Technology Stack

**Core**: Python 3.14 managed by `uv`.
**Chatbot Agent Code**: openai agents sdk.
**UI**: Streamlit (latest version).
**Testing**: pytest.
**Version Control**: git (track all project files).

## Quality Gates

**Testing**: All tests must pass (100% pass rate).
**Coverage**: At least 80% code coverage required.
**Validation**: No merge without passing tests and adequate coverage.

## Governance

**Supremacy**:
This constitution supersedes other project documents.

**Amendments**:
Changes require a Pull Request and consensus.

**Versioning**:
Follow semantic versioning (MAJOR.MINOR.PATCH).

**Compliance**:
All code and architectural changes must comply with these principles.

**Version**: 1.0.0 | **Ratified**: 2025-11-28 | **Last Amended**: 2025-11-28