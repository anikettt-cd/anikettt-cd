<!-- ═══════════════ HEADER BANNER ═══════════════ -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=220&section=header&text=Aniket%20Saini&fontSize=62&fontColor=ffffff&animation=fadeIn&fontAlignY=36&desc=Python%20Backend%20%26%20Full-Stack%20Engineer&descSize=22&descAlignY=58" alt="Aniket Saini banner" width="100%" />

<a href="https://github.com/anikettt-cd">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=900&color=00D4FF&center=true&vCenter=true&width=760&lines=Building+high-performance+Python+REST+APIs;Designing+Agentic+RAG+%26+MCP+architectures;Engineering+self-healing+distributed+systems;Final-year+IT+Engineering+%7C+Open+to+opportunities+%F0%9F%9A%80" alt="Typing animation" />
</a>

<br/><br/>

<a href="https://linkedin.com/in/it-aniketsaini"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="mailto:sainianiket751@gmail.com"><img src="https://img.shields.io/badge/Email-Say%20Hello-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
<a href="https://github.com/anikettt-cd?tab=repositories"><img src="https://img.shields.io/badge/Repositories-Explore-181717?style=for-the-badge&logo=github&logoColor=white" alt="Repositories" /></a>
<img src="https://komarev.com/ghpvc/?username=anikettt-cd&label=Profile%20Views&color=00D4FF&style=for-the-badge" alt="Profile views" />

</div>

<br/>

<!-- ═══════════════ ABOUT ═══════════════ -->
## 👨‍💻 About Me

```bash
$ whoami
aniket-saini   # python backend · agentic RAG · distributed systems

$ cat current_focus.txt
CloudHeal      → multi-laptop mini-cloud with deterministic self-healing
Agentic RAG    → MCP tool-calling over hybrid search (BM25 + pgvector + RRF)

$ ls ~/goals
ai-engineering/   production-grade-backends/   open-source/
```

```python
class Aniket:
    role       = "Python Backend & Full-Stack Engineer"
    education  = "B.E. Information Technology  |  CGPA 8.95 / 10  |  Class of 2027"
    college    = "Pillai HOC College of Engineering & Technology"
    experience = "Python Full-Stack Developer Intern @ Viraj Profiles Ltd."
    focus      = ["FastAPI", "Distributed Systems", "Agentic RAG", "MCP", "ETL"]
    building   = "CloudHeal: a multi-node self-healing platform"
    status     = "Open to entry-level Python / Backend roles 🚀"
```

<table>
<tr>
<td width="50%" valign="top">

