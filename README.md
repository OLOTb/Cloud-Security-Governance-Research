# Cloud Security & Governance Research

### Cloud Security and Misconfiguration Risks: IaaS, PaaS, SaaS, Shared Responsibility and Security Frameworks

**Academic Research Project | Cybersecurity | Cloud Computing | Security Governance**

---

## Overview

Cloud computing has transformed modern IT infrastructures by providing organizations with scalable, flexible, and cost-efficient services. However, the widespread adoption of cloud technologies has introduced significant cybersecurity challenges, particularly regarding **security misconfigurations, access management, and the shared responsibility model**.

This repository presents an academic literature review investigating the security risks associated with cloud environments and the effectiveness of modern security governance frameworks.

The research examines how organizations can secure their cloud infrastructure, prevent configuration errors, and improve security governance across **Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS)** environments.

The project combines scientific literature, institutional cybersecurity reports, industry frameworks, and a real-world investigation of the **2019 Capital One data breach**.

### Research Question

> How do the shared responsibility model and the complexity of multi-cloud environments contribute to misconfigurations, and how do current frameworks help address these issues?

## Research Objectives

The research focuses on six main objectives:

1. Understand the security responsibilities of cloud providers and customers across IaaS, PaaS, and SaaS.
2. Identify common cloud security misconfigurations, vulnerabilities, and their consequences.
3. Analyze the organizational and technical causes of cloud security failures.
4. Compare preventive security approaches with continuous cloud monitoring solutions.
5. Evaluate cybersecurity governance frameworks such as NIST CSF, CSA CCM, and CIS Benchmarks.
6. Investigate a real-world cloud security incident to understand how configuration weaknesses can lead to large-scale data breaches.

## 1. Cloud Computing and Shared Responsibility

Cloud computing relies on different service models that distribute operational and security responsibilities between cloud service providers (CSPs) and their customers.

| Service Model | Description | Main Customer Responsibilities |
|---|---|---|
| **IaaS** | Virtualized infrastructure, including computing, storage, and networking | Operating systems, applications, network configurations, identities, and data |
| **PaaS** | Managed environments for developing and deploying applications | Application security, identity management, access permissions, and data |
| **SaaS** | Fully managed applications accessed over the Internet | User access, data governance, account security, and available security settings |

### Shared Responsibility Model

One of the central concepts examined in this research is the **Shared Responsibility Model**.

Cloud providers generally secure the underlying infrastructure, while customers remain responsible for configuring and protecting the resources they manage.

These responsibilities vary depending on the service model and provider.

A misunderstanding of these boundaries can create security gaps, particularly in complex multi-cloud infrastructures.

## 2. Cloud Security Threats and Misconfigurations

The research identifies several recurring cloud security weaknesses.

### Publicly Exposed Cloud Storage

Incorrectly configured storage permissions can expose sensitive information to unauthorized users.

Examples include:

- Publicly accessible Amazon S3 buckets
- Misconfigured Azure Blob Storage containers
- Incorrect access control lists (ACLs)
- Excessively permissive storage policies

**Potential impact:** Sensitive information disclosure, data breaches, and compliance violations.

### Excessive IAM Permissions

Identity and Access Management (IAM) defines which users and services can access cloud resources.

Overly permissive IAM policies violate the **Principle of Least Privilege (PoLP)**.

Common examples include:

- Wildcard permissions (`Action: "*"`)
- Unrestricted resource access (`Resource: "*"`)
- Excessive administrative privileges
- Improperly managed service identities

**Potential impact:** Privilege escalation, account compromise, and unauthorized access to sensitive resources.

### Exposed Administration Services

Cloud instances can be exposed to external attacks when sensitive administration ports are publicly accessible.

Examples:

- SSH (TCP port 22)
- RDP (TCP port 3389)
- Inbound network rules allowing access from `0.0.0.0/0`

**Potential impact:** Brute-force attacks, unauthorized system access, and infrastructure compromise.

### Root Causes

The literature identifies several contributing factors:

- Human configuration errors
- Misunderstanding of shared security responsibilities
- Shadow IT and uncontrolled resource deployment
- Rapid CI/CD deployment processes
- Insufficient Infrastructure as Code (IaC) security validation
- Lack of continuous monitoring
- Multi-cloud configuration complexity

