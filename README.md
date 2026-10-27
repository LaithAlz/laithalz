# Laith Alzoubi

Backend and distributed systems. Computer Science at the University of Toronto.
Currently building test-automation agents at Dayforce.

Everything below is public and clickable.

---

## Projects

### [jobsched](https://github.com/LaithAlz/jobsched) · Go
A distributed job scheduler. Priority queue with FIFO tie-breaking feeding a goroutine
worker pool, exponential-backoff retry on a sub-10s curve that Kubernetes' native `Job`
backoff cannot express, and per-job CPU and memory limits verified at the cgroup v2 level
by reading `memory.max` and `cpu.max` from inside the container.

Benchmarking against a bare-Kubernetes control disproved my own hypothesis about the
bottleneck: 12 to 21 seconds of pod startup, not my 38 µs/job of scheduling overhead.

`Go` `Kubernetes` `client-go` `cgroup v2` `Docker` `Prometheus`

### [Stoop](https://github.com/LaithAlz/stoop-backend) · Python, TypeScript
Tenant maintenance texts triaged by severity, with landlord-voiced replies drafted for
one-tap approval. A deterministic rule-based safety filter wraps the LLM so model output
is never trusted unvalidated, held to a zero-missed-emergency bar by a 20-scenario
evaluation harness used as a release gate. Exactly-once escalation across process crashes
via PostgreSQL advisory locks and compare-and-swap row claims.

Architecture, schema, evals and roadmap are complete and in the repo. The backend is
being built issue by issue; the marketing site and waitlist are live.

`FastAPI` `LangGraph` `Anthropic SDK` `PostgreSQL` `Cloudflare Workers` `Fly.io`

### [OnSide](https://getonside.ca) · TypeScript
A soccer field finding app for the GTA, shipped solo to the iOS App Store, now with 50+
signed-up users. Fastify backend with PostGIS radius search, Redis caching and row-level
security, React Native client, OAuth 2.0 with Google and Apple. CI gates every pull
request on typecheck, lint, test and migration validation.

Source: [LaithAlz/onside](https://github.com/LaithAlz/onside)

`Fastify` `PostgreSQL` `PostGIS` `Redis` `React Native` `GitHub Actions`

### [HomeKept](https://github.com/LaithAlz/HomeKept) · Java
Subscription home maintenance for the GTA. Spring Boot API on Java 17 with Postgres and
Flyway, TanStack Start frontend on Cloudflare Workers, Testcontainers-backed integration
tests.

Includes a deliberate simplification refactor that deleted about 7,500 net lines with no
behaviour change, every pull request reviewed and CI green, and a self-initiated
adversarial security review against my own code that found and fixed JWT/RBAC and
input-validation defects.

`Spring Boot` `Java 17` `PostgreSQL` `Flyway` `Testcontainers` `TanStack Start`

### [Market Feed](https://github.com/LaithAlz/Market-Data-Aggregator) · Python
Real-time stock price aggregator. Alpaca IEX WebSocket ingest normalised into a
validated `Tick` model, buffered 500ms then bulk-inserted into TimescaleDB, latest
price written through to Redis, OHLCV history served from FastAPI, and a Rich
terminal dashboard on top.

The aggregation leans on what TimescaleDB adds over plain Postgres: hypertable
partitioning so a time-bounded query scans one chunk, and `time_bucket()` with
`first()`/`last()` to build candles in SQL instead of pulling raw rows into Python.

`FastAPI` `TimescaleDB` `Redis` `WebSockets` `Pydantic` `Docker`

### [Walk the Past](https://walk-the-past.vercel.app) · TypeScript
One historical photograph turned into a walkable 3D world rendered in the browser. World
generation runs as persistent async jobs on Cloudflare Workers and Durable Objects, so
you can close the tab and come back to a finished result. In-world voice agent via the
OpenAI Realtime API with tool calling into app features. Built at Hack the North 2026.

Source: [LaithAlz/WalkThePast](https://github.com/LaithAlz/WalkThePast)

`Three.js` `Cloudflare Workers` `Durable Objects` `OpenAI Realtime`

### [Scriptorium](https://github.com/LaithAlz/Scriptorium) · TypeScript
Collaborative coding and blogging platform. Sandboxed code execution across 10+
languages, JWT auth, role-based access control and moderation workflows, data modelled
with Prisma and PostgreSQL.

`Next.js` `Prisma` `PostgreSQL` `TailwindCSS`

---

## Stack

**Languages** Go, Java, TypeScript, Python, SQL, C

**Backend** Spring Boot, FastAPI, Fastify, REST APIs, PostgreSQL, PostGIS, Redis

**Infrastructure** Kubernetes, Docker, Unix/Linux, Prometheus, AWS, Cloudflare Workers,
GitHub Actions, CI/CD

**Practices** Benchmarking, profiling, eval harnesses, determinism, code review

---

## Contact

[laithalzoubi.com](https://laithalzoubi.com) ·
[LinkedIn](https://www.linkedin.com/in/laith-alzoubi/) ·
allaith2004@gmail.com
