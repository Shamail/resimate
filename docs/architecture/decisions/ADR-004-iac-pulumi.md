# ADR-004: Use Pulumi for Infrastructure as Code

**Status**: Accepted  
**Date**: September 1, 2025  
**Deciders**: Shamail Saidi, Floyd (CTO)  

## Context

We need an Infrastructure as Code solution that supports multiple cloud providers with a consistent programming model and strong typing.

## Decision

We will use Pulumi for infrastructure provisioning and management across AWS, Azure, GCP, and on-premise environments.

## Consequences

### Positive
- Real programming languages (Python, TypeScript) instead of DSL
- Type safety and IDE support
- Excellent multi-cloud support
- Strong state management and secrets handling
- Good integration with existing CI/CD pipelines

### Negative
- Smaller community than Terraform
- Requires programming knowledge
- Commercial features require paid subscription

## Alternatives Considered

1. **Terraform**: Excellent but HCL is limiting, less type safety
2. **AWS CDK**: AWS-specific
3. **Azure Bicep**: Azure-specific
4. **Crossplane**: Kubernetes-native but less mature
5. **Ansible**: Better for configuration management than infrastructure