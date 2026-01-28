This repository implements an efficient and adaptive reasoning framework for Large Language Models (LLMs) operating on heterogeneous graphs. It introduces a multi-agent system with a dual-evolving mechanism that jointly optimizes:

Graph-Evolving: Dynamic subgraph construction, pruning, and edge reweighting for task-specific relevance.
Reasoning-Evolving: Adaptive selection of LLM reasoning strategies (CoT, ToT, self-reflection, planning) via meta-controllers and bandit-style exploration.

Together, these enable robust, scalable, and cost-effective reasoning over complex, multi-relational data.

Key Features

- Multi-Agent Reasoning: Coordinator, Planner, Retriever, Reasoner, Verifier agents with message-passing and role specializations.
- Dual-Evolving Optimization:

- Graph: Structure-aware pruning, meta-path expansion, relevance scoring, neighborhood sampling.
- Reasoning: Policy-driven selection of prompting strategies; self-improvement through feedback.

- Heterogeneous Graph Support: Nodes/edges with types, attributes, and relation-specific encoders.
- Plug-in LLMs: Compatible with local and hosted LLMs (OpenAI, Azure OpenAI, vLLM, llama.cpp).
- Modular Retrieval: Hybrid graph + text retrieval; supports semantic search, path-based expansion.
- Evaluation Suite: Accuracy, F1, path-quality, cost/latency, ablations, and reproducibility scripts.
- Resource Efficiency: Caching, adaptive depth, batched queries, cost-aware policies.

Conceptual Architecture
+----------------------------- Multi-Agent Layer -----------------------------+
|  Coordinator  <---->  Planner  <---->  Retriever  <---->  Reasoner  <----> |
|                                                              Verifier       |
+------------------------- Dual-Evolving Controllers -------------------------+
|  Graph-Evolving (structure)      |      Reasoning-Evolving (policies)      |
|  - subgraph sampling             |      - strategy selection (CoT/ToT/etc) |
|  - edge reweighting              |      - feedback + bandits/meta-learning |
|  - meta-path expansion           |      - self-reflection & verification   |
+------------------------ Heterogeneous Graph Subsystem ----------------------+
|  Node/Edge Types, Relation Encoders, Hybrid Retrieval, Cache               |
+---------------------------------------------------------------------------+

Project Structure
├── configs/
│   ├── default.yaml
│   ├── graph.yaml
│   └── llm.yaml
├── data/
│   ├── raw/
│   ├── processed/
│   └── samples/
├── docs/
│   └── examples.md
├── src/
│   ├── agents/
│   │   ├── coordinator.py
│   │   ├── planner.py
│   │   ├── retriever.py
│   │   ├── reasoner.py
│   │   └── verifier.py
│   ├── controllers/
│   │   ├── graph_evolving.py
│   │   └── reasoning_evolving.py
│   ├── graph/
│   │   ├── hetero_graph.py
│   │   ├── encoders.py
│   │   └── samplers.py
│   ├── llm/
│   │   ├── providers.py
│   │   ├── prompts/
│   │   │   ├── cot.txt
│   │   │   ├── tot.txt
│   │   │   └── verify.txt
│   │   └── cache.py
│   ├── retrieval/
│   │   ├── hybrid_retrieval.py
│   │   └── scoring.py
│   ├── evaluation/
│   │   ├── metrics.py
│   │   └── ablations.py
│   └── utils/
│       ├── logging.py
│       ├── config.py
│       └── io.py
├── tests/
│   ├── test_graph.py
│   ├── test_agents.py
│   └── test_evolving.py
├── scripts/
│   ├── preprocess.py
│   ├── run_experiment.py
│   └── evaluate.py
├── LICENSE
├── README.md
└── requirements.txt


