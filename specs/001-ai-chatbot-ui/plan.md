# Implementation Plan: AI Chatbot UI

**Branch**: `001-ai-chatbot-ui` | **Date**: 2025-11-28 | **Spec**: [specs/001-ai-chatbot-ui/spec.md](specs/001-ai-chatbot-ui/spec.md)
**Input**: Feature specification from `/specs/001-ai-chatbot-ui/spec.md`

**Note**: This template is filled in by the `/sp.plan` command. See `.specify/templates/commands/plan.md` for the execution workflow.

## Summary

The goal is to build a Streamlit-based AI Chatbot UI that interfaces with the OpenAI Assistants API. The system will allow users to have persistent conversations with an AI agent. Key features include a chat interface (input/output), history persistence within the session, and robust error handling. The implementation will follow TDD and use the OpenAI Python SDK (Beta Assistants API).

## Technical Context

**Language/Version**: Python 3.14 (using `|` union types, running on latest stable compatible env)
**Primary Dependencies**: `streamlit`, `openai-agents`, `python-dotenv`
**Storage**: In-memory (`st.session_state`) for chat history; OpenAI Cloud for Thread state.
**Testing**: `pytest`, `streamlit.testing` (AppTest)
**Target Platform**: Local Web Browser (Streamlit Server)
**Project Type**: Web Application (Streamlit)
**Performance Goals**: Response latency < 2s (time to first token), UI render < 100ms
**Constraints**: Must handle API rate limits and network errors gracefully.
**Scale/Scope**: Single-user session focus (prototype/assignment level).

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- **TDD**: Plan explicitly includes writing `AppTest` cases before implementation. ✅
- **Modern Python**: Uses Python 3.14 syntax conventions. ✅
- **Clean Code**: Will separate Agent logic (`src/agent.py`) from UI (`src/app.py`). ✅
- **ADR**: Will document "Streamlit vs Custom React" if significant, but Streamlit is a requirement. N/A for now.
- **Context7**: Documentation for OpenAI and Streamlit validated via Context7. ✅

## Project Structure

### Documentation (this feature)

```text
specs/001-ai-chatbot-ui/
├── plan.md              # This file
├── research.md          # Phase 0 output
├── data-model.md        # Phase 1 output
├── quickstart.md        # Phase 1 output
├── contracts/           # Phase 1 output
└── tasks.md             # Phase 2 output
```

### Source Code (repository root)

```text
src/
├── app.py               # Main Streamlit application entry point
└── agent.py             # ChatAgent service wrapping OpenAI SDK

tests/
├── test_app.py          # Integration/UI tests using AppTest
└── test_agent.py        # Unit tests for ChatAgent (mocked API)

.env                     # Configuration (not committed)
requirements.txt         # Dependencies
```

**Structure Decision**: Single project structure with `src/` and `tests/` at root. This is standard for simple Streamlit applications.

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| None | | |
