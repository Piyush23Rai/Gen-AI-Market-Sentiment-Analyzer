# ✅ Real-Time Market Sentiment Analyzer

## 📚 Overview

This project builds a real-time market sentiment analysis pipeline using LangChain chains, Google Gemini-2.0-flash, and MLflow for observability.
It accepts a company name as input, fetches its stock code, retrieves recent news, analyzes sentiment, and outputs structured JSON.

---

## ⚙️ Setup Instructions

1. Clone this repository:
    ```bash
    git clone <repo-url>
    cd <repo-directory>
    ```

2. Install required Python packages:
    ```bash
    python -m pip install langchain langchain-core langchain-community langchain-experimental --quiet
    python -m pip install -U langchain-google-genai --quiet
    python -m pip install mlflow --quiet
    python -m pip install yahooquery --quiet
    ```

3. Set up environment variables:
    - Create a `.env` file in the root directory with:
      ```bash
      GOOGLE_API_KEY=<YOUR_GOOGLE_GENAI_API_KEY>
      MLFLOW_TRACKING_URI=http://localhost:5000
      ```

---

## ⚡ Gemini and MLflow Configuration

### 1️⃣ Google Gemini-2.0-flash
- Ensure your service account is authenticated:
    ```bash
    gcloud auth application-default login
    ```
- Set `GOOGLE_API_KEY` in `.env`.

### 2️⃣ MLflow Tracking
- Set `MLFLOW_TRACKING_URI` in `.env`.
- Example local server start (optional):
    ```bash
    mlflow server --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./mlruns --host 0.0.0.0 --port 5000
    ```

---

## ▶️ Sample Command to Run the Chain

```python
from pipeline import run_pipeline_with_tracing

result = run_pipeline_with_tracing("Google Inc")
print(json.dumps(result, indent=2))
