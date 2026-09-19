# FinSight AI — Final Master Product & Engineering Blueprint v2

**Status:** Final implementation baseline  
**Project:** FinSight AI  
**Type:** Portfolio / Educational / Non-commercial  
**Primary purpose:** Build a realistic, evidence-grounded financial research application while learning AI engineering and full-stack engineering through implementation.

> This document is the implementation source of truth. Future changes should be made only when implementation reveals a genuine requirement, limitation, or better-supported design decision.

---

# 1. Product Identity

## 1.1 Name

**FinSight AI**

## 1.2 Positioning

**Evidence-Grounded Financial Intelligence & Research Platform**

## 1.3 One-line definition

> FinSight combines market data, company financials, financial documents, AI-assisted research, deterministic calculations, validation, evidence and decision support to help users make better-informed financial decisions.

---

# 2. Why We Are Building FinSight

FinSight is deliberately an evolution of the earlier AI Stock Analysis Dashboard rather than a completely unrelated portfolio application.

The earlier application already established:

- market-data retrieval
- financial visualization
- historical stock analysis
- investment profit/loss analysis
- AI-assisted financial research
- Cohere embeddings
- FAISS
- LLM integration
- Excel export

The evolution is:

```text
Old Dashboard
“How is this stock performing?”
        ↓
FinSight
“What is happening with this company,
why is it happening, what evidence supports it,
what is inconsistent, and what should I consider?”
```

The earlier dashboard already contained the foundations of market data, financial visualization, P&L, AI-assisted research, embeddings/FAISS, LLM integration and Excel export. FinSight extends those foundations into a broader evidence-grounded research and decision-support workflow. fileciteturn0file2L50-L63

---

# 3. Core Product Problem

Financial research is fragmented.

A researcher may need to move between:

```text
Market data
+
Financial statements
+
Annual reports
+
Investor presentations
+
Earnings-call material
+
Spreadsheets
+
Research notes
+
AI assistants
```

The information is also split between:

## Structured information

- price
- OHLC
- volume
- revenue
- profit
- debt
- EPS
- cash flow
- valuation/statistical fields where available

## Unstructured information

- annual reports
- management commentary
- investor presentations
- earnings calls
- research PDFs
- user-uploaded documents

FinSight brings these together.

---

# 4. The Product's Real Outcome

FinSight is not primarily a:

- stock charting app
- document chatbot
- generic ChatGPT clone
- financial calculator

Those are individual capabilities.

The actual workflow is:

```text
DISCOVER
   ↓
SELECT
   ↓
ANALYZE
   ↓
RESEARCH
   ↓
VALIDATE
   ↓
SYNTHESIZE
   ↓
DECISION SUPPORT
   ↓
REPORT / EXPORT
```

The user's final decision remains the user's decision.

FinSight supplies evidence and analysis rather than autonomous guaranteed investment advice.

---

# 5. Product Principles

## 5.1 Group UI by user jobs

Do not create a new page simply because another technology exists.

## 5.2 Keep complexity under the hood

Users should see a clean research product.

Developers should see the AI engineering details through AI Ops.

## 5.3 Deterministic operations stay deterministic

Financial formulas, exact transformations, schema checks and validation rules belong in code.

## 5.4 Never fabricate missing financial data

Unsupported/unavailable values are:

```text
N/A
```

## 5.5 Evidence is inspectable

Important AI claims should link to supporting documents, pages or structured data.

## 5.6 Evaluation is part of engineering

AI quality is measured, not assumed.

## 5.7 Start simple, then optimize

We do not add a sophisticated component unless it solves a demonstrated problem or is important enough to learn.

---

# 6. User Roles

## 6.1 Financial Researcher

Primary goal:

> Research a company, understand its market and financial performance, investigate documents, ask AI questions, inspect evidence, review validation and reach an informed decision-support view.

## 6.2 AI Ops / Developer

Primary goal:

> Operate, inspect, evaluate and improve the AI system powering the researcher experience.

AI Ops is an engineering control plane, not a generic administration page.

---

# 7. Final User Navigation

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

No additional top-level user pages are planned.

---

# 8. Dashboard

## User question

> “What is happening in the market, what companies should I look at, and what research can I continue?”

## Functions

### Market Overview

Supported indexes such as:

- NIFTY 50
- SENSEX

Show where available:

- current value
- daily change
- percentage change
- last updated time

### Popular Companies

Cards may show:

- company logo
- company name
- ticker
- current price
- daily percentage change
- up/down indicator
- selected supported market metric

### Company Search

Search using:

- company name
- ticker

### Recent Research

Show:

- recent company sessions
- recent AI Researcher sessions
- recently viewed reports

### Quick Actions

- Research a Company
- Start AI Research
- Upload Document
- Open Data Center

### Boundary

Dashboard is discovery/navigation.

