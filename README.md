# Chetan Gupta — TPM & AI Product Portfolio

**Technical Program Manager | AI/ML Products · Workflow Automation · GovTech & SaaS**
📍 Seattle, WA | [LinkedIn](https://www.linkedin.com/in/chetan-gupta-pm/) | PMP Certified · UT Austin AI/ML

---

## About This Portfolio

I'm a Technical Program Manager with 10+ years of experience shipping AI-powered products and automation programs across GovTech, SaaS, and EdTech. This portfolio demonstrates my technical depth — I can write product specs, review code, build automation scripts, and work alongside engineering teams from discovery through launch.

The projects here span three areas:
- **AI/ML product prototyping** — RAG pipelines, LLM integrations, predictive modeling
- **Workflow automation** — Python scripts solving real operational problems at scale
- **Program delivery artifacts** — examples of how I think about scope, milestones, and execution

---

## Projects

### 🔍 Amazon Product Reviews — RAG System
**`/amazon-review-rag`**

**The problem:** Amazon customers leave thousands of reviews per product. Finding signal in that noise — what do customers actually love, hate, or ask about most — requires reading hundreds of reviews manually.

**What I built:** A Retrieval-Augmented Generation (RAG) pipeline that ingests Amazon product reviews, embeds them into a vector store, and lets users query them in natural language. Ask "What are the most common complaints about battery life?" and get a grounded, cited answer from actual reviews — not a hallucination.

**Tech stack:** Python · Mistral-7B (via HuggingFace) · LangChain · ChromaDB · Sentence Transformers

**Why it matters as a TPM artifact:**
This project mirrors the kind of AI product problem I'd own as a TPM — defining the retrieval architecture, evaluating embedding models, and validating that the system returns grounded responses. It's the technical foundation for any AI assistant built on unstructured customer data.

**Key design decisions:**
- Chose ChromaDB over FAISS for persistent local storage and easier iterative testing
- Used Mistral-7B for cost-effective local inference without API rate limits
- Chunked reviews by sentence boundary rather than fixed token count to preserve semantic coherence

---

### ⚙️ Document Processing Automation
**`/document_processing`**

**The problem:** At the Consulate General of India (Seattle), consular staff manually extracted applicant data from Word documents into Excel tracking sheets — a process prone to errors and consuming hours per week.

**What I built:** A Python automation suite that extracts structured data from OCI Detail Enquiry Word documents and exports it directly into formatted Excel workbooks, with per-field error isolation and logging.

**Tech stack:** Python · python-docx · openpyxl · pandas · logging

**Real-world impact:** Deployed in production at the Consulate, processing hundreds of OCI applicant records. Reduced manual data entry time by ~80% and eliminated transcription errors across the workflow.

**Why it matters as a TPM artifact:**
This is exactly the kind of 0-to-1 automation program a TPM drives in an enterprise or government environment — identifying the manual bottleneck, scoping the solution, coordinating with operations stakeholders, and shipping something that runs reliably in production.

---

### 🤖 ML Projects — Applied AI/ML Notebooks
**`/ml_projects`**

A collection of applied machine learning projects from my UT Austin AI/ML postgraduate program, each focused on a business problem rather than a benchmark.

| Project | Problem | Approach |
|---|---|---|
| Churn Prediction | Identify customers at risk of churning before they leave | Random Forest + feature importance analysis |
| Sales Forecasting | Predict monthly revenue from historical sales data | Time series modeling with trend decomposition |
| Visa Approval Classifier | Predict visa approval likelihood based on applicant profile | Logistic Regression + XGBoost comparison |
| Helmet Detection (CV) | Detect safety helmet compliance on construction sites | CNN with transfer learning (ResNet) |
| RAG Medical Assistant | Answer clinical questions from unstructured medical notes | NLP + RAG pipeline with HuggingFace |

**Tech stack:** Python · scikit-learn · TensorFlow · Keras · pandas · NumPy · Matplotlib · HuggingFace Transformers

---

## How I Work

As a TPM, I sit at the intersection of engineering and product. These projects reflect how I approach technical problems:

1. **Start with the business problem** — not the technology. Every project here begins with "what pain does this solve?"
2. **Design for real constraints** — the document processing scripts handle malformed files, partial extractions, and edge cases because real operational data is messy
3. **Ship something that runs** — all scripts are production-tested, not just notebooks that work on demo data
4. **Document decisions** — I note why I made key architectural choices, not just what I built

---

## Tech Stack Summary

| Category | Tools |
|---|---|
| Languages | Python, SQL |
| AI/ML | LangChain, HuggingFace, Mistral-7B, scikit-learn, TensorFlow, Keras |
| Vector Stores | ChromaDB |
| Data | pandas, NumPy, openpyxl |
| Visualization | Matplotlib, Power BI, Tableau |
| Cloud | Microsoft Azure, Azure ML |
| PM/TPM Tools | Jira, Confluence, Agile/Scrum |

---

## Certifications

- PMP — Project Management Professional (PMI)
- Postgraduate Program in AI & ML — UT Austin McCombs School of Business (2024–2025)
- Microsoft Certified: Azure Fundamentals
- Tableau Desktop Specialist
- Google Analytics Certified

---

## Contact

Open to Senior PM and TPM roles in Seattle — ideally in AI-powered products, workflow automation, or enterprise/civic tech.

📧 Connect on [LinkedIn](https://www.linkedin.com/in/chetan-gupta-pm/) | 💼 [GitHub Profile](https://github.com/cgsalwan)
