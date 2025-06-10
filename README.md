# 📦 HTS AI Agent  
_Comprehensive Trade Intelligence System for the U.S. Harmonized Tariff Schedule (HTS)_

<div align="center">
  <!-- Technology Badges -->
  ![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python)
  ![LangChain](https://img.shields.io/badge/LangChain-0.0.305-yellow?style=for-the-badge)
  ![FAISS](https://img.shields.io/badge/FAISS-VectorStore-green?style=for-the-badge)
  ![Streamlit](https://img.shields.io/badge/Streamlit-UI-FF4B4B?style=for-the-badge&logo=streamlit)
  ![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)
</div>

---

## 📋 Table of Contents

1. [What Is HTS AI Agent?](#what-is-hts-ai-agent)  
2. [Why You’ll Love It](#why-youll-love-it)  
3. [Key Features](#key-features)  
4. [📂 Project Structure](#project-structure)  
5. [⚙️ Installation & Setup](#installation--setup)  
6. [🚀 Quick Start Guide](#quick-start-guide)  
7. [🔧 Detailed Usage](#detailed-usage)  
8. [🧠 Architecture Overview](#architecture-overview)  
9. [🤝 Contributing & License](#contributing--license)  
10. [👤 Author](#author)  

---

## 📌 What Is HTS AI Agent?

**HTS AI Agent** is an open-source Python tool designed to help importers, trade analysts, and supply-chain teams to:

- **Understand trade policies** (RAG-powered Q&A on General Notes)  
- **Compute import duties & landed costs** from real HTS codes  
- **Batch-process** multiple shipments at once  
- **Parse invoices** for automated rate lookups  

_All delivered via both a simple CLI and an interactive Streamlit dashboard._

---

## 💖 Why You’ll Love It

- **Beginner-Friendly**: Clear docs, easy setup, no prior AI experience needed.  
- **Accurate Calculations**: Leverages official HTS data and FAISS for semantic search.  
- **Extensible**: Modular code—add new parsers, export formats, or UI features with minimal effort.  

---

## ✨ Key Features

| 🔧 Feature                | 🚀 Benefit                                           |
|---------------------------|------------------------------------------------------|
| **Policy Q&A**            | Ask “What is the Generalized System of Preferences?” |
| **Duty Calculator**       | Get duties ($ per unit, % ad valorem, ¢/kg)          |
| **Batch Processing**      | Process hundreds of HTS codes in one command         |
| **Invoice Parsing**       | Extract product details and match HTS codes          |
| **Memory System**         | Remembers past queries to speed up follow-ups        |
| **Streamlit UI**          | Launch a web dashboard with `streamlit run app.py`   |
| **CLI Tool**              | Lightweight, scriptable interface for power users    |
| **Export Options**        | Save results as Excel, PDF or JSON reports           |

---

## 📂 Project Structure

```
HTSAgent-Task-Sivamani/
│
├── data/                  # Raw & processed data storage
│   ├── general_notes/     # HTS General Notes PDFs
│   ├── hts_csvs/          # Official HTS CSV files
│   └── vector_store/      # FAISS index & embeddings
│
├── scripts/               # Data ingestion & preprocessing
│   ├── ingest_data.py     # PDF → text chunks → embeddings
│   └── process_hts.py     # CSV → SQLite DB
│
├── tools/                 # Core functionality modules
│   ├── rag_tool.py        # RAG-based Q&A logic
│   ├── tariff_calculator.py  # Duty & landed cost calculator
│   ├── invoice_parser.py  # Invoice data extractor
│   └── memory_handler.py  # Query history manager
│
├── agent/                 # Agent orchestration
│   └── tariff_bot.py      # Main AI agent loop
│
├── app.py                 # Streamlit web application
├── main.py                # CLI entry point
├── requirements.txt       # Dependencies list
└── README.md              # This file
```

---

## ⚙️ Installation & Setup

1. **Clone the Repo**  
   ```bash
   git clone https://github.com/YourUsername/HTSAgent-Task-Sivamani.git
   cd HTSAgent-Task-Sivamani
   ```

2. **Create & Activate Virtual Environment**  
   ```bash
   python -m venv venv
   source venv/bin/activate   # Linux/macOS
   venv\Scriptsctivate      # Windows
   ```

3. **Install Dependencies**  
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Download Official Data**  
   - General Notes PDF & HTS CSVs from [hts.usitc.gov](https://hts.usitc.gov)

5. **Build Data Stores**  
   ```bash
   python scripts/ingest_data.py   # Preprocess General Notes
   python scripts/process_hts.py   # Load CSVs into SQLite
   ```

---

## 🚀 Quick Start Guide

### 1. Run a Policy Query (CLI)
```bash
python main.py --mode policy   --question "What is the Generalized System of Preferences?"
```

### 2. Calculate Duties (CLI)
```bash
python main.py --mode calculate   --hts 0101.30.00.00   --value 10000   --weight 500
```

### 3. Launch the Web Dashboard
```bash
streamlit run app.py
```
_Open your browser at_ `http://localhost:8501`

---

## 🧠 Architecture Overview

```
  [General Notes PDF]
           │
         ingest_data.py
           ▼
  [Text Chunks & Embeddings]
           │
         rag_tool.py
           ▼
      FAISS Vector Store
           ▲
tariff_calculator.py     sqlite: [HTS CSVs] → [Tariff DB]
           │                       ▲
           └──────────agent───────┘
                    ▲
             main.py / app.py
```

---


🎉 **You’re all set!**  
Feel free to open issues, submit PRs, and share feedback.