It does not contain the heavy reasoning pipeline.

---

# 9. Research Workspace

## User question

> “I want to deeply understand this one company.”

Selecting a company creates a company-specific context.

## Final structure

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

The grouping is based on user jobs, not implementation technologies.

---

# 10. Research Workspace — Overview

## User question

> “What is the current picture of this company?”

## Content

### Market snapshot

- stock price
- daily change
- market capitalization
- P/E where available
- EPS where available
- 52-week range

### Business snapshot

- revenue
- net profit
- EBITDA where available
- debt where available
- cash where available

### Quick trends

- stock trend
- revenue trend
- profit trend

### Quick actions

- Analyze Investment
- Ask AI Analyst
- View Documents
- Open Decision Center

---

# 11. Research Workspace — Analysis

## User question

> “What does the quantitative data tell me?”

Analysis contains:

```text
Market
Investment
Financials
```

---

## 11.1 Market

### Purpose

Analyze stock-market behavior.

### Features

- historical data
- supported intraday data
- date/time selection
- price charts
- candlestick charts
- volume
- returns
- moving averages
- selected supported technical indicators
- market-index comparison where possible

Typical time ranges:

```text
1D | 1W | 1M | 6M | 1Y | 5Y
```

---

## 11.2 Investment

### Purpose

Calculate investment outcome.

### Inputs

```text
Company
Investment Amount
Purchase Date
Exit / Current Date
```

### Outputs

```text
Initial Investment
Current / Exit Value
Profit / Loss
Return %
Annualized Return where appropriate
```

Optional:

- index comparison

All arithmetic is performed deterministically.

Example:

```text
Investment: ₹100,000
Buy: 01-Jan-2025
Exit: 01-Sep-2026

Initial Value: ₹100,000
Final Value: ₹127,430
Profit: ₹27,430
Return: 27.43%
```

---

## 11.3 Financials

### Purpose

Understand the underlying business.

### Income Statement

- revenue
- EBITDA where available
- operating income where available
- net income
- EPS

### Balance Sheet

- assets
- liabilities
- current assets
- current liabilities
- debt
- equity
- cash

### Cash Flow

- operating cash flow
- investing cash flow
- financing cash flow
- free cash flow where available

### Analysis

- historical trends
- year-over-year comparison
- period comparison
- supported ratios

Financial metrics can become inputs to AI tools.

---

# 12. Research Workspace — Research

## User question

> “What do the company's documents and qualitative information tell me?”

Contains:

```text
Documents
AI Analyst
```

---

# 13. Documents

## Purpose

Create a company-specific evidence base.

## Expected source types

- annual reports
- financial statements
- investor presentations
- earnings-call material
- research reports
- user PDFs
- supported URLs
- supported text/CSV sources where relevant

## Processing lifecycle

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
Metadata
 ↓
Embed
 ↓
Index
 ↓
Ready
```

Processing states:

```text
Uploaded
Processing
Parsed
Embedding
Indexed
Ready
Failed
```

---

# 14. Table-Aware Document Intelligence

Financial documents are not only prose.

Critical information can be contained in:

- financial tables
- segment tables
- balance sheets
- income statements
- cash-flow tables
- comparative year tables

Therefore the document pipeline explicitly supports structured/table extraction.

```text
PDF
 ↓
Structure Detection
 ├── Text
 └── Tables
      ↓
Unified Document Representation
      ↓
Chunk / Index / Retrieve
```

Example use case:

> “What was TCS revenue by business segment in FY2025?”

The system should preserve enough structure to identify:

```text
Document
Page
Table
Row
Column
Period
Value
```

A full general multimodal vision system is not required at first.

---

# 15. AI Analyst

## Purpose

Answer questions about the currently selected company.

Examples:

- Why did revenue decline?
- Compare FY2024 and FY2025.
- Is debt increasing?
- What risks does management mention?
- Explain margin changes.
- What are the main financial concerns?
- What should I investigate further?

## Context

The AI Analyst can use:

```text
Company Context
+
Market Data
+
Financial Data
+
Company Documents
+
Deterministic Tools
+
Validation / Evidence
```

---

# 16. AI Analyst Core Pipeline

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
 ┌─────────────┬───────────────┬──────────────┐
 │             │               │
 ▼             ▼               ▼
RAG       Financial Tools   Market Data Tools
 │             │               │
 ▼             ▼               │
Qdrant      Exact Math          │
 │             │               │
 └─────────────┴───────────────┘
                ↓
           Validation
                ↓
        Evidence Assembly
                ↓
          LLM Synthesis
                ↓
        Output Guardrails
                ↓
        Claim / Citation Checks
                ↓
             Answer
```

---

# 17. AI Researcher

## Purpose

Generalized research not tied to one company.

### AI Analyst

> Analyze the selected company.

