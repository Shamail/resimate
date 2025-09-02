# ADR-005: Retain PostgreSQL as Primary Database

**Status**: Accepted  
**Date**: September 1, 2025  
**Deciders**: Shamail Saidi, Floyd (CTO)  

## Context

We need to decide whether to retain PostgreSQL or migrate to a different database system for our cloud-agnostic architecture.

## Decision

We will retain PostgreSQL as our primary database, using cloud-managed instances where available and PostgreSQL Operator for on-premise deployments.

## Consequences

### Positive
- No data migration required (risk reduction)
- Team expertise already exists
- Excellent cloud support (RDS, Azure Database, Cloud SQL)
- Strong ACID compliance for business data
- PostgreSQL Operator enables Kubernetes-native deployment

### Negative
- Not "cloud-native" like some NoSQL alternatives
- Requires careful scaling planning
- Multi-region replication complexity

## Alternatives Considered

1. **CockroachDB**: Cloud-native but migration risk
2. **MongoDB**: NoSQL doesn't fit our relational data model
3. **Amazon Aurora**: Excellent but AWS-specific
4. **Vitess**: Good for scaling but added complexity
5. **YugabyteDB**: Promising but less mature