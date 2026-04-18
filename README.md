# NEWS-MLOPS: Retrieval-Augmented News Query System

## Overview

NEWS-MLOPS is an end-to-end Machine Learning Operations (MLOps) pipeline implementing a Retrieval-Augmented Generation (RAG) system for financial news intelligence.

The system processes financial news data, generates embeddings, stores them in a vector database, and retrieves relevant context to generate grounded responses using a FastAPI backend and an optional Gradio user interface.

The project demonstrates a production-oriented pipeline covering data ingestion, preprocessing, feature engineering, retrieval, deployment, monitoring, and automation.

---

## Live Demo

Access the deployed application (no installation required):

https://huggingface.co/spaces/Riya1217/financial-news-rag

---

## Key Features

* Automated data generation and ingestion
* Text preprocessing and normalization
* Embedding-based feature engineering (Sentence Transformers)
* Vector database using ChromaDB
* Retrieval-Augmented Generation (RAG)
* FastAPI backend (`/ask` endpoint)
* Interactive Gradio UI
* Logging and artifact tracking
* GitHub Actions pipeline automation
* Docker-ready environment for reproducibility

---

## Repository Structure

```
NEWS-MLOPS/
│
├── app_fastapi.py        # FastAPI backend
├── rag.py                # Gradio UI
├── create_data.py        # Data generation
├── ingest_data.py        # Preprocessing (JSON → cleaned text)
├── vector_db.py          # Embedding + vector DB creation
├── vectordb_query.py     # Retrieval testing
├── search.py             # Search utilities
│
├── requirements.txt
├── Dockerfile
│
├── artifacts/
│   └── logs.txt          # System logs
└── chroma_db/            # Persistent vector database
```

---

## Pipeline Architecture

**Offline Pipeline (Data Flow)**
SQLite → Data Export → Preprocessing → Embedding Generation → ChromaDB

**Online Pipeline (Query Flow)**
User Query → API/UI → Retrieval → RAG + LLM → Response

---

## How to Run

### Option 1: Use Deployed App (Recommended)

No setup required:

https://huggingface.co/spaces/Riya1217/financial-news-rag

---

### Option 2: Run Locally

1. Clone the repository:

```
git clone <your-repo-link>
cd NEWS-MLOPS
```

2. Install dependencies:

```
pip install -r requirements.txt
```

3. Create a `.env` file in the root folder:

```
GROQ_API_KEY=your_api_key_here
```

4. Run the pipeline:

```
python create_data.py
python ingest_data.py
python vector_db.py
```

5. Start the API:

```
uvicorn app_fastapi:app --host 0.0.0.0 --port 8000
```

API docs:
http://localhost:8000/docs

6. (Optional) Run UI:

```
python rag.py
```

---

### Option 3: Run with Docker

Build image:

```
docker build -t news-mlops .
```

Run container:

```
docker run -p 8000:8000 --env-file .env news-mlops
```

---

## API Usage

**Endpoint:** `POST /ask`

Example request:

```
{
  "query": "What is happening in global markets?"
}
```

---

## Automation (GitHub Actions)

The pipeline is automated using GitHub Actions:

* Runs every 2 hours
* Can be triggered manually
* Executes:

  * Data generation
  * Data ingestion
  * Vector database update

Workflow file:

```
.github/workflows/schedule.yml
```

---

## Artifacts

Stored in:

* `artifacts/logs.txt`
* `chroma_db/`

Includes:

* Logs for ingestion, retrieval, and API activity
* Persisted vector database

---

## Monitoring

The system logs:

* Data ingestion processes
* Embedding creation
* API requests
* Retrieval results

---

## Deployment

The system supports:

* FastAPI backend (API-based interaction)
* Gradio frontend (user interface)
* Docker containerization
* Cloud deployment via Hugging Face

---

## Reproducibility

Reproducibility is ensured through:

* Fixed dependencies (`requirements.txt`)
* Structured pipeline design
* Docker containerization
* Devcontainer support (Codespaces)
* Externalized environment variables (`.env`)

---

## Important Notes

* `.env` file is required locally and is not included in the repository
* API and UI must be started manually when running locally
* GitHub Actions automates the pipeline but does not host the API

---

## Authors

Riya Pokharel
Sristi Kulung Rai

MSc Business Data Science
Data Engineering and Machine Learning Operations in Business
