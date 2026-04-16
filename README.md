# NEWS-MLOPS: Retrieval-Augmented News Query System

## Overview

This project implements an end-to-end MLOps pipeline for a news-based Retrieval-Augmented Generation (RAG) system.

The system ingests data, generates embeddings, stores them in a vector database (ChromaDB), retrieves relevant documents, and serves responses via an API built with FastAPI.

## Features

* Data generation and ingestion
* Embedding-based feature engineering
* Vector database using ChromaDB
* Retrieval-Augmented Generation (RAG)
* API deployment using FastAPI
* Artifact tracking and logging
* Docker containerization
* Automated pipeline execution using GitHub Actions


## Repository Structure

NEWS-MLOPS/
│
├── app_fastapi.py
├── rag.py
├── create_data.py
├── ingest_data.py
├── vector_db.py
├── vectordb_query.py
├── search.py
├── requirements.txt
├── Dockerfile
│
├── artifacts/
│   └── logs.txt
│
└── chroma_db/

## How to Run Locally

### 1. Install dependencies
pip install -r requirements.txt

### 2. Generate data
python create_data.py

### 3. Build vector database
python vector_db.py

### 4. Start the API
uvicorn app_fastapi:app --host 0.0.0.0 --port 8000

API documentation:
http://localhost:8000/docs

## Running with Docker

### Build image

docker build -t news-mlops .

### Run container

docker run -p 8000:8000 news-mlops

#API documentation:
http://localhost:8000/docs

## API Usage

### Endpoint

POST /ask

### Example Request

{
  "query": "What is happening in global markets?"
}

### Response
Returns a generated answer based on retrieved news context.

## Pipeline Automation

The pipeline is automated using GitHub Actions:

* Runs on a schedule
* Updates data and vector database
* Can also be triggered manually from the Actions tab

## Artifacts
Artifacts are stored in the artifacts/ directory:
* logs.txt: pipeline logs
* chroma_db/: vector database files

## Monitoring

The system logs:
* Data ingestion
* Vector database creation
* API requests
* Retrieval results

Logs are stored in:
artifacts/logs.txt

## Reproducibility

Reproducibility is ensured through:
* Deterministic data generation
* Fixed dependencies (requirements.txt)
* Docker containerization
* Automated pipeline execution

## Author
Riya Pokharel
MSc BDS – Data Engineering and Machine Learning Operations in Business

## License
This project is submitted as part of the MLOps exam assignment.
