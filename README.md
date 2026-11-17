# RagForge

**RagForge is a hands-on learning project focused on building, deploying, evaluating, and security-testing production-grade Retrieval-Augmented Generation (RAG) systems.**

The goal is to learn how RAG works beneath the abstractions by designing and implementing the important components, understanding their trade-offs, and validating them through experiments.

This is an engineering learning project, not a finished product or a general-purpose RAG framework. It will evolve as features are built, tested, measured, and improved.

## What I'm building

RagForge is being developed as a multi-tenant knowledge assistant for teams and companies.

Organizations will be able to upload documents to a shared knowledge base and ask questions about that information. The application will retrieve relevant content and generate answers grounded in those sources, with citations that help users verify the answers.

The first goal is deliberately small: build and deploy a working RAG MVP. From there, the system will grow through incremental releases covering retrieval quality, generation, production operations, security, and multimodal data.

## What I'm learning

The project is structured around learning the concepts by implementing them in a working application.

### 1. RAG fundamentals

- RAG architecture and the retrieval-generation workflow
- Knowledge bases, retrievers, embeddings, and vector search
- Grounding LLM responses in retrieved context
- Hallucinations, citations, and context-window constraints
- The trade-offs between retrieval quality, answer quality, latency, and cost

### 2. Document ingestion and indexing

- Document parsing and text extraction
- Text cleaning and normalization
- Chunking strategies and chunk-size trade-offs
- Embedding generation and vector storage
- Metadata and document lifecycle management

### 3. Information retrieval and search

- Keyword search, TF-IDF, and BM25
- Dense semantic search and vector similarity measures
- Metadata filtering
- Hybrid search and Reciprocal Rank Fusion (RRF)
- Retrieval evaluation using Precision@K, Recall@K, MAP@K, and MRR

### 4. Vector search and advanced retrieval

- Exact nearest-neighbour search and Approximate Nearest Neighbours (ANN)
- Navigable Small World (NSW) and Hierarchical Navigable Small World (HNSW)
- Fixed-size, recursive, semantic, and contextual chunking
- Query rewriting, named-entity recognition (NER), and HyDE
- Bi-encoders, cross-encoders, ColBERT, and reranking

### 5. LLM generation and evaluation

- Transformer and language-model fundamentals
- Model selection and generation parameters
- Prompt construction and context management
- Faithfulness, response relevancy, and citation quality
- Hallucination detection and mitigation
- RAG evaluation, including RAGAS and LLM-as-a-judge approaches
- RAG versus fine-tuning, and where each approach fits
- Agentic RAG patterns such as routing, iterative retrieval, sequential, and parallel workflows

### 6. Production engineering

- Designing reliable ingestion and query pipelines
- Background processing, retries, and idempotency
- Logging, tracing, monitoring, and observability
- Evaluation datasets and regression testing
- Latency, throughput, and cost measurement
- Caching, model routing, and performance optimization
- Deployment, configuration, secrets, and operational practices

### 7. RAG security and privacy

- Authentication, authorization, and multi-tenant isolation
- Document-level access control and data leakage prevention
- Direct and indirect prompt injection
- Malicious document and metadata poisoning
- Retrieval manipulation and sensitive-data exposure
- Embedding privacy and inversion risks
- Agent and tool abuse, where agentic capabilities are introduced
- Threat modelling, adversarial testing, remediation, and regression tests

### 8. Multimodal RAG

- Scanned documents, OCR, and layout-aware extraction
- Tables, diagrams, images, and slide decks
- Multimodal embeddings and vision-language models
- Retrieval and grounding across text and visual content

## How I'm approaching the work

- **Build incrementally:** Each release adds a useful capability while keeping the application working.
- **Learn the internals:** Implement core RAG components directly before relying on high-level abstractions to hide their behaviour.
- **Stay technology-agnostic:** Choose tools based on the requirements and trade-offs of each feature, rather than committing to a stack prematurely.
- **Measure, don't guess:** Use repeatable datasets and metrics to assess whether a change actually improves the system.
- **Treat security as an engineering concern:** Test access boundaries and AI-specific attack surfaces as the product evolves.
- **Deploy the product:** The goal is to make the MVP and subsequent releases available through a public production URL, not leave the work as a local-only demo.

Features are developed in small increments, with their own design decisions, implementation, tests, and review. The roadmap describes the intended direction; it is not a claim that every listed capability already exists.

## Project status

RagForge is under active development. Capabilities should be considered experimental until they are implemented, tested, and documented in the repository.

## License

No license has been selected yet. Until a license is added, all rights are reserved by default; please don't assume the code is available for reuse.
