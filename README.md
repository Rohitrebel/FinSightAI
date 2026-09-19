# FinSight AI

## Evidence-Grounded Financial Intelligence & Research Platform

FinSight AI is a full-stack financial research application that combines structured market and financial data with company documents and an AI engineering layer.

The goal is not to build another stock dashboard or a generic document chatbot.

FinSight is designed around a complete research workflow:

```text
Discover
   ↓
Analyze
   ↓
Research
   ↓
Validate
   ↓
Decision Support
   ↓
Report / Export
```

The application is a **portfolio / educational / non-commercial project**.

---

# 1. Why FinSight Exists

FinSight is the next step from an earlier AI Stock Analysis Dashboard.

The earlier project already provided market-data retrieval, financial visualization, investment profit/loss, historical stock analysis, AI-assisted research, embeddings/FAISS, LLM integration and Excel export. fileciteturn0file2L50-L63

FinSight takes that foundation and asks a larger question:

> **What is happening with this company financially, why is it happening, what evidence supports the conclusion, are the underlying figures consistent, and what should the researcher consider before making a decision?**

That means FinSight combines:

```text
Market Data
+
Financial Data
+
Financial Documents
+
RAG
+
Agentic Reasoning
+
Deterministic Tools
+
Validation
+
Evidence
+
Decision Support
```

---

# 2. What Problem It Solves

Financial research is usually spread across:

- market-data sites
- financial statements
- annual reports
- investor presentations
- earnings calls
- spreadsheets
- research notes
- AI assistants

There are also two types of information.

## Structured information

Examples:

- stock price
- OHLC
- volume
- revenue
- profit
- debt
- EPS
- cash flow
- valuation fields

## Unstructured information

Examples:

- annual reports
- management commentary
- earnings-call documents
- investor presentations
- PDFs
- research notes

FinSight creates a single research environment where these sources can be combined.

---

# 3. The User Story

Imagine a financial researcher wants to understand **TCS**.

The journey is:

```text
Dashboard
   ↓
Research Workspace
   ↓
TCS
   ↓
Overview
   ↓
Analysis
   ↓
Research
   ↓
Decision Center
   ↓
Reports
```

The researcher can also start a broader investigation through:

```text
AI Researcher
```

and work across multiple companies or sources.

---

# 4. User Roles

FinSight has two roles.

## Financial Researcher

This is the primary user.

They can:

- research companies
- analyze market performance
- calculate investment performance
- inspect financial statements
- upload documents
- ask AI questions
- inspect evidence
- review validation
- use Decision Center
- generate reports
- export datasets
- continue historical research

## AI Ops / Developer

This role operates the AI engineering side.

They can:

- inspect the knowledge base
- inspect agent/tool behavior
- evaluate retrieval
- evaluate generation
- compare prompts
- benchmark embeddings/chunking
- inspect traces
- monitor latency/tokens/cost
- inspect routing
- inspect cache behavior
- review feedback
- investigate guardrails

The AI Ops side exists because the person using an AI system and the engineer operating that AI system have different questions.

---

# 5. User Navigation

```text
USER
│
├── Dashboard
├── Research Workspace
├── AI Researcher
├── Data Center
├── Research History
└── Profile
```

Inside a selected company:

```text
Company
│
├── Overview
├── Analysis
│   ├── Market
│   ├── Investment
│   └── Financials
│
├── Research
│   ├── Documents
│   └── AI Analyst
│
├── Decision Center
└── Reports
```

This grouping is deliberate.

We group pages around **what the user is trying to accomplish**, not around technologies such as RAG, embeddings or validation.

---

# 6. Dashboard

The Dashboard is the starting point for discovery.

It provides:

## Market Overview

Examples:

```text
NIFTY 50
SENSEX
```

Show:

- current value
- daily change
- daily percentage change
- update time

## Popular Companies

Cards can show:

```text
TCS
₹3,421.20
▲ 1.82%
```

