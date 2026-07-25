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

**The problem:** Amazon customers leave thousands of reviews per product. Finding signal in that noise requires reading hundreds of reviews manually.

**What I built:** A RAG pipeline that ingests Amazon product reviews, embeds them into a vector store, and lets users query them in natural language. Ask "What are the most common complaints about battery life?" and get a grounded, cited answer from actual reviews — not a hallucination.

**Tech stack:** Python · Mistral-7B (via HuggingFace) · LangChain · ChromaDB · Sentence Transformers

**Key design decisions:**
- Chose ChromaDB over FAISS for persistent local storage and easier iterative testing
- Used Mistral-7B for cost-effective local inference without API rate limits
- Chunked reviews by sentence boundary rather than fixed token count to preserve semantic coherence

---

### ⚙️ Document Processing Automation
**`/document_processing`**

**The problem:** Consular staff manually extracted applicant data from Word documents into Excel tracking sheets — hours of error-prone work per week.

**What I built:** A Python automation suite that extracts structured data from OCI Detail Enquiry Word documents and exports it directly into formatted Excel workbooks, with per-field error isolation and logging.

**Tech stack:** Python · python-docx · openpyxl · pandas · logging

**Real-world impact:** Deployed in production at the Consulate General of India (Seattle), processing hundreds of OCI applicant records. Reduced manual data entry time by ~80%.

---

### 🤖 ML Projects — Applied AI/ML Notebooks
**`/ml_projects`**

| Project | Problem | Approach |
|---|---|---|
| Churn Prediction | Identify customers at risk of churning | Random Forest + feature importance |
| Sales Forecasting | Predict monthly revenue | Time series + trend decomposition |
| Visa Approval Classifier | Predict approval likelihood | Logistic Regression + XGBoost |
| Helmet Detection (CV) | Safety compliance on construction sites | CNN with ResNet transfer learning |
| RAG Medical Assistant | Answer questions from medical notes | NLP + RAG pipeline (HuggingFace) |

**Tech stack:** Python · scikit-learn · TensorFlow · Keras · pandas · NumPy · HuggingFace Transformers

---

## How I Work

1. **Start with the business problem** — not the technology
2. **Design for real constraints** — scripts handle malformed files and edge cases
3. **Ship something that runs** — all scripts are production-tested
4. **Document decisions** — I note why I made key architectural choices

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

Open to Product Manager and Technical Program Manager roles in Seattle — AI-powered products, workflow automation, or enterprise/civic tech.

📧 [LinkedIn](https://www.linkedin.com/in/chetan-gupta-pm/) | 💼 [GitHub](https://github.com/cgsalwan)
