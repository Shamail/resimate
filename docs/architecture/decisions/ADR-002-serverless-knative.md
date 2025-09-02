# ADR-002: Use Knative for Serverless API Deployment

**Status**: Accepted  
**Date**: September 1, 2025  
**Deciders**: Shamail Saidi, Floyd (CTO)  

## Context

We need a serverless platform that provides scale-to-zero capabilities, automatic scaling, and event-driven architecture while remaining cloud-agnostic and avoiding vendor lock-in.

## Decision

We will use Knative Serving for deploying our API services in a serverless manner on Kubernetes.

## Consequences

### Positive
- Scale-to-zero reduces costs by 40-60% during low usage
- Cloud-agnostic serverless on any Kubernetes cluster
- Progressive deployment strategies (blue-green, canary)
- Native Kubernetes integration
- Event-driven capabilities with Knative Eventing

### Negative
- Additional complexity in Kubernetes stack
- Cold start latency (mitigated to <2 seconds)
- Requires Istio or similar service mesh

## Alternatives Considered

1. **AWS Lambda**: Excellent but AWS-specific
2. **Azure Functions**: Azure-specific lock-in
3. **Google Cloud Run**: GCP-specific (though Knative-based)
4. **OpenFaaS**: Less mature, smaller community
5. **Traditional Kubernetes Deployments**: No scale-to-zero, higher costs