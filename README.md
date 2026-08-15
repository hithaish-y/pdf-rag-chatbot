🤖 Hithaish PDF RAG Chatbot

Transform your PDFs into an intelligent, conversational knowledge base
powered by AI.

A Retrieval-Augmented Generation (RAG) system that enables
natural-language conversations with PDF documents using LangChain, FAISS
vector search, HuggingFace embeddings, Groq LLM inference, and
Streamlit.

📑 Table of Contents

Features

Live Demo

Tech Stack

UI Overview

Quick Start

Installation

Configuration

Usage Guide

Architecture

Project Structure

Troubleshooting

Contributing

Contact

✨ Features

Core Capabilities

📁 Multi-PDF Upload --- Process one or multiple PDF documents.

🔍 Semantic Search --- FAISS-powered vector similarity search.

🤖 Groq LLM Support --- Fast LLM inference using Groq.

🔄 OpenAI Fallback --- Optional fallback LLM support.

📚 Source Citations --- Display document sources used for
answers.

💬 Chat History --- Continue conversations with uploaded
documents.

⚡ Persistent FAISS Index --- Reuse the generated vector index
for subsequent queries.

Advanced Features

🎨 Modern UI --- Dark glassmorphic Streamlit interface.

📊 Real-Time Logs --- View application processing information.

🔧 Debug Context --- Inspect retrieved document context.

📥 Export Options --- Download chat history when available.

⚡ OCR Fallback --- Supports image-based PDF text extraction
when configured.

🎯 Adaptive Retrieval --- Configurable chunk size and Top-K
retrieval.

🌐 Live Demo

The project currently runs locally through Streamlit.

Run locally

streamlit run app.py

The application will open at:

http://localhost:8501

A public demo URL is not included yet because the current application
is running locally.

🛠 Tech Stack

Layer           Technology                          Purpose

Frontend        Streamlit                           Interactive web interface
LLM             Groq / Llama                        Fast AI inference
Fallback LLM    OpenAI                              Optional fallback
Embeddings      HuggingFace Sentence Transformers   Sentence embeddings
Vector Store    FAISS                               Similarity search
Orchestration   LangChain                           RAG pipeline management
PDF Parsing     PyMuPDF + Unstructured              PDF text extraction
Language        Python 3.9+                         Core application logic

Key Dependencies

langchain==0.2.16
langchain-groq>=0.0.1
faiss-cpu>=1.7.4
sentence-transformers>=2.2.2
streamlit>=1.28.0

🖥️ UI Overview

🏠 Main Page



📄 PDF Upload



💬 Chatbot Answer



📚 Sources



Main Interface Components

Header --- Hithaish PDF RAG Chatbot branding.

Quick Guide --- Visual workflow from PDF upload to answer
generation.

File Uploader --- Drag-and-drop PDF upload area.

Tabbed Navigation --- Chat, Info & Tech Stack, Logs, and Notes.

Configuration Sidebar --- Embedding model, chunk size, and Top-K
settings.

LLM Status --- Displays configured LLM availability.

📁 PDF Upload

The PDF upload section allows users to:

Upload one or more PDF files.

Process PDF documents.

Extract text from documents.

Split documents into chunks.

Generate document embeddings.

Build or update the FAISS vector index.

💬 Chatbot Answer

The chat interface allows users to:

Ask questions about uploaded PDFs.

Receive AI-generated answers.

Continue conversations.

Clear conversation history.

View retrieved document information.

Inspect retrieved context when needed.

Chat Features

Text input

Query submission

Conversation history

Clear conversation

Message bubbles

Source information

Debug context

📚 Source Citations

The source section displays document information used to generate the
answer.

This helps users:

Verify the generated answer.

Identify the relevant document.

Understand the retrieved context.

Improve transparency of the RAG response.

🚀 Quick Start

Prerequisites

Python 3.9 or higher

Groq API key

Optional OpenAI API key

Git

Windows

git clone https://github.com/hithaish-y/pdf-rag-chatbot.git
cd pdf-rag-chatbot

If the setup script is available:

setup.bat

Then run:

streamlit run app.py

Linux / macOS

git clone https://github.com/hithaish-y/pdf-rag-chatbot.git
cd pdf-rag-chatbot
pip install -r requirements.txt
streamlit run app.py

📦 Installation

Step 1: Clone Repository

git clone https://github.com/hithaish-y/pdf-rag-chatbot.git
cd pdf-rag-chatbot

