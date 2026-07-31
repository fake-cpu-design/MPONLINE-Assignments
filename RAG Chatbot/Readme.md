# Production Enterprise RAG System

## Architecture Overview
This project implements a production-grade Retrieval-Augmented Generation (RAG) platform. The architecture separates document parsing, vector indexing, neural reranking, and generation into modular components designed to eliminate hallucinations and supply accurate source attributions.

[ Raw Documents ]
│
▼
[ Sentence Splitter ] ──(Chunks: 256 / Overlap: 32)
│
▼
[ BGE Embeddings ] ──(BAAI/bge-small-en-v1.5)
│
▼
[ ChromaDB Persistent Storage ]
│
▼  (Top-5 Vector Search)
[ BGE Cross-Encoder Reranker ] ──(BAAI/bge-reranker-base -> Top-2)
│
▼
[ Deterministic Prompt Guard ] ──(GPT-4o-mini, Temp=0.0)
│
▼
[ Gradio UI + Citations ]


## Production Technical Stack
* **Orchestration Framework:** LlamaIndex
* **Vector Database:** ChromaDB (`PersistentClient` disk-backed deployment)
* **Embedding Model:** `BAAI/bge-small-en-v1.5` (HuggingFace)
* **Neural Reranker:** `BAAI/bge-reranker-base` (Cross-Encoder post-processor)
* **LLM Engine:** OpenAI `gpt-4o-mini`
* **Interface Layer:** Gradio

## Key Engineering Features
1. **Two-Stage Retrieval Architecture:** Initial broad retrieval fetches the top 5 most similar nodes via vector search. A secondary Cross-Encoder reranking model scores the retrieved contexts against the query to prune noise, passing only the top 2 highest-quality nodes to the LLM.
2. **Persistent Vector Storage:** Utilizes ChromaDB disk persistence (`./enterprise_chroma`), allowing embedded vectors to persist across notebook sessions without re-computation costs.
3. **Deterministic Grounding:** Features custom QA prompt templates enforcing strict context-only answers and precise fallback messages when context is insufficient.
4. **Transparent Auditability:** Outputs exact document filenames, reranker relevance scores, and verbatim text snippets alongside every answer in the Gradio UI.

## Execution Steps
1. Open Google Colab and execute Task 1 to install the full production framework stack.
2. Execute Task 2 to generate enterprise policy, compliance, and architecture documents.
3. Run Task 3, entering your OpenAI API Key when prompted.
4. Run Tasks 4 and 5 to create the persistent database index and configure the reranking pipeline.
5. Launch Task 6 to spin up the web interface via the generated public Gradio URL.