### AI Researcher

> Investigate this broader research question using multiple relevant sources and companies.

## Example questions

- Compare profitability of TCS, Infosys and HCLTech.
- What are the main risks facing Indian IT companies?
- Compare management commentary across annual reports.
- Investigate an industry trend.
- Find contradictions across several reports.

## Research session

```text
Research Session
│
├── Companies
├── PDFs
├── URLs
├── CSVs
└── Text
```

## Flow

```text
Question
 ↓
Source Selection
 ↓
Routing
 ↓
Agent
 ↓
Multi-source Retrieval / Tools
 ↓
Comparison
 ↓
Validation
 ↓
Evidence
 ↓
LLM Synthesis
 ↓
Research Result
```

---

# 18. Decision Center

## Purpose

Decision Center is the culmination of company-specific research.

It is not merely another analysis tab.

It answers:

> **“After everything analyzed, what are the major factors I should consider?”**

## Inputs

```text
Market Analysis
+
Investment Analysis
+
Financial Analysis
+
Documents
+
AI Findings
+
Validated Calculations
+
Evidence
+
Contradictions
```

## Outputs

### Overall assessment

- financial health summary
- positive signals
- risk signals
- evidence strength
- confidence

### Decision factors

Examples:

- growth
- profitability
- liquidity
- leverage
- cash flow

### Evidence & validation

- supporting sources
- page references
- verified calculations
- contradictions
- missing information

### Human review

```text
Not Required
Recommended
Required
```

### Next questions

Examples:

```text
Why did leverage increase?

Why are two sources reporting different values?

Is management guidance supported by the evidence?
```

## Boundary

FinSight supports the user's decision.

It does not produce guaranteed buy/sell instructions.

---

# 19. Validation

Validation is a **cross-cutting capability**, not a standalone company page.

It appears in:

- Analysis
- Research
- AI Analyst
- Decision Center
- Reports
- AI Ops

Examples:

```text
✓ Calculation verified
✓ Evidence found
⚠ Contradiction detected
⚠ Missing source
```

Validation includes:

- numeric consistency
- formula verification
- source availability
- document completeness
- claim/evidence matching
- contradiction detection
- confidence signals

---

# 20. Evidence and Citations

Every important AI conclusion should be traceable.

```text
Claim
 ↓
Evidence
 ↓
Document / Data Source
 ↓
Page / Location
 ↓
Relevant Text / Structured Value
```

Evidence appears in:

- AI answers
- Decision Center
- AI Researcher
- Reports
- AI Ops traces

---

# 21. Confidence

Confidence is a support signal based on factors such as:

- retrieval relevance
- evidence quality/quantity
- calculation verification
- contradictions
- validation results

Example:

```text
Confidence: 87%
```

The system must not imply that the number is a guarantee of correctness.

The confidence formula is finalized during implementation and evaluation.

---

# 22. Reports

## Purpose

Package completed research into reusable output.

Potential structure:

```text
Executive Summary
Market Performance
Investment Analysis
Financial Analysis
Research Findings
Risk Factors
Decision-Support Summary
Validation Findings
Evidence
Sources
```

Exports:

- PDF
- Excel

---

# 23. Data Center

## Purpose

The Data Center answers:

> **“I want to explore structured financial data and build a dataset.”**

It is broader than historical stock-price export.

## 23.1 Market Data

Potential fields:

- historical price
- OHLC
- adjusted close where available
- volume
- dividends where available
- splits where available
- quotes where supported
- technical indicators where supported

## 23.2 Fundamentals

Potential fields:

- income statement
- balance sheet
- cash flow
- earnings/EPS
- company information
- valuation/statistical fields where supplied

## 23.3 Compare

Compare companies such as:

```text
TCS
INFY
HCLTECH
```

using available:

- returns
- revenue
- profit
- margins
- EPS
- debt
- valuation statistics

## 23.4 Dataset Builder

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

## 23.5 Research Evidence Dataset

Where appropriate:

```text
Question
Company
Claim
Answer
Evidence
Document
Page
Confidence
Validation Status
```

## Data integrity

Unavailable fields = **N/A**.

---

# 24. Research History

## Purpose

Allow users to continue prior work.

Contains:

- company sessions
- AI Analyst conversations
- AI Researcher sessions
- saved reports

User can reopen and continue.

---

# 25. Profile

Simple account area.

Contains:

- name
- email
- role
- account information
- preferences
- logout

Potential preferences:

- default market
- preferred currency
- notifications

No advanced AI functionality.

---

# 26. AI Ops

The developer side is intentionally limited to five areas:

```text
AI Ops Overview
Knowledge Base
Agent & Tools
Evaluation Lab
AI Monitoring
```

There are no standalone pages for:

- System Health
- Models
- Semantic Cache
- Audit Logs
- Experiments

