# Customer Requirements Interview Template

**Project**: Resimate Cloud Migration  
**Interview Type**: Customer Requirements Gathering  
**Customer**: [Customer Name]  
**Date**: [YYYY-MM-DD]  
**Duration**: 60-90 minutes  
**Interview Format**: [Video Call / In-Person]  

## Interview Team

**Resimate Representatives:**
- Patrick (CEO) - Business relationship owner
- Shamail Saidi - Technical consultant
- [Floyd (CTO) - Optional for technical deep-dives]

**Customer Representatives:**
- [Name, Title] - Business stakeholder
- [Name, Title] - Technical/IT lead
- [Name, Title] - Security/Compliance officer
- [Name, Title] - End user representative

## Interview Objectives

1. Understand customer's cloud deployment requirements and constraints
2. Identify specific compliance and security needs
3. Define integration requirements with existing systems
4. Establish success criteria and timeline expectations
5. Determine support and operational requirements
6. Identify potential risks and concerns

## Pre-Interview Preparation

**Materials to Share (24-48 hours before):**
- [ ] High-level architecture overview
- [ ] Deployment options summary
- [ ] Security and compliance capabilities
- [ ] Timeline and implementation approach

**Internal Preparation:**
- [ ] Review customer's industry and business model
- [ ] Research specific compliance requirements
- [ ] Prepare demonstration if requested
- [ ] Identify key questions based on customer type

## Interview Guide

### Section 1: Business Context (10 minutes)

**Opening & Introductions**
- Thank you for participating
- Brief project overview
- Interview objectives and structure

**Business Understanding**
1. Can you describe your organization's current resilience management challenges?
2. What drove your interest in a customer-deployed solution vs. SaaS?
3. What are your top 3 priorities for this deployment?
4. How many users do you anticipate? What roles?
5. What's your target timeline for deployment?

**Expected Outcomes:**
- [ ] Clear understanding of business drivers
- [ ] Confirmed deployment timeline
- [ ] User scale and growth projections

### Section 2: Technical Environment (15 minutes)

**Cloud Platform & Infrastructure**
1. Which cloud platform do you prefer? (AWS / Azure / GCP / On-premise)
   - [ ] AWS
   - [ ] Azure  
   - [ ] GCP
   - [ ] On-premise
   - [ ] Hybrid: ___________

2. Do you have existing Kubernetes infrastructure?
   - [ ] Yes - Version: _______ Provider: _______
   - [ ] No - Open to Kubernetes
   - [ ] No - Prefer alternative: _______

3. What's your current authentication/identity provider?
   - [ ] Active Directory / Azure AD
   - [ ] Okta
   - [ ] Auth0
   - [ ] Other: _______
   - [ ] None / Need solution

**Network & Security Requirements**
4. Network architecture requirements:
   - [ ] Air-gapped / Isolated network
   - [ ] VPN access only
   - [ ] Private subnet deployment
   - [ ] Internet-facing acceptable
   - [ ] Specific IP whitelisting

5. Egress/Ingress restrictions:
   - [ ] No external internet access
   - [ ] Whitelist-only external access
   - [ ] Proxy requirements
   - [ ] Firewall rules needed

**Data Residency & Sovereignty**
6. Data location requirements:
   - Specific region/country: _______
   - Multiple regions needed: _______
   - Data replication requirements: _______

**Integration Requirements**
7. Systems requiring integration:
   - [ ] ERP System: _______
   - [ ] SIEM/Logging: _______
   - [ ] Monitoring: _______
   - [ ] Ticketing: _______
   - [ ] Data warehouse: _______
   - [ ] Other: _______

### Section 3: Compliance & Security (20 minutes)

**Regulatory Compliance**
1. Which compliance frameworks must you adhere to?
   - [ ] GDPR (EU Data Protection)
   - [ ] HIPAA (Healthcare)
   - [ ] SOC2 Type I/II
   - [ ] ISO 27001
   - [ ] PCI DSS
   - [ ] FedRAMP
   - [ ] Industry-specific: _______
   - [ ] Other: _______

2. Audit requirements:
   - Frequency: _______
   - Internal/External: _______
   - Specific audit trails needed: _______

**Security Requirements**
3. Authentication & Authorization:
   - [ ] Multi-factor authentication (MFA) required
   - [ ] Single Sign-On (SSO) required
   - [ ] Role-based access control (RBAC)
   - [ ] Attribute-based access control (ABAC)
   - [ ] Session timeout requirements: _______

4. Encryption requirements:
   - [ ] Encryption at rest (Database)
   - [ ] Encryption in transit (TLS version: _____)
   - [ ] Field-level encryption
   - [ ] Bring your own keys (BYOK)
   - [ ] HSM requirements

5. Security monitoring:
   - [ ] Security scanning requirements
   - [ ] Vulnerability assessment frequency
   - [ ] Penetration testing requirements
   - [ ] Security incident response SLA

**Data Protection**
6. Backup and recovery:
   - RPO (Recovery Point Objective): _______
   - RTO (Recovery Time Objective): _______
   - Backup retention period: _______
   - Backup location requirements: _______

