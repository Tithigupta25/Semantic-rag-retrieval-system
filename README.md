# Semantic Document Retrieval System (RAG – Retrieval Only)

## Overview
This project implements a semantic document retrieval system that returns the
Top-K most relevant document chunks for a given user query.  
The solution focuses only on the **retrieval part of RAG** and does not use any
LLM or text generation.


## Workflow
PDF -> Text Chunking -> Embeddings -> Vector Database -> Query Embedding -> Top-K Similar Chunks


## Input Document
example.pdf (stored in `data/` folder)


## Chunking Strategy
Chunk size: 500 characters  
Chunk overlap: 100 characters  
Metadata stored: source file, page number, chunk ID


## Embeddings
Model: `sentence-transformers/all-MiniLM-L6-v2`
Chosen for being free, fast, and effective for semantic similarity


## Vector Database
ChromaDB (local, persistent)
Used for efficient similarity search


## Retrieval
User queries are embedded and matched against stored document embeddings.
Top-K most relevant chunks are returned based on vector distance  
(lower score = better match).


## Sample Queries
What are the responsibilities of top management?
What is the purpose of an information security management system?
What are information security risk assessment requirements?


## Sample Output
```json
{
  "chunk_text": "...",
  "score": 0.603,
  "source": "data/example.pdf",
  "page": 8,
  "chunk_id": 57
}