### 🔭 Currently Building
**[CloudHeal](https://github.com/anikettt-cd/CloudHeal)**: a team-built mini cloud that runs Docker workloads across real laptops over Tailscale, with a FastAPI control plane, node agents, a reconciler, and deterministic self-healing.

### 🧠 Currently Exploring
Failure detection, leases and fencing, hybrid retrieval, agentic tool-calling and MCP servers.

</td>
<td width="50%" valign="top">

### 💼 Recent Experience
**Python Full-Stack Developer Intern**, Viraj Profiles Ltd.
Shipped a production material-request portal with multi-stage approvals, 7-role RBAC, and ERP/MRP ETL pipelines.

### 🎯 Looking For
Entry-level **Python Developer / Backend Developer** roles where I can build reliable, maintainable systems.

</td>
</tr>
</table>

<br/>

<!-- ═══════════════ TECH STACK ═══════════════ -->
## 🛠️ Tech Stack

<div align="center">

| | |
| :--- | :--- |
| **Languages** | <img src="https://skillicons.dev/icons?i=py,js&theme=dark" alt="Languages" /> |
| **Backend & APIs** | <img src="https://skillicons.dev/icons?i=fastapi,flask&theme=dark" alt="Backend" /> `SQLAlchemy` `Pydantic` `JWT` `RBAC` |
| **Databases** | <img src="https://skillicons.dev/icons?i=postgres,mysql,supabase,sqlite&theme=dark" alt="Databases" /> `pgvector` |
| **AI & Retrieval** | `RAG` `FastMCP` `LangGraph` `Embeddings` `BM25` `RRF` `LLM APIs` `Tool Calling` |
| **Data Processing** | <img src="https://skillicons.dev/icons?i=pandas,numpy&theme=dark" alt="Data" /> `OpenPyXL` `ETL` |
| **Frontend** | <img src="https://skillicons.dev/icons?i=react,vite,tailwind&theme=dark" alt="Frontend" /> |
| **Infrastructure & Tools** | <img src="https://skillicons.dev/icons?i=docker,git,github,linux,vscode&theme=dark" alt="DevOps" /> `Tailscale` `uv` `pytest` |

</div>

<br/>

<!-- ═══════════════ CLOUDHEAL SPOTLIGHT ═══════════════ -->
## ☁️ Spotlight: CloudHeal

> **A policy-based, self-healing mini cloud built on real laptops.**
> Final-year major project (team of 4). CloudHeal runs workloads in Docker across multiple machines, watches them, and recovers them when things break. The goal is *measurable* self-healing, not just a dashboard.

### Architecture

```mermaid
flowchart TB
    subgraph CP["Control Plane · FastAPI"]
        API[REST API] --> SCH[Resource-aware<br/>Scheduler]
        SCH --> REC[Reconciler<br/>desired vs observed state]
        API --> DB[(SQLite<br/>state + event history)]
        REC --> DB
    end

    subgraph NET["Tailscale private network"]
        A1[Node Agent<br/>macOS laptop]
        A2[Node Agent<br/>Windows laptops]
    end

    SCH -->|execute / status| A1
    SCH -->|execute / status| A2
    A1 -. heartbeat .-> API
    A2 -. heartbeat .-> API
    A1 --> D1[(Docker)]
    A2 --> D2[(Docker)]

    LF[Leases + Fencing<br/>planned]:::planned -.-> CP
    GW[Stable App Gateway<br/>planned]:::planned -.-> NET
    AI[AI Diagnosis + Planning<br/>planned · behind safety gate]:::planned -.-> CP

    classDef planned fill:#161b22,stroke:#8b949e,stroke-dasharray: 5 5,color:#8b949e
    style CP fill:#0d1117,stroke:#1f6feb,color:#fff
    style NET fill:#0d1117,stroke:#238636,color:#fff
```

### Target recovery flow

```mermaid
flowchart LR
    F([Failure detected]) --> C[Classify<br/>container · node · uncertain]
    C --> S{Desired state RUNNING<br/>and recovery safe?}
    S -->|no| B[Block action<br/>+ record event]
    S -->|yes| P[Select eligible node<br/>capacity-aware]
    P --> G[Allocate higher<br/>placement generation]
    G --> E[Execute replacement<br/>via Node Agent]
    E --> V{Container + app<br/>healthy?}
    V -->|yes| OK([Recovered ✅])
    V -->|no| R[Bounded retry<br/>or escalate]
    R --> C

    style F fill:#0d1117,stroke:#f85149,color:#fff
    style OK fill:#238636,stroke:#3fb950,color:#fff
    style S fill:#1f6feb,stroke:#58a6ff,color:#fff
    style V fill:#1f6feb,stroke:#58a6ff,color:#fff
```

### Project status

| Area | Status |
| :--- | :--- |
| Node registration, heartbeats, system & Docker runtime reporting | ✅ Working |
| Workload creation, resource-aware scheduling, Docker execution via Node Agents | ✅ Working |
| Reconciler loop with stopped / missing-container recovery (verified against real Docker) | ✅ Working |
| SQLite persistence and execution-event history | 🔄 Partially implemented, verification ongoing |
| Automated tests | ✅ 23 control-plane tests passing (last recorded run) |
| Second real laptop (Windows) as a compute node over Tailscale | 🔄 In progress |
| Node health state machine: `HEALTHY → SUSPECT → UNAVAILABLE` | 🗺️ Planned |
| Leases, placement generations, agent-enforced fencing, cross-node failover | 🗺️ Planned |
| Bounded retries, crash-loop detection, recovery concurrency limits | 🗺️ Planned |
| Stable application URL (gateway) and repeatable experiment runner | 🗺️ Planned |
| AI-assisted diagnosis and constrained recovery planning | 🗺️ Planned |

### Design principles

- **Deterministic first, AI second.** Safety and recovery logic is rule-based. The AI layer may only *recommend*, and every recommendation must pass a deterministic safety gate.
- **Infrastructure never depends on the model.** If the LLM API is down, the platform keeps running.
- **Scheduling ≠ execution ≠ health.** A placement decision, a started container, and a healthy application are treated as three separate stages.
- **A timeout is not a failure.** An unreachable node does not prove its containers have stopped, so the design handles uncertain outcomes explicitly.
- **Measure, don't assume.** Recovery is evaluated through repeated failure experiments (detection time, recovery time, duplicate execution, retries).

<br/>

<!-- ═══════════════ PROJECTS ═══════════════ -->
## ⚡ More Projects

<table>
<tr>
<td width="50%" valign="top">

### 📄 Enterprise Document Intelligence
*RAG pipeline with provenance*

PDF extraction, chunking, embeddings and **hybrid search** (BM25 + semantic vectors fused with Reciprocal Rank Fusion) with source-document and page-level provenance.

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-336791?style=flat-square)
![RAG](https://img.shields.io/badge/RAG-FF6F61?style=flat-square)

</td>
<td width="50%" valign="top">

### 🤖 Agentic RAG with MCP
*Tool-calling retrieval architecture*

FastMCP server exposing entity extraction, query refinement and relevance evaluation tools; an MCP client lets an LLM discover and invoke them for multi-step retrieval.

![FastMCP](https://img.shields.io/badge/FastMCP-000000?style=flat-square)
![LLM](https://img.shields.io/badge/LLM_APIs-8A2BE2?style=flat-square)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

</td>
</tr>
<tr>
<td colspan="2" valign="top">

### 🏭 [Material Request System](https://github.com/anikettt-cd/Material-request-management-system)
*Built for Viraj Profiles Ltd.*

Full-stack portal automating requests through multi-stage approval to material-code generation, with JWT + HTTP-only cookie auth, bcrypt hashing, 7-role RBAC and Pandas/OpenPyXL ETL for ERP/MRP.

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

</td>
</tr>
</table>

<br/>

<!-- ═══════════════ RAG DIAGRAM ═══════════════ -->
## 🧩 How My Agentic RAG Works

```mermaid
flowchart LR
    U([User Query]) --> C[MCP Client<br/>LLM + tool discovery]
    C -->|tool call| S{{FastMCP Server}}
    S --> E[Entity Extraction]
    S --> Q[Query Refinement]
    S --> R[Relevance Check]
    E --> H[(Hybrid Search<br/>BM25 + pgvector + RRF)]
    Q --> H
    H --> R
    R --> A([Grounded Answer<br/>with page provenance])

    style U fill:#0d1117,stroke:#00d4ff,color:#fff
    style A fill:#0d1117,stroke:#00d4ff,color:#fff
    style S fill:#1f6feb,stroke:#58a6ff,color:#fff
    style H fill:#238636,stroke:#3fb950,color:#fff
```

<br/>

<!-- ═══════════════ HIGHLIGHTS ═══════════════ -->
## 🏆 Highlights

| | |
| :---: | :--- |
| 🎓 | **8.95 CGPA** in B.E. Information Technology (Expected 2027) |
| 🔐 | Designed **JWT + HTTP-only cookie auth with 7-role RBAC** for a production internal portal |
| ☁️ | Built a **multi-node scheduler, reconciler and Docker-based recovery loop** with SQLite event history (CloudHeal) |
| 🔎 | Implemented **hybrid retrieval (BM25 + vectors + RRF)** with page-level provenance |
| 🛠️ | Delivered **freelance** work: industrial box/rack tracking and a computer-vision people-tracking pipeline |
| 🧮 | Practising DSA through **LeetCode 75** and collaborative Git workflows (feature branches, PR reviews) |

<br/>

<!-- ═══════════════ STATS ═══════════════ -->
## 📊 GitHub Analytics

<div align="center">

<img height="180" src="https://github-readme-stats.vercel.app/api?username=anikettt-cd&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide_border=true&border_radius=12" alt="GitHub stats" />
<img height="180" src="https://github-readme-stats.vercel.app/api/top-langs/?username=anikettt-cd&layout=compact&theme=tokyonight&hide_border=true&langs_count=6&border_radius=12" alt="Top languages" />

<br/>

<img src="https://streak-stats.demolab.com?user=anikettt-cd&theme=tokyonight&hide_border=true&border_radius=12" alt="GitHub streak" />

<br/><br/>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/anikettt-cd/anikettt-cd/output/github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/anikettt-cd/anikettt-cd/output/github-snake.svg" />
  <img alt="Contribution snake animation" src="https://raw.githubusercontent.com/anikettt-cd/anikettt-cd/output/github-snake-dark.svg" />
</picture>

</div>

<br/>

<!-- ═══════════════ CONNECT ═══════════════ -->
## 🤝 Let's Connect

I'm actively looking for **entry-level Python / Backend Developer** roles and open to collaborating on **FastAPI, RAG and distributed systems** projects.

<div align="center">

<a href="https://linkedin.com/in/it-aniketsaini"><img src="https://img.shields.io/badge/LinkedIn-it--aniketsaini-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="mailto:sainianiket751@gmail.com"><img src="https://img.shields.io/badge/Email-sainianiket751@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>

<br/><br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=120&section=footer" alt="footer" width="100%" />

<sub>⭐ If you like what you see, drop a star on a repo, it genuinely helps!</sub>

</div>
