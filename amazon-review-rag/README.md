# Amazon Product Reviews — RAG System

**A Retrieval-Augmented Generation pipeline for querying Amazon product reviews in natural language**

> Built as a technical showcase of LLM integration, vector search, and AI product architecture — aligned with Amazon's focus on customer-obsessed AI tooling.

---

## The Problem

Amazon customers generate millions of product reviews. For a product manager, seller, or customer service team, extracting actionable signal from that volume is nearly impossible manually:

- "What are the top 3 complaints about this product?"
- "Do customers mention battery life issues?"
- "What do reviewers say about the packaging experience?"

Reading hundreds of reviews to answer these questions takes hours. A keyword search misses context. A simple summarizer hallucinates and loses attribution.

---

## The Solution

A RAG (Retrieval-Augmented Generation) pipeline that:

1. **Ingests** Amazon product reviews from a structured dataset
2. **Chunks and embeds** reviews into a persistent vector store
3. **Retrieves** the most semantically relevant review chunks for any natural language query
4. **Generates** a grounded, cited answer using a local LLM — no hallucinations, no fabricated quotes

---

## Architecture

```
User Query
    │
    ▼
Query Embedding (Sentence Transformers)
    │
    ▼
Vector Similarity Search (ChromaDB)
    │
    ▼
Top-K Relevant Review Chunks Retrieved
    │
    ▼
Prompt Construction (Query + Context)
    │
    ▼
LLM Generation (Mistral-7B via HuggingFace)
    │
    ▼
Grounded Answer with Source Attribution
```

---

## Tech Stack

| Component | Tool | Reason for Choice |
|---|---|---|
| LLM | Mistral-7B (HuggingFace) | Cost-effective local inference, no API rate limits |
| Orchestration | LangChain | Modular chain construction, easy swap of components |
| Vector Store | ChromaDB | Persistent local storage, simple API, fast iteration |
| Embeddings | Sentence Transformers | Strong semantic similarity on review text |
| Language | Python 3.10+ | — |
| Data | Amazon Product Reviews dataset | Real-world unstructured text |

---

## Key Design Decisions

**Why ChromaDB over FAISS?**
FAISS is faster at scale but in-memory only. ChromaDB persists the vector store to disk, which means the embedding step runs once — important for iterative testing without re-processing the full dataset each run.

**Why Mistral-7B over GPT-3.5/4 via API?**
Local inference removes API cost and rate limit concerns during development. Mistral-7B performs competitively on retrieval-augmented tasks where the answer is grounded in retrieved context rather than generated from parametric memory.

**Why sentence-boundary chunking over fixed token chunking?**
Fixed token chunking splits mid-sentence, breaking semantic coherence. Sentence-boundary chunking preserves the meaning of each review fragment, which improves retrieval precision for opinionated, short-form text like reviews.

---

## What This Demonstrates (TPM Lens)

This project mirrors the architecture decisions a TPM would own when shipping an AI product:

- **Scope definition** — what questions should the system answer, and what's out of scope
- **Component selection** — evaluating embedding models, vector stores, and LLMs against real constraints (cost, latency, accuracy)
- **Failure mode analysis** — what happens when retrieved chunks don't contain the answer? The system returns a low-confidence signal rather than fabricating
- **Iteration planning** — chunking strategy, retrieval top-K, and prompt template are all tunable parameters with clear trade-offs documented

---

## Project Structure

```
amazon-review-rag/
│
├── data/                   # Raw and processed review datasets
├── embeddings/             # ChromaDB persistent vector store
├── notebooks/
│   ├── 01_data_prep.ipynb       # Load, clean, chunk reviews
│   ├── 02_embedding.ipynb       # Embed chunks into ChromaDB
│   ├── 03_rag_pipeline.ipynb    # Full RAG query pipeline
│   └── 04_evaluation.ipynb      # Retrieval quality evaluation
├── src/
│   ├── chunker.py          # Sentence-boundary text chunking
│   ├── embedder.py         # Embedding + ChromaDB ingestion
│   ├── retriever.py        # Similarity search wrapper
│   └── generator.py        # LLM prompt construction + generation
├── requirements.txt
└── README.md
```

---

## Sample Queries & Outputs

**Query:** *"What do customers say about the battery life?"*

> **Answer:** Based on 12 retrieved reviews, customers frequently mention battery life as a pain point. Several note the battery drains within 4–6 hours of continuous use. A minority of reviewers report no issues, typically under lighter workloads. [Sources: Review #142, #387, #521...]

**Query:** *"What aspects do customers rate most positively?"*

> **Answer:** Sound quality and build quality appear most frequently in positive reviews. Customers consistently praise the clarity of audio at higher volumes and describe the product as feeling premium. [Sources: Review #23, #89, #204...]

---

## Setup & Usage

```bash
# Clone the repo
git clone https://github.com/cgsalwan/chetan-gupta-tpm-portfolio.git
cd chetan-gupta-tpm-portfolio/amazon-review-rag

# Install dependencies
pip install -r requirements.txt

# Run notebooks in order
# 01 → 02 → 03
# Or run the full pipeline directly:
python src/generator.py --query "What are the most common complaints?"
```

---

## Relevance to Amazon TPM Roles

Amazon's AI product teams — Rufus, Alexa, Search, Recommendations — work on exactly this class of problem: grounding LLM responses in customer data at scale. This project demonstrates:

- Hands-on experience with RAG architecture, not just conceptual familiarity
- Ability to evaluate and select AI components based on real constraints
- Product thinking applied to AI system design (what should it answer, what should it decline)
- End-to-end ownership from data ingestion through response generation

---

*Part of the [Chetan Gupta TPM Portfolio](https://github.com/cgsalwan/chetan-gupta-tpm-portfolio)*
