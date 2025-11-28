# Tasks: AI Chatbot UI

**Feature**: `001-ai-chatbot-ui`
**Status**: In Progress

## Phase 1: Setup
**Goal**: Initialize project structure and dependencies.

- [ ] T001 Create project directories `src/` and `tests/`
- [ ] T002 Create `requirements.txt` with `streamlit`, `openai-agents`, `python-dotenv`, `pytest`
- [ ] T003 Create `.env.example` with placeholder `OPENAI_API_KEY`
- [ ] T004 Create `.gitignore` excluding `.env` and `__pycache__`

## Phase 2: Foundational
**Goal**: Implement core backend logic and data structures (Blocking prerequisites).

- [ ] T005 Implement `Message` data model (dataclass) and `ChatAgent` class skeleton in `src/agent.py`
- [ ] T006 Create `tests/test_agent.py` with unit tests for `ChatAgent` initialization (mocking `openai`)

## Phase 3: User Story 1 - Core Chat Interaction (P1)
**Goal**: User can send a message and receive a response.
**Independent Test**: Launch app, type "Hello", verify response appears.

- [ ] T007 [US1] Implement `ChatAgent.send_message` in `src/agent.py` using `openai-agents` SDK
- [ ] T008 [US1] Create `src/app.py` with basic Streamlit layout (Title, Chat Input)
- [ ] T009 [US1] Integrate `ChatAgent` in `src/app.py` to handle user input and display AI response
- [ ] T010 [US1] Create `tests/test_app.py` and add test case for basic message flow using `AppTest`

## Phase 4: User Story 2 - Conversation History Persistence (P1)
**Goal**: Chat history remains visible across UI re-renders.
**Independent Test**: Send 2+ messages; verify all remain visible in correct order.

- [ ] T011 [US2] Implement `st.session_state` initialization for `messages` in `src/app.py`
- [ ] T012 [US2] Update `src/app.py` to render all messages from `st.session_state` on every script rerun
- [ ] T013 [US2] Update `tests/test_app.py` to verify message history persistence after interaction

## Phase 5: User Story 3 - Input Validation & Stability (P2)
**Goal**: Handle invalid inputs and errors gracefully.
**Independent Test**: Send empty message (no action); Simulate network error (see error message).

- [ ] T014 [US3] Add client-side validation in `src/app.py` to ignore empty or whitespace-only inputs
- [ ] T015 [US3] Add try/except blocks in `src/app.py` around `agent.send_message` to handle network errors
- [ ] T016 [US3] Add test cases in `tests/test_app.py` for empty input and mocked API failure

## Phase 6: User Story 4 - Extended Features: Personality & Controls (P3)
**Goal**: User can clear chat and change AI personality.
**Independent Test**: Click "Clear", history vanishes. Change personality, response style changes.

- [ ] T017 [US4] Implement `ChatAgent.clear_session` in `src/agent.py`
- [ ] T018 [US4] Add "Clear Chat" button to `src/app.py` sidebar and connect to state clearing logic
- [ ] T019 [US4] Add "Personality" selector to `src/app.py` sidebar and pass instruction to `ChatAgent`
- [ ] T020 [US4] Add test cases in `tests/test_app.py` for "Clear Chat" and personality switching functionality

## Phase 7: Polish
**Goal**: Final code quality checks and documentation.

- [ ] T021 Run full regression suite (`pytest`) and fix any linting issues
- [ ] T022 Update `README.md` with setup and usage instructions

## Dependencies

1. **Setup** (Phase 1) → **Foundational** (Phase 2)
2. **Foundational** → **US1** (Phase 3)
3. **US1** → **US2** (Phase 4) *Note: US2 is tight with US1, but can be refined after basic send/receive works.*
4. **US2** → **US3** (Phase 5) & **US4** (Phase 6)

## Implementation Strategy

- **MVP**: Complete Phases 1-4 (Setup + Core Chat + History). This delivers a working chatbot.
- **Robustness**: Add Phase 5 (Validation/Error Handling).
- **Bonus**: Add Phase 6 (Features) last.
