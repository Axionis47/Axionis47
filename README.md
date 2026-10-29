# Siddharth Yalamanchili

I build AI applications and backend services. My work includes causal-analysis agents, retrieval experiments, insurance analytics, and a healthcare startup backend.

[AI engineering](#ai-engineering) · [Software engineering](#software-engineering) · [Work experience](#work-experience) · [Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=flat-square)

## AI engineering

**Skills:** context engineering, agent workflows, retrieval, evaluation, and model-output validation.

### Causal Analysis Desk

A score difference between students who took a course and those who did not can reflect who enrolled. Choosing an analysis requires knowing how the course was assigned, when variables were measured, and which comparisons the data supports.

I built a desk that profiles a CSV and interviews the analyst about those missing facts. Answers become claims with sources and confirmation status. Code checks each method's requirements; the model interprets answers and makes choices within the allowed options. The selected analysis runs through DoWhy, pyfixest, or rdrobust.

That separation reaches the code: the analysis receives a typed context pack, calculations run in Python, and generated explanations must cite artifacts the run actually produced.

[Walk through a run](https://github.com/Axionis47/causal-inference-agent#see-it) · [Decision boundary](https://github.com/Axionis47/causal-inference-agent/blob/main/docs/adr/0002-code-computes-facts-the-model-judges-the-harness-gates.md) · [Handoff tests](https://github.com/Axionis47/causal-inference-agent/blob/main/causal_agent/desk/tests/test_handoff.py)

### FinRAG: testing which evidence reaches the model

A generated answer starts with whatever retrieval found. I separated query planning, retrieval, and reranking so I could inspect missing evidence and change one stage at a time.

One experiment compared dense retrieval with graph expansion. The entity and temporal graphs shared the same dense seeds, scoring rule, and hop limit; the edge layer changed.

| Test | Dense baseline | Graph variant | Result |
| --- | --- | --- | --- |
| Find a correct section on 10 time questions | 9/10 | Temporal links | 7/10 |
| Retrieve both sources for 4 conflicting claims | 2/4 | Entity links | 3/4 |

The temporal failure was specific: broad quarter links promoted Q1 and Q2 sections above a correct Q3 seed. That points to a graph-schema problem. The documented next experiment is a narrower temporal schema. These results come from a small constructed corpus; the metrics measure retrieval coverage.

[Experiment setup and limits](https://github.com/Axionis47/finsolve-abac-rag/blob/main/docs/experiments.md) · [Saved results](https://github.com/Axionis47/finsolve-abac-rag/tree/main/evals/results) · [Success and failure traces](https://github.com/Axionis47/finsolve-abac-rag/blob/main/docs/walkthrough.md)

**AI and ML tools**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-189AB4?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langgraph&logoColor=white)
![LangSmith](assets/tech-stack/langsmith.svg)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)

<details>
<summary>Retrieval, analysis, and model platforms</summary>

![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=flat-square&logo=neo4j&logoColor=white)
![ChromaDB](https://img.shields.io/badge/ChromaDB-F7B93E?style=flat-square)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=flat-square)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Vertex AI](https://img.shields.io/badge/Vertex%20AI-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Amazon Bedrock](assets/tech-stack/amazon-bedrock.svg)

</details>

## Software engineering

**Skills:** backend APIs, authentication and authorization, database integrations, background jobs, testing, and cloud deployment.

### Backend services at Friennly

The backend had to coordinate patient and provider onboarding, scheduling, chat, and file sharing. I built six TypeScript/Node.js services with GraphQL APIs and deployed them with Docker on Cloud Run.

Firebase enforced user roles. Signed URLs kept file uploads outside application servers. Cloud Tasks handled background jobs and retries. Terraform defined infrastructure, and GitHub Actions ran releases.

### Keeping API contracts and tests close to the code

Causal Desk's Python API and React client need to agree on response shapes. The API produces an OpenAPI schema, TypeScript types are generated from it, and CI checks that both stay current. A changed response field is caught during the build.

At LTI Mindtree, my Python connector tests checked schema mappings, record counts, and transformed outputs across Fosfor Spectra pipelines with Snowflake and Elasticsearch. Those checks test whether the data arrived correctly across the full pipeline.

[API contracts and CI](https://github.com/Axionis47/causal-inference-agent/blob/main/docs/architecture.md#the-wire) · [Package boundaries](https://github.com/Axionis47/causal-inference-agent/blob/main/docs/architecture.md#the-layers)

**Backend and delivery tools**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=flat-square&logo=graphql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat-square&logo=terraform&logoColor=white)

<details>
<summary>Databases, data processing, cloud, and development tools</summary>

**Application development**

![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![SQLGlot](https://img.shields.io/badge/SQLGlot-336791?style=flat-square)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)

**Databases and data processing**

![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white)
![Firestore](https://img.shields.io/badge/Firestore-DD2C00?style=flat-square&logo=firebase&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)

**Cloud and delivery**

![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Cloud Run](https://img.shields.io/badge/Cloud%20Run-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![AWS](assets/tech-stack/aws.svg)
![Amazon S3](assets/tech-stack/amazon-s3.svg)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

**Testing and monitoring**

![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Ruff](https://img.shields.io/badge/Ruff-261230?style=flat-square&logo=ruff&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

</details>

## Work experience

| Role | Dates | Work |
| --- | --- | --- |
| **Software Engineer (contract), Florida Blue** | Aug to Dec 2024 | Claims text-to-SQL with schema retrieval, SQL validation, and read-only PostgreSQL execution. |
| **Software Engineer, Friennly** | Feb to Nov 2023 | Six backend services, GraphQL APIs, Firebase authorization, and Cloud Run deployment. |
| **Software Engineer Intern, LTI Mindtree** | May to Dec 2022 | Python test flows for ETL/ELT connectors, including Snowflake and Elasticsearch. |
| **Battery Simulation Intern, Sirius Motorsports** | 2022 | Embedded C battery protection firmware, ADC calibration, and bench testing. |

## Working notes

The [engineering notes](thinking/README.md) explore context, tool boundaries, recovery, and evaluation through illustrative cases. The projects above link to implementations, runs, and experiment reports.

Open to AI engineering and software engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:sidsy04@gmail.com)
