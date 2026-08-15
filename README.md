# 🤖 Hithaish PDF RAG Chatbot

Transform your PDFs into an intelligent, conversational knowledge base powered by cutting-edge AI.

A production-ready Retrieval-Augmented Generation (RAG) system that enables natural language conversations with your PDF documents. Built with enterprise-grade technologies including LangChain, FAISS vector search, and high-speed LLM inference via Groq.

---
## 🖥️ UI Overview

### 🏠 Main Page
![Main Page](screenshots/main-page.png)

### 📄 PDF Upload
![PDF Upload](screenshots/pdf-upload.png)

### 💬 Chatbot Answer
![Chatbot Answer](screenshots/chatbot-answer.png)

### 📚 Sources
![Sources](screenshots/sources.png)

## 📑 Table of Contents

- Features
- Live Demo
- Tech Stack
- UI Overview
- Quick Start
- Installation
- Configuration
- Usage Guide
- Architecture
- Troubleshooting
- Contributing
- License
- Contact

---

## ✨ Features

### Core Capabilities

📁 **Multi-PDF Upload** - Process single or multiple PDF documents simultaneously

🔍 **Semantic Search** - FAISS-powered vector similarity search for accurate retrieval

🤖 **Dual LLM Support** - Groq (ultra-fast) with OpenAI fallback

📚 **Source Citations** - Every answer includes document references with page numbers

💬 **Chat History** - Persistent conversation tracking with download capability

🔄 **Smart Caching** - Persistent FAISS index for instant subsequent queries

### Advanced Features

🎨 **Modern UI** - Glassmorphic design with gradient animations

📊 **Real-time Logs** - Interactive log viewer with filtering

🔧 **Debug Mode** - View retrieved context chunks for transparency

📥 **Export Options** - Download chat history as text files

⚡ **OCR Fallback** - Automatic image-based PDF text extraction

🎯 **Adaptive Retrieval** - Configurable Top-K and chunk parameters

---

## 🌐🎬 Live Demo

🚀 Try it now:

- **Streamlit Profile:** YOUR_STREAMLIT_PROFILE_URL
- **Project Demo:** YOUR_STREAMLIT_APP_URL

Upload a PDF and ask questions in seconds!

---

## 🛠 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | Streamlit 1.51+ | Interactive web interface |
| LLM | Groq (Llama 3.3 70B) | Lightning-fast inference |
| Fallback LLM | OpenAI GPT-3.5 | Backup for high availability |
| Embeddings | HuggingFace Transformers | Sentence embeddings |
| Vector Store | FAISS | High-performance similarity search |
| Orchestration | LangChain 0.2.16 | RAG pipeline management |
| PDF Parsing | PyMuPDF + Unstructured | Text extraction with OCR fallback |
| Language | Python 3.9+ | Core application logic |

### Key Dependencies

