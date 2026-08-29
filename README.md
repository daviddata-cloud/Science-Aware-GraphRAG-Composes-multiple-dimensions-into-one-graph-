# Physics-Aware GraphRAG: Composing Multi-Dimensional World Models

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![Framework: LangGraph](https://img.shields.io/badge/Framework-LangGraph-orange.svg)](https://github.com/langchain-ai/langgraph)
[![Database: Neo4j](https://img.shields.io/badge/Database-Neo4j-blueviolet.svg)](https://neo4j.com/)

A production-pattern Proof-of-Concept (PoC) demonstrating **Spatiotemporal GraphRAG governed by Explicit Graph Engineering and Physics-Informed Neural Networks (PINNs)**. 

This repository implements a "World AI" blueprint that embeds reality as a continuous, interconnected network fabric of composable dimensions layered into a single knowledge graph. By forcing LLM retrieval agents to operate inside strict mathematical boundaries and deterministic state machines, this architecture completely eradicates unconstrained agent hallucinations during multi-hazard cascade tracking.

---

## 🌌 The Multi-Dimensional Architecture
Linkedin: https://www.linkedin.com/feed/update/urn:li:activity:7499558786852917248/

Large Language Models are excellent text articulators, but they are natively blind to physical invariants, causality, and temporal progression. This framework scales retrieval into higher dimensional spaces (5D, 6D+) to bind autonomous predictions to real-world conservation laws:
<img width="653" height="860" alt="image" src="https://github.com/user-attachments/assets/a3e8c49f-1193-4e19-9fc7-edbde270ea5b" />

```text
     [ GEOSPATIAL FIELD DATA ]         [ MATHEMATICAL INVARIANTS / LAWS ]
   (NWSS Metrics, NOAA Fluid Feeds)     (SIR ODEs, Navier-Stokes, Heat Eq)
                 │                                       │
                 ▼                                       ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                  PINN LOSS-REGULATED EMBEDDING GATEWAY                       │
│  - Solves Residual Derivatives (f = dI/dt - (beta*S*I - gamma*I) = 0)        │
│  - Guarantees Physical Conservation Bounds Before Ingestion                  │
└────────────────────────────────┬─────────────────────────────────────────────┘
                                 │
                                 ▼ (Physically-Consistent State Vectors)
┌──────────────────────────────────────────────────────────────────────────────┐
│                    SPATIOTEMPORAL KNOWLEDGE GRAPH FABRIC                     │
│  - Uber H3 Geospatial Cells          - Explicit Ancestral & Version Edges    │
│  - Sliding Temporal Graph Windows    - Multi-Field Covariation Metrics       │
└────────────────────────────────┬─────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                   SHARED WORKFLOW STATE OBJECT (LANGGRAPH)                   │
│  { inputs, active_h3_cells, physics_residuals, cypher_query, audit_trail }   │
└────────────────────────────────┬─────────────────────────────────────────────┘
                                 │
                                 ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                  FORMAL AGENTIC CONTROL GRAPH ENGINE                         │
│                                                                              │
│    ┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐   │
│    │ Entity-Extract  │ ────► │ Cypher-Gen Node │ ────► │ Execution Node  │   │
│    │      Node       │       └────────┬────────┘       └────────┬────────┘   │
│    └─────────────────┘                │                         │            │
│             ▲                         ▼ Conditional Route       ▼            │
│             │                ┌─────────────────┐       ┌────────┴────────┐   │
│             └────────────────┤  Syntax Fixer   │       │ Deterministic   │   │
│                 Retry Loop   │      Node       │       │ Quality Gate    │   │
│                              └─────────────────┘       └────────┬────────┘   │
│                                                                 │            │
│                                                                 ▼            │
│                                                        [ Verified Output ]   │
└──────────────────────────────────────────────────────────────────────────────┘
```

1. **3D Space (Spatial Field):** Geographic coordinates are mapped precisely via an inspectable visual grid leveraging **Uber H3 Hexagonal Indexing**.
2. **4D Time (Temporal Progression):** Shifting state telemetry points are linked via chronological sequence markers (`[:NEXT_STATE]`), enabling native execution tracing for "what was true then."
3. **5D Physical Invariants (PINN Constraints):** Prior to data ingestion, telemetry parameters pass through neural differential solvers to minimize physical residual losses. Inputs that violate thermodynamics or epidemic conservation models are flagged.
4. **6D Intent & Causality (Graph Engineering):** A deterministic multi-agent state graph isolates execution scopes, evaluates strict quality metrics, and handles runtime failures automatically via validation loops.

---

## 📁 Repository Structure

```text
├── .env.example              # Central configuration profiles (Endpoints, Neo4j Credentials)
├── requirements.txt          # Strictly versioned package dependency manifests
├── README.md                 # System overview, deployment manual, and architecture map
├── data/                     # Sample public health metrics, weather feeds, and fluid vectors
├── src/
│   ├── parser.py             # Asynchronous multi-format time-series ingest pipelines
│   ├── pinn_validator.py     # Custom PINN loss optimization layers tracking physical residuals
│   ├── ingest_stream.py      # Asynchronous, thread-safe, non-blocking Kafka/log listener script
│   └── agent_engine.py       # Deterministic LangGraph execution workflows, nodes, and self-healing edges
└── web_ui.py                 # Interactive visualization client mapping localized neighborhoods
```

---

## 🛠️ Core Engineering Highlights

### 1. Asynchronous, Auto-Refreshing Ingestion (`src/ingest_stream.py`)
To prevent mid-batch `401 Unauthorized` crashes during high-load historical ingest runs, the pipeline entirely bypasses static, short-lived tokens. It implements a non-blocking `get_bearer_token_provider` loop via Microsoft's `azure-identity` layer to refresh infrastructure access credentials transparently in the background.

### 2. Injection-Proof Structural Sanitization
Unstructured data feeds are string-scrubbed by dedicated sanitation filters prior to transactional injection, ensuring character sequences like `'`, `"`, or `` ` `` cannot execute parameter escapes or break database query schemas during real-time ingest.

### 3. Self-Healing Agent Execution Graph (`src/agent_engine.py`)
Rather than relying on unstructured, free-form loops that display high execution variance, agent actions are completely isolated into independent python handlers. If an agent hits a database syntax warning or a physics residual threshold breach, conditional control flow edges redirect the transaction payload to an automated repair node natively.

### 4. Deterministic Performance Breakers
Unbounded open-ended traversal parameters (e.g., `MATCH (a)-[*1..10]->(b)`) cause sudden memory exhaustion crashes under high concurrency loads. This architecture forces rigid multi-hop bounds and deploys hard `450ms` execution circuit breakers inside query engines.

---

## ⚡ Quickstart Guide

### 1. Provision Infrastructure Dependencies
Ensure an active, local or cloud-native Neo4j Database instance is accessible via Bolt protocol, alongside access to Azure OpenAI completions endpoints.

### 2. Clone Repository & Install Manifest
```bash
git clone https://github.com/yourusername/physics-aware-graphrag.git
cd physics-aware-graphrag
pip install -r requirements.txt
```

### 3. Establish Runtime Configurations
Copy the environment variables sample file and populate your respective target enterprise tokens:
```bash
cp .env.example .env
nano .env
```

### 4. Run the Ingestion Stream
Start the asynchronous stream listener to monitor, process, and map real-time physics-constrained telemetry logs:
```bash
python src/ingest_stream.py
```

### 5. Execute the Physics-Aware Agent Engine
Initialize the LangGraph orchestration framework to process spatiotemporal queries safely:
```bash
python src/agent_engine.py
```

---

## 🔬 Scope & Frontier Lines
*This system is fundamentally structured as a Proof-of-Concept (PoC).* It successfully confirms that the architectural pattern of multi-dimensional constraint coupling delivers stable, predictable world models. Production-hardening steps—such as full Attribute-Based Access Control (ABAC) isolation boundaries, containerized multi-node clusters, and strict enterprise authentication—are roadmap requirements.
