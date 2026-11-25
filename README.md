English · [Português](README.pt-BR.md)

### Hi, I'm Mateus

Computer Engineer with a postgraduate specialization in **Artificial Intelligence for Software Testing Engineering** (IARTES · UFAM, 2026). Based in Manaus, Brazil · INDT.

I work on **data engineering**, **test automation** and **backend**.

#### Data Engineering
Designed and built a **lakehouse data platform from scratch** (Apr 2025 – present, 70+ releases), self-hosted on-prem with a hybrid AWS deployment:

- **Ingestion:** Apache Airflow 3 (Celery) running PySpark jobs that pull business data from a REST API (companies, business units, cost/profit centers, employees, suppliers), plus file uploads (XLSX/CSV/JSON/Parquet)
- **Storage:** Apache Iceberg tables on S3-compatible object storage (MinIO / AWS S3), organized as **Bronze → Silver → Gold** layers (raw → cleaned, deduplicated and incrementally merged → business aggregates)
- **Catalog:** Project Nessie for Git-like versioning. Every pipeline run writes to its own branch and merges into `main` only when it succeeds
- **Consumption:** Trino for federated SQL and Apache Superset for dashboards
- **Security:** Keycloak SSO (OIDC) across every tool, per-group table access in Trino enforced by Open Policy Agent, HashiCorp Vault for secrets, Nginx/APISIX as the gateway
- **Alerting:** my most recent work is an alerting system for the platform

#### Test Automation (SDET)
- Built agent-based tools to create, analyze and execute test cases
- Automated task creation from user stories, work that became the paper *An Approach to Automating User Story Management for Testing Process Optimization in Large Distributed Teams*
- Automated day-to-day team processes and built dashboards to track them

I also run the infrastructure of a platform of tools for manual and automated test developers:
- **SSO:** OAuth 2.0 single sign-on across the platform's tools
- **Server:** manage the server hosting the platform's 5 tools, monitored with Grafana
- **Async work:** RabbitMQ as the central broker for asynchronous queues, consumed by Celery workers
- **App servers:** Gunicorn managing Uvicorn workers, so the apps use every CPU core, crashed or hung workers are replaced automatically, and workers are recycled periodically to keep memory usage flat
- **Nginx:** a gateway that acts as reverse proxy and load balancer, plus one Nginx per application serving its static files. Upstreams are resolved dynamically, so the gateway stays up and keeps routing even when one of the services behind it goes down

#### Publications and talks
- *An Approach to Automating User Story Management for Testing Process Optimization in Large Distributed Teams*
- *Otimização da Geração de Casos de Teste em Aplicativos Móveis via Aprendizado por Reforço e Agentes de IA* (Optimizing Test Case Generation for Mobile Apps with Reinforcement Learning and AI Agents). Postgraduate research, presented at [SAST · CBSoft 2026](https://cbsoft.sbc.org.br/2026/en/symposiums/sast/event/)

#### Stack
**Languages:** Python · Java · JavaScript/TypeScript · SQL

**Backend:** Django · Django REST · FastAPI · Spring Boot · Celery · RabbitMQ

**Data:** Apache Spark · Airflow · Iceberg · Nessie · Trino · Superset · MinIO/S3 · PostgreSQL

**Testing & AI:** Android · Reinforcement learning · AI agents

**Infra & Security:** Docker · Nginx · APISIX · Gunicorn · Uvicorn · Grafana · OAuth 2.0 · Keycloak · HashiCorp Vault · OPA · Linux
