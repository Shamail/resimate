# Current State Analysis: Resimate Platform

**Document Version**: 1.0  
**Date**: September 1, 2024  
**Analysis Based On**: C4 Container Diagram (2025-Q3-resimate_c4-Container)

## Executive Summary

Resimate currently operates a single-tenant, microservices-based resilience management platform built entirely on Google Cloud Platform (GCP) and Firebase services. The architecture consists of 5 core container services with clear separation of concerns, serving three primary user types through a Next.js frontend.

## System Overview

### Business Domain
**Resilience Management Platform** for organizations to:
- Model and assess organizational resilience
- Engage stakeholders through targeted campaigns  
- Generate reports and insights for decision makers

### User Personas
1. **Project Manager / Resilience Manager**: Views reports, provides information
2. **Business User**: Consumes reports, provides verification data
3. **Resimate Consultant**: Uploads data, triggers actions, provides expert guidance

### High-Level Architecture Pattern
- **Pattern**: Microservices with API Gateway pattern
- **Deployment**: Serverless-first (Firebase Functions)
- **Data**: Centralized PostgreSQL with schema-based multi-tenancy
- **Communication**: Synchronous REST APIs
- **Authentication**: Centralized Firebase Auth

## Container Architecture Analysis

### 1. Frontend Container
**Technology**: TypeScript / Next.js  
**Hosting**: Firebase App Hosting  
**Responsibilities**:
- User interface for all three user personas
- Client-side routing and state management
- Authentication integration with Firebase Auth
- API consumption from backend services

**Dependencies**:
- Firebase Auth SDK for authentication
- Firebase Hosting for deployment
- REST API calls to backend services
- Customer's email infrastructure (for notifications)

### 2. Core Model API Container
**Technology**: Python / Google Cloud Functions (Flask)  
**Hosting**: Firebase Functions → GCP Cloud Run  
**Responsibilities**:
- CRUD operations on core resilience model
- Business logic calculations  
- Data validation and processing
- Core domain entity management

**Data Access Patterns**:
- Direct read/write to Platform DB
- Schema-based tenant isolation
- Transactional operations for data consistency

### 3. Campaigns API Container  
**Technology**: Python / Google Cloud Functions (Flask)  
**Hosting**: Firebase Functions → GCP Cloud Run  
**Responsibilities**:
- Campaign management and execution
- Stakeholder engagement orchestration
- Event-driven campaign workflows
- Email integration coordination

**Integration Points**:
- Platform DB for campaign data
- Email service for stakeholder communications
- Event-driven triggers from user actions

### 4. Config/Users API Container
**Technology**: Python / Google Cloud Functions (Flask)  
**Hosting**: Firebase Functions → GCP Cloud Run  
**Responsibilities**:
- User configuration management
- System configuration settings
- Administrative operations
- User role and permission management

**Access Patterns**:
- Lower frequency, administrative operations
- Configuration read/write operations
- User preference management

### 5. Platform DB Container
**Technology**: PostgreSQL  
**Hosting**: GCP Cloud SQL  
**Architecture**: 
- Dedicated schemas (namespaces) per container/tenant
- Relational data model
- Centralized data store for all services

**Data Organization**:
```sql
-- Tenant isolation through schemas
tenant_1_schema.resilience_models
tenant_1_schema.campaigns  
tenant_1_schema.users
tenant_1_schema.configurations

tenant_2_schema.resilience_models
-- ... and so on
```

## Supporting Services Analysis

### IAM Service Container
**Current State**: GCP IAM + Firebase Auth  
**Responsibilities**:
- User authentication and authorization
- Session management
- API access control
- Role-based permissions

**Integration Pattern**:
- Firebase Auth SDK in frontend
- Firebase Admin SDK in backend APIs
- JWT token validation across services

### Secrets Manager Container  
**Technology**: GCP Secrets Manager  
**Usage Pattern**:
- Database connection strings
- API keys and service credentials
- Environment-specific configuration
- Integration credentials (email, third-party services)

### Email Service Integration
**Architecture**: External dependency
**Integration**: Customer's email infrastructure
**Communication Pattern**: Outbound email delivery
**Trigger Sources**: Campaigns API, system notifications

## Data Flow Analysis

### Primary Data Flows

1. **User Authentication Flow**
   ```
   Frontend → Firebase Auth → Backend APIs (JWT validation)
   ```

2. **Resilience Model Management**
   ```
   Frontend → Core Model API → Platform DB
   ```

3. **Campaign Execution Flow**
   ```
   Frontend → Campaigns API → Platform DB + Email Service
   ```

