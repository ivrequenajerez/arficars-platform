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
