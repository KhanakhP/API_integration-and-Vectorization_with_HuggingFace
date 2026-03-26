# AI Tasks – Gemini API + Embeddings Similarity

## Overview
This repository contains two core tasks:
- **Task B:** Gemini API integration for text generation  
- **Task C:** Text embedding and similarity search using sentence-transformers  

The goal is to demonstrate practical LLM usage and semantic retrieval, which are key building blocks for modern AI systems like RAG.

---

## Task B – Gemini API Integration

### What I implemented
- A function that:
  - takes a prompt as input
  - sends it to Gemini API
  - returns the generated response

### Why this approach
- Focused on core functionality instead of overengineering  
- Avoided unnecessary API layers for simplicity in Colab  
- Can be easily extended into a FastAPI service  

### Tech Stack
- Python  
- Requests  
- Gemini API  

---

## Task C – Embeddings + Similarity Search

### What I implemented
- Used `intfloat/e5-small-v2` to generate embeddings  
- Converted sentences and query into vectors  
- Computed cosine similarity to find the most relevant match  

### Key Detail
- Used `"query:"` and `"passage:"` prefixes as required by the model  
- This improves semantic accuracy  

### Why this approach
- Enables semantic comparison instead of keyword matching  
- Foundation for search systems, retrieval, and RAG pipelines  

### Tech Stack
- sentence-transformers  
- scikit-learn  

---





# AI Pipeline Tasks (Task 1 & Task 2)

## Overview
This repository contains two tasks demonstrating core components of modern AI systems:

- **Task 1:** Moderation + GPT-style pipeline (mocked)
- **Task 2:** Retrieval-Augmented Generation (RAG) pipeline using embeddings and FAISS

The focus is on building a **clean, modular pipeline** rather than overengineering.

---

# Task 1 — Moderation + GPT Pipeline

## Description
A simple pipeline that processes input text through:
1. Moderation layer  
2. GPT response generation (mocked)

## Flow

Input → Moderation → GPT → Response


## Components

### 1. Input
- Accepts text input (string or PDF)

### 2. Moderation (Mocked)
- Checks for unsafe content using basic rules
- Returns:
  ```json
  { "allowed": false, "flag": "category" }
3. GPT Module (Mocked)
Generates response if input is safe
4. Retry Mechanism
Retries GPT call if it fails
Improves robustness
Why this design
Separates concerns (moderation, generation)
Easy to replace mock modules with real APIs
Reflects production pipeline structure

# Task 2 — RAG Pipeline

## Description
This task implements a basic Retrieval-Augmented Generation (RAG) pipeline to retrieve relevant information from a PDF document.

---

## Flow

PDF → Chunking → Embeddings → FAISS → Retrieval


---

## Steps

### 1. PDF Parsing
- Extract text from PDF using PyPDF2  
- Convert document into raw text  

### 2. Chunking
- Split text into fixed-size chunks (e.g., 150–200 characters)  
- Improves retrieval accuracy and keeps input manageable  

### 3. Embeddings
- Model used: `intfloat/e5-small-v2`  
- Converts text into vector representations  

**Important:**
- Use `"passage:"` prefix for document chunks  
- Use `"query:"` prefix for user queries  
- Required for better semantic alignment  

### 4. Vector Store (FAISS)
- Store embeddings using FAISS  
- Normalize embeddings and use inner product for cosine similarity  
- Enables efficient nearest-neighbor search  

### 5. Retrieval
- Convert query into embedding  
- Search FAISS index  
- Retrieve top-k most relevant chunks  
