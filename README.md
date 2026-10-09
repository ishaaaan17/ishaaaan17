<div align="center">

<img src="snake-frame.svg" width="100%" alt="Ishaan Maheshwari, with an animated snake circling the profile banner"/>

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=500&size=20&duration=2600&pause=700&color=C4B5FD&center=true&vCenter=true&width=780&lines=distributed+systems+%2F%2F+graph+ML+%2F%2F+network+protocols;IT+%2B+MBA+%40+ABV-IIITM+Gwalior;500%2B+DSA+solved+in+C%2B%2B+%C2%B7+JEE+98.6%25ile;I+build+systems+I+can+measure%2C+not+just+describe" alt="headline" />

<br/>
<p align="center">
  <a href="https://www.linkedin.com/in/ishaan-maheshwari-967741292">
    <img src="https://img.shields.io/badge/LINKEDIN-Ishaan%20Maheshwari-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>

  <a href="mailto:ishaan.maheshwari101@gmail.com">
    <img src="https://img.shields.io/badge/EMAIL-ishaan.maheshwari101%40gmail.com-1a1a2e?style=for-the-badge&labelColor=EA4335" alt="Email">
  </a>
</p>

<img src="https://komarev.com/ghpvc/?username=ishaaaan17&label=PROFILE+VIEWS&color=8B5CF6&style=flat-square" alt="profile views" />

</div>


## About

**Integrated B.Tech (IT) + MBA student at ABV-IIITM Gwalior** (Aug 2023 – May 2028). I engineer at the intersection where machine learning meets high-performance systems: retrieval pipelines with zero tolerance for hallucination, graph neural networks evaluated without temporal leakage, and socket-level network protocols you can watch recover under Wireshark packet drops.

> **The thesis behind everything I build:** A system isn't finished when it runs without errors once. It is finished when I can put a hard number on it (latency percentiles, PR-AUC, false-positive rate at fixed recall) and explain mechanically why that number moved.

### Quick facts

