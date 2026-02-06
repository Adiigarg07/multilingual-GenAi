# 🌍 Multilingual FAQ Assistant with FAISS & ScaleDown

An **AI-powered multilingual FAQ question-answering system** that combines **semantic search (FAISS)**, **sentence embeddings**, **machine translation**, and **ScaleDown prompt compression** to deliver accurate answers efficiently with reduced token usage.

This project is **Colab-ready**, hackathon-friendly, and designed with **production-safe fault tolerance**.

---

## 🚀 Key Features

* 🔍 **Semantic Search** using FAISS (Inner Product / Cosine similarity)
* 🧠 **Sentence Transformers** for multilingual embeddings
* 🌐 **Multilingual Input & Output** (English, Hindi, Spanish, French, German)
* ✂️ **ScaleDown API Integration** for prompt compression & cost optimization
* 🛡️ **Fault-Tolerant Design** (automatic fallback if ScaleDown fails)
* 📄 **CSV-based Knowledge Base** (easy to extend)
* ⚡ **Fast & Lightweight** (CPU-only compatible)

---

## 🧩 Architecture Overview

```
User Query (Any Language)
        ↓
Translate → English
        ↓
ScaleDown (Optional Prompt Compression)
        ↓
Sentence Embedding (MiniLM)
        ↓
FAISS Semantic Search
        ↓
Best Answer Retrieved
        ↓
Translate → Output Language
```

ScaleDown is used as an **optional optimization layer**. If unavailable, the system automatically falls back to the original prompt.

---

## 🛠️ Tech Stack

* **Python 3**
* **Google Colab**
* **Sentence-Transformers** (`paraphrase-multilingual-MiniLM-L12-v2`)
* **FAISS (CPU)**
* **HuggingFace Transformers** (MarianMT)
* **ScaleDown API** (Prompt Compression)
* **Pandas / NumPy**

---

## 📦 Installation (Colab)

```bash
pip install -q torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
pip install -q sentence-transformers faiss-cpu transformers pandas langdetect requests
```

---

## 📂 Knowledge Base Format

The system expects a CSV file (e.g. `kb_1000_faqs.csv`) with the following columns:

| column   | description          |
| -------- | -------------------- |
| question | FAQ question text    |
| answer   | Corresponding answer |

---

## 🔑 ScaleDown API Setup

To enable prompt compression:

1. Obtain a **valid ScaleDown API key**
2. Set it in the notebook:

```python
SCALEDOWN_API_KEY = "YOUR_API_KEY"
```

### ⚠️ Important

* If the API key is **invalid, expired, or restricted**, the system will **log a warning** and continue using the original prompt.
* This ensures **zero downtime** and uninterrupted QA behavior.

---

## 🔁 ScaleDown Response Handling

The project supports **multiple ScaleDown API response formats**:

* New nested format (`results.compressed_prompt`)
* Older flat format (`compressed_prompt`)

Defensive parsing is used to prevent runtime errors if the API schema changes.

---

## ▶️ Running the Assistant

1. Upload the CSV knowledge base
2. Choose output language:

```
en = English
hi = Hindi
es = Spanish
fr = French
de = German
```

3. Ask questions interactively:

```
Ask your question (type 'exit' to quit): how to reset a password?
```

---

## ✅ Example Output

```
Matched Question: How can I reset my password?
Answer: Click on Forgot Password on the login page and follow the instructions.
```

---

## 🧠 Design Philosophy

* **Accuracy first**: Semantic retrieval over keyword matching
* **Cost-aware AI**: ScaleDown reduces token usage while preserving intent
* **Resilient systems**: External APIs never block core functionality
* **Extensible**: Easy to add languages, data, or LLMs

---

## 🏆 Ideal For

* Hackathons & demos
* AI agents & RAG systems
* Multilingual customer support bots
* FAQ automation
* AI cost-optimization experiments

---

## 📌 Future Improvements

* 📊 Token savings dashboard
* 🔁 Retry & backoff for ScaleDown
* 🧪 Offline mock compression mode
* 🧠 LLM-based answer generation (RAG)
* 🌐 Web UI / API service




---

## 🙌 Acknowledgements

* HuggingFace 🤗
* Facebook AI (FAISS)
* ScaleDown Team

---

> *Built with a focus on reliability, multilingual access, and real-world AI optimization.*
# multilingual-GenAi
