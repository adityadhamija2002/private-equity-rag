# private-equity-rag
RAG pipeline answering questions from private equity reports using LangChain, FAISS and Gemini
# Private Equity RAG System

A retrieval augmented generation pipeline that answers questions from three private equity reports without the model fabricating facts.

## What it does

The system loads reports from Bain, McKinsey and an academic source, splits them into chunks, embeds them with a sentence-transformer model, and stores them in a FAISS vector index. When a question is asked, only the most relevant chunks are retrieved and passed to Google Gemini, so every answer is grounded in the source documents rather than the model's general knowledge.

## Stack

- LangChain for the pipeline
- FAISS for the vector store
- sentence-transformers (all-MiniLM-L6-v2) for embeddings
- Google Gemini (gemini-2.5-flash) for generation

## What it tests

Three prompting strategies are compared across the same set of questions: one-shot, few-shot and a structured step-by-step prompt. The pipeline also runs a hallucination check, feeding the system deliberately unanswerable questions to see whether it refuses or invents an answer.

## Notes

- The API key is loaded from Colab Secrets and is not stored in the code.
- The token figures in the results table are rough word-based estimates, not true token counts.

Built as part of an MSc in Management and Business Analytics at Oxford Brookes University.
