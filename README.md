<img src="./assets/banner.svg" alt="Khusham Bansal — GSoC 2026 @ Meshery (CNCF / Layer5)" width="100%" />

<p align="center">
  <i>I build systems that fail well — retries, dead letters, and recovery paths,<br/>
  whether the thing failing is a worker process or a language model.</i>
</p>

<p align="center">
  <a href="https://khushambansal.me"><img alt="Portfolio" src="https://img.shields.io/badge/Portfolio-khushambansal.me-2DD4BF?style=for-the-badge&logo=vercel&logoColor=white"></a>
  <a href="https://www.linkedin.com/in/khushambansal/"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"></a>
  <a href="mailto:kbkhushambansal@gmail.com"><img alt="Email" src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white"></a>
  <a href="https://leetcode.com/u/KhushamBansal/"><img alt="LeetCode" src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black"></a>
</p>

---

### What I'm doing now

- 🛠️ **GSoC 2026 Contributor** at **[Meshery](https://meshery.io/)** (CNCF / Layer5) — **70+ PRs authored, 130+ reviewed** across UI reliability, registry workflows, Sistent design-system integration, and Playwright E2E coverage.
- 🔬 **Research Intern** at **[AIISC](https://aiisc.ai/)** — grounding LLMs with knowledge graphs to reduce hallucinations, and designing evaluations for accuracy at scale.
- 🎓 **B.E. Computer Engineering** at Thapar Institute — CGPA **8.92/10**, graduating **2027**.
- 🌍 Working with teams across **India and the US** — enough timezone math that I now think in UTC.

### Things I've built

| Project | What it does | Stack |
| --- | --- | --- |
| **[relayq](https://github.com/KhushamBansal/relayq)** | Durable job queue with leased workers, exponential-backoff retries, a dead-letter queue, and idempotent enqueue. Drains **2,000 jobs at ~5.4k jobs/s**; recovers in-flight work after a worker crash. | `Go` `Redis` |
| **[Milepost](https://github.com/KhushamBansal/eld-trip-planner)** · [live](https://eld-trip-planner-seven-mocha.vercel.app) | Plans property-carrying HGV trips and generates FMCSA driver daily logs under the 70hr/8-day HOS ruleset — routing, required stops, one log sheet per calendar day. | `Django` `DRF` `React` `TypeScript` `PostgreSQL` |
| **Ivo** · [demo](https://drive.google.com/file/d/16pp5bbNdyEUMzRb0Fj0CA-vsOgdfV82B/view?usp=sharing) | Local AI agent with LangGraph orchestration (plan → tool calls → results) and SQLite + FTS5 RAG memory spanning semantic, episodic, and procedural recall. MCP gateway with human-in-the-loop approval on high-risk sends. | `LangGraph` `FastAPI` `React` `MCP` |

### How relayq works

The through-line in most of what I build is failure handling. Here's the queue,
in one picture — leases so crashed workers don't lose jobs, backoff so retries
don't stampede, and a dead-letter queue so nothing disappears silently.

```mermaid
flowchart LR
    P["Producer"] -->|"idempotent enqueue"| Q[("Redis<br/>pending")]
    Q -->|"lease · TTL"| W1["Worker 1"]
    Q -->|"lease · TTL"| W2["Worker 2"]
    W1 -->|"ack"| OK["Done"]
    W2 -.->|"crash — lease expires"| Q
    W1 -->|"nack"| R{"retries<br/>left?"}
    R -->|"yes · exp. backoff"| Q
    R -->|"no"| DLQ[("Dead letter")]

    classDef store fill:#0b4f4a,stroke:#2dd4bf,color:#e7ebf2
    classDef work fill:#11151e,stroke:#60a5fa,color:#e7ebf2
    classDef term fill:#11151e,stroke:#6a7283,color:#9ba3b4
    class Q,DLQ store
    class W1,W2 work
    class P,OK,R term
```

**2,000 jobs drained at ~5.4k jobs/s** with 4 workers · 200 concurrent
idempotent requests collapsed to **1** job · in-flight work recovered after a
worker crash. → **[github.com/KhushamBansal/relayq](https://github.com/KhushamBansal/relayq)**

### Tech

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=flat-square&logo=neo4j&logoColor=white)

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![LangChain](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)

![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=flat-square&logo=nodedotjs&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

### Recognition

- 🥉 **3rd Prize**, Israeli-Indian Hackathon — out of **600+ teams**
- 🎖️ **Reliance Foundation Scholar 2023** — $2,300 merit scholarship
- 🏅 **International Rank 97**, NSTSE 2022
- 📋 Shortlisted, **Smart India Hackathon** 2023 & 2024

<div align="center">
  <img src="./profile-3d-contrib/profile-night-green.svg" alt="Contribution graph" width="100%" />
</div>

<p align="center">
  <sub>More at <a href="https://khushambansal.me">khushambansal.me</a></sub>
</p>
