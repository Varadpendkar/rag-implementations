# RAG LLM - PDF Question Answering System

## Overview

This project implements a **Retrieval-Augmented Generation (RAG)** system that allows you to ask questions about PDF documents. The system retrieves relevant information from a PDF, processes it, and uses an LLM to generate accurate answers based on the document content.

Think of it as having a smart assistant that reads through your PDF and answers your questions intelligently!

## How It Works

1. **Load PDF** → Downloads and reads a PDF document
2. **Split into Chunks** → Breaks the document into smaller, manageable pieces
3. **Create Embeddings** → Converts text chunks into numerical representations
4. **Store in Vector Database** → Saves embeddings in Chroma for fast retrieval
5. **Query with LLM** → When you ask a question, the system finds relevant chunks and uses an LLM to answer

## Requirements

### Python Packages

```
chromadb               # Vector database
langchain              # LLM framework
langchain-groq         # Groq LLM integration
langchain-community    # Community tools
langchain-chroma       # Chroma integration
langchain-text-splitters  # Text splitting utilities
sentence-transformers  # Text embeddings
langchain-unstructured # PDF/document loading
langchain-huggingface  # HuggingFace embeddings
unstructured[pdf]      # PDF parsing
```

### System Dependencies

- **poppler-utils** - For PDF processing
- **tesseract-ocr** - For OCR (optional, for scanned PDFs)

### API Keys

- **GROQ_API_KEY** - Your Groq API key for LLM access

## Installation

### 1. Install Python Packages

```bash
pip install -U chromadb langchain langchain-groq langchain-community \
  langchain-chroma langchain-text-splitters sentence-transformers \
  langchain-unstructured langchain-huggingface
pip install -U "unstructured[pdf]"
```

### 2. Install System Dependencies (macOS)

```bash
brew install poppler
brew install tesseract
```

### 3. Set API Key

Get your API key from [Groq Console](https://console.groq.com) and set it in the notebook or environment:

```python
os.environ["GROQ_API_KEY"] = "your-api-key-here"
```

## Usage

### Running the Notebook

Simply run through the cells in order:

1. Install dependencies
2. Import libraries
3. Load the PDF
4. Process and embed the content
5. Ask your questions!

### Example Query

```python
query = "Explain about filter, map, reduce"
response = qa_chain.invoke({"query": query})
print(response['result'])
```

## Output Example

Here's an example of what the system can do:

![Filter, Map, Reduce Explanation](https://via.placeholder.com/800x600?text=Filter,+Map,+Reduce+Example)

The system retrieves relevant documentation from the PDF and generates a comprehensive explanation with code examples.

## Project Structure

```
Rag_llm.ipynb
├── Install Dependencies
├── Load PDF
├── Split Documents
├── Create Embeddings
├── Build Vector Database
├── Initialize LLM
├── Create QA Chain
└── Query Interface
```

## Key Features

✅ **Fast Retrieval** - Vector embeddings enable quick document search  
✅ **Accurate Answers** - LLM generates context-aware responses  
✅ **Source References** - Returns the document chunks used for answers  
✅ **Easy to Customize** - Change PDF, embeddings model, or LLM  
✅ **Persistent Storage** - Saves vector database locally

## Troubleshooting

**Q: ModuleNotFoundError for langchain modules?**  
A: Make sure to run the installation cell first and restart the kernel.

**Q: API Key error?**  
A: Verify your GROQ_API_KEY is set correctly and has valid permissions.

**Q: PDF loading errors?**  
A: Ensure poppler and tesseract are installed on your system.

## Future Improvements

- Support multiple PDFs
- Custom prompt templates
- Citation tracking
- Streaming responses
- Web interface

---

**Built with ❤️ using LangChain, Chroma, and Groq**