These capabilities live inside the five areas.

---

# 27. AI Ops Overview

## Purpose

High-level answer:

> “How is the AI platform doing?”

Show:

- request count
- average latency
- groundedness
- citation accuracy
- cache hit rate
- estimated cost
- error rate
- current model/configuration
- routing distribution
- recent failures
- recent evaluations

This is a summary dashboard.

---

# 28. Knowledge Base

## Purpose

Answer:

> “What is actually inside our RAG knowledge layer?”

Show:

- company
- document
- pages
- sections
- chunks
- tables detected
- embedding model
- index status
- document version
- processing state

Inspect:

```text
Document
 ↓
Sections
 ↓
Chunks
 ↓
Tables
 ↓
Metadata
 ↓
Embeddings
 ↓
Qdrant
```

Operations:

- upload/reprocess
- delete
- inspect
- rebuild index
- re-embed
- inspect extracted tables

---

# 29. Agent & Tools

## Purpose

Answer:

> “What can the agent do and what did it actually do?”

Core tools:

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

Show:

- tools
- descriptions
- permissions/boundaries
- recent executions
- status
- latency
- structured inputs/outputs where appropriate

Example trace:

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

---

# 30. Guardrails

Guardrails are part of the AI service and are visible operationally in AI Ops.

## Input guardrails

- malformed input detection
- request limits
- file validation
- untrusted-content classification
- prompt-injection detection
- unauthorized tool request prevention

## Trust boundaries

```text
System Instructions
       ≠
User Instructions
       ≠
Retrieved Documents
       ≠
Tool Outputs
```

Retrieved text is evidence/data, not an instruction.

## Output guardrails

```text
LLM Output
 ↓
Schema Validation
 ↓
Evidence Check
 ↓
Financial-claim Check
 ↓
Citation Check
 ↓
Final Response
```

---

# 31. Model Router and LLM Gateway

## Purpose

Not every request needs the same level of model capability.

### Concept

```text
User Question
 ↓
Intent / Complexity Classifier
 ↓
Model Router
 ↓
Simple → lighter model
Complex → stronger model
 ↓
LLM Gateway
 ↓
OpenRouter
 ↓
Selected Model
```

## Example

Simple:

> “What was revenue in FY2025?”

Complex:

> “Compare TCS, Infosys and HCLTech, identify contradictions, calculate profitability trends and explain the main financial risks.”

## Record

- routing decision
- selected model
- route/category
- latency
- tokens
- estimated cost
- success/failure

## Boundary

Model routing is an internal AI capability.

It is not a user-facing page.

The exact model set is selected only after evaluation establishes a useful reason to route between models.

---

# 32. LLM Gateway

The agent does not call a vendor-specific API everywhere.

Instead:

```text
Agent
 ↓
LLM Gateway
 ↓
OpenRouter
 ↓
Selected Model
```

This keeps the AI code organized and gives us a clean place for:

- model selection
- retries
- usage tracking
- request metadata
- provider errors
- future provider replacement

---

# 33. Prompt Engineering and Versioning

Prompts define:

- system behavior
- task instructions
- context expectations
- evidence requirements
- tool-use behavior
- output structure

Each important prompt has:

```text
Prompt ID
Version
Purpose
Model
Created At
Evaluation Result
```

Example:

```text
AI Analyst Prompt v1
AI Analyst Prompt v2
AI Analyst Prompt v3
```

We evaluate before promoting a new version.

---

# 34. Agent Architecture

The agent is a controlled orchestrator.

It can:

1. understand the question
2. decide what information is required
3. call tools
4. request retrieval
5. request deterministic calculations
6. gather evidence
7. invoke validation
8. pass validated context for synthesis

It is not intended to be an unrestricted autonomous agent.

---

# 35. RAG Architecture

## Final planned pipeline

```text
Query
 ↓
Query Preparation
 ↓
Dense Retrieval
 +
Sparse Retrieval
 ↓
Hybrid Fusion
 ↓
Metadata Filtering
 ↓
Candidate Set
 ↓
Reranking
 ↓
Top Context
 ↓
Agent / LLM
```

### Dense retrieval

Semantic embedding similarity.

### Sparse retrieval

Useful for exact terms, numbers, acronyms and named financial entities.

### Hybrid retrieval

Combines semantic and exact-match strengths.

### Reranking

A second-stage relevance model rescoring a smaller candidate set.

The exact reranker remains **TBD until implementation/evaluation**.

---

# 36. Embedding Strategy

## Initial provider

**Cohere**

Reason:

- suitable for our document-retrieval use case
- continuity with the earlier project
- practical development path

## Benchmarking

Alternative configurations can be evaluated later.

One primary embedding configuration is used initially.

---

# 37. Vector Store

## Primary

**Qdrant**

Used for:

- vector storage
- metadata filtering
- dense retrieval
- sparse/hybrid retrieval
- multi-stage retrieval support

FAISS is not the primary FinSight vector store.

FAISS belongs to the earlier project and may be used only for optional experimentation.

---

# 38. Semantic Cache

## Purpose

Avoid repeating expensive AI work for semantically equivalent queries.

```text
New Query
 ↓
Embedding
 ↓
Similarity Search
 ↓
Threshold
 ├── Match → reuse
 └── No match → execute pipeline
                     ↓
                  cache result
```

Track:

- hit
- miss
- hit rate
- latency
- tokens saved
- estimated cost saved

Semantic cache is surfaced in AI Monitoring.

---

# 39. Financial Tools

Deterministic tools include:

```text
get_market_data()
get_financial_metric()
calculate_ratio()
compare_periods()
compare_companies()
```

Initial calculations include:

- current ratio
- debt-to-equity
- profit margin
- revenue growth
- additional supported ratios

The LLM requests calculations; code performs them.

---

# 40. Validation Engine

## Goal

Separate verification from generation.

### Checks

- numeric consistency
- ratio correctness
- source availability
- document completeness
- claim/evidence matching
- contradiction detection

The validation engine produces structured findings that can be consumed by Decision Center.

---

# 41. Contradiction Detection

Contradictions may appear across:

- annual reports
- financial statements
- management commentary
- user documents

Result:

```text
Conflict
Source A
Location

Source B
Location

Potential explanation
Confidence
```

Contradiction detection is a component of Validation, not a separate system.

---

# 42. Evaluation Lab

## Purpose

Answer:

> **“Is our AI actually good, and which configuration should we use?”**

---

# 43. Evaluation Dataset

FinSight maintains a small domain-specific benchmark.

Categories:

```text
Financial factual QA
Document retrieval
Numerical reasoning
Cross-company comparison
Contradiction detection
Decision support
Citation/evidence
```

Each case can contain:

```text
Question
Company
Expected evidence
Expected calculation
Tags
Evaluation criteria
```

The dataset is versioned and reviewed.

---

# 44. Retrieval Evaluation

Metrics:

- Recall@K
- Precision@K
- MRR

Goal:

> Determine whether the right evidence is retrieved.

---

# 45. Generation Evaluation

Measure:

- relevance
- groundedness
- citation accuracy
- instruction following
- domain-specific correctness where measurable

---

# 46. AI-as-a-Judge

Used when open-ended responses cannot be evaluated by exact matching.

Example:

```text
Question
 ↓
Response A
Response B
 ↓
Judge
 ↓
Compare relevance
grounding
completeness
evidence support
instruction following
```

Because judges can also be wrong:

- judge prompts are versioned
- criteria are explicit
- samples receive human review
- judge scores are not treated as absolute truth

---

# 47. Comparative Evaluation

Compare:

```text
Prompt v1 vs v2
Embedding A vs B
Chunking A vs B
Top-K 5 vs 10
Reranking on vs off
Model A vs B
```

Measure:

- quality
- latency
- tokens
- estimated cost

---

# 48. Embedding Benchmark

Evaluate:

```text
Embedding Configuration
×
Chunking Strategy
×
Top-K
```

Measure:

- retrieval quality
- latency
- storage implications
- downstream answer quality

---

# 49. Chunking Benchmark

Initial strategies:

## Fixed-size

```text
500 tokens
50 overlap
```

## Larger fixed-size

```text
1000 tokens
100 overlap
```

## Semantic / section-based

Use document headings/structure where appropriate.

The exact winning strategy is determined by measurement.

---

# 50. Prompt Experimentation

Prompt versions can be evaluated using the same benchmark.

Example:

```text
Prompt v1 → baseline
Prompt v2 → clearer evidence requirements
Prompt v3 → improved tool-use instructions
```

The Evaluation Lab records results.

---

# 51. User Feedback Loop

After an AI response:

```text
Was this useful?

👍
👎
```

Optional reasons:

```text
Correct
Missing Evidence
Wrong Calculation
Irrelevant
Contradiction Missed
Other
```

Pipeline:

```text
User Feedback
 ↓
Feedback Dataset
 ↓
Evaluation
 ↓
Identify Weakness
 ↓
Experiment
 ↓
Improved Configuration
```

Feedback is improvement data, not automatic training data.

---

# 52. AI Monitoring

AI Monitoring is the detailed operational/observability area.

## Show

- request table
- filters
- traces
- routing decisions
- tool executions
- guardrail events
- latency breakdown
- token usage
- cache details
- failures

## Main question

> **“What actually happened inside this request?”**

---

# 53. AI Ops Overview vs AI Monitoring

These are intentionally different.

## AI Ops Overview

> “How is the AI platform doing overall?”

Summary metrics and status.

