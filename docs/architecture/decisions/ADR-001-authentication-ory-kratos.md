# ADR-001: Use Ory Kratos for Authentication

**Status**: Accepted  
**Date**: September 1, 2025  
**Deciders**: Shamail Saidi, Floyd (CTO)  

## Context

We need to replace Firebase Authentication with a cloud-agnostic solution that supports multi-cloud deployments while maintaining enterprise features like SSO, MFA, and compliance requirements.

## Decision

We will use Ory Kratos as our authentication and identity management system.

## Consequences

### Positive
- Cloud-agnostic, self-hosted solution
- API-first design aligns with our architecture
- Lightweight compared to alternatives (50% less resource usage than Keycloak)
- Strong privacy and GDPR compliance features
- Active open-source community

### Negative
- Less mature than Keycloak
- Requires more custom UI development
- Migration complexity from Firebase Auth

## Alternatives Considered

1. **Keycloak**: More feature-complete but heavier and Java-based
2. **Auth0**: Excellent features but vendor lock-in
3. **AWS Cognito**: AWS-specific, not cloud-agnostic
4. **Custom Solution**: Too much development effort and security risk