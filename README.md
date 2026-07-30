# 🤖 AI Meeting Intelligence Assistant

An end-to-end **AI-powered meeting intelligence system** that transforms meeting recordings, YouTube videos, and audio/video files into structured, actionable insights. The system uses **Whisper and Sarvam AI for transcription**, **LLMs for summarization and information extraction**, and **Retrieval-Augmented Generation (RAG)** for grounded question answering over meeting content.

---

## 🚀 Overview

Meetings contain valuable information such as decisions, action items, deadlines, responsibilities, and follow-ups that can be difficult to track manually.

The **AI Meeting Intelligence Assistant** automates this process by:

* 🎙️ Transcribing meeting audio/video
* 📝 Generating AI-powered meeting summaries
* 🔍 Extracting important meeting information
* 🧠 Enabling context-aware question answering
* 📌 Identifying action items and assigned owners
* ⏰ Extracting deadlines and follow-ups
* 💬 Providing an interactive Streamlit interface
* 📄 Generating structured meeting reports

The project combines **Speech-to-Text, Large Language Models, Embeddings, Vector Databases, and RAG** into a complete end-to-end AI application.

---

## ✨ Key Features

### 🎙️ Audio & Video Transcription

Supports multiple input sources:

* YouTube videos
* Audio files
* Video files

The application uses **OpenAI Whisper** and **Sarvam AI** to convert spoken content into text transcripts.

---

### 📝 AI-Powered Meeting Summarization

The system processes meeting transcripts using LLMs to generate concise and structured summaries containing:

* Meeting overview
* Key discussion points
* Important topics
* Major decisions
* Conclusions
* Next steps

---

### 🧠 Retrieval-Augmented Generation (RAG)

A RAG pipeline enables users to ask questions about meetings while grounding responses in the actual transcript.

```text
Meeting Transcript
        ↓
Text Chunking
        ↓
HuggingFace Embeddings
        ↓
ChromaDB Vector Store
        ↓
Semantic Retrieval
        ↓
Relevant Context
        ↓
LLM
        ↓
Grounded Answer
```

This allows the assistant to retrieve relevant information from long meeting transcripts before generating an answer.

---

### 📌 Automated Information Extraction

The system automatically extracts:

* ✅ Action items
* 👤 Responsible owners
* 📅 Deadlines
* 🎯 Key decisions
* ❓ Open questions
* 🔄 Follow-up tasks

Example:

```text
Action Item: Prepare the project proposal
Owner: Rahul
Deadline: August 5
Status: Pending
```

---

### 💬 Context-Aware Question Answering

Users can ask natural-language questions about the meeting, such as:

```text
What were the main decisions made?

Who is responsible for preparing the project proposal?

What deadlines were mentioned?

What issues are still unresolved?

What are the next steps?
```

The RAG pipeline retrieves relevant transcript sections and provides context-grounded answers.

---

### 📊 Streamlit Interface

The project includes an interactive **Streamlit web application** for:

* Uploading audio/video files
* Processing YouTube videos
* Viewing transcripts
* Generating summaries
* Extracting action items
* Asking questions about meetings
* Generating structured meeting reports

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │ YouTube / Audio /    │
                    │ Video Input          │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Speech-to-Text        │
                    │ Whisper / Sarvam AI   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Meeting Transcript   │
                    └──────────┬───────────┘
                               │
                 ┌─────────────┼─────────────┐
                 │             │             │
                 ▼             ▼             ▼
          ┌────────────┐ ┌────────────┐ ┌──────────────┐
          │ Summary    │ │ Information│ │ Text         │
          │ Generation │ │ Extraction │ │ Chunking     │
          └────────────┘ └────────────┘ └──────┬───────┘
                                               │
                                               ▼
                                    ┌────────────────────┐
                                    │ HuggingFace        │
                                    │ Embeddings         │
                                    └─────────┬──────────┘
                                              │
                                              ▼
                                    ┌────────────────────┐
                                    │ ChromaDB           │
                                    │ Vector Database    │
                                    └─────────┬──────────┘
                                              │
                                      User Question
                                              │
                                              ▼
                                    ┌────────────────────┐
                                    │ Semantic Retrieval │
                                    └─────────┬──────────┘
                                              │
                                              ▼
                                    ┌────────────────────┐
                                    │ LLM + Context      │
                                    └─────────┬──────────┘
                                              │
                                              ▼
                                    ┌────────────────────┐
                                    │ Grounded Answer    │
                                    └────────────────────┘
```

---

## 🛠️ Tech Stack

| Technology      | Purpose                                  |
| --------------- | ---------------------------------------- |
| **Python**      | Core programming language                |
| **Whisper**     | Speech-to-text transcription             |
| **Sarvam AI**   | Speech and language processing           |
| **LLMs**        | Summarization and information extraction |
| **LangChain**   | RAG pipeline orchestration               |
| **HuggingFace** | Text embeddings                          |
| **ChromaDB**    | Vector database and semantic search      |
| **Streamlit**   | Interactive web application              |
| **YouTube**     | Video input source                       |

---

## 📂 Project Structure

```text
AI-Meeting-Intelligence-Assistant/
│
├── app.py
├── requirements.txt
├── README.md
├── .env
│
├── data/
│   ├── audio/
│   ├── video/
│   └── transcripts/
│
├── modules/
│   ├── transcription.py
│   ├── summarization.py
│   ├── extraction.py
│   └── rag.py
│
└── chroma_db/
```

> The exact structure may vary depending on the implementation.

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd AI-Meeting-Intelligence-Assistant
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

### 3. Activate the Virtual Environment

**Windows PowerShell:**

```powershell
venv\Scripts\activate
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Variables

