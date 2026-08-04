# Enterprise Multi-Agent Workflow Engine

Enterprise-grade production platform for stateful, multi-agent AI workflows. This repository provides a hardened backend for coordinating LangGraph-based agents with a high-performance FastAPI backend, persistent vector memory, observability, and containerized deployment.

## Key Features

- **Stateful Agent Orchestration:** LangGraph-based state machines with checkpointing and human-in-the-loop support.
- **High-Performance FastAPI Backend:** Async endpoints, JWT authentication, rate limiting, and robust error handling.
- **Vector Memory & Persistence:** mem0 + pgvector for long-term semantic storage with Alembic migrations for schema management.
- **Containerized Microservices:** Docker Compose topology for API, PostgreSQL, and optional monitoring stacks.
- **Observability:** Structured `structlog` logs, Prometheus metrics, and optional Langfuse tracing for LLM calls.
- **LLM Resilience:** Managed LLM registry with retries, timeouts, and configurable fallback strategies.
- **Automated Evaluation:** Built-in evals framework to measure helpfulness, relevancy, and hallucination.

## Quickstart

1. Copy the example environment file and customize secrets:

```bash
cp .env.example .env.development
# edit .env.development and set your DB and LLM keys
```

1. Build and start the stack using Docker Compose:

```bash
docker compose up --build
```

1. Open the interactive API docs after the server starts:

```text
http://localhost:8000/docs
```

## Running Tests

```bash
pytest
```

## Architecture Overview

- `app/core/langgraph/` — agent graph definitions and tools.
- `app/services/` — LLM, memory, and database service layers.
- `app/models/` — SQLModel ORM schema and Alembic migrations.
- `evals/` — evaluation harness and metric prompts.

## Configuration

All runtime configuration is driven by environment variables. See `.env.example` for defaults and key names.

## Support & Contributing

This repository is maintained for the Enterprise Agent Platform team. For contribution guidance and development notes, consult the `docs/` directory.

## License

See [LICENSE](LICENSE) for licensing terms.
