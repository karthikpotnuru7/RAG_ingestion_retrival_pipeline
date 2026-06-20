# RAG Ingestion Retrieval Pipeline

## Project Overview

This project implements a Retrieval-Augmented Generation (RAG) system for document analysis. The system processes uploaded text documents, converts them into vector embeddings, stores them in a vector database, and retrieves relevant information to answer user queries accurately.

The project consists of two major components:

1. Ingestion Pipeline
2. Retrieval Pipeline

---

## Objectives

* Load and process text documents.
* Split large documents into manageable chunks.
* Generate embeddings using OpenRouter.
* Store embeddings in ChromaDB.
* Retrieve relevant document chunks based on user queries.
* Generate context-aware answers using an LLM.

---

## Tech Stack

### Programming Language

* Python

### Development Environment

* Google Colab

### Frameworks and Libraries

* LangChain Community
* LangChain Text Splitters
* OpenAI SDK
* ChromaDB

### Embedding Model

* OpenAI Text Embedding 3 Small (via OpenRouter)

### Vector Database

* ChromaDB

### LLM Provider

* OpenRouter

---

# System Architecture

Document Upload
↓
Document Loading
↓
Chunking
↓
Embedding Generation
↓
ChromaDB Storage
↓
-

↓
User Query
↓
Query Embedding
↓
Similarity Search
↓
Retrieve Relevant Chunks
↓
LLM Response Generation
↓
Final Answer

---

# Ingestion Pipeline

## Step 1: Document Upload

The user uploads a text file into Google Colab.

Example:

* Google.txt
* Microsoft.txt
* Research papers
* Study materials

---

## Step 2: Document Loading

The uploaded document is loaded using LangChain's TextLoader.

Output:

* Document object
* Metadata information

---

## Step 3: Chunking

The document is split into smaller chunks using RecursiveCharacterTextSplitter.

Configuration:

* Chunk Size: 1000
* Chunk Overlap: 200

Purpose:

* Preserve context
* Improve retrieval quality

---

## Step 4: Embedding Generation

Each chunk is converted into a numerical vector representation using:

openai/text-embedding-3-small

via OpenRouter.

Purpose:

* Capture semantic meaning of text
* Enable similarity search

---

## Step 5: Vector Storage

Generated embeddings are stored in ChromaDB.

Stored Data:

* Chunk IDs
* Document Chunks
* Embedding Vectors

---

# Retrieval Pipeline

## Step 6: User Query

The user asks a question related to the uploaded document.

Example:

* Who founded Google?
* What is PageRank?
* When was Google established?

---

## Step 7: Query Embedding

The user query is converted into an embedding vector using the same embedding model.

---

## Step 8: Similarity Search

ChromaDB performs semantic similarity search and retrieves the most relevant chunks.

Top-K Retrieval:

* K = 3

---

## Step 9: Context Construction

Retrieved chunks are combined into a context block.

Purpose:

* Provide relevant information to the LLM.

---

## Step 10: Answer Generation

The context and user query are sent to an LLM through OpenRouter.

The model generates a final answer based on retrieved document content.

---

# Features

* Document-based Question Answering
* Semantic Search
* Vector Database Storage
* Retrieval-Augmented Generation (RAG)
* OpenRouter Integration
* ChromaDB Integration
* Context-Aware Responses

---

# Future Enhancements

* PDF Support
* Multiple Document Upload
* Persistent ChromaDB Storage
* Question Bank Generation
* Automatic Quiz Generation
* Duplicate Question Detection
* Hallucination Reduction Techniques
* Research-Oriented Evaluation Metrics

---

# Research Extensions

Possible research directions include:

1. Chunk Size Comparison

   * 500 vs 1000 vs 1500

2. Chunk Overlap Analysis

   * 100 vs 200 vs 300

3. Embedding Model Comparison

   * OpenAI Embeddings
   * BGE Embeddings
   * Gemini Embeddings

4. Retrieval Performance Analysis

5. Automatic Question Generation with Semantic Deduplication

6. Hallucination Detection and Reduction

---

# Conclusion

This project demonstrates a complete Retrieval-Augmented Generation (RAG) workflow, including document ingestion, embedding generation, vector storage, semantic retrieval, and LLM-based answer generation. The system improves factual accuracy by grounding responses in retrieved document content.
