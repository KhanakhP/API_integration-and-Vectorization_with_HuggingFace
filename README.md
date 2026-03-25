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

## How to Run (Colab)

### Install dependencies
```bash
pip install sentence-transformers