| | |
|---|---|
| **Program** | Integrated B.Tech in IT + Master of Business Administration (MBA), ABV-IIITM Gwalior |
| **Duration** | Aug 2023 – May 2028 · Gwalior, India |
| **Languages** | C++, Python, JavaScript, SQL, C |
| **Focus areas** | Distributed systems · network protocols · Graph ML · RAG pipelines & vector search |
| **Problem solving** | **500+ DSA problems** solved in C++ on LeetCode |
| **Competitive exam** | **JEE Main 2023 · 98.6 percentile** among 1.1M+ candidates nationwide |
| **Contact** | [ishaan.maheshwari101@gmail.com](mailto:ishaan.maheshwari101@gmail.com) · [LinkedIn](https://www.linkedin.com/in/ishaan-maheshwari-967741292) |

### Project timeline

| Date | System | Core measured outcome |
|---|---|---|
| Oct 2026 | **MarketStream Lakehouse Platform** | 81k EPS ingestion · 5.05x small-file compaction speedup · exactly-once chaos verified |
| Aug 2026 | **SEC Financial Intelligence RAG Engine** | 7.25 ms P50 latency · 100% Top-4 table retrieval · zero-leakage payload isolation |
| Jan 2026 | **GraphSAGE AML Transaction Monitoring** | 18.3x PR-AUC gain over rules (0.0089 → 0.1633) · 80% false-positive cut at 90% recall |
| Sep 2025 | **Decentralized P2P File Sharing Engine** | Trackerless C++17 UDP protocol · zero-drop swarm recovery · O(1) memory persistence |


<div align="center">

<img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=6,11,20&height=3" width="100%"/>

<h2>SELECTED WORK</h2>

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=500&size=15&duration=3200&pause=1000&color=8B5CF6&center=true&vCenter=true&width=640&lines=%E2%99%A0+%E2%99%A5+++four+builds%2C+one+throughline%3A+measure+everything+++%E2%99%A6+%E2%99%A3;from+raw+UDP+sockets+to+GNNs%2C+lakehouses%2C+and+state+machine+RAG+%E2%86%93" alt="section tease" />

</div>

### [MarketStream Lakehouse](https://github.com/ishaaaan17/market-stream-lakehouse) — High-Throughput Stream Processing & Medallion Lakehouse

> `[ DuckDB ] [ Polars ] [ PyArrow ] [ Redpanda / Kafka ] [ dbt ] [ Parquet / Iceberg ] [ Exactly-Once ]`

A high-throughput financial market stream processing engine and Medallion Lakehouse platform built to handle **80,000+ events/sec**. Solves the three primary failure modes of real-time streaming architectures: the Lakehouse **Small-File Problem** via an autonomous compaction worker, **at-least-once duplicate corruption** via deterministic event-time watermarking, and **consumer worker crashes** verified via automated chaos testing.

<p align="center">
  <img src="lakehouse-architecture.svg" alt="MarketStream Lakehouse Architecture" width="100%" />
</p>

| Pipeline Dimension | Empirical Benchmark | Engineering Significance |
|---|---|---|
| **Producer Ingestion Throughput** | **81,196 events/sec** | High-frequency multi-venue equities order flow |
| **Consumer & Dedup Drain Rate** | **750,564 events/sec** | Monotonic watermarking & in-memory state tracking |
| **Compaction Scan Acceleration** | **5.05x FASTER** | Scan latency dropped from **13.98 ms → 2.77 ms** |
| **Lakehouse Storage Compression** | **18.94% reduction** | Consolidated dictionary encoding & row group striping |
| **Worker Crash Fault Tolerance** | **0 Duplicates · 0 Lost Records** | Exactly-Once state verified after forceful `SIGKILL` termination |

**Battle-tested architectural decisions**
- **Solving the Small-File Problem (`CompactionWorker`):** Micro-batch streaming writes small 20KB–500KB Parquet files that cause metadata thrashing and disk seek bottlenecks. The autonomous compaction engine gathers fragmented partitions exceeding threshold (`min_files = 4`), merges Arrow tables in zero-copy chunks, and writes consolidated 128MB Parquet files, accelerating analytical query scans by **5.05x**.
- **Event-Time Watermarking & Idempotent Deduplication:** Maintains a monotonic high-water mark with a 30-second bounded delay window, quarantining out-of-order ticks from disparate exchanges while deduplicating replayed primary keys idempotently.
- **Chaos Engineering & Exactly-Once Semantics:** Forcefully terminates consumer processes mid-flight (`SIGKILL`) with injected duplicate bursts and late ticks; replayed broker streams recover state with zero duplicate trades and zero lost executions.
- **Medallion Architecture & Kimball Data Marts:** Raw immutable Bronze append logs promote to cleaned Silver fact tables with Dead-Letter Queue (DLQ) quarantine, feeding Gold marts (`agg_intraday_vwap`, `fct_execution_slippage`, `dim_venues`) with strict dbt data contract assertions.

`Python` `DuckDB` `Polars` `PyArrow` `Redpanda` `dbt` `Streamlit` `Docker` `Medallion Architecture`

---

### [SEC Financial Intelligence RAG Engine](https://github.com/ishaaaan17/financial-intelligence-rag) — Autonomous Multi-Hop RAG over 10-K / 10-Q Filings

> `[ LangGraph ] [ Qdrant ] [ RAG ] [ grounding verification ] [ FlashRank ] [ $0 Cloud Stack ]`

Financial regulatory filings are a notoriously hostile retrieval target: essential numerical answers live inside dense, multi-column financial statements, comparative questions cross arbitrary quarters, and an ungrounded hallucination is worse than a hard refusal. This is an autonomous, multi-hop retrieval and reasoning engine for SEC 10-K and 10-Q documents, orchestrated as a **LangGraph state machine** over a **Qdrant** vector store with local cross-encoder reranking.

<p align="center">
  <img src="rag-architecture.svg" alt="SEC Financial Intelligence RAG Architecture" width="100%" />
</p>

| Metric | Result | Engineering context |
|---|---|---|
| **P50 / P95 Latency** | **7.25 ms · 17.76 ms** | Filtered vector search + local reranking pass |
| **Metadata Isolation** | **100%** | Query-time Qdrant payload filters prevent cross-quarter bleed |
| **Table Retrieval** | **100% Top-4** | Custom table parsing prioritizes tables over narrative boilerplate |
| **Inference Cost** | **$0.00** | Groq (`llama-3.3-70b`) + local embeddings (`all-MiniLM-L6-v2`) |

**Battle-tested architectural decisions**
- **DEC-005 — Database-level metadata isolation over application filtering:** Naive vector search over multi-quarter corpora risks retrieving chunks from the wrong quarter if semantic embeddings are close. Enforced `ticker`, `fiscal_year`, and `fiscal_period` as indexed payload filters evaluated *at query time* inside Qdrant. This prevents cross-period context contamination by construction rather than post-hoc filtering.
- **DEC-009 — Table-preserving extraction (`pdfplumber`):** Generic PDF loaders destroy column alignment when extracting financial tables. Implemented table-aware extraction with Markdown table serialization, tagging chunks as `type: table` so tabular data retains mathematical structure.
- **DEC-006 — Local Cross-Encoder Reranking (`FlashRank`):** Narrative disclosures (risk factors, boilerplate) often match raw query keywords better than numbers. Applied a local `ms-marco-TinyBERT-L-2-v2` cross-encoder reranking pass in single-digit milliseconds, lifting financial balance sheets to the top of the context window.
- **DEC-007 & DEC-014 — Two-pass synthesis with bounded hallucination recovery:** A single prompt that generates and "self-checks" its own output routinely confirms its own errors. Decoupled generation into `generate_comparison` and an independent `verify_grounding` node. If grounding checks fail, a bounded retry loop (`MAX_GENERATION_RETRIES = 1`) triggers regeneration with explicit context before safely falling back to `handle_missing_data`.
- **DEC-015 — Bounded backoff and observability:** Wrapped LLM chains in `tenacity` exponential backoff restricted strictly to transient faults (rate limits, timeouts), with structured per-node latency logging.

`Python` `LangGraph` `Qdrant Cloud` `AWS EC2` `Docker` `FastAPI` `Streamlit` `FlashRank` `pdfplumber` `Groq`

---

### [GraphSAGE AML Transaction Monitoring](https://github.com/ishaaaan17/aml-transaction-monitoring) — Graph Neural Networks for Money-Mule Detection

> `[ GraphSAGE ] [ PyTorch Geometric ] [ XGBoost ] [ fraud / AML ] [ Optuna ] [ leakage-free ML ]`

Money laundering is fundamentally a relational graph problem: individual transactions look completely legitimate in tabular rows, while the illicit pattern exists in cyclic layering, fan-out distributions, and multi-hop mule account chains. Modeled **5M+ IBM transactions** as a dynamic graph and trained an inductive **GraphSAGE** classifier to flag money-mule laundering typologies that conventional rule engines miss.

<p align="center">
  <img src="aml-architecture.svg" alt="GraphSAGE AML Transaction Monitoring Architecture" width="100%" />
</p>

| Model | PR-AUC | False-Positive Rate @ 90% Recall | Architecture notes |
|---|---|---|---|
| **Rule Baseline** | 0.0089 | 33.28% | Industry standard heuristic rules |
| **Tuned XGBoost** | 0.0830 | 11.38% | Tabular gradient boosting (Optuna-tuned) |
| **GraphSAGE (GNN)** | **0.1633** | **6.58%** | **18.3x over rules · 2x over XGBoost · 80% fewer alerts** |

**Battle-tested architectural decisions**
- **Linear chain graph vs. explosive all-pairs line graph:** Connecting all transaction pairs sharing an account would produce **~14 billion edges** from the single largest hub account alone (168,672 transactions), exceeding hardware limits. Engineered a chronological chain graph where each transaction links only to its temporal neighbor per account, keeping edge complexity linear (~1.82 average degree) while preserving layering typology sequences.
- **Evaluation trap: `average_precision_score` vs invalid `auc()`:** Discovered that trapezoidal `auc(recall, precision)` interpolates linearly between PR points, artificially overestimating step-function scores by up to 3.7x on discrete baselines. Switched strictly to Average Precision scoring.
- **Strict chronological split (no lookahead leakage):** Velocity and temporal features depend on history. Standard random cross-validation leaks future transactions into historical windows. Enforced strict 70/15/15 chronological quantile splitting (3.5M train / 761K val / 761K test).
- **Dataset artifact detection:** Identified an uncharacteristic background traffic collapse in the raw IBM dataset after Day 10; restricted training window to Days 1–10 to avoid training on degenerate synthetic artifacts.
- **Optuna GNN optimization:** Evaluated neighbor aggregation functions (mean, lstm, max-pooling) under a 4GB VRAM constraint (RTX 3050), opting for GraphSAGE over memory-intensive GAT attention layers.

`Python` `PyTorch Geometric` `GraphSAGE` `XGBoost` `Optuna` `scikit-learn` `temporal validation` `PR-AUC`

---

### [Decentralized P2P File Sharing Engine](https://github.com/ishaaaan17/p2p-file-sharing) — Trackerless Protocol over Raw UDP in C++17

> `[ C++17 ] [ Winsock ] [ UDP sockets ] [ protocol design ] [ game theory ] [ Wireshark ]`

A decentralized peer-to-peer file distribution protocol written in C++17 from the socket layer up, with zero external networking libraries and no centralized tracker. Because raw UDP provides neither ordering nor delivery guarantees, protocol reliability, piece scheduling, anti-leeching game theory, and disk persistence were engineered directly into the software architecture.

<p align="center">
  <img src="p2p-architecture.svg" alt="Decentralized P2P File Sharing Engine Architecture" width="100%" />
</p>

| Component | Engineering mechanism | Key property |
|---|---|---|
| **Wire Protocol** | 7-type custom framed binary format (`SYN`, `SYN_ACK`, `DATA`, `ACK`, `FIN`, `CHOKE`, `UNCHOKE`) | Compact byte packing over raw UDP |
| **Reliability** | 500 ms sweep retransmission timer, up to 5 retries | Zero-drop packet recovery across swarms |
| **Scheduling** | Rarest-first bitfield scheduler across peer snapshots | Speeds piece propagation, eliminates bottlenecks |
| **Fairness** | Tit-for-Tat game-theoretic choking state machine | Enforces bandwidth reciprocity, prevents leechers |
| **Storage** | Pre-allocated disk layout with `seekp`/`seekg` random writes | Flat O(1) RAM usage regardless of transfer size |
| **Telemetry** | Non-blocking loopback UDP socket dispatch (:6000) to Python | Real-time Streamlit swarm dashboard, Wireshark verified |

**Battle-tested architectural decisions**
- **Decoupled threading model (`SocketManager`):** Dedicated background listener thread runs a blocking `recvfrom()` loop, deserializing datagrams into `Packet` structures and pushing to a thread-safe queue. The main loop polls at 10 ms intervals, completely isolating socket IO from scheduling state machines.
- **Zero-allocation direct-to-disk persistence (`PieceManager`):** Rather than caching multi-megabyte payloads in memory, `initialize_file_layout()` pre-allocates zero-filled files on startup. Inbound chunks are written directly to exact offsets via `seekp(piece_idx * piece_size)` under mutex protection.
- **Rarest-first swarm distribution:** Peers evaluate connected bitfield rarity counts to request least-frequent pieces first, preserving rare chunks from dropping offline if seeders exit.
- **Bandwidth reciprocity (`ChokeManager`):** Evaluates upload vs. download byte ratios per peer; sends `CHOKE` frames to uncooperative nodes to incentivize balanced contribution.

`C++17` `Winsock` `raw UDP datagrams` `CMake` `Wireshark` `GoogleTest` `Streamlit` `multithreading`

---

## What these projects have in common

| Engineering Habit | How it shows up in my work |
|---|---|
| **Measure, then claim** | Verified P50/P95 latencies, PR-AUC improvements, and false-positive drops at fixed recall thresholds. |
| **Evaluate without leakage** | Strict chronological quantile splitting, tuned comparative baselines, and ground-truth validation nodes. |
| **Own the stack end-to-end** | Raw binary sockets in C++17, custom inductive GNN training in PyTorch, state machine orchestration in LangGraph. |
| **Inspectable by design** | Packet-level Wireshark captures, live UDP telemetry streams, and citation-level grounding checks on every LLM claim. |


```
──────────────────────────────  A R S E N A L  ──────────────────────────────
```

<div align="center">

![C++](https://img.shields.io/badge/C++17-0d1117?style=for-the-badge&logo=cplusplus&logoColor=00599C)
![Python](https://img.shields.io/badge/Python-0d1117?style=for-the-badge&logo=python)
![C](https://img.shields.io/badge/C-0d1117?style=for-the-badge&logo=c&logoColor=A8B9CC)
![JavaScript](https://img.shields.io/badge/JavaScript-0d1117?style=for-the-badge&logo=javascript)
![SQL](https://img.shields.io/badge/SQL-0d1117?style=for-the-badge&logo=postgresql)

![PyTorch](https://img.shields.io/badge/PyTorch-0d1117?style=for-the-badge&logo=pytorch)
![PyG](https://img.shields.io/badge/PyTorch_Geometric-0d1117?style=for-the-badge&logo=pytorch&logoColor=EE4C2C)
![DuckDB](https://img.shields.io/badge/DuckDB-0d1117?style=for-the-badge&logo=duckdb&logoColor=FFF000)
![Polars](https://img.shields.io/badge/Polars-0d1117?style=for-the-badge&logo=polars&logoColor=00599C)
![dbt](https://img.shields.io/badge/dbt-0d1117?style=for-the-badge&logo=dbt&logoColor=FF694B)
![Redpanda](https://img.shields.io/badge/Redpanda_Kafka-0d1117?style=for-the-badge&logo=apachekafka&logoColor=white)
![Lakehouse](https://img.shields.io/badge/Iceberg_Parquet-0d1117?style=for-the-badge&logo=apache&logoColor=58a6ff)
![LangGraph](https://img.shields.io/badge/LangGraph-0d1117?style=for-the-badge&logo=langchain&logoColor=white)
![Qdrant](https://img.shields.io/badge/Qdrant-0d1117?style=for-the-badge&logo=qdrant&logoColor=DC2626)
![FastAPI](https://img.shields.io/badge/FastAPI-0d1117?style=for-the-badge&logo=fastapi)
![Streamlit](https://img.shields.io/badge/Streamlit-0d1117?style=for-the-badge&logo=streamlit&logoColor=FF4B4B)
![Docker](https://img.shields.io/badge/Docker-0d1117?style=for-the-badge&logo=docker)
![AWS EC2](https://img.shields.io/badge/AWS_EC2-0d1117?style=for-the-badge&logo=amazonaws&logoColor=FF9900)
![Linux](https://img.shields.io/badge/Linux-0d1117?style=for-the-badge&logo=linux&logoColor=FCC624)
![CMake](https://img.shields.io/badge/CMake-0d1117?style=for-the-badge&logo=cmake)
![Wireshark](https://img.shields.io/badge/Wireshark-0d1117?style=for-the-badge&logo=wireshark)

</div>

| Area | Tools & Core Competencies |
|---|---|
| **Data Engineering & Lakehouse** | Stream processing, event-time watermarking, Medallion Architecture (Bronze/Silver/Gold), DuckDB, Polars, PyArrow, Redpanda / Kafka, dbt, Apache Iceberg, Parquet compaction, exactly-once idempotency |
| **Systems & Networking** | Distributed systems, multithreading, socket programming (TCP/raw UDP), Winsock, wire protocols, Linux |
| **Machine Learning & AI** | PyTorch, PyTorch Geometric, Graph Neural Networks (GraphSAGE), XGBoost, RAG, Qdrant, LangGraph, Optuna |
| **Backend & Infrastructure** | FastAPI, Docker, Docker Compose, AWS EC2, Git, CI/CD GitHub Actions, CMake, GoogleTest |
| **Coursework** | Data Structures & Algorithms · Computer Networks · Operating Systems · DBMS · Distributed Systems · Systems Programming |

---

## Beyond Code

- **Algorithmic Problem Solving:** 500+ Data Structures and Algorithms problems solved in C++ on LeetCode.
- **Leadership & Communication:** Managed technical documentation, presentations, and operations for 5+ flagship events during the Annual Technical Festival at ABV-IIITM Gwalior.
- **Academic Distinction:** Scored **98.6 percentile** in JEE Main 2023 nationwide among 1.1M+ candidates.


```
────────────────────  C O M M I T   H I S T O R Y  ────────────────────
```

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=ishaaaan17&show_icons=true&theme=transparent&title_color=8B5CF6&icon_color=A78BFA&text_color=C4B5FD&hide_border=true" alt="GitHub stats" width="48%"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ishaaaan17&layout=compact&theme=transparent&title_color=8B5CF6&text_color=C4B5FD&hide_border=true" alt="Top languages" width="48%"/>

<img src="https://streak-stats.demolab.com?user=ishaaaan17&theme=dark&hide_border=true&background=00000000&ring=8B5CF6&fire=A78BFA&currStreakLabel=C4B5FD&sideLabels=C4B5FD&dates=8B949E&stroke=8B5CF6" alt="streak stats" width="60%"/>
<img src="https://ghchart.rshah.org/8B5CF6/ishaaaan17" alt="contribution graph" width="92%"/>

<br/><br/>

<img src="https://raw.githubusercontent.com/ishaaaan17/ishaaaan17/output/github-contribution-grid-snake-dark.svg" alt="snake eating my contributions" width="92%"/>

<br/><br/>

## Let's talk

If you are building systems where latency, correctness, or scalability needs to be measured and proven rather than assumed, I'd love to connect.

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=600&size=22&duration=2800&pause=900&color=8B5CF6&center=true&vCenter=true&width=700&lines=measure+first%2C+optimize+second;shipping+%3E+talking;if+you're+building+systems+that+hold+up+%E2%80%94+let's+talk;ishaan.maheshwari101%40gmail.com" alt="outro" />

<br/>

[![Say hi](https://img.shields.io/badge/SAY_HI-ishaan.maheshwari101@gmail.com-8B5CF6?style=for-the-badge)](mailto:ishaan.maheshwari101@gmail.com)
[![Connect](https://img.shields.io/badge/CONNECT-LinkedIn-0A66C2?style=for-the-badge)](https://www.linkedin.com/in/ishaan-maheshwari-967741292)

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=160&section=footer&text=see%20you%20in%20the%20commits&fontSize=28&fontColor=fff&animation=twinkling&fontAlignY=72" width="100%"/>

</div>