with:

- logo
- ticker
- company name
- price
- daily change
- selected supported metric

## Search

Search by:

- company name
- ticker

## Recent Research

Users can reopen:

- recent company research
- AI Analyst sessions
- AI Researcher sessions
- reports

## Quick Actions

- Research Company
- Start AI Research
- Upload Document
- Open Data Center

The Dashboard is mainly discovery and navigation.

---

# 7. Research Workspace

Research Workspace is the main company-specific environment.

The user selects a company and creates a context around it.

Example:

```text
TCS
Tata Consultancy Services
```

The workspace is divided into:

```text
Overview
Analysis
Research
Decision Center
Reports
```

---

# 8. Overview

Overview answers:

> **“What is the current picture of this company?”**

It can show:

### Market

- price
- daily change
- market cap
- P/E where available
- EPS where available
- 52-week high/low

### Business

- revenue
- net profit
- EBITDA where available
- debt where available
- cash where available

### Trends

- stock trend
- revenue trend
- profit trend

It also provides quick actions into deeper research.

---

# 9. Analysis

Analysis answers:

> **“What does the quantitative data tell me?”**

It contains:

```text
Market
Investment
Financials
```

## Market

Users can inspect:

- historical prices
- supported intraday data
- OHLC
- volume
- returns
- charts
- candlesticks
- moving averages
- selected technical indicators
- index comparisons where supported

Typical ranges:

```text
1D | 1W | 1M | 6M | 1Y | 5Y
```

## Investment

A user can enter:

```text
Amount
Purchase Date
Exit / Current Date
```

FinSight calculates:

```text
Initial Investment
Current / Exit Value
Profit / Loss
Return %
```

Example:

```text
₹100,000
01-Jan-2025
01-Sep-2026

→ ₹127,430
→ ₹27,430 profit
→ 27.43% return
```

The calculation is performed by deterministic code rather than asking the LLM to do arithmetic.

## Financials

Shows available:

- income statement
- balance sheet
- cash flow
- EPS
- supported ratios
- historical trends
- period comparisons

---

# 10. Research

Research answers:

> **“What do the company's documents and qualitative information tell me?”**

It contains:

```text
Documents
AI Analyst
```

---

# 11. Documents and the Knowledge Pipeline

A user can upload things such as:

- annual reports
- financial statements
- investor presentations
- earnings-call material
- research PDFs

The processing pipeline is:

```text
Upload
 ↓
Validate
 ↓
Parse
 ↓
Extract
 ↓
Structure
 ↓
Chunk
 ↓
Embed
 ↓
Index
 ↓
Ready for AI
```

The system shows a processing state so the user knows when the document is usable.

---

# 12. Table-Aware Document Processing

Financial documents contain important information in tables.

For example:

```text
Revenue by Segment
FY2024
FY2025
Growth %
```

Treating every PDF as plain text can damage the relationships between rows, columns and values.

FinSight therefore plans a structure-aware document pipeline:

```text
PDF
 ↓
Structure Detection
 ├── Text
 └── Tables
      ↓
Unified Representation
      ↓
Chunk / Index / Retrieve
```

This lets the system preserve information such as:

```text
Document
Page
Table
Row
Column
Period
Value
```

A full visual multimodal pipeline is not required initially; the first objective is reliable financial-document structure extraction.

---

# 13. RAG

RAG stands for **Retrieval-Augmented Generation**.

The problem it solves is simple:

An LLM should not be expected to know the exact contents of a report that the user has uploaded.

Instead:

```text
Question
 ↓
Retrieve relevant evidence
 ↓
Give evidence to the LLM
 ↓
Generate answer
```

Our planned retrieval architecture is:

```text
Question
 ↓
Dense Retrieval
 +
Sparse Retrieval
 ↓
Hybrid Fusion
 ↓
Metadata Filtering
 ↓
Reranking
 ↓
Relevant Context
 ↓
Agent / LLM
```

