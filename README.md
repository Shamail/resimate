# Resimate Cloud Migration Project

A software consulting repository for migrating [Resimate.io](https://resimate.io) from a single-tenant GCP/Firebase architecture to a cloud-agnostic, containerized solution.

## Project Goals

Enable Resimate to deploy their resilience management platform in customer cloud environments:
- **Target Clouds**: AWS, Azure, GCP, On-premise
- **Expected Deployments**: 5 in next 12-24 months
- **Architecture**: Single-tenant per customer
- **Compliance**: GDPR, HIPAA, SOC2 ready

## Current State → Target State

| Component | Current (GCP/Firebase) | Target (Cloud-Agnostic) |
|-----------|------------------------|-------------------------|
| **Frontend** | Next.js on Firebase Hosting | Containerized Next.js on Kubernetes |
| **APIs** | Python Flask on Firebase Functions | Knative Services on Kubernetes |
| **Database** | Cloud SQL PostgreSQL | Cloud-managed PostgreSQL / PostgreSQL Operator |
| **Authentication** | Firebase Auth | Ory Kratos |
| **Secrets** | GCP Secrets Manager | HashiCorp Vault |
| **Logging** | Firebase/GCP Logging | OpenTelemetry + Loki |
| **Infrastructure** | Manual GCP Console | Pulumi (Multi-cloud IaC) |

## Services Overview

### API Services (Knative)
- **Core Model API**: Resilience model management and calculations
- **Campaigns API**: Stakeholder engagement and campaign execution  
- **Config/Users API**: Administrative operations and user management

### Always-On Services (Kubernetes)
- **Frontend**: Next.js web application
- **Ory Kratos**: Authentication and identity management
- **PostgreSQL**: Primary data store
- **HashiCorp Vault**: Secrets management

## Repository Structure

```
├── docs/                    # 📚 Project documentation
│   ├── architecture/        # System design and architecture decisions
│   ├── requirements/        # Business and technical requirements
│   ├── technical/          # Implementation guides and specifications
│   └── project/            # Project management and meeting notes
├── infrastructure/         # 🏗️  Infrastructure as Code
│   ├── pulumi/            # Multi-cloud Pulumi configurations
│   ├── docker/            # Container definitions and Dockerfiles
│   ├── kubernetes/        # Kubernetes manifests and configurations
│   └── helm/             # Helm charts for deployment
├── migration/             # 🔄 Migration tools and strategies
├── services/              # ⚙️  Service configurations (Kratos, monitoring)
└── tools/                # 🛠️  Custom deployment and validation tools
```

## Quick Start

1. **Review Documentation**: Start with `docs/project/project-charter.md`
2. **Understand Architecture**: Read `docs/architecture/target-architecture.md`
3. **Check Migration Plan**: See `docs/architecture/migration-roadmap.md`
4. **Explore Infrastructure**: Browse `infrastructure/pulumi/` for deployment code

## Key Documentation

| Document | Purpose |
|----------|---------|
| [Project Charter](docs/project/project-charter.md) | Project scope, objectives, and stakeholders |
| [Current State Analysis](docs/architecture/current-state-analysis.md) | Existing GCP/Firebase architecture |
| [Target Architecture](docs/architecture/target-architecture.md) | Cloud-agnostic design |
| [Migration Roadmap](docs/architecture/migration-roadmap.md) | Phased migration approach |
| [Technology Migration Matrix](docs/technical/technology-migration-matrix.md) | Service-by-service migration mapping |

## Deployment Targets

### Phase 1 (Proof of Concept)
- Local Kubernetes (Docker Desktop/K3s)
- GCP GKE (familiar environment)

### Phase 2 (Multi-Cloud)
- AWS EKS
- Azure AKS  
- On-premise Kubernetes

## Technology Stack

### Core Technologies
- **Kubernetes**: Universal container orchestration
- **Knative**: Serverless container platform
- **Ory Kratos**: Identity and user management
- **PostgreSQL**: Primary database
- **HashiCorp Vault**: Secrets management
- **Pulumi**: Infrastructure as Code

### Cloud Platforms
- **AWS**: EKS, RDS, Application Load Balancer
- **Azure**: AKS, Azure Database for PostgreSQL, Application Gateway
- **GCP**: GKE, Cloud SQL, Cloud Load Balancing
- **On-Premise**: Self-managed Kubernetes, PostgreSQL Operator

## Compliance & Security

- **GDPR**: Data protection and privacy controls
- **HIPAA**: Healthcare data security requirements
- **SOC2**: Security controls and audit procedures
- **Multi-tenant Isolation**: Each customer has dedicated infrastructure
- **Network Security**: Configurable per customer environment

## Project Status

🚧 **In Progress**: Active development of migration documentation and proof-of-concept infrastructure

### Current Phase
- Creating comprehensive documentation
- Designing cloud-agnostic architecture  
- Building Pulumi infrastructure code
- Developing migration tools and automation

### Next Steps
- Proof-of-concept deployment on GCP
- Firebase Auth to Ory Kratos migration
- Multi-cloud deployment validation
- Customer environment automation

---

**Contact**: This is a consulting project. For project-specific questions, refer to meeting notes in `docs/project/meeting-notes/`.