## 3. Literature Review and Security Approaches

The project compares peer-reviewed scientific publications, government cybersecurity guidance, and professional security reports.

The literature highlights two complementary approaches for reducing cloud misconfiguration risks.

### Shift-Left Security

Shift-left security integrates security controls into the software development lifecycle before infrastructure reaches production.

Typical practices include:

- Infrastructure as Code security scanning
- Static analysis of Terraform and CloudFormation configurations
- Automated checks in CI/CD pipelines
- Early detection of insecure permissions
- Security policy enforcement before deployment

**Tools examined:** Checkov and KICS.

**Advantages:**

- Identifies security weaknesses before deployment
- Reduces the cost of remediation
- Integrates security into DevSecOps workflows

**Limitations:**

- False positives and inconsistent detection results
- Limited visibility into manually modified cloud resources
- Incomplete coverage of some cloud services

### Runtime Security and Continuous Monitoring

Runtime security evaluates the configuration and security posture of deployed cloud environments.

Technologies covered include:

- **CSPM:** Cloud Security Posture Management
- **CWPP:** Cloud Workload Protection Platform
- **CNAPP:** Cloud-Native Application Protection Platform

These technologies help organizations identify configuration drift, risky permissions, and security weaknesses across running cloud resources.

### Comparative Analysis

| Criteria | Shift-Left Security | Runtime Security |
|---|---|---|
| Security stage | Before deployment | After deployment |
| Main approach | Static IaC analysis | Continuous cloud assessment |
| Example solutions | Checkov, KICS | CSPM, CWPP, CNAPP |
| Main advantage | Prevents insecure deployments | Detects configuration drift |
| Visibility | Infrastructure definitions and code | Deployed resources and configurations |
| Main limitations | False positives, incomplete coverage | Alert fatigue, post-deployment detection |

**Key finding:** Neither approach is sufficient on its own. Effective cloud security requires both preventive controls and continuous monitoring.

## 4. Real-World Case Study: Capital One (2019)

The research examines the **2019 Capital One data breach**, one of the most significant examples of a cloud security incident involving configuration weaknesses.

### Incident Overview

In 2019, Capital One suffered a major security breach involving its Amazon Web Services (AWS) environment.

The incident affected approximately:

- **100 million individuals in the United States**
- **6 million individuals in Canada**

Compromised information included personal identification data and financial information, including approximately 140,000 Social Security numbers and 80,000 linked bank account numbers.

### Attack Chain

The technical analysis identifies four major stages.

**1. Web Application Firewall Misconfiguration**

A vulnerability involving a misconfigured Web Application Firewall (WAF) enabled a Server-Side Request Forgery (SSRF) attack.

**2. Instance Metadata Service Access**

The attacker exploited SSRF to access the AWS EC2 Instance Metadata Service (IMDS), exposing temporary credentials associated with an IAM role.

**3. Excessive IAM Permissions**

The compromised IAM role had broader permissions than necessary, allowing access to sensitive cloud resources.

**4. Unauthorized Data Access**

The attacker used the obtained permissions to access and extract sensitive information stored in Amazon S3.

### Security Lessons

The incident illustrates the importance of:

- Enforcing least-privilege IAM policies
- Protecting instance metadata services
- Using secure configurations and restrictive defaults
- Continuously auditing cloud environments
- Monitoring sensitive resource access
- Understanding customer responsibilities within the cloud

It demonstrates how multiple configuration weaknesses can combine to create a major security incident.

## 5. Cybersecurity Governance Frameworks

The research evaluates three major approaches to cloud security governance.

### NIST Cybersecurity Framework 2.0

The **NIST CSF 2.0**, published in February 2024, provides a structured approach to cybersecurity risk management.

It organizes cybersecurity activities into six core functions:

| Function | Purpose |
|---|---|
| Govern | Establish cybersecurity strategy, policies, and risk oversight |
| Identify | Understand assets, systems, and security risks |
| Protect | Implement safeguards to reduce risk |
| Detect | Identify cybersecurity incidents and anomalies |
| Respond | Manage and contain security incidents |
| Recover | Restore affected services and capabilities |

The framework supports organization-wide cybersecurity governance and risk management.

### Cloud Security Alliance — Cloud Controls Matrix

