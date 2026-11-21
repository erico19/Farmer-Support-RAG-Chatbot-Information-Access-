<div align="center">
  <!-- <img src="https://emojicdn.elk.sh/🌾?style=google" width="120" height="120"/> -->
  <img src="docs/logo.svg" width="120" height="120"/>
</div>

# AgriRAG Assistant

AgriRAG is an Artificial Intelligence application based on Retrieval-Augmented Generation (RAG). It is designed to provide highly contextualized answers to agricultural questions by leveraging a local document database tailored to local soils, crops, and climate conditions in Uganda and East Africa.

## 🚀 Objectives

- Facilitate access to accurate agricultural information for smallholder farmers and agripreneurs.
- Exploit local documents (technical guides, PDFs, research reports) to answer specific farming questions without AI hallucinations.
- Deploy an accessible AI agent online (via Streamlit or Hugging Face Spaces) to empower agricultural extension workers.

## 🏗️ Project Architecture

```mermaid
graph LR
    subgraph Frontend
        A[Streamlit UI] --> B[main.py]
    end

    subgraph Backend
        B --> C[Retriever FAISS/ChromaDB]
        D[Local Documents .pdf, .docx] --> C
        B --> E[LLM via OpenAI / HuggingFace]
        E --> F[Augmented Response]
    end

    subgraph "Data Pipeline"
        J[Data Ingestion] -- Chunking & Embedding --> K[Vector Store]
        K -- Semantic Search --> D
    end

    subgraph Deployment
        G[GitHub] --> H[CI/CD]
        H --> I[Streamlit Cloud / Hugging Face]
    end