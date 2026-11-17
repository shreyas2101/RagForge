# RagForge — Product Roadmap

## Product vision

RagForge is a production-oriented knowledge assistant for teams and companies. Organizations can upload shared documents, ask questions across their knowledge base, and receive answers grounded in retrieved sources.

We will build it incrementally: deliver a useful MVP first, then improve retrieval, generation, production operations, security, and multimodal capabilities. The roadmap is technology-agnostic. Architecture and technology choices are made as part of each feature's design.

## Product principles

- **Ship in small increments:** Every milestone should leave the product in a working state.
- **Deploy continuously:** Maintain a working production deployment from the earliest release onward.
- **Security by design:** Organization boundaries, authorization, and customer data protection are core requirements.
- **Measure improvements:** Use repeatable evaluations to compare retrieval and generation changes.
- **Avoid premature complexity:** Build what the current milestone needs; don't implement speculative abstractions.
- **Learn by building:** Understand and validate each capability rather than hiding it behind a large framework.

## Target users and initial workflow

**Target users:** Teams and companies that need to search and ask questions about shared internal knowledge.

**Initial workflow:** A user signs in, accesses their organization's workspace, uploads PDF documents, and asks questions. RagForge retrieves relevant passages and generates an answer with source references.

The MVP deliberately supports a narrow workflow. More file formats, sophisticated permissions, and advanced retrieval strategies will come later.

---

## Release 0 — Foundation and first deployment

**Goal:** Establish a deployable application and a repeatable way to ship changes.

### Scope

- Application foundation and basic application shell.
- Development and production configuration.
- First deployment to a stable public production URL.
- Health check or equivalent availability signal.
- Configuration and secret management.
- Basic error visibility and deployment documentation.

### Acceptance criteria

- The application is reachable through a stable public URL.
- A health check confirms that the application is running.
- Production secrets are not stored in the repository.
- The application can be built, tested, and deployed using a repeatable process.
- A failed deployment can be diagnosed and safely rolled back or redeployed.

**Exit outcome:** A live application foundation ready for product features.

## Release 1 — MVP: Basic enterprise RAG

**Goal:** Deliver the complete document-to-answer workflow for an organization.

### Scope

- Organization/workspace creation and membership.
- Basic authentication and organization-scoped access.
- PDF upload with file validation and size limits.
- Document metadata and processing status.
- Text extraction and extraction error handling.
- Baseline text chunking strategy.
- Embedding generation.
- Persistence of documents, chunks, and embeddings.
- Semantic vector retrieval scoped to the organization.
- Answer generation using retrieved context.
- Source citations linking answers to documents or passages.
- Basic loading, empty, and error states.
- Automated tests for the ingestion and question-answering workflows.

### Acceptance criteria

- A user can sign in and access their organization's workspace.
- An authorized user can upload a supported PDF.
- The document reaches a clear completed or failed processing state.
- Extracted content is chunked and indexed.
- A user can ask a question about indexed documents.
- The answer is grounded in retrieved context and includes source references.
- The system handles insufficient evidence without presenting unsupported claims as sourced facts.
- One organization cannot retrieve another organization's documents or chunks.
- The complete workflow is deployed and usable through the production URL.

**Exit outcome:** A working, narrow, multi-tenant RAG product—not just a local demo.

## Release 2 — Retrieval foundations and hybrid search

**Goal:** Improve retrieval quality and make it measurable.

### Scope

- Metadata-based filtering.
- Keyword retrieval baseline.
- TF-IDF and BM25 experiments.
- Dense semantic retrieval improvements.
- Hybrid retrieval combining lexical and semantic results.
- Reciprocal Rank Fusion (RRF) or another evaluated fusion strategy.
- Retrieval test dataset with known relevant documents.
- Precision@K, Recall@K, MAP@K, and MRR measurements.
- Baseline comparisons between retrieval approaches.

### Acceptance criteria

- Authorization and metadata constraints are applied before results reach generation.
- Keyword, semantic, and hybrid retrieval can be evaluated independently.
- Retrieval metrics can be computed reproducibly on a fixed dataset.
- A baseline and the observed trade-offs are documented.

**Exit outcome:** Retrieval changes are supported by measurements rather than intuition.

## Release 3 — Advanced retrieval

**Goal:** Explore and implement advanced retrieval methods.

### Scope

- Configurable chunking strategies.
- Fixed-size/overlap and recursive or structure-aware chunking.
- Semantic or contextual chunking experiments.
- Query rewriting.
- Query parsing and named-entity recognition (NER).
- Hypothetical Document Embeddings (HyDE).
- Exact nearest-neighbour versus approximate nearest-neighbour comparisons.
- HNSW indexing and parameter experiments.
- Candidate over-fetching.
- Bi-encoder and cross-encoder comparison.
- Reranking pipeline.
- Retrieval latency and quality comparisons.

### Acceptance criteria

- Chunking and retrieval strategies can be compared on the same evaluation dataset.
- ANN/HNSW quality and latency trade-offs are documented against exact search.
- Reranking can be evaluated against the non-reranked baseline.
- The chosen default pipeline is justified by measured quality, latency, and cost.

**Exit outcome:** A configurable, experimentally validated retrieval engine.

