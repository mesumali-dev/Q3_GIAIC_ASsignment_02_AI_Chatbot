# Quickstart: AI Chatbot UI

## Prerequisites
- Python 3.14 (or 3.10+)
- `uv` package manager
- OpenAI API Key

## Setup

1.  **Clone and Enter**:
    ```bash
    git clone <repo>
    cd ai-chatbot-ui
    ```

2.  **Environment**:
    Create a `.env` file:
    ```bash
    echo "OPENAI_API_KEY=sk-..." > .env
    ```

3.  **Install Dependencies**:
    ```bash
    pip install openai-agents streamlit python-dotenv # or `uv add openai-agents streamlit python-dotenv`, etc
    # OR create requirements.txt manually then:
    # pip install -r requirements.txt
    ```

## Running the App

```bash
streamlit run src/app.py
```

## Running Tests

```bash
pytest
```
