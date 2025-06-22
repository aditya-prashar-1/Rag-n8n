# 🔍 AI-Powered Agentic RAG System using n8n

![Workflow Diagram]
![image](https://github.com/user-attachments/assets/f481104b-057b-4116-854d-d4fd26804fd9)

## 📘 Overview

This project is a fully functional **Agentic RAG system** built on [n8n](https://n8n.io), integrating OpenAI's GPT models, Supabase, and Google Drive. It enhances the standard Retrieval-Augmented Generation (RAG) technique by introducing **intelligent tool selection**, **structured document storage**, and **automated multi-format file processing**.

> ⚙️ Developed for robust document question-answering over diverse file types like PDFs, CSVs, Google Docs, and Excel Sheets.

---

## ✨ Features

- 🧠 **Agentic RAG Reasoning** — Smart agent switches between RAG, SQL queries, or full-document reads.
- 🗂️ **Multi-format File Support** — Supports PDFs, DOCs, Sheets, CSVs, XLSX.
- 🔁 **Automated Document Ingestion** — Upload to a Google Drive folder and trigger the pipeline automatically.
- 🔗 **Supabase Vector Store Integration** — Stores document embeddings with pgvector.
- 🗃️ **Metadata + Row Storage** — Document metadata and tabular rows stored in Postgres for fast querying.
- 🧾 **Document Summarization** — Extracts key summaries from documents on upload.

---

## 🛠️ Tech Stack

- [n8n](https://n8n.io) — Workflow automation platform
- [OpenAI GPT-4 / Embeddings](https://platform.openai.com/docs) — LLM & vector embedding
- [Supabase](https://supabase.com) — Postgres + pgvector vector store
- [Google Drive](https://www.google.com/drive/) — Document source
- [LangChain](https://www.langchain.com) — Used via n8n integrations for RAG components

---

## 🧰 How It Works

1. **Trigger**: When a file is created or updated in a specific Google Drive folder.
2. **Format Detection**: File type is checked (PDF, Google Doc, Excel, etc.).
3. **Text Extraction**: Text is extracted from the file.
4. **Embedding Creation**: OpenAI embeddings are generated.
5. **Storage**:
   - Text chunks go to the `documents` vector DB table.
   - Tabular data (CSV/XLSX) goes to `document_rows` as JSONB.
   - Metadata goes to `document_metadata`.
6. **Chatbot Agent**: Users query through a chat interface, and the agent:
   - Performs RAG.
   - Switches to SQL if numerical/tabular answer needed.
   - Returns answers based on full document context.

---

## 🚀 Getting Started

### 1. Prerequisites

- n8n instance (cloud or self-hosted)
- Supabase project with Postgres + pgvector extension
- Google Drive API credentials
- OpenAI API key

### 2. Setup Instructions

1. **Clone this repository**  
   ```bash
   git clone https://github.com/your-username/agentic-rag-n8n.git
   cd agentic-rag-n8n