## AI Monitoring

> “What happened in this particular request or period?”

Detailed request-level investigation.

This avoids building two copies of the same dashboard.

---

# 54. Request Trace

Example:

```text
Question
 ↓
Input Guardrails
 ↓
Router
 ↓
Prompt Version
 ↓
Cache Check
 ↓
Retrieval
 ↓
Agent
 ↓
Tools
 ↓
LLM
 ↓
Output Guardrails
 ↓
Validation
 ↓
Response
```

---

# 55. Decision Lineage

Decision lineage answers:

> **“Why did FinSight produce this conclusion?”**

Store/trace where appropriate:

- question
- session/user
- retrieved evidence
- sources
- tool calls
- tool outputs
- selected model
- routing decision
- prompt version
- response
- validation outcome
- confidence
- guardrail events
- timestamps
- human review
- feedback

---

# 56. Human-in-the-Loop

Human review is used when:

- evidence is insufficient
- contradictions are significant
- confidence is low
- explicit confirmation is required

Possible actions:

```text
Approve
Reject
Request More Information
Override
```

Human action becomes part of lineage.

---

# 57. Data Architecture

## PostgreSQL

Persistent relational/application data:

- users
- roles
- companies
- market data cache
- financial data
- documents
- document metadata
- research sessions
- conversations
- messages
- analyses
- validation
- contradictions
- citations
- tool calls
- AI request metadata
- prompt versions
- routing decisions
- guardrail events
- cache metadata
- evaluation datasets
- evaluation results
- feedback
- reports
- lineage
- human reviews

## Qdrant

Retrieval data:

- document vectors
- retrieval metadata
- dense/sparse retrieval structures

---

# 58. Market Data Architecture

## Providers

### Primary

**Twelve Data**

### Fallback

**Alpha Vantage**

**yfinance**

## Internal boundary

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
Normalize
 ↓
PostgreSQL cache
 ↓
Application
```

The rest of FinSight never depends directly on provider-specific response shapes.

---

# 59. Market Data Normalization

Internal schema example:

```json
{
  "symbol": "TCS",
  "exchange": "NSE",
  "timestamp": "2026-09-14T15:30:00+05:30",
  "open": 3400.10,
  "high": 3440.20,
  "low": 3388.50,
  "close": 3421.20,
  "volume": 1245000,
  "source": "twelve_data"
}
```

The exact relational schema is finalized during implementation.

---

# 60. Market Data Cache

```text
User Request
 ↓
PostgreSQL Cache?
 ├── Yes → Return
 └── No
       ↓
   External Provider
       ↓
   Normalize
       ↓
   Persist
       ↓
   Return
```

Purpose:

- reduce provider calls
- reduce latency
- preserve previously retrieved data
- make free-tier constraints manageable

---

# 61. AI Service

One Python/FastAPI service contains:

```text
ingestion
parsing
tables
chunking
embeddings
retrieval
reranking
rag
prompts
guardrails
routing
agents
tools
financial
validation
evidence
caching
evaluation
feedback
llm
```

No separate AI microservices are planned.

---

# 62. Service Responsibilities

## React + Vite

- UI
- routing
- forms
- charts
- dashboards
- research interfaces
- Decision Center
- Data Center
- AI Ops visualization

## Node.js + Express

- REST API
- authentication/authorization
- users/roles
- companies
- application data
- document metadata
- sessions/conversations
- reports
- PostgreSQL access
- market-data orchestration
- AI-service communication
- business rules

## Python + FastAPI

All AI/ML responsibilities.

## PostgreSQL

Persistent application and structured data.

## Qdrant

Vector/retrieval storage.

---

# 63. LLM Architecture

The exact underlying LLM is not permanently locked yet.

The application architecture is:

```text
AI Analyst / AI Researcher
          ↓
        Agent
          ↓
   LLM Gateway
          ↓
      OpenRouter
          ↓
   Selected Model
