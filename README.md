# Siddharth Yalamanchili

I build AI systems across model training and application engineering: distilling retrieval models, learning over graphs, designing causal-analysis agents, testing retrieval, and adapting vision transformers.

My software engineering work includes six **TypeScript/Node.js services with GraphQL APIs at Friennly**, and **Python/FastAPI claims-analytics APIs at Florida Blue**. That work spans database integrations, authorization, background jobs, and cloud delivery.

[Projects](#selected-projects) · [Engineering experiments](#engineering-experiments) · [Skills](#skills) · [Experience](#work-experience) · [Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/)

## Selected projects

### 1. Knowledge distillation for semantic search

A cross-encoder reads each query and passage together, making it expensive to score a large corpus. I distilled its relevance judgments into a smaller bi-encoder whose document embeddings can be computed ahead of time.

The training code combines pairwise margins, ranking distributions, and contrastive learning; serving uses FAISS and FastAPI. A saved evaluation on **200 held-out queries** measured **nDCG@10 of 0.3796 for the vanilla student and 0.5432 after distillation**, on a 9,992-chunk corpus.

*PyTorch · Sentence-Transformers · Knowledge distillation · FAISS · FastAPI*

[Code](https://github.com/Axionis47/semantic-search-kd) · [Loss implementation](https://github.com/Axionis47/semantic-search-kd/blob/main/src/kd/losses.py) · [Recorded evaluation](https://github.com/Axionis47/semantic-search-kd/blob/main/evidence/production/EVALUATION_SUMMARY.md)

### 2. Graph learning for session-based recommendations

An anonymous shopper has a short click session and no established user history. I modeled item co-occurrence as a graph, then compared GraphSAGE, graph attention, and a graph transformer for next-item prediction.

The transformer uses attention over neighbors and Laplacian positional encodings. The reduced model reached **38.28% validation Recall@10**; the case study reports **33.10% on the later held-out test split**. The walkthrough explains the temporal split, baselines, model changes, and generalization gap.

*PyTorch Geometric · Graph neural networks · Graph transformers · Temporal evaluation*

[Code](https://github.com/Axionis47/GAT-Recommendation) · [Walkthrough notebook](https://github.com/Axionis47/GAT-Recommendation/blob/main/notebooks/session_recsys_walkthrough.ipynb) · [Results and design discussion](https://axionis47.github.io/portfolio/projects/gat-recommendation.html)

### 3. Causal Analysis Desk

A difference in outcomes can reflect how people entered a treatment group. Selecting an analysis therefore needs facts about assignment, sampling, and variable timing that column names cannot supply.

I built a LangGraph agent that profiles a dataset and interviews the analyst for that context. Sourced claims and method requirements feed a typed handoff to one of three analysis families. Statistical execution runs through **DoWhy, pyfixest, or rdrobust**, and explanations cite the resulting artifacts.

*Python · LangGraph · Pydantic · Causal inference · FastAPI · React/TypeScript*

[Code and demonstration](https://github.com/Axionis47/causal-inference-agent#see-it) · [Architecture and API contracts](https://github.com/Axionis47/causal-inference-agent/blob/main/docs/architecture.md) · [Handoff tests](https://github.com/Axionis47/causal-inference-agent/blob/main/causal_agent/desk/tests/test_handoff.py)

### 4. FinRAG: retrieval strategies and evidence access

If retrieval selects the wrong reporting period or misses one side of a conflict, generation starts with incomplete evidence. I separated query planning, retrieval, and reranking to test those choices independently, with access checks around source selection.

In the controlled graph comparison, entity links found both sources for **3/4 conflict questions**, versus **2/4 with dense retrieval**. Temporal links reduced correct-section retrieval from **9/10 to 7/10 time questions**. The saved traces show broad quarter links displacing a correct Q3 source on this small constructed corpus.

*Python · FastAPI · Vertex AI · Neo4j · BM25 · GraphRAG · Evaluation*

[Code](https://github.com/Axionis47/finsolve-abac-rag) · [Experiments and results](https://github.com/Axionis47/finsolve-abac-rag/blob/main/docs/experiments.md) · [Success and failure traces](https://github.com/Axionis47/finsolve-abac-rag/blob/main/docs/walkthrough.md)

### 5. LoRA adaptation of a vision transformer

I adapted a pretrained **SegFormer-B0** encoder to binary drivable-area segmentation with custom low-rank attention adapters and a trainable decode head, while keeping the original encoder weights frozen.

The documented BDD100K experiment used **200 training images, 100 validation images, and three epochs**, reaching **0.806 mean IoU**. The case study covers the adapter injection, trainable parameter accounting, segmentation outputs, and the limits of that small-subset evaluation.

*PyTorch · SegFormer · Custom LoRA · Computer vision · Semantic segmentation*

[Implementation and evaluation case study](https://axionis47.github.io/portfolio/projects/laneguard-adas.html)

## Engineering experiments

These studies examine how an agent's behavior changes when its memory, domain representation, or tool interface changes. Each links to the implementation and available evidence.

| Study | What I investigated | Inspect the work |
| --- | --- | --- |
| **Agent memory** | Integrated five released memory mechanisms with an AppWorld agent and no-memory controls; followed learning into stored knowledge, supplied context, actions, and outcomes. | [Repository](https://github.com/Axionis47/agent-memory-comparison) · [Code study](https://github.com/Axionis47/agent-memory-comparison/blob/main/docs/CODE-STUDY.md) · [Findings](https://github.com/Axionis47/agent-memory-comparison/blob/main/docs/FINDINGS.md) |
| **Ontology and domain relationships** | Made domain relationships explicit through schemas and generated functions; inspected verification gates, committed actions, and failures across versions. | [Repository](https://github.com/Axionis47/ontology-agent-lab) · [AppWorld experiment](https://github.com/Axionis47/ontology-agent-lab/tree/main/experiments/appworld-ontology) |
| **Tool surfaces, Basis engineering** | Compared small, grouped, and whole-task tools for the same shipping workflow across model sizes; examined completion, argument errors, and recovery. | [Original lab](https://github.com/Axionis47/agent-engineering-fp/blob/main/01-mcp-tool-gateway/SHIPPING-ACTION-SPACE-LAB.md) · [E04 study and results](https://github.com/Axionis47/trajectory-observability-evals/tree/main/experiments/e04-tool-abstraction-model-capability) |
| **Evaluation and observability** | Compared final-output checks with component and trajectory evidence; used OpenTelemetry and SQLite to inspect the first observed failure. | [Studies and experiment index](https://github.com/Axionis47/trajectory-observability-evals) |

## Skills

### AI engineering

**Agent systems:** AI agents, context engineering, RAG, retrieval, LLM evaluations, and guardrails.

**Model work:** training, knowledge distillation, graph learning, and LoRA adaptation, demonstrated in the projects above.

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langgraph&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LangSmith](assets/tech-stack/langsmith.svg)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)

### Software engineering

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=flat-square)

**Backend and APIs:** REST APIs, structured request/response validation, and database-backed services.

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=flat-square&logo=graphql&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![SQLGlot](https://img.shields.io/badge/SQLGlot-336791?style=flat-square)

**Data systems:** databases, search, and ETL/ELT.

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white)
![Firestore](https://img.shields.io/badge/Firestore-DD2C00?style=flat-square&logo=firebase&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

**Cloud platforms**

![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Cloud Run](https://img.shields.io/badge/Cloud%20Run-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Vertex AI](https://img.shields.io/badge/Vertex%20AI-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![AWS](assets/tech-stack/aws.svg)
![Amazon Bedrock](assets/tech-stack/amazon-bedrock.svg)
![Amazon S3](assets/tech-stack/amazon-s3.svg)

**Production engineering:** CI/CD, automated testing, and observability.

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat-square&logo=terraform&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

## Work experience

| Role | Dates | Work |
| --- | --- | --- |
| **Software Engineer (contract), Florida Blue** | Aug to Dec 2024 | Python/FastAPI text-to-SQL API, semantic schema retrieval, Pydantic and SQLGlot validation, and read-only PostgreSQL execution. |
| **Software Engineer, Friennly** | Feb to Nov 2023 | Built six TypeScript/Node.js services with GraphQL APIs on Cloud Run, supporting the product's first 500 customers. Firebase authorization, signed-URL uploads, Cloud Tasks, Terraform, and GitHub Actions. |
| **Software Engineer Intern, LTI Mindtree** | May to Dec 2022 | Python/YAML connector test flows for Fosfor Spectra. Automated 12% of the Snowflake and 8% of the Elasticsearch cases in the existing manual QA checklists. |
| **Battery Simulation Intern, Sirius Motorsports** | 2022 | Embedded C battery-protection firmware, ADC calibration, and bench testing. |

## Education

- **Rutgers University:** M.S. in Statistics - Data Science, 2024 to 2025.
- **Princeton University:** Visiting Student, Jan to May 2025. Coursework in graph learning and advanced probabilistic methods.
- **BITS Pilani:** B.E. in Electrical and Electronics, minor in Data Science, 2019 to 2023.

## Awards

**RU AWS GenAI Health Hack 2025, winner.** Led a nine-person team and built a rubric-based clinical-presentation evaluation API. [Case study](https://axionis47.github.io/portfolio/projects/hackathon-osce-grader.html).

Open to AI engineering and software engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:siddharth.yalamanchili47@gmail.com)
