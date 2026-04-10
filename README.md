# ARFICARS Platform

ARFICARS Platform is the initial monorepo for the ARFICARS digital platform.

The project is built around a real automotive workshop and is intended to support the professional publication, management and commercialisation of selected used and restored vehicles. Its initial scope is not a marketplace of third parties, but a product-owned commercial catalogue with a public website, an internal backoffice, media management and lead capture.

This repository contains the first technical baseline of the platform:
- a Spring Boot core backend
- a public Nuxt application
- an admin Nuxt application
- local infrastructure for development
- architecture and decision documentation

## Purpose

The goal of this repository is to provide a clean, explainable and executable baseline for ARFICARS.

It is designed to serve two purposes at the same time:
1. support a real product with real business constraints
2. establish a technically serious foundation that can evolve without being rebuilt from scratch

At this stage, the priority is not feature breadth. It is architectural clarity, disciplined bootstrapping and a reliable local development setup.

## Initial architecture baseline

The initial architecture decisions for ARFICARS are already closed and reflected in this repository:

- **Public frontend:** Nuxt
- **Admin frontend:** Nuxt in a separate application
- **Backend:** Spring Boot with Java
- **Backend style:** modular monolith
- **Backend internal structure:** hexagonal architecture by module
- **Primary database:** PostgreSQL
- **Identity provider:** Keycloak
- **Binary media storage:** S3-compatible object storage
- **Local infrastructure:** Docker Compose
- **Application runtime in development:** backend and frontend apps run from IDE/editor, infrastructure runs in containers

This repository intentionally avoids premature complexity. The following are explicitly out of scope for the initial bootstrap:
- business microservices
- Redis
- Kafka or RabbitMQ
- dedicated search engine
- Kubernetes
- heavy observability stack
- buyer authentication flows
- e-commerce implementation
- deployment orchestration beyond basic CI

## Repository structure

```text
.
├─ .github/
│  └─ workflows/
├─ backend/
│  └─ arfi-core-api/
├─ docs/
│  └─ adr/
├─ frontend/
│  ├─ apps/
│  │  ├─ arfi-public-web/
│  │  └─ arfi-admin-web/
│  └─ pnpm-workspace.yaml
├─ infra/
│  └─ compose/
├─ .editorconfig
├─ .env.example
├─ .gitattributes
├─ .gitignore
└─ README.md
````

## Main components

### `backend/arfi-core-api`

Main business backend.

It will host the ARFICARS core API as a Spring Boot application, following a modular monolith approach with explicit module boundaries and hexagonal architecture inside each module.

### `frontend/apps/arfi-public-web`

Public web application.

It will serve the public catalogue, vehicle detail pages, brand presentation and lead/contact entry points, with strong SEO orientation.

### `frontend/apps/arfi-admin-web`

Admin web application.

It will serve authenticated internal workflows such as vehicle management, media management, publication control and lead review.

### `infra/compose`

Local infrastructure baseline.

It will contain the Docker Compose setup for:

* PostgreSQL
* Keycloak
* object storage

The purpose of this directory is to provide repeatable local infrastructure without forcing the application runtimes themselves into containers during normal development.

### `docs`

Architecture and engineering documentation.

This directory will contain:

* architecture baseline
* repository strategy
* local development guide
* ADRs
* future technical reference documents

## Development model

The baseline development model is intentionally simple:

* infrastructure services run with Docker Compose
* backend runs locally from IntelliJ
* frontend apps run locally from VS Code or terminal
* documentation is versioned in the same repository
* CI validates the baseline continuously

This keeps iteration fast while preserving realistic dependencies.

## Current status

This repository is currently in **bootstrap phase**.

The purpose of the current phase is to produce the initial baseline for development, including:

* monorepo structure
* base documentation
* backend scaffolding
* frontend scaffolding
* local infrastructure setup
* basic CI pipeline

No business implementation is expected yet. At this point, structure and discipline matter more than ornamental progress.

## Planned bootstrap deliverables

The first milestone is considered complete only when all of the following exist:

* repository base structure
* `README.md`
* `docs/architecture.md`
* `docs/adr/ADR-001.md` to `ADR-005.md`
* `backend/arfi-core-api`
* `frontend/apps/arfi-public-web`
* `frontend/apps/arfi-admin-web`
* `infra/compose/compose.yaml`
* basic GitHub Actions CI workflow
* evidence that the baseline builds and starts correctly

## Documentation

The repository documentation will progressively define:

* architecture baseline
* repository strategy
* local development conventions
* architectural decision records
* implementation boundaries for the bootstrap phase

## Working principles

This repository follows a few non-negotiable principles:

* business usefulness first
* modularity before distribution
* explicit boundaries
* no generic shared dumping ground
* no decorative enterprise complexity
* documentation that explains actual decisions, not aspirations

## License

License to be defined.
