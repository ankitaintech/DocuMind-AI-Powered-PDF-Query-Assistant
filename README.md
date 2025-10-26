# DocuMind — AI-Powered Multi-PDF Query Assistant

---

## Project Overview
DocuMind is an AI-powered PDF knowledge assistant that enables users to interact with one or more PDFs in a contextual and intelligent way.  
It leverages Retrieval-Augmented Generation (RAG) to extract relevant information from documents and provide precise answers while tracking citations and sources.

---

## Problem Statement
Tools like ChatPDF, ChatDOC, and Humata allow users to query PDFs using AI, but they often face several limitations:

- Weak context retention when handling long, multi-section documents
- Lack of explainability or traceable citations for answers
- Inability to work with multiple PDFs simultaneously
- Generic, surface-level summaries instead of contextual insights

These challenges create a need for a smarter, context-aware, multi-document assistant that can understand, summarize, and answer questions grounded in real document content.

---

## Solution Summary
DocuMind addresses these limitations by providing:

- **Multi-PDF Support:** Users can upload multiple PDFs, and DocuMind indexes all content for unified querying.
- **RAG-Powered Search:** Uses FAISS vector store to retrieve the most relevant chunks from uploaded documents.
- **LLM-Powered Answers:** Google Gemini 2.5 generates concise, factual answers based on the retrieved context.
- **Citations & Explainability:** Every answer is grounded in document references with page numbers, file names, and confidence scores.
- **Web-Based Interface:** Streamlit UI allows users to upload, query, and view citations in a clean, interactive manner.

The system works end-to-end, combining AI retrieval and generative capabilities with a structured, user-friendly interface.

---

## Tech Stack
- **Backend:** Python, FastAPI  
- **Frontend:** Streamlit  
- **Vector Database:** FAISS  
- **LLM / AI Models:** Google Gemini 2.5 (Generative Language API)  
- **Cloud / Hosting:** Local / Optional deployment on Render / Vercel  
- **Version Control:** Git + GitHub  

---

## Project Structure
```
.
├── backend/
│   ├── __pycache__/             # Python's cached bytecode (ignored by Git)
│   ├── app.py                   # Main API/Logic entry point (e.g., FastAPI)
│   ├── embeddings.py            # Code for generating text embeddings
│   ├── pdf_reader.py            # Logic for parsing and extracting text from PDFs
│   ├── processor.py             # Core processing logic
│   ├── requirements.txt         # Python dependencies for the backend
│   └── vectorstore.py           # Module for managing the vector database
├── frontend/
│   ├── requirements.txt         # Python dependencies for the frontend
│   └── streamlit_app.py         # The Streamlit application interface
├── uploaded_pdfs/               # Directory for storing user-uploaded documents (IGNORED)
├── .env                         # Environment variables (API keys, secrets, etc. - IGNORED)
├── .env.example                 # Template for setting up environment variables
├── .gitignore                   # Specifies files/directories to ignore in Git
├── README.md                    # Project documentation, this file
└── .venv-backend, .venv-frontend # Virtual environment directories (IGNORED)
```

---

## Setup Instructions
Follow these exact steps to run your project locally.
```bash or terminal
# 1. Clone the repository
git clone https://github.com/ankitaintech/DocuMind-AI-Powered-PDF-Query-Assistant.git
cd DocuMind-AI-Powered-PDF-Query-Assistant
# 2. Create and activate virtual environment for backend seperately and install dependencies
python -m venv .venv-backend
.venv-backend\Scripts\activate
pip install -r backend/requirements.txt
# 3. Create and activate virtual environment for frontend and install dependencies
python -m venv .venv-frontend
.venv-frontend\Scripts\activate
pip install -r frontend/requirements.txt
# 4. To switch the environment
deactivate
# 5. Set Up Local Environment
copy .env.example .env 
""" Open the newly created .env file and update the placeholder values.
Replace your_gemini_api_key_here with your actual Google Gemini API Key."""
# 6. Run the backend (FastAPI)
uvicorn backend.app:app --reload
# 7. Run the frontend (Streamlit)
streamlit run frontend/streamlit_app.py
```
---

## Deployment
app can be run locally using the setup steps mentioned above.

---

## Demo Video
**YouTube Link:**
`https://youtu.be/your-demo-link`
> This demo video clearly show:
> - How the 

---

## Features
- Upload and query multiple PDFs simultaneously
- RAG-powered contextual retrieval for long documents
- Google Gemini-powered generative answers
- Automatic citation tracking with file names, page numbers, and confidence scores
- Clean, interactive Streamlit interface

---

## 🧩 Technical Architecture
Workflow:
1. Upload PDFs: Users upload one or more documents via Streamlit UI.
2. PDF Processing: Backend extracts text, splits into chunks, and generates embeddings.
3. Vector Storage: FAISS indexes embeddings for fast semantic retrieval.
4. Query Handling: User query is converted into embeddings and relevant chunks are retrieved.
5. Answer Generation: Retrieved chunks + user query are sent to Google Gemini LLM to generate a concise answer.
6. Citations: Each answer is accompanied by file name, page number, rank, and score for traceability.
7. Frontend Display: Streamlit shows answer and a collapsible list of grounded citations.

ASCII Diagram:

User → Streamlit UI → FastAPI Backend → FAISS Vector Store
                              ↓
                          Google Gemini
                              ↓
                           Answer + Citations
                              ↓
                          Displayed to User

---

## 🧾 References
- [OpenAI API](https://platform.openai.com/)
- [LangChain Documentation](https://python.langchain.com)
- [Hugging Face Datasets](https://huggingface.co/datasets)
- [FAISS Library](https://github.com/facebookresearch/faiss)

---

## Acknowledgements
- Google Generative AI API (Gemini)
- GitHub Copilot for resolving module related errors 
- FAISS library for vector search
- Streamlit for rapid frontend prototyping
- Hugging Face and Sentence Transformers for embeddings and data processing