```

The actual model choice will be determined by evaluation, availability and practical cost/latency constraints.

---

# 64. Open-Source Model Experimentation

Open-source models may be tested in Google Colab for:

- learning
- model comparison
- benchmarking
- fine-tuning experiments
- GPU experimentation

Colab is not the permanent FinSight application server.

---

# 65. Security

Minimum controls:

- password hashing
- secrets in environment variables
- `.env` excluded from Git
- role-based authorization
- protected AI Ops routes
- input validation
- upload validation
- file-size limits
- file-type checks
- prompt-injection defenses
- tool authorization
- output validation
- rate limiting where appropriate
- sanitized logs
- no secrets in traces

---

# 66. API Contract Baseline

These are starting groups, not immutable contracts.

## Authentication

```text
POST /api/auth/register
POST /api/auth/login
GET  /api/auth/me
POST /api/auth/logout
```

## Companies

```text
GET  /api/companies
GET  /api/companies/:id
POST /api/companies
```

## Market

```text
GET /api/market/:symbol
GET /api/market/:symbol/history
```

## Investment

```text
POST /api/investments/calculate
```

## Financials

```text
GET /api/companies/:id/financials
```

## Documents

```text
POST   /api/documents
GET    /api/documents/:id
DELETE /api/documents/:id
POST   /api/documents/:id/reprocess
```

## AI Analyst

```text
POST /api/analyst/chat
GET  /api/analyst/conversations/:id
```

## AI Researcher

```text
POST /api/research/sessions
GET  /api/research/sessions
GET  /api/research/sessions/:id
POST /api/research/sessions/:id/sources
POST /api/research/sessions/:id/messages
POST /api/research/sessions/:id/report
```

## Data Center

```text
GET  /api/data/market
POST /api/data/export
```

## Reports

```text
POST /api/reports
GET  /api/reports/:id
GET  /api/reports/:id/download
```

## AI Ops

```text
GET  /api/ops/overview
GET  /api/ops/knowledge
GET  /api/ops/agents
GET  /api/ops/tools
GET  /api/ops/evaluations
POST /api/ops/evaluations/run
GET  /api/ops/monitoring
GET  /api/ops/traces/:id
```

---

# 67. Logical Database Entities

Initial entities:

```text
users
roles
companies
documents
document_sections
document_tables
document_chunks
research_sessions
research_sources
conversations
messages
analyses
financial_metrics
market_data
validation_results
contradictions
citations
tool_calls
ai_requests
prompt_versions
routing_decisions
guardrail_events
cache_entries
evaluation_datasets
evaluation_cases
evaluation_runs
evaluation_results
experiments
feedback
reports
decision_lineage
human_reviews
```

Exact relationships and indexes are designed before implementation.

---

# 68. Repository Structure

```text
FinSightAI/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── context/
│   │   └── utils/
│   └── package.json
│
├── backend/
│   ├── src/
│   │   ├── config/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── models/
│   │   ├── middleware/
│   │   ├── validators/
│   │   └── utils/
│   ├── app.js
│   ├── server.js
│   └── package.json
│
├── ai-service/
│   ├── app/
│   │   ├── ingestion/
│   │   ├── parsing/
│   │   ├── tables/
│   │   ├── chunking/
│   │   ├── embeddings/
│   │   ├── retrieval/
│   │   ├── reranking/
│   │   ├── rag/
│   │   ├── prompts/
│   │   ├── guardrails/
│   │   ├── routing/
│   │   ├── agents/
│   │   ├── tools/
│   │   ├── financial/
│   │   ├── validation/
│   │   ├── evidence/
│   │   ├── caching/
│   │   ├── evaluation/
│   │   ├── feedback/
│   │   └── llm/
│   └── requirements.txt
│
├── database/
│   ├── schema/
│   ├── migrations/
│   └── seeds/
│
├── docs/
│
├── .env.example
├── .gitignore
├── README.md
└── LICENSE
```

---

# 69. Development Method

FinSight is built while learning.

We do not treat the books as a separate syllabus.

The process for every important capability is:

```text
Problem
 ↓
Why do we need this?
 ↓
Concept explanation
 ↓
Small example
 ↓
Implement in FinSight
 ↓
Test
 ↓
Debug
 ↓
Refactor
 ↓
Commit
```

No independent multi-hour course is required unless a concept genuinely cannot be understood from the implementation context.

---

# 70. Implementation Phases

## Phase 0 — Product Baseline

- blueprint
- sitemap
- architecture
- initial API map
- initial data model

## Phase 1 — Foundation

- Git
- React/Vite
- Express
- PostgreSQL
- FastAPI
- service communication
- environment configuration

## Phase 2 — User Foundation

- authentication
- authorization
- Dashboard
- Profile
- Research Workspace shell
- AI Ops shell

## Phase 3 — Market / Investment / Data Center

- Twelve Data
- fallback provider support
- normalization
- caching
- market UI
- investment calculations
- Financials
- Data Center
- Dataset Builder
- CSV/Excel

## Phase 4 — Documents

- upload
- parsing
- table extraction
- metadata
- chunking

## Phase 5 — RAG

- Cohere
- Qdrant
- dense retrieval
- sparse retrieval
- hybrid retrieval
- reranking
- citations

## Phase 6 — AI Analyst

- financial tools
- market tools
- agent orchestration
- company context
- structured output
- prompt versioning

## Phase 7 — Reliability

- input guardrails
- prompt-injection defense
- output guardrails
- validation
- contradiction detection
- evidence
- confidence
- human review

## Phase 8 — Decision Center / AI Researcher

- Decision Center
- research sessions
- multi-source retrieval
- comparison
- reports

## Phase 9 — AI Ops

- Overview
- Knowledge Base
- Agent & Tools
- Evaluation Lab
- Monitoring

## Phase 10 — Evaluation / Optimization

- evaluation dataset
- AI-as-a-Judge
- embedding benchmarks
- chunking benchmarks
- prompt experiments
- model routing
- semantic cache
- latency/tokens/cost measurement
- user feedback

## Phase 11 — Portfolio Release

- tests
- hardening
- deployment
- documentation
- screenshots
- architecture diagrams
- demo
- resume material

---

# 71. MVP

Minimum version that still communicates the FinSight story:

```text
React
 ↓