---

# 14. Embeddings

Embeddings turn text into numerical representations that capture semantic relationships.

For example:

Document:

> “The company experienced moderation in discretionary technology spending.”

User:

> “Why did growth slow?”

The words are different, but the meaning is related.

Embeddings help the retrieval system connect those concepts.

Our initial embedding provider is:

**Cohere**

The application starts with one primary configuration.

Alternative embedding configurations can later be benchmarked in Evaluation Lab.

---

# 15. Qdrant

Qdrant is the primary vector database.

It stores the searchable representations of document chunks and metadata.

Conceptually:

```text
Document Chunk
 ↓
Embedding
 ↓
Qdrant
```

Qdrant is used for:

- vector search
- metadata filtering
- dense retrieval
- sparse/hybrid retrieval
- multi-stage retrieval

The earlier project used FAISS.

FinSight deliberately upgrades the retrieval layer to Qdrant.

FAISS is not the primary FinSight vector store.

---

# 16. Hybrid Retrieval

Why combine dense and sparse retrieval?

Because financial documents contain both:

### Semantic language

> “The company experienced moderation in discretionary spending.”

and exact information such as:

```text
EBITDA
26.3%
FY2025
₹12.4 Cr
```

Dense search is useful for meaning.

Sparse search is useful for exact terms and numbers.

So:

```text
Dense
  +
Sparse
  ↓
Hybrid Retrieval
```

Then the candidate results are reranked.

The exact reranking model is chosen when the retrieval phase is implemented and evaluated.

---

# 17. AI Analyst

The AI Analyst is **company-scoped**.

If the user is inside:

```text
TCS
```

then asking:

> “Why is debt increasing?”

means TCS.

The AI Analyst can use:

```text
TCS Market Data
+
TCS Financial Data
+
TCS Documents
+
Financial Tools
+
Validation
```

---

# 18. Why We Need an Agent

A basic RAG chatbot does:

```text
Question
 ↓
Retrieve
 ↓
LLM
 ↓
Answer
```

FinSight needs more because financial questions can require multiple operations.

For:

> “Is increasing debt concerning?”

the system may need to:

```text
Get debt
 ↓
Get equity
 ↓
Calculate debt/equity
 ↓
Compare previous periods
 ↓
Search management commentary
 ↓
Validate evidence
 ↓
Explain result
```

The **agent** is the orchestrator that decides which capabilities are necessary.

It is not an unrestricted autonomous system.

---

# 19. Tools

Tools are deterministic or controlled capabilities the agent can call.

Initial tools include:

```text
search_documents()
get_source_evidence()
get_market_data()
get_financial_metric()
calculate_ratio()
compare_periods()
compare_companies()
detect_contradictions()
validate_claim()
```

This lets the system divide responsibilities correctly.

```text
LLM
→ reasoning / language

Python tools
→ exact calculations

Qdrant
→ retrieval

PostgreSQL
→ persistence

Validation
→ verification
```

---

# 20. AI Analyst Request Pipeline

The intended flow is:

```text
User Question
 ↓
Input Guardrails
 ↓
Intent / Complexity Routing
 ↓
Prompt Version
 ↓
Semantic Cache
 ↓
Context Construction
 ↓
Agent
 ↓
RAG / Tools / Market Data
 ↓
Validation
 ↓
Evidence Assembly
 ↓
LLM Synthesis
 ↓
Output Guardrails
 ↓
Citation / Claim Checks
 ↓
Answer
```

---

# 21. Validation

Validation answers:

> **“Can we support and verify what the system is saying?”**

It is not a separate page.

It appears wherever necessary.

Examples:

```text
✓ Calculation verified
✓ Evidence found
⚠ Conflicting values
⚠ Missing source
```

Validation checks can include:

- calculation correctness
- numeric consistency
- claim/evidence matching
- document completeness
- source availability
- contradiction detection