The **CSA Cloud Controls Matrix (CCM)** provides cloud-specific security control guidance.

It supports:

- Cloud security governance
- Assessment of cloud service providers
- Security control evaluation
- Shared responsibility analysis
- Cloud compliance and assurance activities

### CIS Benchmarks

The **Center for Internet Security (CIS) Benchmarks** provide technical configuration recommendations for securing systems and cloud environments.

They can be applied to services and infrastructure from providers such as AWS, Microsoft Azure, and Google Cloud.

Common security areas include:

- Identity and access configuration
- Network security
- Audit logging
- Storage protection
- Secure service configuration

### Framework Comparison

| Framework | Primary Focus | Role in Cloud Security |
|---|---|---|
| NIST CSF 2.0 | Governance and risk management | Organization-wide security strategy |
| CSA CCM | Cloud-specific controls and assurance | Cloud security assessments and provider evaluation |
| CIS Benchmarks | Technical hardening | Secure cloud resource configuration |

**Research conclusion:** These frameworks are complementary. Organizations benefit from combining strategic governance, cloud-specific control requirements, and technical security benchmarks.

## 6. Research Findings

The literature review identifies several important findings.

**1. Misconfiguration is a major cloud security risk.**

Many security weaknesses originate from customer-managed settings rather than vulnerabilities in the underlying physical cloud infrastructure.

**2. Shared responsibility remains difficult to manage.**

The division of responsibilities changes between service models, providers, and individual cloud services.

**3. Preventive and detective controls must work together.**

Static analysis helps prevent insecure deployments, while runtime monitoring detects deviations and previously unidentified weaknesses.

**4. Secure defaults can reduce exposure.**

Research highlights the importance of provider-level security defaults in limiting accidentally exposed resources.

**5. Multi-cloud environments increase governance complexity.**

Different providers introduce distinct permissions, security policies, management interfaces, and monitoring mechanisms.

**6. Automation introduces additional challenges.**

False positives, missing contextual information, and potential service disruption can limit the effectiveness of automated remediation.

## 7. Limitations and Future Research

Despite improvements in cloud security technologies, several challenges remain unresolved.

### Multi-Cloud Governance

Managing consistent security policies across multiple cloud providers is difficult because of differences in architectures, identity systems, and configuration mechanisms.

### Cloud-Native and Ephemeral Workloads

Containers, Kubernetes environments, and serverless architectures introduce additional security challenges because resources can be created and destroyed rapidly.

### Alert Fatigue

Continuous security monitoring can generate large volumes of findings, making it difficult for security teams to distinguish critical incidents from lower-priority alerts.

### Automated Remediation

Automated security corrections may disrupt legitimate applications when alerts lack sufficient contextual information.

### Future Research Directions

The review identifies promising areas for further investigation:

- Context-aware security remediation
- Unified multi-cloud security policies
- Improved cloud identity governance
- Better detection of serverless misconfigurations
- More effective security monitoring for ephemeral workloads
- Improved integration of development and security operations

## 8. Recommended Security Practices

Based on the literature analysis, an effective cloud security strategy should combine the following practices:

1. **Apply least privilege:** Minimize permissions for users, applications, and service accounts.
2. **Adopt secure defaults:** Restrict public access and unnecessary network exposure.
3. **Scan Infrastructure as Code:** Detect insecure configurations before deployment.
4. **Implement continuous monitoring:** Use posture-management solutions to detect drift and configuration weaknesses.
5. **Protect sensitive information:** Apply encryption and appropriate access controls.
6. **Review cloud permissions regularly:** Audit identities, roles, and access policies.
7. **Integrate security into CI/CD:** Establish automated security checks in deployment workflows.
8. **Establish clear ownership:** Define responsibilities between cloud providers, platform teams, developers, and security teams.
9. **Use recognized frameworks:** Align governance and technical configuration practices with relevant NIST, CSA, and CIS guidance.

## 9. Research Methodology

This project follows a structured, evidence-based literature review methodology.

The research process includes:

1. Defining the research question and investigation scope.
2. Identifying scientific publications and authoritative cybersecurity sources.
3. Studying cloud architectures, security responsibilities, and common vulnerabilities.
4. Comparing prevention and runtime detection approaches.
5. Examining findings, disagreements, and limitations across publications.
6. Investigating the Capital One security incident.
7. Mapping relevant security measures to governance frameworks.
8. Synthesizing conclusions and identifying research gaps.

