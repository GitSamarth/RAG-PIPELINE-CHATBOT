# RAG-PIPELINE-CHATBOT
# 📄 n8n RAG Pipeline & Chatbot Template

This is a **No-Code AI Agent** template built with **n8n** that turns any Google Drive folder into a **knowledge base** for a chatbot.  
When you drop documents into the folder, the system automatically updates the chatbot’s knowledge so it can answer questions based on the new content.

---

## 🚀 Overview

- **Trigger**: Google Drive folder (named `FAQ`)  
- **Pipeline**:  
  1. Detect new document uploads (PDF, DOCX, TXT, etc.)  
  2. Download the file  
  3. Extract & embed the content using **OpenAI embeddings**  
  4. Store embeddings in **Pinecone** (namespace: `faq`)  
- **Chatbot**:  
  - Uses an **AI Agent** in n8n  
  - Powered by any **OpenRouter** LLM model  
  - Retrieves relevant document chunks from Pinecone before responding

---

## ✨ Features

- Works with **any document type** supported by Google Drive
- Fully automated — no manual uploading or re-indexing
- Uses **vector search** for accurate, context-based answers
- Flexible — choose **any OpenRouter LLM model**
- No coding required — built entirely in **n8n**

---

## 📋 Prerequisites

Before using this template, you should have:

- A **basic understanding of n8n** workflows and nodes
- Google Drive API access
- Accounts for:
  - **Pinecone** (vector store)
  - **OpenAI** (for embeddings)
  - **OpenRouter** (for chatbot model access)

---

## 🛠️ How It Works

1. **Google Drive Trigger Node**  
   - Watches the `FAQ` folder for new files.  
   - When a new document is added, retrieves its file ID and name.

2. **Google Drive Download Node**  
   - Downloads the file for processing.

3. **Default Data Loader**  
   - Reads the document content (PDF, DOCX, TXT, etc.)  
   - Converts it into text for embedding.

4. **OpenAI Embeddings Node**  
   - Generates vector representations of the document text.

5. **Pinecone Vector Store Node**  
   - Stores embeddings in the namespace `faq`.

6. **AI Agent (Chatbot)**  
   - Listens for chat inputs inside n8n  
   - Uses OpenRouter to call your chosen LLM  
   - Retrieves context from Pinecone before generating the final response.

---

## ⚡ Getting Started

1. Import this workflow template into n8n.  
2. Connect your credentials:
   - **Google Drive API**
   - **Pinecone API**
   - **OpenAI API**
   - **OpenRouter API**
3. Change the folder name in the **Google Drive Trigger** to your desired name (default is `FAQ`).
4. Activate the workflow.
5. Upload a document to the folder and start chatting with your AI agent.

---

## 💬 Usage Example

**Uploaded File:**  
`Policy and FAQ Document.pdf` containing store policies and FAQs.

**User Query:**  
> "What is our warranty policy?"

---

## 📌 Notes

- All embeddings are stored under the namespace `faq` in Pinecone.
- You can swap out the OpenRouter model without changing the workflow.
- This template is designed for **learning purposes** and as a **starter project** for building RAG-powered chatbots in n8n.