---

# 22. Contradiction Detection

Suppose:

```text
Annual Report:
Revenue = ₹12.4 Cr
```

but another source says:

```text
Revenue = ₹10.9 Cr
```

FinSight should not quietly choose one.

It should surface:

```text
Potential contradiction

Source A
Page / location

Source B
Page / location

Possible explanation
Confidence
```

Contradiction detection is one component of the broader Validation engine.

---

# 23. Evidence and Citations

The system should not merely say:

> “Revenue declined because of X.”

It should provide the user with:

```text
Claim
 ↓
Evidence
 ↓
Document
 ↓
Page
 ↓
Relevant passage / value
```

This is what makes FinSight **evidence-grounded**.

---

# 24. Confidence

Confidence represents the strength of support for a result.

Possible factors:

- retrieval relevance
- evidence quality
- calculation verification
- contradiction state
- validation state

Example:

```text
Confidence: 87%
```

The system must not present this as a mathematical guarantee of correctness.

---

# 25. Decision Center

This is the most important product-level AI feature.

Decision Center is where the output of all the previous research is synthesized.

It combines:

```text
Market
+
Investment
+
Financials
+
Documents
+
AI Findings
+
Validation
+
Evidence
```

and produces:

```text
Positive Signals
Risk Signals
Decision Factors
Evidence Strength
Confidence
Human Review Status
Next Research Questions
```

For example:

```text
Financial Health
72 / 100

Positive:
✓ Improving margins
✓ Positive operating cash flow

Risks:
⚠ Increasing leverage
⚠ Liquidity concern

Evidence:
High

Review:
Recommended
```

The purpose is not to tell the user:

> “BUY.”

It is to help the user understand the factors relevant to their decision.

---

# 26. AI Researcher

AI Researcher is different from AI Analyst.

## AI Analyst

> **“Analyze this company.”**

## AI Researcher

> **“Investigate this broader question.”**

Example:

```text
Research Session:
Indian IT Profitability
```

Sources:

```text
TCS
Infosys
HCLTech
Industry Report
Annual Reports
```

The researcher can compare companies and sources, identify evidence and generate a research result.

---

# 27. Data Center

The Data Center is for users who need structured data rather than an AI answer.

It supports:

## Market Data

- historical prices
- OHLC
- volume
- supported indicators
- dividends/splits where available

## Fundamentals

- income statement
- balance sheet
- cash flow
- EPS
- supported company/valuation fields

## Compare

```text
TCS | INFY | HCLTECH
```

## Dataset Builder

```text
Companies
+
Fields
+
Period
+
Frequency
 ↓
Preview
 ↓
CSV / Excel
```

## Evidence dataset

Where useful:

```text
Question
Claim
Evidence
Document
Page
Confidence
Validation
```

Unavailable data is shown as **N/A**.

---

# 28. Reports

Reports package the result.

Potential output:

```text
Executive Summary
Market Performance
Investment Analysis
Financial Analysis
Research Findings
Risks
Decision-Support Summary
Validation
Evidence
Sources
```

Exports:

- PDF
- Excel

---

# 29. Research History

Research History lets users return to:

- previous company research
- AI Analyst conversations
- AI Researcher sessions
- reports

It is about **continuing work**, not replacing Reports.

---

# 30. Profile

Profile is intentionally simple:

- user information
- role
- preferences
- logout

---

# 31. AI Ops Overview

The AI Ops Overview asks:

> **“How is the AI platform doing overall?”**

Example metrics:

```text
AI Requests
Average Latency
Groundedness
Citation Accuracy
Cache Hit Rate
Estimated Cost
Error Rate
```

It also shows:

- recent requests
- recent evaluations
- recent failures
- active configuration
- routing distribution

---

# 32. Knowledge Base

Knowledge Base is the developer view of the retrieval system.

The developer can inspect:

```text
Document
 ↓
Section
 ↓
Chunk
 ↓
Table
 ↓
Metadata
 ↓
Embedding
 ↓
Qdrant
```

This is useful when a bad answer is actually caused by:

```text
bad parsing
or
bad chunking
or
bad retrieval
```

rather than a bad LLM.

---

# 33. Agent & Tools

This page makes the agent's behavior inspectable.

Example:

```text
Question
 ↓
Agent
 ↓
search_documents()
 ↓
calculate_ratio()
 ↓
validate_claim()
 ↓
Answer
```

The developer can inspect:

- available tools
- tool descriptions
- permissions
- execution status
- latency
- inputs/outputs where appropriate

---

# 34. Guardrails

FinSight consumes untrusted content.

That includes:

- user prompts
- PDFs
- URLs
- retrieved chunks
- tool outputs

The AI must distinguish:

```text
System Instructions
       ≠
User Instructions
       ≠
Retrieved Data
       ≠
Tool Results
```

An uploaded document must not be able to rewrite the agent's system instructions.

This is why prompt-injection protection is part of the AI service.

---

# 35. Model Router

Not every query needs the same model.

Example:

```text
“What was revenue in FY2025?”
```

may need a lighter path.

While:

```text
“Compare three companies, identify contradictions,
calculate profitability trends and explain the risks.”
```

may need a stronger model.

So:

```text
Question
 ↓
Router
 ↓
Model A / Model B
```

The exact models will be chosen after evaluation.

The routing decision becomes part of AI Monitoring and Decision Lineage.

---

# 36. LLM Gateway

The Agent does not hard-code vendor-specific logic everywhere.

Instead:

```text
Agent
 ↓
LLM Gateway
 ↓
OpenRouter
 ↓
Model
```

The gateway is responsible for the consistent model-call interface and request metadata.

---

# 37. Prompt Versioning

We treat prompts like code/configuration.

A prompt has:

```text
ID
Version
Purpose
Model
Created At
Evaluation Result
```

This allows us to answer:

> “Which prompt version generated this result?”

That information becomes part of traceability.

---

# 38. Semantic Cache

If users ask semantically equivalent questions:

```text
“What was TCS revenue in FY2025?”

“How much revenue did TCS report in 2025?”
```

we can reuse a previous valid result.

```text
Question
 ↓
Embedding
 ↓
Semantic Similarity
 ↓
Cache Hit?
 ├── Yes → Reuse
 └── No → Full pipeline
```

This can reduce:

- latency
- token usage
- cost

---

# 39. Evaluation Lab

The Evaluation Lab asks:

> **“Is our AI actually good?”**

Instead of testing only by manually asking questions, we maintain a domain-specific evaluation dataset.

Example categories:

```text
Financial QA
Retrieval
Numerical Reasoning
Cross-Company Comparison
Contradiction Detection
Decision Support
Citation Accuracy
```

---

# 40. Retrieval Metrics

We measure:

### Recall@K

Did the correct evidence appear in the top K?

### Precision@K

How much of the retrieved set was relevant?

### MRR

How high in the ranking was the first relevant result?

These tell us whether the retrieval layer is working.

---

# 41. Generation Metrics

We evaluate:

- relevance
- groundedness
- citation accuracy
- instruction following
- domain correctness where measurable

---

# 42. AI-as-a-Judge

For open-ended answers, exact string comparison is insufficient.

So one model can evaluate another response against explicit criteria.

Example:

```text
Question
 ↓
Answer A
 ↓
Judge
 ↓
Relevance
Grounding
Completeness
Evidence support
```

Because judges can be imperfect, their prompts are versioned and sampled results are checked by humans.

---

# 43. Experiments

Experiments are records inside Evaluation Lab.

Examples:

```text
Prompt v1 vs v2
Embedding A vs B
Chunking A vs B
Top-K 5 vs 10
Reranking on vs off
Model A vs B
```

An experiment records:

- configuration
- evaluation data
- metrics
- latency
- token usage
- estimated cost
- result

We do not build an “Experiments” page.

---

# 44. Embedding and Chunking Benchmarks

We can compare:

```text
Embedding configuration
×
Chunking strategy
×
Top-K
```

Example chunking strategies:

```text
500 tokens / 50 overlap
1000 tokens / 100 overlap
semantic / section-based
```

The goal is to select based on measured retrieval and downstream quality.

---

# 45. User Feedback

After an AI response:

```text
👍
👎
```

The user can optionally say:

```text
Correct
Missing Evidence
Wrong Calculation
Irrelevant
Contradiction Missed
Other
```

The feedback becomes improvement data.

```text
Feedback
 ↓
Evaluation Dataset
 ↓
Experiment
 ↓
Improved Configuration
```

---

# 46. AI Monitoring

AI Monitoring is for detailed investigation.

It includes:

- request logs
- trace details
- routing
- tool execution
- guardrails
- latency
- tokens
- cache
- failures

The key distinction:

```text
AI Ops Overview
→ overall health / quality

AI Monitoring
→ detailed “what happened?”
```

---

# 47. Request Trace

A request can be understood as:

```text
Question
 ↓
Guardrails
 ↓
Router
 ↓
Prompt
 ↓
Cache
 ↓
Retrieval
 ↓
Agent
 ↓
Tools
 ↓
LLM
 ↓
Guardrails
 ↓
Validation
 ↓
Response
```

This makes debugging possible.

---

# 48. Decision Lineage

Decision lineage preserves the provenance of a result.

Example:

```text
Question
 ↓
Sources
 ↓
Retrieved Chunks
 ↓
Tool Calls
 ↓
Calculations
 ↓
Model
 ↓
Prompt
 ↓
Validation
 ↓
Decision-Support Result
```

The purpose is to answer:

> **“Why did FinSight produce this conclusion?”**

---

# 49. Human-in-the-Loop

Human review is not required for every response.

It is triggered when:

- evidence is insufficient
- contradictions are important
- confidence is low
- explicit confirmation is needed

Actions can be:

```text
Approve
Reject
Request More Information
Override
```

---

# 50. Market Data Architecture

Twelve Data is the primary provider.

Alpha Vantage and yfinance are fallbacks.

The architecture is:

```text
React
 ↓
Node / Express
 ↓
Market Data Service
 ↓
Twelve Data
 ↓
Fallback when necessary
 ↓
Normalized schema
 ↓
PostgreSQL
```

The user-facing application should not know the vendor's raw response structure.

---

# 51. Why PostgreSQL Caching Matters

We do not want:

```text
Every user request
       ↓
External API
```

Instead:

```text
Request
 ↓
Cache?
 ├── Yes → Return
 └── No
      ↓
External API
      ↓
Normalize
      ↓
Store
      ↓
Return
```

This reduces provider usage and latency while teaching a useful ingestion/caching pattern.

---

# 52. Why There Is One AI Service

We deliberately do not create:

```text
Embedding Service
RAG Service
Agent Service
Evaluation Service
Cache Service
```

That would add operational complexity without enough benefit for a portfolio project.

Instead:

```text
Python / FastAPI
      ↓
One AI service
      ├── ingestion
      ├── retrieval
      ├── RAG
      ├── agents
      ├── tools
      ├── evaluation
      ├── guardrails
      ├── cache
      └── LLM
```

---

# 53. Overall Technology Stack

```text
Frontend
React + Vite

Styling
Tailwind CSS

Charts
Recharts

Application Backend
Node.js + Express

AI Backend
Python + FastAPI

Database
PostgreSQL

Market Data
Twelve Data
  + Alpha Vantage fallback
  + yfinance fallback

Embeddings
Cohere

Vector Store
Qdrant

Retrieval
Dense + Sparse / Hybrid

Reranking
Planned; selected through evaluation

LLM Gateway
OpenRouter

AI
RAG + Agents + Tools

Reliability
Guardrails + Validation + Evidence

Optimization
Semantic Cache + Model Routing

Evaluation
Domain Dataset + Retrieval Metrics +
Generation Evaluation + AI Judge

Operations
AI Monitoring + Traces + Decision Lineage
```

