# PaperWise-QA
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

Screenshots / Visuals

(Place the provided images in `assets/images/` and use the filenames shown below to embed them.)

Web UI / demo screenshot:
![Web UI screenshot — PaperWise-QA demo](assets/images/screenshot_ui.png)
_Figure 1: The Gradio/Streamlit UI for asking questions about papers; shows short highlights and the chat area._

Analysis / notebook visualizations:
![Analysis plots — Question / context analytics](assets/images/screenshot_plots.png)
_Figure 2: Exploratory analysis from QASPER — context length distribution, question vs answer scatter, top question words histogram._

If you want Bengali captions instead:
![Web UI screenshot — PaperWise-QA demo](assets/images/screenshot_ui.png)
_Figure 1: Web UI — গবেষণা পেপার সংক্রান্ত প্রশ্নের ইন্টারফেস (ডেমো)।_

![Analysis plots — Question / context analytics](assets/images/screenshot_plots.png)
_Figure 2: বিশ্লেষণ — কনটেক্সট দৈর্ঘ্য, প্রশ্ন বনাম উত্তর, সর্বোচ্চ প্রশ্ন শব্দসমূহ।_

---

Repo name & branding suggestions
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

Features
- Retrieval-Augmented Generation (RAG) over scholarly articles
- FAISS vector store for fast similarity search
- Handles long documents via adaptive chunking & context-length management
- Evidence-based answers: returned responses include supporting passages and locations
- Configurable LLM backends (OpenAI, local LLMs, or other API providers)
- Demo-ready: instructions included for local run and Hugging Face Spaces deployment

---

How to add the provided images to the repo (quick)

1. Create the folder and copy the images into it (locally):
```bash
mkdir -p assets/images
# Save your two images as:
# - assets/images/screenshot_ui.png
# - assets/images/screenshot_plots.png
```

2. Update README.md (already contains the markdown to show them), then commit:
```bash
git add assets/images/screenshot_ui.png assets/images/screenshot_plots.png README.md
git commit -m "Add README with embedded screenshots"
git push origin main
```
(Replace `main` with your default branch name if different.)

---

Indexing, quickstart & other docs
- See `scripts/build_index.py` for ingesting and chunking PDFs
- See `app.py` for the demo UI (Gradio/Flask) and the runtime flags for `--index-path` and `--llm-provider`
- `notebooks/analysis.ipynb` contains the plots shown in Figure 2 (context length, top question words, etc.)

---

Would you like me to:
- 1) Create these image files and commit them to the repo for you (I can push to `sultanakona/Scholarly-Q-A-Bot-using-LLM` if you want — I will ask for confirmation before writing), or
- 2) Just provide the updated README (above) and the exact filenames so you can upload the images locally and commit?

If you want me to commit the images, tell me:
- Which branch to push to (default: `main`)
- Confirm the image filenames you'd like (I used `screenshot_ui.png` and `screenshot_plots.png`) or provide alternatives.

I'll proceed with the commit if you confirm.
