# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a software consulting repository for migrating **Resimate** (resimate.io) from a single-tenant GCP/Firebase architecture to a cloud-agnostic, containerized solution deployable on AWS, Azure, GCP, and on-premise environments.

**Client**: Resimate.io - Security consultants building resilience management software
**Project Goal**: Enable customer-deployed instances across multiple cloud providers
**Timeline**: 5 deployments expected in 12-24 months (1 AWS, 1 GCP, 2 Azure, 1 on-prem)

## Current Architecture (Firebase/GCP)

**Services:**
- Frontend: Next.js (Firebase Hosting)
- APIs: Python Flask (Firebase Functions/Cloud Run)
  - Core Model API (resilience model management)
  - Campaigns API (stakeholder engagement)
  - Config/Users API (administrative operations)
- Database: PostgreSQL (Cloud SQL)
- Auth: Firebase Auth
- Secrets: GCP Secrets Manager
- Logging: Firebase/GCP Logging

## Target Architecture (Cloud-Agnostic)

**Stack:**
- **Container Orchestration**: Kubernetes
- **Serverless**: Knative (for APIs)
- **Authentication**: Ory Kratos
- **Secrets Management**: HashiCorp Vault
- **Database**: Cloud-managed PostgreSQL or PostgreSQL Operator
- **Infrastructure**: Pulumi (multi-cloud IaC)
- **Logging**: OpenTelemetry + Loki

## Key Technology Decisions

1. **Ory Kratos** over Keycloak (lightweight, API-first, cloud-native)
2. **Knative** for APIs (serverless experience, scale-to-zero, event-driven)
3. **Standard K8s Deployments** for Frontend, Auth, Database
4. **Pulumi** for Infrastructure as Code
5. **Kubernetes** as the universal platform abstraction

## Repository Structure

```
├── docs/                    # Project documentation
│   ├── architecture/        # Architecture decisions and designs
│   ├── requirements/        # Business and technical requirements
│   ├── technical/          # Implementation guides
│   └── project/            # Project management documents
├── infrastructure/         # Infrastructure as Code
│   ├── pulumi/            # Multi-cloud Pulumi code
│   ├── docker/            # Container definitions
│   ├── kubernetes/        # K8s manifests
│   └── helm/             # Helm charts
├── migration/             # Migration tools and strategies
├── services/              # Service configurations (Kratos, etc.)
└── tools/                # Custom deployment and validation tools
```

## Compliance Requirements

- **GDPR**: Data protection and privacy
- **HIPAA**: Healthcare data security
- **SOC2**: Security controls and procedures

## Development Workflow

1. **Documentation-First**: Create comprehensive migration docs
2. **Infrastructure as Code**: Use Pulumi for all cloud resources
3. **Containerization**: Docker for all services
4. **Kubernetes-Native**: Deploy using K8s primitives and Knative
5. **Multi-Cloud Testing**: Validate on AWS, Azure, GCP, on-prem

## Commands

*Note: Commands will be added as the project develops build and deployment scripts.*

## Migration Status

This is an active consulting project. Current focus:
- Creating comprehensive documentation
- Designing cloud-agnostic architecture
- Building proof-of-concept deployments
- Developing migration tools and automation