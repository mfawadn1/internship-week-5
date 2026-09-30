# 🔍 Retrieval-Augmented Generation (RAG) & Vector Database Architecture

**Author:** Fawad  
**Program:** AI Software Development Internship (.NET + Angular + AI)  
**Milestone:** Week 5 — Manual RAG Pipeline, Vector Embeddings & FastAPI Integration  

[![Python: 3.10+](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![ChromaDB](https://img.shields.io/badge/Vector_DB-ChromaDB-FF6F00?logo=chroma&logoColor=white)](https://www.trychroma.com/)
[![Architecture: 8--Stage RAG](https://img.shields.io/badge/Architecture-8--Stage_RAG-blueviolet)](https://github.com/)

---

## 🌟 Overview

This repository contains the complete implementation for **Week 5: Retrieval-Augmented Generation (RAG)**. It covers everything from mathematical vector space fundamentals to a fully grounded, production-style knowledge retrieval service.

```
       ┌────────────────┐      ┌─────────────────┐      ┌────────────────┐
       │ Ingest / Chunks│ ───> │ Vector Database │ <─── │ User Question  │
       │ (Fixed+Overlap)│      │  (ChromaDB HNSW)│      │   Embedding    │
       └────────────────┘      └─────────────────┘      └────────────────┘
                                        │
                                        ▼ Top-K Chunks
                               ┌─────────────────┐
                               │ Prompt Template │
                               │ Strict Grounding│
                               └─────────────────┘
                                        │
                                        ▼
                               ┌─────────────────┐
                               │ LLM Generation  │ ───> Grounded Answer +
                               │ (OpenAI / Claude)│      Source Citations
                               └─────────────────┘
```

---

## 📂 Repository Structure

| Directory / File | Description |
| :--- | :--- |
| **`Week5_PartA_Embeddings/`** | Vector embedding generation, Cosine Similarity, Euclidean distance, and top-$k$ semantic search rankings. |
| **`Week5_PartB_VectorDB/`** | ChromaDB collection indexing, L2 distance queries, and compound `$and` metadata filtering. |
| **`Week5_PartC_RAGPipeline/`** | Manual 8-stage RAG pipeline with chunking, retrieval, prompt assembly, and hallucination guardrails. |
| **`Week5_PartD_RAGQuality/`** | Quantitative RAG evaluation framework measuring chunk size trade-offs and hit rate @ $k$. |
| **`Week5_PartE_FastAPI_Ask/`** | FastAPI microservice exposing `/ask` with Pydantic validation, CORS, error handling, and citations. |
| **`Week5_PartF_GitRevert/`** | Git revert documentation and safe commit rollback walkthroughs. |
| **`Week5_Project_LibraryAssistant/`** | End-to-end Library Assistant CLI & grounding test suite over persistent catalog vectors. |
| **`Week5_CheckStage_Answers.md`** | Comprehensive architectural and theoretical answers to all Week 5 assessment questions. |

---

## 🚀 Quickstart & Execution

### 1. Setup Virtual Environment
```bash
python -m venv .venv
# Windows PowerShell
.venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt
```

### 2. Run Module Demos

#### Part A: Vector Embeddings & Similarity
```bash
python Week5_PartA_Embeddings/embed_demo.py
```

#### Part B: ChromaDB Vector Storage & Metadata Filtering
```bash
python Week5_PartB_VectorDB/chroma_demo.py
```

#### Part C: Manual 8-Stage RAG Pipeline
```bash
python Week5_PartC_RAGPipeline/rag_pipeline.py
```

#### Part D: RAG Quality & Evaluation Suite
```bash
python Week5_PartD_RAGQuality/rag_evaluation.py
```

#### Part E: FastAPI /ask Microservice
```bash
uvicorn Week5_PartE_FastAPI_Ask.app:app --reload --port 8000
# Interactive Swagger Documentation: http://127.0.0.1:8000/docs
```

#### Project: Grounding & Verification Test Suite
```bash
python Week5_Project_LibraryAssistant/test_grounding.py
```

---

## 🛡️ Grounding & Hallucination Guardrails

The RAG pipeline enforces strict negative constraint prompting:
- **Strict Grounding:** The LLM is explicitly commanded to rely solely on the retrieved context chunks.
- **Zero-Shot Refusal:** If the answer is not present in the retrieved documents, the system returns `"I don't have that information."` rather than hallucinating external facts.
- **Source Attribution:** Every response includes the list of source document names referenced during generation.

---

## 👤 Author

- **Name:** Fawad  
- **Internship:** AI Software Development Internship (.NET + Angular + AI)
