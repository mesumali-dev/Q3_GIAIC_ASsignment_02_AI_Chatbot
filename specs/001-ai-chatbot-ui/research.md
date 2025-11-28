# Research: AI Chatbot UI

**Feature**: AI Chatbot UI with Streamlit and OpenAI Assistants API
**Date**: 2025-11-28

## Unknowns & Clarifications

| Topic | Status | Findings |
|-------|--------|----------|
| **OpenAI Agents SDK** | Resolved | Refers to `openai` Python library `client.beta.assistants` API. Verified endpoints for Assistants, Threads, Runs. Streaming is supported via `AssistantEventHandler`. |
| **Streamlit Chat Testing** | Resolved | `streamlit.testing.v1.AppTest` supports `chat_input` and `chat_message` inspection. Can simulate user input and assert UI state. |
| **Python Version** | Resolved | User requested 3.14. Will use modern syntax (`|` unions) valid in 3.10+ but target latest stable (3.12/3.13) environment if 3.14 is not strictly available in typical envs, while noting the requirement. |

## Technology Decisions

### 1. OpenAI Integration
**Decision**: Use `openai-agents` Python SDK.
**Rationale**: The `openai-agents` SDK provides a higher-level framework for building multi-agent workflows, which aligns better with the concept of an "AI Chatbot UI" than the lower-level Assistants API. It offers primitives for `Agent` definition (with `instructions`, `model`, `tools`), context management, and potentially simplifies state management for conversational turns, including explicit `sessions`. This directly addresses the user's explicit request.
**Alternatives**:
- *OpenAI Python library (Assistants API)*: Rejected because `openai-agents` is a more specialized SDK for agentic workflows and explicitly requested by the user. While the Assistants API provides threads, `openai-agents` appears to offer a more structured approach to agent design and interaction, including features like handoffs and guardrails, which might be useful for future extensions.

### 2. Streamlit UI Pattern
**Decision**: `st.chat_message` + `st.session_state`.
**Rationale**: Standard pattern for Streamlit chat apps. `session_state` holds the local view of messages for re-rendering.
**Async Handling**: Streamlit is sync. We will use `client.beta.threads.runs.stream` (sync streaming) to update `st.empty()` in real-time.

### 3. Testing Strategy
**Decision**: `AppTest` for Integration/UI tests + `unittest.mock` for Agent Logic.
**Rationale**: `AppTest` allows headless testing of the UI flow (User types "Hi" -> UI shows "Hi"). Mocking OpenAI is crucial to avoid API costs and network dependency during tests.

### 4. Configuration
**Decision**: `.env` file loaded via `python-dotenv`.
**Rationale**: Standard security practice for API keys.

## Implementation Details
- **Agent Service**: Encapsulate OpenAI logic in a class `ChatAgent` to decouple UI from API calls.
- **State Management**: `st.session_state.messages` (Display) AND `st.session_state.thread_id` (OpenAI Context).