## Release 4 — Generation quality and orchestration

**Goal:** Improve answer faithfulness, relevance, and handling of complex questions.

### Scope

- Prompt templates and versioning.
- Context selection and context-window management.
- Model comparison and selection.
- Generation parameter experiments.
- Explicit insufficient-evidence behaviour.
- Citation correctness and answer-grounding checks.
- Hallucination mitigation experiments.
- LLM-as-a-judge evaluation.
- RAGAS metrics such as faithfulness and response relevancy.
- User feedback on answers.
- RAG versus fine-tuning experiments.
- Agentic RAG patterns: routing, iterative retrieval, sequential, and parallel workflows.

### Acceptance criteria

- Generation changes can be compared on a representative dataset.
- Faithfulness, relevance, citation quality, and failure cases are tracked separately.
- Complex orchestration is introduced only where it demonstrates a measurable benefit.
- The application has a predictable fallback when an agentic workflow fails.

**Exit outcome:** Answer quality is evaluated and improved systematically.

## Release 5 — Production operations and efficiency

**Goal:** Make the service observable, reliable, and economical under real usage.

### Scope

- Structured logs, traces, and request correlation.
- Ingestion and query pipeline observability.
- Evaluation datasets and repeatable evaluation runs.
- Operational dashboards and alerts.
- Latency and throughput measurements.
- Token, embedding, and storage cost tracking.
- Background processing and retry handling.
- Idempotency and duplicate-upload handling.
- Caching experiments, including semantic caching.
- Model routing and tiered model usage.
- Quantization and embedding-size experiments where applicable.
- Rate limits and resource-abuse controls.
- Backup, recovery, and data-retention procedures.

### Acceptance criteria

- Failures can be traced across ingestion and question-answering stages.
- Service quality, latency, and cost have measurable baselines.
- Background work can recover safely from transient failures.
- Operational alerts and recovery procedures are documented.
- Performance optimizations have before-and-after measurements.

**Exit outcome:** A service that can be operated and improved responsibly.

## Release 6 — Security, privacy, and AI red teaming

**Goal:** Assess and strengthen the security of the RAG application and its data.

### Scope

- Authentication, authorization, and role-based access control.
- Organization and document-level isolation.
- Server-side authorization enforcement and database isolation controls.
- Cross-tenant and cross-role access tests.
- Secure file handling and parser hardening.
- Direct and indirect prompt injection testing.
- Malicious document and metadata poisoning.
- Sensitive information disclosure and data-exfiltration testing.
- Retrieval manipulation and unauthorized context exposure.
- Embedding privacy and inversion-risk experiments.
- Agent/tool authorization and abuse tests, if agents are present.
- Threat model and security test harness.
- Findings with evidence, severity, remediation, and regression tests.

### Acceptance criteria

- Security tests verify that unauthorized users cannot access protected documents or retrieved chunks.
- Adversarial tests cover the application layer and the LLM/RAG-specific attack surface.
- Findings are reproducible and include remediation guidance.
- Fixed vulnerabilities have regression tests.
- Security claims are limited to the tested scope; no claim of complete security is made.

**Exit outcome:** A security-assessed RAG product with repeatable adversarial testing.

## Release 7 — Multimodal knowledge retrieval

**Goal:** Extend knowledge ingestion and retrieval beyond plain extracted text.

### Scope

- Scanned PDF and OCR workflows.
- Tables, diagrams, and layout-aware document processing.
- Image and text representation experiments.
- Vision-language model (VLM)-based extraction and retrieval.
- Multimodal embeddings.
- Image and document-page retrieval.
- Multimodal answer grounding and source references.
- Evaluation datasets for multimodal content.

### Acceptance criteria

- Supported multimodal content can be ingested with clear processing status and error handling.
- Retrieval can find relevant visual or layout-dependent information.
- Answers identify the source page or visual evidence where possible.
- Multimodal quality and cost are evaluated against defined test cases.

**Exit outcome:** A broader knowledge assistant for complex enterprise documents.

---

## Definition of done — applies to every feature

A feature is complete when:

- Its user problem and scope are clear.
- Its acceptance criteria are met.
- Relevant automated tests pass.
- Authorization, tenant isolation, and data handling have been considered.
- Failure states and operational impact are addressed.
- Documentation is updated where behaviour or operations changed.
- The feature has been reviewed and merged through the agreed branch/PR workflow.
- The production deployment is healthy after release.

## Release discipline

- Keep `main` deployable.
- Use one feature branch per independently reviewable feature.
- Prefer small pull requests over large milestone-sized changes.
- Deploy after meaningful merges; do not wait until an entire release is complete.
- Each release should have a short release note describing shipped capabilities, known limitations, and evaluation results.
- Add roadmap items only when their user value and acceptance criteria are understood.

## Current status

- [ ] Release 0 — Foundation and first deployment
- [ ] Release 1 — MVP: Basic enterprise RAG
- [ ] Release 2 — Retrieval foundations and hybrid search
- [ ] Release 3 — Advanced retrieval
- [ ] Release 4 — Generation quality and orchestration
- [ ] Release 5 — Production operations and efficiency
- [ ] Release 6 — Security, privacy, and AI red teaming
- [ ] Release 7 — Multimodal knowledge retrieval