```text
langchain==0.2.16
langchain-groq>=0.0.1
faiss-cpu>=1.7.4
sentence-transformers>=2.2.2
streamlit>=1.28.0

UI Overview
Main Interface

Components

Header - Hithaish PDF RAG Chatbot branding

Quick Guide - Visual workflow (Upload → Process → Query → Answer)

File Uploader - Drag-and-drop PDF upload zone

Tabbed Navigation - Chat, Info, Logs, Notes

📁 PDF Upload

The PDF upload section allows users to:

Upload one or more PDF files
Process PDF documents
Extract text from documents
Generate document embeddings
Build the FAISS vector index

💬 Chatbot Answer

The Chat interface allows users to:

Ask questions about uploaded PDFs
Receive AI-generated answers
Continue conversations
Clear conversation history
View retrieved document information
Chat Features
Text Area Input
Enter Query Button
Clear Conversation
Message Bubbles
Source Expanders
Debug Context


📚 Source Citations

The source section displays the document information used to generate the answer.

This helps users:

Verify the generated answer
Identify the relevant document
Understand the retrieved context
Improve transparency

🚀 Quick Start
Prerequisites
Python 3.9 or higher
Groq API Key
OR OpenAI API Key
One-Command Setup (Windows)
# Clone repository
git clone https://github.com/hithaish-y/pdf-rag-chatbot.git
cd pdf-rag-chatbot

# Run setup script
setup.bat

One-Command Setup (Linux/Mac)
# Clone repository
git clone https://github.com/hithaish-y/pdf-rag-chatbot.git
cd pdf-rag-chatbot

# Install and run
pip install -r requirements.txt
export GROQ_API_KEY="your_key_here"
streamlit run app.py

📦 Installation
Step 1: Clone Repository
git clone https://github.com/hithaish-y/pdf-rag-chatbot.git
cd pdf-rag-chatbot

Step 2: Create Virtual Environment
Windows
python -m venv venv
venv\Scripts\activate

Linux/Mac
python3 -m venv venv
source venv/bin/activate

Step 3: Install Dependencies
pip install -r requirements.txt

Step 4: Configure API Keys
Option A: Environment Variables
Windows PowerShell
$env:GROQ_API_KEY="gsk_your_groq_api_key_here"

Windows CMD
set GROQ_API_KEY=gsk_your_groq_api_key_here

Linux/Mac
export GROQ_API_KEY="gsk_your_groq_api_key_here"

Step 5: Run Application
streamlit run app.py

The app will open at:
http://localhost:8501

⚙️ Configuration
Customizable Parameters
Vector Store
INDEX_DIR = "faiss_index_storage"

Embeddings
EMBEDDING_MODEL_NAME = "sentence-transformers/all-mpnet-base-v2"

Performance Tuning
| Use Case        | CHUNK_SIZE | TOP_K | Model         |
| --------------- | ---------: | ----: | ------------- |
| Precise Answers |        500 |    15 | llama-3.3-70b |
| Balanced        |        800 |    10 | llama-3.1-70b |
| Speed Priority  |       1000 |     5 | llama-3.1-8b  |

📖 Usage Guide
Basic Workflow
Upload PDFs
Click the file uploader.
Select one or more PDF files.
Wait for processing to complete.
Ask Questions
Type your question in the text area.
Click Enter Query.
Wait for the AI response.
Review Answers
Read the AI-generated response.
View the sources.
Check retrieved context when needed.
Manage Conversation
Click Clear Conversation to reset the chat.
Download chat history when required.

┌─────────────┐
│  PDF Upload │
└──────┬──────┘
       │
       ▼
┌─────────────────┐
│ PyMuPDF Loader  │
└──────┬──────────┘
       │
       ▼
┌──────────────────────┐
│ Text Splitter        │
│ Chunk: 800           │
│ Overlap: 150         │
└──────┬───────────────┘
       │
       ▼
┌──────────────────────┐
│ HuggingFace Embedder │
│ all-mpnet-base-v2    │
└──────┬───────────────┘
       │
       ▼
┌──────────────────────┐
│ FAISS Vector Store   │
│ Persistent Index     │
└──────┬───────────────┘
       │
       ▼
┌──────────────────────┐
│ User Query           │
└──────┬───────────────┘
       │
       ▼
┌──────────────────────┐
│ Similarity Search    │
│ Top-K Retrieval      │
└──────┬───────────────┘
       │
       ▼
┌──────────────────────┐
│ LLM (Groq/OpenAI)    │
│ Context + Query      │
└──────┬───────────────┘
       │
       ▼
┌──────────────────────┐
│ Answer + Citations   │
└──────────────────────┘

pdf-rag-chatbot/
│
├── app.py
├── requirements.txt
├── LICENSE
├── README.md
├── QUICKSTART.md
├── .gitignore
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
└── app.log

📄 License

This project is licensed under the MIT License.

See the LICENSE file for details.

MIT License Summary

✅ Commercial use

✅ Modification

✅ Distribution

✅ Private use

❌ Liability

❌ Warranty

📞 Contact
Hithaish Y

Information Science Engineering Student

GitHub

https://github.com/hithaish-y

LinkedIn

https://www.linkedin.com/in/hithaish-y-9856562a1

<div align="center">
🚀 Hithaish PDF RAG Chatbot

Built with ❤️ by Hithaish Y

Python • LangChain • FAISS • Groq • Streamlit • HuggingFace

⭐ Star this repository if you find it useful!

</div> ```