# Fisheries - LLM using - RAG

An intelligent chatbot for fisheries management using Retrieval-Augmented Generation (RAG) to provide accurate, context-grounded answers from specialized knowledge bases.

## Overview
This bot leverages RAG technology to deliver expert guidance on fisheries-related queries by combining semantic search with AI-powered responses. It uses FAISS for efficient vector similarity search and OpenAI's language models for natural language understanding and generation.

## Technologies Used

### Core Dependencies
- **Flask** - Web framework for serving the application
- **Flask-CORS** - Cross-Origin Resource Sharing support
- **python-dotenv** - Environment variable management
- **OpenAI** - Language model API for intelligent responses
- **sentence-transformers** - Semantic embeddings generation
- **FAISS-CPU** - Fast similarity search and clustering
- **NumPy** - Numerical computing library

### Voice Integration
- **torchaudio** - Audio processing with PyTorch
- **SpeechBrain** - Speech recognition and synthesis
- **soundfile** - Audio file I/O

## Features
- **RAG-based Q&A**: Retrieves relevant context from knowledge base and generates accurate responses
- **Semantic Search**: Uses `all-MiniLM-L6-v2` embeddings for finding relevant information
- **Voice Interaction**: Support for speech-based queries and responses
- **Web Interface**: Flask-based API for easy integration
- **FAISS Indexing**: Efficient vector storage and retrieval

## Prerequisites
- Python 3.10+ recommended
- OpenAI API key (set as `OPENAI_API_KEY`)
- Optional: `OPENAI_MODEL` environment variable to override default model

## Setup

1. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   venv\Scripts\activate  # On Windows
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Create a `.env` file in the project root**
   ```env
   OPENAI_API_KEY=your-key-here
   OPENAI_MODEL=gpt-3.5-turbo
   ```

## Build the Index

Run the ingestion script to process your knowledge base and build the FAISS index:
```bash
python ingest.py
```
This will generate:
- `agri.index` - FAISS vector index
- `chunks.pkl` - Serialized text chunks

## Running the Application

### Web Server
```bash
python server.py
```

### Query Interface
```bash
python query.py
```

### Interactive Voice Mode
```bash
python app.py
```

## Project Structure
- `ingest.py` - Data ingestion and index building
- `query.py` / `query2.py` - Query processing scripts
- `app.py` - Main application with voice interaction
- `server.py` - Flask web server
- `generate_voices.py` - Voice synthesis utilities
- `index.html` - Web interface
- `agri.index` - FAISS vector index
- `static/` - Static assets (audio, voices)
- `pretrained_models/` - Pre-trained speaker recognition models

## Notes
- The bot uses top-k retrieval to find the most relevant context chunks
- Responses are generated based on retrieved context to ensure accuracy
- If no relevant context is found, the bot will indicate it cannot answer the question
- Voice features require pretrained models in the `pretrained_models/` directory
.\venv\Scripts\activate