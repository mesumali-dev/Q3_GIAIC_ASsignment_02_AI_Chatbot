# Data Model: AI Chatbot UI

## Entities

### 1. Message
Represents a single unit of communication in the chat history.

| Field | Type | Description | Validation |
|-------|------|-------------|------------|
| `role` | `str` | Sender of the message. | Must be "user" or "assistant". |
| `content` | `str` | Text content of the message. | Cannot be empty or whitespace only. |
| `id` | `str` | Unique ID (optional, mostly for internal tracking if needed). | UUID v4. |

### 2. ChatSession (Runtime State)
Managed within `st.session_state`.

| Field | Type | Description |
|-------|------|-------------|
| `messages` | `list[Message]` | Local history of the conversation for display. |
| `session_id` | `str | None` | OpenAI Agents SDK Session ID. |
| `agent_id` | `str | None` | ID of the active OpenAI Agents SDK Agent. |

## Configuration (Environment)

| Variable | Type | Required | Description |
|----------|------|----------|-------------|
| `OPENAI_API_KEY` | `str` | Yes | Secret key for OpenAI API access. |
| `OPENAI_ASSISTANT_ID`| `str` | No | Optional pre-configured assistant ID (otherwise create one). |
