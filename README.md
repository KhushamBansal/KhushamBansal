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

### Now

- **GSoC 2026** at **[Meshery](https://meshery.io/)** (CNCF / Layer5) — **70+ PRs authored, 130+ reviewed**
- **Research Intern**, AI Institute of South Carolina — grounding LLMs with knowledge graphs
- **B.E. Computer Engineering**, Thapar Institute — graduating 2027

### Built

| Project | | Stack |
| --- | --- | --- |
| **[relayq](https://github.com/KhushamBansal/relayq)** | Durable job queue — leased workers, backoff retries, dead-letter queue | `Go` `Redis` |
| **[Milepost](https://github.com/KhushamBansal/eld-trip-planner)** · [live](https://eld-trip-planner-seven-mocha.vercel.app) | HGV trip planner generating FMCSA daily logs under 70hr/8-day HOS rules | `Django` `React` `PostgreSQL` |
| **Ivo** · [demo](https://drive.google.com/file/d/16pp5bbNdyEUMzRb0Fj0CA-vsOgdfV82B/view?usp=sharing) | Local AI agent — LangGraph orchestration, SQLite + FTS5 RAG memory, MCP gateway | `LangGraph` `FastAPI` `MCP` |

### How relayq handles failure

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

<sub>2,000 jobs at **~5.4k jobs/s** · 200 concurrent idempotent requests collapsed to **1** · in-flight work recovered after a crash</sub>

### Tech

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![LangChain](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)

### Recognition

🥉 **3rd / 600+ teams**, Israeli-Indian Hackathon · 🎖️ **Reliance Foundation Scholar 2023** · 🏅 **Intl. Rank 97**, NSTSE 2022

<div align="center">
  <img src="./profile-3d-contrib/profile-night-green.svg" alt="Contribution graph" width="100%" />
</div>