Step 2: Create a Virtual Environment

Windows

python -m venv venv
venv\Scriptsctivate

Linux / macOS

python3 -m venv venv
source venv/bin/activate

Step 3: Install Dependencies

pip install -r requirements.txt

Step 4: Configure API Keys

Create or configure:

.streamlit/secrets.toml

Example:

GROQ_API_KEY = "your_groq_api_key_here"
OPENAI_API_KEY = "your_openai_api_key_here"

Do not commit real API keys to GitHub.

Step 5: Run the Application

streamlit run app.py

The app will normally open at:

http://localhost:8501

⚙️ Configuration

The application uses configurable RAG parameters.

Vector Store

INDEX_DIR = "faiss_index_storage"

Embedding Model

EMBEDDING_MODEL_NAME = "sentence-transformers/all-mpnet-base-v2"

Retrieval Parameters

CHUNK_SIZE = 800
CHUNK_OVERLAP = 150
TOP_K = 10

Performance Tuning

Use Case            CHUNK_SIZE   TOP_K Model

Precise Answers            500      15 Llama 70B
Balanced                   800      10 Llama 70B
Speed Priority            1000       5 Llama 8B

📖 Usage Guide

1. Upload PDFs

Open the Streamlit application.

Use the PDF uploader.

Select one or more PDF files.

Wait for document processing and indexing.

2. Ask Questions

Open the Chat section.

Enter a question about the uploaded documents.

Submit the question.

Wait for the AI-generated response.

3. Review Answers

Read the generated answer.

Check the displayed sources.

Inspect retrieved context when necessary.

4. Manage Conversation

Continue asking questions about the uploaded documents.

Clear the conversation when required.

Download chat history when the export option is available.

🏗️ Architecture

┌─────────────────┐
│   PDF Upload    │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  PDF Processing │
│     PyMuPDF     │
└────────┬────────┘
         │
         ▼
┌─────────────────────┐
│    Text Splitter    │
│ Chunk: 800          │
│ Overlap: 150        │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│ HuggingFace Embedder│
│ all-mpnet-base-v2   │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│   FAISS Vector      │
│      Store           │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│     User Query      │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  Similarity Search  │
│    Top-K Retrieval  │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│    LLM Inference    │
│    Groq / OpenAI    │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│ Answer + Sources    │
└─────────────────────┘

RAG Workflow

PDF documents are uploaded.

Text is extracted from the PDFs.

Extracted text is divided into chunks.

Chunks are converted into vector embeddings.

Embeddings are stored in FAISS.

A user question is processed for retrieval.

Relevant chunks are retrieved using similarity search.

Retrieved context is passed to the LLM.

The LLM generates an answer.

Relevant sources are displayed with the response.

📂 Project Structure

pdf-rag-chatbot/
│
├── app.py
├── requirements.txt
├── README.md
├── QUICKSTART.md
├── .gitignore
├── Dockerfile
├── run.bat
├── setup.bat
│
├── .streamlit/
│   └── secrets.toml
│
├── screenshots/
│   ├── main-page.png
│   ├── pdf-upload.png
│   ├── chatbot-answer.png
│   └── sources.png
│
├── faiss_index_storage/
│   ├── index.faiss
│   └── index.pkl
│
└── uploaded_pdfs/

🐛 Troubleshooting

Application does not start

pip install -r requirements.txt
streamlit run app.py

API key error

Check that your API key is correctly configured in:

.streamlit/secrets.toml

Never publish API keys in your repository.

Answers are not found

Try:

Re-uploading the PDF.

Rebuilding the FAISS index.

Asking a question directly related to the PDF.

Checking the Logs or Debug Context section.

Slow processing

PDF processing and embedding generation can take time depending on the
PDF size and hardware.

🤝 Contributing

Contributions and suggestions are welcome.

Fork the repository.

Create a new branch.

Make your changes.

Test the application.

Commit your changes.

Push the branch.

Open a pull request.

📞 Contact

Hithaish Y

Information Science Engineering Student

GitHub:
https://github.com/hithaish-y

LinkedIn:
https://www.linkedin.com/in/hithaish-y-9856562a1

::: {align="center"}

🚀 Hithaish PDF RAG Chatbot

Built with ❤️ by Hithaish Y

Python • LangChain • FAISS • Groq • Streamlit • HuggingFace

⭐ Star this repository if you find it useful!
:::