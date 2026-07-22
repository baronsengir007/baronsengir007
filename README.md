# Hi, I'm Rienk

I spent fifteen years auditing financial institutions before I started
building AI. That order matters: I learned what makes systems trustworthy
before I learned to build them.

Most agentic AI fails in production for two reasons: nobody can explain
what the agent did, and nobody asked the people who have to work with it.
So I build the other way around. Compliance (EU AI Act, GDPR, NIS2) is a
design input, not a checklist at the end. And adoption starts with the
employees, not the demo.

Below: how I structure agent work, and five things I built.

## How I work: Interpretable Context Methodology (ICM)

As an auditor I documented processes so that any colleague could execute
them. ICM applies that same discipline to AI agents: I codify a thinking
process into folder architecture, so the structure itself steers the agent.

- Folders are work modes (research, write, review, deliver), not subject
  bins. The agent's current folder defines its job.
- Context loads in layers: a routing map that is always loaded, a
  per-phase contract, and stable reference knowledge. The agent only sees
  what its current phase needs.
- Phases hand work to each other through files, one way. That keeps
  long-running agent work from drifting.
- Filenames carry state (draft -> review -> final), so the file system is
  the single source of truth.

The result: a consulting method or business process becomes something an
AI agent can reliably run, and something a colleague can pick up without
a handover meeting.

## Case studies

Client and employer work stays private, so these are anonymized: problem,
approach, stack and result, without code or client names. The pinned
repos below show personal work where the code is public.

### 1. Claims triage that saves 1.5 FTE

**Problem.** A claims inbox at an insurance broker receiving 150 emails
per day, all triaged by hand.

**Approach.** Deployed n8n on the client's Azure infrastructure as the
automation foundation, then built an AI email classification agent that
reads, classifies and routes incoming claims mail, plus additional inbox
automation flows on the same foundation.

**Stack.** n8n, Microsoft Azure, LLM-based classification.

**Result.** Live in production. The classification agent saves 1 FTE;
the additional flows save another 0.5 FTE.

### 2. SEO content grounded in what customers actually ask

**Problem.** A B2B software vendor wanted industry-specific content at
scale, grounded in real customer questions instead of marketing guesses.

**Approach.** An agent pipeline distills blog topics from sales
conversations, clusters recurring questions (when many customers ask
about security, the next blog is about security), runs keyword research
and writes the post section by section. Four human approval gates sit
between topic extraction and a release-ready draft. The pipeline is part
of a broader AI marketing assistant that also handles chat, transcript
analysis, website SEO analysis, competitor research and scheduled tasks.

**Stack.** Python, FastAPI, agent framework with Claude, Next.js/React/
TypeScript frontend, Qdrant vector store with RAG, Semrush API, Docker
Compose.

**Result.** A working application producing review-ready, SEO-optimized
drafts across more than 20 industries; the pilot showed a 35% higher
conversion rate.

### 3. A security advisory report, written by an agent pipeline

**Problem.** A client wanted to use AI on their business data within a
Microsoft stack, GDPR and NIS2 proof. Their access control lived in the
reporting layer: users saw aggregated dashboards but the underlying data
was wide open, which breaks the moment AI agents query it.

**Approach.** This is ICM in practice. Four folders as work modes
(research, write, review, deliver) with one-way file handoffs and
filename-as-state. The advice itself covered moving authorization into
the data layer (row, object and column level security in the semantic
model), a controlled agent lifecycle with per-agent identity and
prompt-injection safeguards, and demonstrable compliance through logging
and monitoring.

**Stack.** Claude Code as agent runtime with folder-based skills,
automated markdown-to-PDF delivery, plus the Microsoft data stack
(Fabric, Entra ID, Purview) as the subject of the advice.

**Result.** A designed advisory report (PDF), an executive slide deck
and a podcast version, all produced through the same folder pipeline and
reviewed by humans at every phase boundary.

### 4. An AI opportunity scan that starts with employees

**Problem.** A workforce-planning consultancy wanted to know which of
their internal processes are ready for AI agents, with employees
involved from the start instead of a tool being imposed top-down.

**Approach.** A phased scan pipeline. Phase zero is an anonymous,
conversational pre-interviewer: employees open a single link, and an AI
interviewer works through five fixed themes in 15-20 minutes, tracking
per turn which themes are covered. Answers stream in real time and are
extracted into structured records that feed a process-scoring model,
producing a prioritized shortlist of AI use cases. Deployed with
security first: rate limiting, strict security headers and constant-time
access-code checks.

**Stack.** Python, FastAPI with server-sent events, Claude API with
structured extraction, SQLite, pytest.

**Result.** A deployed, tested scan instrument that turns employee
interviews into a prioritized AI roadmap.

### 5. A 3D mech shooter, built in hackathon time

**Problem.** Build a playable 3D game within hackathon time.

**Approach.** AI-assisted development with a strict modular setup: ten
plain JavaScript modules (flight, weapons, enemies, tactical view, UI)
around a classic game loop, all 3D geometry generated procedurally so no
asset pipeline was needed.

**Stack.** Three.js, WebGL, vanilla JavaScript, roughly 3,700 lines, no
build step: it runs in the browser from a single HTML file.

**Result.** A fully playable game: six-degrees-of-freedom flight, two
weapon systems with missile lock-on, summonable AI allies, an RTS-style
tactical pause view to command them, and three levels with boss fights.

## Toolbox

- **Agentic AI:** Python, Pydantic AI, MCP, Claude Code
- **LLM integration:** Anthropic Claude, OpenAI, Mistral, structured outputs with Pydantic
- **RAG and vector search:** PostgreSQL with pgvector, Qdrant, Docling
- **Event-driven architecture:** FastAPI, Celery, Redis
- **Evals and observability:** LangFuse (tracing and prompt management), Logfire, Sentry, evals with unit tests and human annotation
- **Guardrails and AI security:** LLM Guard (PII removal, prompt injection detection, toxicity checks)
- **Workflow automation:** n8n, Microsoft Graph
- **Deployment:** Docker, Microsoft Azure
- **AI governance:** EU AI Act, GDPR, NIS2, Responsible AI

## Contact

LinkedIn: [linkedin.com/in/rienkrienks](https://linkedin.com/in/rienkrienks)
GitHub: [@baronsengir007](https://github.com/baronsengir007)