4. **Reporting and Analytics**
   ```
   Frontend → Core Model API → Platform DB → Generated Reports
   ```

### Cross-Service Communication
- **Pattern**: REST API calls between services
- **Authentication**: Firebase Auth JWT tokens
- **Data Format**: JSON payloads
- **Error Handling**: HTTP status codes and error responses

## Current Technology Dependencies

### Google Cloud Platform Services
| Service | Usage | Criticality |
|---------|--------|-------------|
| **Firebase Functions** | API hosting (serverless) | High |
| **GCP Cloud Run** | Container runtime for functions | High |
| **Cloud SQL PostgreSQL** | Primary database | Critical |
| **GCP Secrets Manager** | Configuration and secrets | High |
| **GCP Logging** | Application and system logs | Medium |
| **Firebase Auth** | User authentication | Critical |
| **Firebase App Hosting** | Frontend deployment | High |

### Development & Runtime Dependencies
```python
# Backend APIs (estimated)
Flask==2.x                    # Web framework
psycopg2==2.x                # PostgreSQL adapter
firebase-admin==6.x          # Firebase Admin SDK
google-cloud-secret-manager  # Secrets access
google-cloud-logging         # Logging integration
```

```typescript
// Frontend (estimated)
next@14.x                    // React framework
firebase@10.x                // Firebase client SDK
@firebase/auth               // Authentication
@firebase/app                // Firebase core
```

## Current Architecture Strengths

### ✅ Positive Aspects
1. **Clear Separation of Concerns**: Well-defined service boundaries
2. **Serverless Benefits**: Auto-scaling, pay-per-use cost model  
3. **Managed Services**: Reduced operational overhead
4. **Single-Tenant Design**: Built-in customer data isolation
5. **PostgreSQL**: Industry-standard, portable database choice
6. **REST APIs**: Standard, well-understood communication pattern

## Current Architecture Limitations  

### ❌ Migration Challenges
1. **Firebase Vendor Lock-in**: Deep integration with Google ecosystem
2. **Limited Multi-Cloud**: Cannot deploy outside GCP infrastructure
3. **Authentication Dependency**: Firebase Auth not available outside Google
4. **Serverless Constraints**: Cold start latency, execution time limits
5. **Secrets Management**: GCP-specific secrets integration
6. **Logging Integration**: Tight coupling with GCP logging services
7. **No Container Orchestration**: Limited control over service deployment

## Operational Characteristics

### Deployment Model
- **Single Tenant**: Each customer has separate infrastructure
- **Deployment Method**: Manual through GCP Console/CLI
- **Environment Isolation**: Complete tenant separation
- **Update Process**: Manual deployment per tenant

### Scalability Profile
- **Frontend**: Auto-scaling via Firebase Hosting CDN
- **APIs**: Firebase Functions auto-scaling (0 to N instances)
- **Database**: Vertical scaling of Cloud SQL instance
- **Current Load**: Low to medium (startup scale)

### Security Model
- **Authentication**: Firebase Auth with JWT tokens
- **Authorization**: Role-based access control (RBAC)
- **Network Security**: GCP VPC and firewall rules
- **Data Encryption**: At-rest and in-transit (GCP default)
- **Secrets**: GCP Secrets Manager with IAM controls

## Migration Assessment

### Migration-Ready Components ✅
1. **PostgreSQL Database**: Portable across cloud providers
2. **Flask APIs**: Container-ready Python applications
3. **Next.js Frontend**: Standard web application
4. **Business Logic**: Cloud-agnostic application code
5. **Data Model**: Relational schema, portable

### Migration Challenges ⚠️
1. **Firebase Auth**: Complex user migration required
2. **Serverless Functions**: Need Kubernetes/Knative equivalent
3. **GCP Integrations**: Secrets, logging, monitoring dependencies
4. **Deployment Automation**: No Infrastructure as Code currently
5. **Multi-Cloud Networking**: Security and ingress configuration

### Data Migration Considerations
- **User Data**: Export from Firebase Auth to new identity system
- **Application Data**: PostgreSQL dump/restore process
- **Configuration**: Environment-specific settings migration  
- **Secrets**: Secure transfer to new secrets management system

## Conclusion

The current Resimate architecture is well-structured with clear service boundaries but heavily dependent on GCP/Firebase services. The microservices design and PostgreSQL choice provide a solid foundation for migration. The primary challenges will be replacing Firebase Auth, implementing Kubernetes-based serverless capabilities, and creating multi-cloud deployment automation.

**Migration Readiness**: Medium-High  
**Architecture Quality**: High  
**Technology Stack**: Migration-friendly  
**Main Blockers**: Authentication system and deployment automation