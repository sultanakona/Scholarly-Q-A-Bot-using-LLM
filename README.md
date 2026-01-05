# PaperGPT
_A professional, LLM-powered Research Paper Question Answering System_  
(Recommended repo name — original repo: `sultanakona/Scholarly-Q-A-Bot-using-LLM`)

---

PaperWise-QA (aka ScholarRAG / ResearchGPT-QA) is a Retrieval-Augmented Generation (RAG) system for asking questions about research papers. It combines a large language model (LLM) with a vector store (FAISS) and the QASPER dataset to produce evidence-based answers that reference paper passages. Built for long-form scholarly documents, PaperWise-QA is resume- and interview-ready.

Quick highlights
- Powered by QASPER dataset (paper Q&A pairs)
- Retrieval with FAISS (RAG pipeline)
- Supports long research papers (chunking & context handling)
- Evidence-backed answers with citations (source passages & locations)
- Clean, professional name suitable for GitHub, resume and posters

---

## Repo name & branding suggestions
Primary recommendation (resume / recruiter friendly):
- Repository name: `PaperWise-QA`
- Tagline: "An LLM-powered Research Paper Question Answering System"

Alternative professional names:
- ScholarRAG
- ResearchGPT-QA
- PaperRAG

Beginner / descriptive:
- ResearchPaperQA
- PaperQABot

Top 3 picks:
1. PaperWise-QA
2. ScholarRAG
3. PaperRAG

Poster / cover title:
- PaperWise-QA — LLM + RAG for Scholarly Q&A

Resume bullet (copy-ready):
- "Built PaperWise-QA: a Retrieval-Augmented LLM system using FAISS + QASPER to answer and cite complex research-paper questions; implemented chunking for long documents and produced evidence-backed responses."

---

## Features
- Retrieval-Augmented Generation (RAG) over scholarly articles
- FAISS vector store for fast similarity search
- Handles long documents via adaptive chunking & context-length management
- Evidence-based answers: returned responses include supporting passages and locations
- Configurable LLM backends (OpenAI, local LLMs, or other API providers)
- Demo-ready: instructions included for local run and Hugging Face Spaces deployment

---

## Architecture (high-level)
1. Ingest PDFs / paper text → text extraction and normalization
2. Chunk long documents into overlapping passages (configurable chunk size & overlap)
3. Generate embeddings for each passage (chosen embedder)
4. Index embeddings in FAISS
5. At query time: retrieve top-k passages, pass retrieved context + user question to LLM
6. LLM composes an answer with cited evidence (passage IDs/pages)

Components:
- Dataset: QASPER (question-answer pairs extracted from papers)
- Retriever: FAISS (vector similarity search)
- Generator: LLM (OpenAI GPT-family or alternative)
- Orchestration: RAG pipeline glue code (query → retrieve → generate → cite)

---

## Quickstart (local)
Prerequisites:
- Python 3.8+
- pip
- Environment variables for LLM provider (e.g., `OPENAI_API_KEY`) if using hosted LLMs

Install:
```bash
git clone https://github.com/sultanakona/Scholarly-Q-A-Bot-using-LLM.git
cd Scholarly-Q-A-Bot-using-LLM
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Prepare data & index:
- Place PDFs / extracted text into a data folder or use the included QASPER loader.
- Run the indexing script:
```bash
python scripts/build_index.py --data-dir data/papers --output faiss_index/
```
(Options: chunk size, overlap, embedder model, etc.)

Run the app (example using a simple Gradio/Flask UI):
```bash
python app.py --index-path faiss_index/ --llm-provider openai
# or
python app.py --index-path faiss_index/ --llm-provider local
```

Example query flow:
- Enter question in UI (or call API)
- System retrieves top-k evidence passages and composes answer with citations
- Response includes supporting passages + confidence / token usage (if available)

---

## Dataset & Analysis
- Primary dataset: QASPER (question-answer pairs over research papers)
- Exploratory analysis examples (visualizations):
  - Context length distribution
  - Question vs Answer length scatter plots
  - Top question words histogram

Tip: Use analysis scripts (`notebooks/analysis.ipynb`) to inspect question lengths, answer lengths, and common tokens to tune chunking and retrieval parameters.

---

## Configuration & Tuning
Key knobs to tune:
- Chunk size & overlap: affects retrieval quality for long papers
- Embedding model: semantic quality vs cost/speed
- Retriever `k` (number of passages returned)
- Prompt template / system instructions for the LLM (control grounding & citation style)

Recommended defaults (starting point):
- chunk_size = 1000 tokens, overlap = 200 tokens
- top_k = 8
- embedder: sentence-transformers or OpenAI embeddings
- generator: GPT-3.5/GPT-4 or an open LLM for privacy/cost-control

---

## Deployment
- For public demos: deploy the app to [Hugging Face Spaces](https://huggingface.co/spaces) using Gradio and GPU if needed.
- For production: containerize with Docker and serve behind an API gateway; optionally use managed vector DBs if scaling beyond FAISS.

Example: Deploy to HF Spaces
- Add `app.py`, `requirements.txt`, and optionally a `runtime.txt`
- Commit and push; follow Hugging Face Spaces docs to enable a GPU-backed instance

---

## Examples (prompts & expected behavior)
User: "What is the main contribution of the paper X?"
- Retrieval: top-5 passages containing contribution/abstract/method sections
- Generation: concise summary with quoted passages and page/section citations

User: "Cite the evaluation metrics and dataset used."
- System returns the metrics paragraph plus source (e.g., "Table 2, page 7") and the linked passage.

---

## Project Structure (suggested)
- app.py — main app + API
- scripts/
  - build_index.py — ingest, chunk, embed, index
  - evaluate_retrieval.py — retrieval metrics
- notebooks/analysis.ipynb — dataset & question analysis visuals
- data/ — sample papers / processed text
- faiss_index/ — generated index files
- requirements.txt
- README.md

---

## Contribution
Contributions welcome! Suggested ways to help:
- Improve PDF text extraction (layout-preserving)
- Add new embedding models / retrievers (Milvus, Pinecone)
- Add multi-document QA and citation formatting
- Benchmarks & automatic evaluation against QASPER test splits

---

## License
Choose an appropriate license for your project (e.g., MIT). If using third-party data/models, ensure compatibility.

---

## Contact / Attribution
Built by: sultanakona (original repo: `sultanakona/Scholarly-Q-A-Bot-using-LLM`)  
If you'd like, I can also:
- Rename the repository and prepare the GitHub rename steps
- Create a polished tagline, resume bullet, and poster cover image text
- Produce a short README badge pack and release notes

---

Appendix — Suggested one-line README header (copy-ready)
> PaperWise-QA — An LLM-powered Research Paper Question Answering System using the QASPER dataset, FAISS retrieval, and evidence-backed RAG answers.