Create a `.env` file in the project root:

```env
SARVAM_API_KEY=your_sarvam_api_key
HUGGINGFACE_API_KEY=your_huggingface_api_key
```

Add any additional API keys required by your selected LLM provider.

### ⚠️ Security

Never commit API keys or `.env` files to GitHub.

Add the following to `.gitignore`:

```text
.env
venv/
__pycache__/
chroma_db/
```

---

## ▶️ Running the Application

Start the Streamlit application using:

```bash
streamlit run app.py
```

The application will open in your default browser.

---

## 🔄 Application Workflow

### Step 1 — Input

Provide a YouTube video or upload an audio/video file.

### Step 2 — Transcription

The application processes the audio and generates a transcript using Whisper and/or Sarvam AI.

### Step 3 — Transcript Processing

The transcript is cleaned and divided into meaningful chunks.

### Step 4 — Embedding Generation

HuggingFace embedding models convert transcript chunks into vector representations.

### Step 5 — Vector Storage

The generated embeddings are stored in **ChromaDB** for semantic retrieval.

### Step 6 — Meeting Intelligence

The LLM analyzes the transcript and generates:

* Meeting summary
* Key decisions
* Action items
* Responsible owners
* Deadlines
* Open questions
* Follow-ups

### Step 7 — RAG Question Answering

When the user asks a question:

```text
User Question
      ↓
Question Embedding
      ↓
Similarity Search
      ↓
Relevant Transcript Chunks
      ↓
Context + Prompt
      ↓
LLM
      ↓
Grounded Answer
```

---

## 💡 Example Output

### Meeting Summary

```text
The team discussed the upcoming product release,
development progress, testing requirements, and
deployment timeline.
```

### 🎯 Key Decisions

* Release candidate testing will begin next week.
* Deployment will be performed in stages.
* QA approval is required before production release.

### 📌 Action Items

| Action                  | Owner              | Deadline |
| ----------------------- | ------------------ | -------- |
| Complete testing        | QA Team            | August 5 |
| Prepare deployment plan | DevOps             | August 7 |
| Finalize documentation  | Documentation Team | August 8 |

### ❓ Open Questions

* Is the production environment ready?
* Are all critical bugs resolved?
* Has the deployment plan been finalized?

---

## 🧠 RAG Pipeline

The RAG implementation follows these major stages:

```text
Documents
    ↓
Text Splitter
    ↓
Embeddings
    ↓
ChromaDB
    ↓
Retriever
    ↓
Relevant Documents
    ↓
Prompt + Context
    ↓
LLM
    ↓
Context-Grounded Answer
```

Instead of passing the entire transcript to the LLM for every question, the system retrieves the most relevant transcript chunks using semantic similarity.

This improves the relevance of responses and makes the system more suitable for working with lengthy meeting transcripts.

---

## 🎯 Use Cases

The AI Meeting Intelligence Assistant can be useful for:

* 👨‍💼 Business meetings
* 👩‍💻 Software development meetings
* 📊 Project discussions
* 🎓 Academic meetings
* 🤝 Client meetings
* 📋 Team stand-ups
* 🧑‍💼 Interviews and discussions
* 📝 Research meetings

---

## 📈 Future Improvements

Potential enhancements include:

* 👥 Speaker diarization
* 🌐 Multilingual meeting support
* 📧 Automated follow-up email generation
* 📅 Calendar integration
* 🔔 Automated deadline reminders
* 📊 Meeting analytics dashboard
* 🧾 PDF meeting report generation
* 🔎 Improved semantic search
* 🤖 Agent-based meeting workflows
* 🗣️ Real-time meeting transcription
* 🔐 User authentication and secure data storage

---

## 🧑‍💻 Skills Demonstrated

This project demonstrates practical experience with:

* Python Development
* Natural Language Processing
* Large Language Models
* Speech-to-Text
* Retrieval-Augmented Generation
* Semantic Search
* Vector Databases
* Text Embeddings
* LangChain
* HuggingFace
* ChromaDB
* Prompt Engineering
* Information Extraction
* Streamlit
* End-to-End AI Application Development

---

## 📌 Project Highlights

* Built an end-to-end **AI Meeting Intelligence Assistant** for processing YouTube videos and audio/video recordings.
* Integrated **Whisper and Sarvam AI** for automated speech transcription.
* Developed a **Retrieval-Augmented Generation pipeline** using LangChain, HuggingFace embeddings, and ChromaDB.
* Enabled **context-grounded question answering** over meeting transcripts.
* Automated extraction of **action items, owners, deadlines, key decisions, open questions, and follow-ups**.
* Developed an interactive **Streamlit interface** for meeting analysis and structured report generation.

---

## 👩‍💻 Author

**Yashashwini Siwach**

**B.Tech — Computer Science & Engineering (Information Security)**
**Vellore Institute of Technology**

Interested in **Data Analytics, Machine Learning, AI, and Software Engineering**.

---

## 📜 License

This project is intended for educational and portfolio purposes.