Sources include peer-reviewed publications from IEEE, ACM, and USENIX, together with institutional and professional cybersecurity reports.

### Research Scope

This is a **bibliographic and analytical cybersecurity research project**.

It does not involve deploying cloud infrastructure, developing a production security platform, or conducting penetration testing.

The primary deliverable is a structured research report supported by scientific references, technical analysis, and a documented case study.

## 10. Selected References

The complete research report contains the full bibliography. Key references include:

### Standards and Institutional Publications

1. **NIST** — *The NIST Definition of Cloud Computing*, SP 800-145 (2011). [Official publication](https://csrc.nist.gov/pubs/sp/800/145/final)
2. **NIST** — *Cybersecurity Framework 2.0* (2024). [Official framework](https://www.nist.gov/cyberframework)
3. **Cloud Security Alliance** — *Security Guidance for Critical Areas of Focus in Cloud Computing*, v5.0 (2024).
4. **Cloud Security Alliance** — *Top Threats to Cloud Computing 2024*. [Report](https://cloudsecurityalliance.org/artifacts/top-threats-to-cloud-computing-post-pandemic-eleven-survey-report)
5. **NSA** — *Mitigating Cloud Vulnerabilities* (2020). [CISA publication](https://www.cisa.gov/news-events/alerts/2020/01/24/nsa-releases-guidance-mitigating-cloud-vulnerabilities)
6. **NSA / CISA** — *Top Ten Cloud Security Mitigation Strategies* (2024). [Official report](https://media.defense.gov/2024/Mar/07/2003407860/-1/-1/0/CSI-CloudTop10-Mitigation-Strategies.PDF)

### Scientific Publications

7. **Rahman et al.** — *The Seven Sins: Security Smells in Infrastructure as Code Scripts*. IEEE/ACM ICSE (2019). [DOI](https://doi.org/10.1109/ICSE.2019.00033)
8. **Rahman et al.** — *Security Smells in Ansible and Chef Scripts: A Replication Study*. ACM TOSEM (2021). [DOI](https://doi.org/10.1145/3408897)
9. **Saavedra and Ferreira** — *GLITCH: Automated Polyglot Security Smell Detection in Infrastructure as Code*. IEEE/ACM ASE (2022). [DOI](https://doi.org/10.1145/3551349.3556945)
10. **Wen et al.** — *PHOENIX: Misconfiguration Detection for AWS Serverless Computing*. IEEE Transactions on Cloud Computing (2025). [DOI](https://doi.org/10.1109/TCC.2025.3577211)
11. **Alahmadi et al.** — *99% False Positives: A Qualitative Study of SOC Analysts' Perspectives on Security Alarms*. USENIX Security (2022). [Publication](https://www.usenix.org/conference/usenixsecurity22/presentation/alahmadi)

### Industry Research

12. **Datadog** — *State of Cloud Security 2024*. [Report](https://www.datadoghq.com/state-of-cloud-security-2024/)

## 11. Project Team

This research was conducted as part of an academic module with 5 different contributors.

## 12. Conclusion

Cloud security depends on more than the security capabilities of cloud service providers.

Organizations must understand the shared responsibility model, maintain secure configurations, enforce strict access controls, and establish effective cybersecurity governance.

The research demonstrates that **cloud misconfiguration risks cannot be addressed through a single framework or tool**.

Instead, an effective security strategy requires a combination of:

- Security governance and risk management
- Preventive Infrastructure as Code analysis
- Continuous cloud security monitoring
- Least-privilege access controls
- Secure configuration benchmarks
- Clear organizational responsibilities

As multi-cloud adoption and cloud-native technologies continue to evolve, maintaining consistent security policies and reducing configuration errors will remain major cybersecurity challenges.

---

**Repository:** [Cloud-Security-Governance-Research](https://github.com/OLOTb/Cloud-Security-Governance-Research)

**Project Type:** Academic Literature Review

**Research Areas:** Cloud Security · Cybersecurity Governance · Risk Management · IAM · DevSecOps · CSPM · NIST · CSA CCM · CIS Benchmarks

**Purpose:** Educational and research-oriented cybersecurity analysis.
