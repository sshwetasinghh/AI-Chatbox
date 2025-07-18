# AI Chatbox – RAG-based PDF Question Answering

This project is a simple yet powerful **AI Chatbot** built using a **RAG (Retrieval-Augmented Generation)** pipeline. It allows users to ask natural language questions based on the content of a PDF document.


# Project Structure
├── data/ # Folder for input PDFs
├── chunks/ # Stores text chunks extracted from the PDF
├── vectordb/ # FAISS vector index and chunk mapping
├── llm.ipynb # Main notebook for building and running the RAG pipeline
├── README.md # Project documentation


# Features

- Reads and processes PDF documents
- Splits content into meaningful chunks
- Embeds chunks using SentenceTransformers
- Stores and retrieves context with FAISS vector search
- Generates answers using Google's Gemini 1.5 Flash model


# Technologies Used

- `PyPDF2` – PDF text extraction  
- `LangChain` – RecursiveCharacterTextSplitter  
- `SentenceTransformers` – for embeddings (`all-MiniLM-L6-v2`)  
- `FAISS` – efficient similarity search  
- `Google Generative AI (Gemini)` – text generation  

# How It Works

1. **Preprocessing**:  
   - Load a PDF from `data/`
   - Split into chunks with overlap
   - Embed using SentenceTransformer
   - Store in FAISS index

2. **Querying**:  
   - User inputs a question
   - Top-k relevant chunks retrieved from vector DB
   - Gemini uses context + question to generate an answer


# Example Query

```python
query = "what is the purpose of this Document?"
answer, source_chunks = rag.run(query)

print("Answer:\n", answer)