Express
 ↓
PostgreSQL
 ↓
FastAPI
 ↓
Twelve Data
 ↓
Documents
 ↓
Cohere
 ↓
Qdrant
 ↓
RAG
 ↓
AI Analyst
 ↓
Evidence
 ↓
Basic Decision Center
```

---

# 72. Portfolio-Ready Version

In addition to MVP:

- AI Researcher
- Decision Center
- validation
- contradiction detection
- guardrails
- prompt versions
- model routing
- semantic cache
- evaluation dataset
- AI-as-a-Judge
- embedding/chunking evaluation
- AI Monitoring
- traces
- feedback loop
- decision lineage
- polished reports
- deployment
- README
- demo

---

# 73. Explicitly Out of Scope

We are not building:

- banking integrations
- automated credit approval
- commercial financial-data service
- enterprise SSO/IAM
- Kubernetes
- unnecessary microservices
- standalone system-health page
- standalone model-management page
- standalone cache page
- standalone audit-log page
- standalone experiments page
- generic ChatGPT clone
- multi-agent swarm
- large custom LLM training infrastructure
- mandatory fine-tuning
- DeepSpeed/multi-GPU training architecture
- Colab as production infrastructure
- broad multimodal vision system unless a real document problem requires it

---

# 74. Deliberately Unlocked Decisions

Not forgotten; intentionally deferred:

- exact LLM model(s)
- exact reranker
- exact auth mechanism
- exact database schema/indexes
- exact provider endpoint matrix
- exact fallback rules
- exact alternative embedding benchmark
- exact guardrail libraries
- exact routing algorithm
- exact AI judge model
- exact table extraction library
- exact deployment provider

These are selected when their implementation phase provides enough information to make a sound decision.

---

# 75. Final Redundancy Rules

## AI Ops Overview vs AI Monitoring

- Overview = high-level platform status
- Monitoring = request-level investigation

## Validation vs Contradiction Detection

- Validation = umbrella capability
- Contradiction detection = one validation mechanism

## Comparative Evaluation vs Experiments

- Comparative evaluation = method
- Experiment = stored comparison record inside Evaluation Lab

## Request Trace vs Decision Lineage

- Trace = execution sequence
- Lineage = provenance/reason-for-result record
- They may share underlying trace/event data

## Market Cache vs Semantic Cache

- Market cache = avoids repeated external data requests
- Semantic cache = avoids repeated AI work

## AI Analyst vs AI Researcher

- AI Analyst = selected company
- AI Researcher = broader multi-source question

## Analysis vs Data Center

- Analysis = understand the selected company
- Data Center = explore/build/export structured datasets

## Decision Center vs Reports

- Decision Center = what the analysis means
- Reports = package the result

---

# 76. Final Mental Model

```text
                       FINSIGHT AI

                         RESEARCH
                            │
          ┌─────────────────┴─────────────────┐
          ▼                                   ▼
   STRUCTURED DATA                      DOCUMENTS
          │                                   │
    Market / Finance                    Reports / PDFs
          │                                   │
          └─────────────────┬─────────────────┘
                            ▼
                       AI RESEARCH
                            │
                       Agent + RAG
                            │
            ┌───────────────┼────────────────┐
            ▼               ▼                ▼
          Tools          Retrieval        Validation
            │               │                │
            └───────────────┼────────────────┘
                            ▼
                         LLM
                            │
                    Evidence + Answer
                            │
                            ▼
                     DECISION CENTER
                            │
                            ▼
                          REPORT
```

Around the AI system:

```text
                    AI OPS
                       │
        ┌──────────────┼───────────────┐
        ▼              ▼               ▼
    Evaluation     Monitoring      Knowledge
        │              │               │
    Benchmarks       Cost            Documents
    AI Judge         Latency         Chunks
    Feedback         Tokens          Tables
    Prompt Versions  Cache           Embeddings
    Experiments      Traces          Qdrant
```

---

# 77. Final Product Statement

> **FinSight is an evidence-grounded financial intelligence platform that combines structured financial data, document intelligence and agentic AI to help users research companies, validate findings and make better-informed financial decisions, while giving AI engineers the tools to evaluate, monitor and continuously improve the AI system behind those decisions.**