---

# 54. What We Intentionally Do Not Build

FinSight is not:

- a banking application
- an automated trading system
- a guaranteed investment-advice system
- a commercial financial-data provider
- a generic ChatGPT clone
- a multi-agent swarm
- a model-training platform
- a Kubernetes project
- a giant microservice platform

The objective is **depth and coherence**, not maximum feature count.

---

# 55. Development Philosophy

This project is being built while learning.

We will not tell the developer:

> “Go learn React for two weeks.”

Instead:

```text
Today’s feature
 ↓
What concept is required?
 ↓
Explain concept
 ↓
Show small example
 ↓
Build it in FinSight
 ↓
Test it
 ↓
Commit it
```

This keeps the learning connected to a real system.

---

# 56. How the Pieces Work Together

The complete architecture is:

```text
                         FINSIGHT AI
                              │
              ┌───────────────┴────────────────┐
              │                                │
         USER EXPERIENCE                    AI OPS
              │                                │
              └───────────────┬────────────────┘
                              ▼
                        React Frontend
                              │
                              ▼
                       Node / Express
                     ┌────────┼─────────┐
                     │        │         │
                     ▼        ▼         ▼
               PostgreSQL  Market    FastAPI
                            Data        │
                              │          ▼
                         Twelve Data  AI Engine
                         + fallbacks     │
                              │     ┌────┼─────┐
                              ▼     ▼    ▼     ▼
                           Cache   RAG Agent Eval
                                      │    │    │
                                      ▼    ▼    ▼
                                    Qdrant Tools
                                      │
                                      ▼
                                Validation
                                      │
                                      ▼
                                LLM Gateway
                                      │
                                  OpenRouter
                                      │
                                      ▼
                                     LLM
                                      │
                          ┌───────────┴───────────┐
                          ▼                       ▼
                      Evidence              Decision
                                                  │
                                                  ▼
                                           Decision Center
                                                  │
                                                  ▼
                                               Reports
```

---

# 57. Final Product Narrative

A researcher opens FinSight and sees market conditions.

They select TCS.

They inspect:

```text
Overview
   ↓
Market
Investment
Financials
```

They upload an annual report.

FinSight parses it, extracts structure and tables, chunks the content, embeds it and indexes it.

The researcher asks the AI Analyst:

> “Why did profitability change?”

The agent determines that it needs:

```text
financial metrics
+
document evidence
+
calculation
```

It retrieves evidence, calls deterministic tools, validates the result, and asks the LLM to synthesize an answer.

The result contains:

```text
Answer
+
Evidence
+
Validation
+
Confidence
```

The user then opens Decision Center to review:

```text
Positive Signals
Risk Signals
Decision Factors
Evidence Strength
Confidence
Human Review
Next Questions
```

The user makes the final decision.

For broader research, the user opens AI Researcher and compares several companies and sources.

When finished, the user generates a report or dataset.

Meanwhile, the AI engineer can open AI Ops to understand:

```text
What documents were indexed?
What did retrieval return?
Which tools ran?
Which model was chosen?
Which prompt version was used?
How long did it take?
How many tokens were used?
Did a cache hit occur?
Were guardrails triggered?
Was the answer grounded?
How did users evaluate it?
```

That is the complete FinSight system.

---

# 58. Final Statement

> **FinSight is an evidence-grounded financial intelligence platform that combines structured financial data, document intelligence and agentic AI to help users research companies, validate findings and make better-informed financial decisions, while giving AI engineers the tools to evaluate, monitor and continuously improve the AI system behind those decisions.**
