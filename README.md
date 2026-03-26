earch Paper Assistant Agent
----------------------------------
🎓 Master’s Final Project — LLM Course

  Model Used: mistral:7b-instruct
  Frameworks: FastAPI · LangChain · Ollama · FAISS · ChromaDB
  Hardware Used: NVIDIA RTX 3090 (24 GB VRAM)


📘 Overview

  Research Paper Assistant Agent is a natural language–driven research assistant that helps users manage and analyze academic papers using an LLM-powered backend.
  It enables paper uploading, internal/external searching, and automatic comparison report generation — all through natural language commands.
  
  The agent integrates Retrieval-Augmented Generation (RAG) and ReAct (Reasoning + Acting) frameworks to dynamically interpret intent and call the appropriate tools for each user query.
  
  This project was developed and tested locally on an NVIDIA RTX 3090 GPU, using Ollama to serve the mistral:7b-instruct model efficiently.


⚙️ Core Features
-----------------
✅ Required Functions

  1. Internal Paper Search — Search uploaded papers stored in the local database and FAISS vector store.
  
  2. Upload PDF Paper — Upload papers from local disk or directly from the internet (e.g., arXiv link).
  
  3. Web Search for Recent Papers — Fetch recent papers from online databases such as arXiv and Semantic Scholar.
  
  4. Paper Comparison and Report Generation — Compare two papers and generate a structured report including goals, methods, and findings.


💡 Extra Functions

  Uploaded papers are stored locally and can be reopened via generated links.
  
  Retrieved papers (from APIs) are stored temporarily in memory for later comparison.
  
  Comparison reports can be exported to PDF.
  
  Display all uploaded papers stored in the local database.
  
  | Component             | Technology                         |
  | --------------------- | ---------------------------------- |
  | **Backend Framework** | FastAPI                            |
  | **Frontend Template** | HTML + JavaScript                  |
  | **Database**          | SQLite (via SQLAlchemy ORM)        |
  | **Vector Store**      | FAISS + ChromaDB                   |
  | **Embeddings**        | `hkunlp/instructor-xl`             |
  | **Language Model**    | `mistral:7b-instruct` (via Ollama) |
  | **PDF Parsing**       | PyMuPDF (fitz), pdfplumber         |
  | **External APIs**     | arXiv API, Semantic Scholar API    |
  | **Hardware**          | NVIDIA RTX 3090 GPU                |

🧱 Project Structure
---------------------

    paper_assistant_agent/
    │
    ├── app.py                  # FastAPI backend with LLM agent and tools
    ├── requirements.txt        # Required Python dependencies
    ├── templates/
    │   └── index.html          # Frontend web interface
    └── README.md


(After running, the following are auto-created:)

    ├── research_papers.db      # SQLite database
    ├── uploaded_papers/        # Folder for uploaded PDFs
    ├── chroma_db/              # Chroma persistence folder
    └── faiss_memory_index/     # FAISS vector store

🚀 How to Run the Project
-------------------------
1️⃣ Create a Python Environment

    python -m venv venv
    source venv/bin/activate  # or venv\Scripts\activate on Windows

2️⃣ Install Dependencies

    pip install -r requirements.txt

3️⃣ Run the App

    uvicorn app:app --reload

4️⃣ Access the Web Interface

  Open your browser and visit:http://127.0.0.1:8000

You can now chat with the Research Paper Assistant through the interactive web interface.

💬 Demo Usage

🧩 Scenario 1

1. Upload paper from https://arxiv.org/abs/2505.10562
2. Find recent papers about vision tokenizers
3. Compare between the uploaded paper and the third paper found

🧠 The agent automatically downloads the paper, searches for related work, and generates a structured comparison.

🤖 Scenario 2

1. Find the latest papers about AI Agent
2. Upload paper from https://arxiv.org/abs/2406.00477v1
3. Compare between the uploaded paper and the first paper found

🧠 The assistant identifies both papers, extracts their abstracts, and produces a detailed comparison report.

🖼️ Example Screenshots
----------------------
  Main chat interface with the research assistant.
  <img width="1368" height="690" alt="image" src="https://github.com/user-attachments/assets/c7292351-f3e1-49f7-827a-4af15d0adf9c" />

  
  <img width="36" height="40" alt="image" src="https://github.com/user-attachments/assets/dae8f4c0-f908-4180-8352-f44b8a5f86d6" />This icon to expand or 
collapse the sidebar which contains all uploaded papers in database with its details.

after expanding, it will show all uploaded papers, as:
<img width="1248" height="586" alt="image" src="https://github.com/user-attachments/assets/9422cd18-0300-4b1d-8bff-f0463f7c10eb" />



  <img width="34" height="28" alt="image" src="https://github.com/user-attachments/assets/49735353-a545-4a44-8993-81d4a58eb3c9" /> This icon to switch 
between dark and light theme.

And in dark theme it can show as: 
<img width="1268" height="598" alt="image" src="https://github.com/user-attachments/assets/8edde607-7382-4846-b2ac-08b78e3d0f6b" />

⚙️ System Requirements
-----------------------
| Component      | Recommended                  |
| -------------- | ---------------------------- |
| **OS**         | Ubuntu 22.04 / Windows 11    |
| **GPU**        | NVIDIA RTX 3090 (24 GB VRAM) |
| **Python**     | 3.10 or later                |
| **RAM**        | ≥ 16 GB                      |
| **Disk Space** | ≥ 5 GB for database + papers |

🧠 System Behavior Overview
---------------------------
| User Query                                                      | Agent Action                                       |
| --------------------------------------------------------------- | -------------------------------------------------- |
| “Find papers about self-supervised learning for robotics.”      | Searches internal FAISS + SQL database.            |
| “Upload this paper from arXiv.”                                 | Downloads, parses, stores, and indexes the paper.  |
| “Find recent ACL papers about multilingual transformers.”       | Fetches papers via arXiv or Semantic Scholar APIs. |
| “Compare my uploaded paper with the first web paper you found.” | Generates structured comparison report.            |

🧰 Tools (LangChain Integration)
---------------------------------
| Tool Name                                         | Function                                   |
| ------------------------------------------------- | ------------------------------------------ |
| `upload_paper_from_path_or_url`                   | Upload local or online papers              |
| `search_MY_LOCAL_LIBRARY_of_papers`               | Search papers stored in the local database |
| `search_ONLINE_ACADEMIC_DATABASES_for_new_papers` | Retrieve new papers via APIs               |
| `compare_papers_and_generate_report`              | Compare two papers and summarize findings  |

🗃️ Database Schema
-------------------
    CREATE TABLE papers (
        id INTEGER PRIMARY KEY,
        title TEXT NOT NULL,
        abstract TEXT,
        source TEXT,
        file_path TEXT,
        source_path TEXT,
        created_at DATETIME DEFAULT CURRENT_TIMESTAMP
    );

🧑‍💻 Author & Academic Info
------------------------------
  **Author:** Salma Morsy  
  **Institution:** National Taiwan University of Science and Technology (NTUST)  
  **Program:** Master’s Degree — LLM Course  
  **Project:** Final Submission — Research Paper Assistant Agent  

🏷️ Suggested GitHub Tags
      LLM · LangChain · FastAPI · Ollama · RAG · Research Assistant · arXiv · Semantic Scholar · RTX3090


✅ Repository Contents
----------------------
    paper_assistant_agent/
    │
    ├── app.py
    ├── requirements.txt
    ├── templates/
    │   └── index.html
    └── README.md

(Auto-generated at runtime:)
    research_papers.db
    uploaded_papers/
    chroma_db/
    faiss_memory_index/


