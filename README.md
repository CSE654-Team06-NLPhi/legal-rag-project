# Legal RAG Project: RAG vs. no-RAG on KVKK

**Course:** CSE 654 Natural Language Processing
**Team:** Team06 NLPhi (Ceyda Nur Uçan Adıgüzel, Berfin Kösemen, Cansu Künar)

## Goal
We compare a no-RAG baseline with a RAG system on Turkish legal question answering, using the Turkish Personal Data Protection Law (KVKK, No. 6698). We test whether RAG helps the model **answer**, **refuse** (when the law does not cover the question) and **correct false premises**.

## Models
- **LLM:** Qwen/Qwen3-8B (4-bit NF4, thinking mode off, greedy decoding, max 512 new tokens)
- **Embedding:** BAAI/bge-m3
- **Vector database:** ChromaDB

## Experiments
- **Baseline:** the model answers each question directly, with no added context.
- **RAG:** KVKK.pdf is split into 512-character chunks (64 overlap). The top 2 chunks are added before each question.
- **The one change:** only the retrieved context. The model, prompt and settings are the same in both conditions.

## Data
- **Knowledge source:** KVKK No. 6698, consolidated text including Law 7499 (mevzuat.gov.tr)
- **Questions:** 120 team-authored Turkish questions: 40 dev, 80 frozen test

## How to run
1. Open the notebook in Google Colab and set the runtime to **T4 GPU**.
2. Run all cells.
3. When asked, upload `Questions(in).csv` and `KVKK.pdf`.

## Output
- `KVKK_cevaplar_v2_Qwen3_8B_4bit.xlsx`: question, baseline answer, RAG answer, retrieved pages and retrieved text
- `README_experiment_Qwen3_8B_4bit.txt`: experiment settings

## Environment
Google Colab, one T4 GPU (about 9 GB GPU memory used)