7. Data classification:
   - Types of sensitive data: _______
   - PII handling requirements: _______
   - Data retention policies: _______
   - Data deletion requirements: _______

### Section 4: Performance & Scalability (10 minutes)

**Performance Requirements**
1. Expected system load:
   - Concurrent users: _______
   - Peak usage times: _______
   - Transaction volume: _______
   - Data volume: _______

2. Performance expectations:
   - Page load time: < _______ seconds
   - API response time: < _______ ms
   - Report generation: < _______ minutes
   - Availability SLA: _______% 

**Scalability Needs**
3. Growth projections:
   - 6 months: _______ users
   - 1 year: _______ users
   - 2 years: _______ users

4. Scaling preferences:
   - [ ] Auto-scaling required
   - [ ] Manual scaling acceptable
   - [ ] Scheduled scaling (business hours)
   - [ ] Multi-region deployment

### Section 5: Operational Requirements (15 minutes)

**Deployment & Maintenance**
1. Deployment preferences:
   - [ ] Fully automated (CI/CD)
   - [ ] Controlled manual deployment
   - [ ] Blue-green deployment
   - [ ] Canary releases
   - [ ] Scheduled maintenance windows: _______

2. Update frequency tolerance:
   - [ ] Continuous updates acceptable
   - [ ] Monthly update cycle
   - [ ] Quarterly update cycle
   - [ ] Annual update cycle
   - [ ] Customer-controlled updates only

**Support & Training**
3. Support requirements:
   - [ ] 24/7 support needed
   - [ ] Business hours only
   - [ ] SLA requirements: _______
   - [ ] Dedicated support contact
   - [ ] Self-service preferred

4. Training needs:
   - [ ] Administrator training
   - [ ] End-user training
   - [ ] Technical operations training
   - [ ] Documentation requirements

**Monitoring & Alerting**
5. Monitoring integration:
   - Existing monitoring tools: _______
   - Metrics required: _______
   - Alerting channels: _______
   - Dashboard requirements: _______

### Section 6: Commercial & Timeline (10 minutes)

**Budget & Licensing**
1. Budget considerations:
   - Infrastructure budget: _______
   - Implementation budget: _______
   - Ongoing operational budget: _______
   - Licensing model preference: _______

**Timeline & Milestones**
2. Implementation timeline:
   - Target go-live date: _______
   - Pilot/POC phase: _______
   - Phased rollout needs: _______
   - Critical deadlines: _______

3. Success criteria:
   - POC success metrics: _______
   - Production success metrics: _______
   - User adoption targets: _______

### Section 7: Concerns & Risks (10 minutes)

**Open Discussion**
1. What are your biggest concerns about this deployment?
2. Have you had similar deployments? What were the challenges?
3. What would constitute a failed implementation?
4. What additional capabilities would you like to see?

**Risk Identification**
- Technical risks: _______
- Business risks: _______
- Timeline risks: _______
- Resource risks: _______

### Section 8: Next Steps (5 minutes)

**Action Items**
1. Information to be provided by customer:
   - [ ] Technical architecture diagrams
   - [ ] Security policies
   - [ ] Compliance documentation
   - [ ] User projections

2. Information to be provided by Resimate:
   - [ ] Detailed deployment architecture
   - [ ] Security compliance matrix
   - [ ] Implementation timeline
   - [ ] Pricing proposal

**Follow-up Plan**
- Next meeting date: _______
- POC/Pilot timeline: _______
- Decision timeline: _______
- Key contacts confirmed: _______

## Summary Template

### Customer Profile Summary

**Customer**: [Name]  
**Industry**: [Industry]  
**Deployment Type**: [AWS/Azure/GCP/On-premise]  
**User Scale**: [Number]  
**Timeline**: [Target Date]  

### Key Requirements

**Must-Have Requirements:**
1. 
2. 
3. 

**Nice-to-Have Requirements:**
1. 
2. 
3. 

**Deal Breakers:**
1. 
2. 

### Compliance Requirements
- Primary: [GDPR/HIPAA/SOC2]
- Secondary: [Others]

### Technical Constraints
- Cloud Platform: 
- Network Requirements:
- Integration Needs:

### Commercial Summary
- Budget Range: 
- Decision Timeline:
- Decision Makers:

### Risk Assessment
- **High Risks**: 
- **Medium Risks**:
- **Low Risks**:

### Recommended Approach
[Based on requirements, recommend specific deployment approach]

## Post-Interview Checklist

- [ ] Send thank you email within 24 hours
- [ ] Distribute interview notes to internal team
- [ ] Update customer requirements matrix
- [ ] Create customer-specific deployment design
- [ ] Prepare follow-up materials
- [ ] Schedule internal review meeting
- [ ] Update project risk register
- [ ] Create customer-specific timeline
- [ ] Prepare pricing proposal if requested

---

**Interview Conducted By**: [Names]  
**Notes Prepared By**: [Name]  
**Distribution**: Patrick, Floyd, Shamail, [Customer Contact]  
**Confidentiality**: Customer Confidential - Do Not Distribute