# AWS CloudOps Health Check

![AWS](https://img.shields.io/badge/AWS-CloudOps-orange)
![Kubernetes](https://img.shields.io/badge/Kubernetes-EKS-blue)
![Terraform](https://img.shields.io/badge/Terraform-IaC-purple)
![CI/CD](https://img.shields.io/badge/CI%2FCD-DevSecOps-green)

## Overview

This repository demonstrates a practical AWS CloudOps / DevOps health check covering:

* AWS infrastructure
* Amazon EKS / Kubernetes
* CI/CD pipelines
* Security
* Reliability
* Observability
* Cost optimization

The objective is to identify infrastructure and operational issues, classify their severity, recommend remediation, and demonstrate the implementation of selected fixes.

---

## Project Scenario

This portfolio project uses a fictional client environment.

**Client:** Acme Technologies

**Application:** Cloud-native microservices application

**Cloud Platform:** Amazon Web Services

**Container Platform:** Amazon EKS

**CI/CD Platform:** GitHub Actions

**Infrastructure as Code:** Terraform

---

## Architecture

The target environment consists of the following components:

```text
                         Internet
                            ↓
                    Application Load
                       Balancer
                            ↓
                    Amazon EKS Cluster
                            ↓
              +-------------+-------------+
              ↓             ↓             ↓
         Microservice   Microservice   Microservice
              ↓             ↓             ↓
              +-------------+-------------+
                            ↓
                     Amazon RDS
                       PostgreSQL

Additional AWS Services:

- Amazon VPC
- IAM
- Amazon ECR
- Amazon S3
- Amazon CloudWatch
- EBS
- Load Balancing
```

---

# Health Check Scope

## 1. AWS Infrastructure

### Networking

The assessment covers:

* VPC
* Availability Zones
* Public subnets
* Private subnets
* Route tables
* Internet Gateway
* NAT Gateway
* Security Groups
* Network ACLs
* Load Balancers
* VPC endpoints

### IAM and Security

The assessment covers:

* IAM users
* IAM roles
* IAM policies
* Least-privilege access
* MFA
* Access keys
* Service roles
* Excessive permissions
* Unused identities

### Compute

The assessment covers:

* EC2 instances
* Auto Scaling Groups
* Instance sizing
* CPU utilization
* Memory utilization
* Idle resources
* Over-provisioned resources

### Storage

The assessment covers:

* EBS volumes
* EBS snapshots
* EFS
* S3
* Encryption
* Lifecycle policies
* Unused storage
* Public access configuration

### Database

The assessment covers:

* Amazon RDS
* Instance sizing
* Storage
* Backup configuration
* Encryption
* Multi-AZ configuration
* Monitoring
* Security Groups

### Load Balancing

The assessment covers:

* Application Load Balancer
* Listeners
* Target Groups
* Health checks
* TLS configuration
* Security Groups

### Monitoring

The assessment covers:

* CloudWatch metrics
* CloudWatch alarms
* CloudWatch logs
* Dashboards
* Operational alerts

### Backup and Recovery

The assessment covers:

* EBS snapshots
* RDS backups
* Backup retention
* Recovery requirements
* Disaster recovery readiness

---

# 2. Amazon EKS / Kubernetes

## Cluster Health

The assessment covers:

* EKS cluster configuration
* Kubernetes version
* Worker nodes
* Node groups
* Node health
* Node utilization
* Availability Zones
* EKS add-ons

## Workloads

The assessment covers:

* Deployments
* ReplicaSets
* Pods
* Services
* Ingress
* ConfigMaps
* Secrets
* Jobs
* CronJobs

## Resource Management

Check for:

* CPU requests
* CPU limits
* Memory requests
* Memory limits
* Resource utilization
* Resource contention

## Application Reliability

Check for:

* Liveness probes
* Readiness probes
* Startup probes
* Pod restart frequency
* CrashLoopBackOff
* OOMKilled
* Pending pods

## High Availability

Check for:

* Multiple replicas
* Pod distribution
* Pod anti-affinity
* Topology spread constraints
* Pod Disruption Budgets
* Multi-AZ scheduling
* Rolling update configuration

## Autoscaling

Check for:

* Horizontal Pod Autoscaler
* Cluster Autoscaler or Karpenter
* Minimum replicas
* Maximum replicas
* Scaling thresholds
* Resource-based scaling

## Kubernetes Networking

Check for:

* Services
* Ingress
* Load Balancers
* Network Policies
* DNS
* Service-to-service communication

## Kubernetes Storage

Check for:

* Persistent Volumes
* Persistent Volume Claims
* Storage Classes
* EBS CSI
* EFS CSI
* Volume utilization
* Backup strategy

## Kubernetes Security

Check for:

* RBAC
* Roles
* ClusterRoles
* RoleBindings
* Service Accounts
* Secrets
* Security Contexts
* Privileged containers
* Root containers
* Network Policies

## Kubernetes Observability

Check for:

* Metrics
* Logs
* Prometheus
* Grafana
* CloudWatch
* Alerting

---

# 3. CI/CD Health Check

## Source Control

Check for:

* Repository structure
* Branching strategy
* Pull request workflow
* Branch protection
* Code review

## Pipeline

Review:

* Build stages
* Unit tests
* Security scanning
* Docker image builds
* Image publishing
* Deployment
* Approval gates
* Rollback

## CI/CD Security

Check for:

* Hardcoded credentials
* Static AWS access keys
* Repository secrets
* AWS OIDC
* Secret management
* Dependency scanning
* Container scanning
* Infrastructure-as-Code scanning

## Deployment

Check for:

* Kubernetes deployment
* Helm
* GitOps
* Argo CD
* Deployment strategy
* Rollback strategy
* Deployment verification

---

# Security Assessment

Security is assessed across three layers:

```text
AWS
 |
 +-- IAM
 +-- Networking
 +-- Encryption
 +-- Storage
 +-- Monitoring

Kubernetes
 |
 +-- RBAC
 +-- Secrets
 +-- Containers
 +-- Network Policies
 +-- Security Context

CI/CD
 |
 +-- Credentials
 +-- Secrets
 +-- Dependency Scanning
 +-- Container Scanning
 +-- IaC Scanning
```

---

# Cost Optimization Assessment

The assessment also identifies potential AWS cost optimization opportunities.

Areas include:

| Area           | Assessment                          |
| -------------- | ----------------------------------- |
| EC2            | Instance sizing and utilization     |
| EBS            | Unused and oversized volumes        |
| EKS            | Node utilization                    |
| RDS            | Instance and storage sizing         |
| NAT Gateway    | Data processing and architecture    |
| S3             | Storage and lifecycle configuration |
| Load Balancers | Unused resources                    |
| Snapshots      | Retention and unused snapshots      |
| Data Transfer  | Cross-AZ and unnecessary transfer   |
| CloudWatch     | Log retention                       |
| Tagging        | Cost allocation                     |

---

# Finding Severity

Each finding is classified according to its potential impact.

| Severity | Description                                       |
| -------- | ------------------------------------------------- |
| Critical | Immediate security, availability, or data risk    |
| High     | Significant security, reliability, or cost impact |
| Medium   | Important improvement with moderate impact        |
| Low      | Best-practice or optimization improvement         |

---

# Finding Format

Each finding follows a consistent structure.

```text
Finding ID: AWS-IAM-001

Severity: High

Category: Security

Issue:
IAM role has permissions beyond what is required.

Impact:
Excessive permissions increase the potential impact
of a compromised identity.

Recommendation:
Apply least-privilege permissions.

Remediation:
Replace the broad policy with permissions required
by the workload.

Priority: P1

Status: Open
```

---

# Example Findings

## AWS-IAM-001 — Excessive IAM Permissions

**Severity:** High

**Category:** Security

**Issue:**

An IAM role contains permissions that are broader than the workload requires.

**Recommendation:**

Review the permissions and implement least-privilege access.

---

## AWS-NET-001 — Unrestricted Security Group Access

**Severity:** Critical

**Category:** Network Security

**Issue:**

A security group allows inbound traffic that is broader than required.

**Recommendation:**

Restrict inbound access to the required ports and trusted sources.

---

## AWS-COST-001 — Unused EBS Volumes

**Severity:** Medium

**Category:** Cost Optimization

**Issue:**

Unattached EBS volumes are consuming storage without providing application value.

**Recommendation:**

Validate the volumes and remove or archive them where appropriate.

---

# Example Kubernetes Findings

## K8S-RES-001 — Missing Resource Requests and Limits

**Severity:** High

**Category:** Reliability

**Issue:**

Production workloads do not define appropriate CPU and memory requests and limits.

**Impact:**

This can result in:

* Unpredictable scheduling
* Resource contention
* Node instability
* Poor autoscaling behavior

**Recommendation:**

Define requests and limits based on observed workload requirements.

---

## K8S-HA-001 - Insufficient Application Replicas

**Severity:** High

**Category:** Availability

**Issue:**

A critical workload is configured with a single replica.

**Recommendation:**

Deploy multiple replicas and distribute them appropriately across the cluster.

---

## K8S-SEC-001 — Container Running as Root

**Severity:** High

**Category:** Security

**Issue:**

An application container runs with root privileges.

**Recommendation:**

Configure the workload to run as a non-root user using Kubernetes security contexts.

---

# Example CI/CD Findings

## CICD-SEC-001 - Static AWS Credentials

**Severity:** Critical

**Category:** CI/CD Security

**Issue:**

Long-lived AWS credentials are used by the CI/CD pipeline.

**Recommendation:**

Use GitHub Actions OIDC with an appropriately scoped AWS IAM role.

---

## CICD-REL-001 — Missing Rollback Strategy

**Severity:** High

**Category:** Deployment Reliability

**Issue:**

The deployment pipeline does not provide a defined automated rollback mechanism.

**Recommendation:**

Implement deployment verification and a documented rollback procedure.

---

# Remediation Process

The project follows this remediation workflow:

```text
Identify
   ↓
Assess Impact
   ↓
Prioritize
   ↓
Design Remediation
   ↓
Implement
   ↓
Validate
   ↓
Document
   ↓
Monitor
```

---

# Infrastructure as Code

Terraform is used to demonstrate infrastructure provisioning and remediation.

```text
terraform/
├── providers.tf
├── variables.tf
├── outputs.tf
├── vpc.tf
├── iam.tf
├── eks.tf
├── rds.tf
├── s3.tf
└── monitoring.tf
```

The Terraform implementation demonstrates:

* AWS infrastructure provisioning
* Infrastructure as Code
* Reusable configuration
* IAM configuration
* Networking
* EKS
* RDS
* Monitoring

---

# Kubernetes Remediation

Kubernetes manifests are used to demonstrate remediation.

```text
kubernetes/
├── namespace.yaml
├── deployment.yaml
├── service.yaml
├── ingress.yaml
├── configmap.yaml
├── secret.yaml
├── hpa.yaml
├── pdb.yaml
└── network-policy.yaml
```

Example remediation areas include:

* Resource requests and limits
* Health probes
* Multiple replicas
* Security contexts
* Rolling updates
* Pod disruption budgets
* Network policies

---

# CI/CD Implementation

GitHub Actions is used to demonstrate the CI/CD workflow.

```text
.github/
└── workflows/
    ├── terraform.yml
    ├── security-scan.yml
    └── application-deploy.yml
```

Pipeline:

```text
Git Push
   ↓
Lint
   ↓
Unit Tests
   ↓
Security Scan
   ↓
Docker Build
   ↓
Container Scan
   ↓
Push Image
   ↓
Deploy
   ↓
Health Check
   ↓
Deployment Verification
```

---

# Observability

The project demonstrates monitoring across AWS, Kubernetes, and the application layer.

```text
AWS
 |
 +-- CloudWatch
 +-- AWS Metrics
 +-- AWS Logs

Kubernetes
 |
 +-- Prometheus
 +-- Grafana
 +-- Kubernetes Metrics

Application
 |
 +-- Logs
 +-- Metrics
 +-- Alerts
```

---

# Before and After

The final portfolio will compare the environment before and after remediation.

| Area            | Before                         | After                 |
| --------------- | ------------------------------ | --------------------- |
| IAM             | Excessive permissions          | Least privilege       |
| Security Groups | Broad access                   | Restricted access     |
| EC2             | Potential over-provisioning    | Right-sized           |
| EBS             | Unused volumes                 | Validated and cleaned |
| Kubernetes      | Missing resource configuration | Requests and limits   |
| Kubernetes      | Insufficient replicas          | Improved availability |
| Kubernetes      | Missing probes                 | Health probes         |
| CI/CD           | Static credentials             | OIDC                  |
| CI/CD           | Limited security checks        | Automated scanning    |
| Deployment      | Manual recovery                | Defined rollback      |
| Monitoring      | Limited visibility             | Actionable monitoring |

The actual before/after values will be based on the demonstration environment and will not be fabricated.

---

# Deliverables

The completed project will contain:

## Assessment Report

```text
docs/
└── assessment-report.md
```

The report will contain:

* Executive summary
* Architecture overview
* Findings
* Severity classification
* Security assessment
* Reliability assessment
* Cost assessment
* Recommendations
* Remediation roadmap

## Architecture Documentation

```text
docs/
└── architecture.md
```

## Remediation Plan

```text
docs/
└── remediation-plan.md
```

## Runbook

```text
docs/
└── runbook.md
```

## Evidence

```text
evidence/
├── before/
└── after/
```

Evidence may include:

* AWS CLI output
* Kubernetes command output
* Terraform plans
* CI/CD execution results
* Monitoring screenshots
* Cost comparison

No credentials, secrets, private keys, customer information, or proprietary employer information should be committed to this repository.

---

# Repository Structure

```text
aws-cloudops-healthcheck/
│
├── README.md
│
├── docs/
│   ├── architecture.md
│   ├── assessment-report.md
│   ├── remediation-plan.md
│   └── runbook.md
│
├── terraform/
│   ├── providers.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── vpc.tf
│   ├── iam.tf
│   ├── eks.tf
│   ├── rds.tf
│   └── monitoring.tf
│
├── kubernetes/
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml
│   ├── configmap.yaml
│   ├── secret.yaml
│   ├── hpa.yaml
│   ├── pdb.yaml
│   └── network-policy.yaml
│
├── .github/
│   └── workflows/
│       ├── terraform.yml
│       ├── security-scan.yml
│       └── application-deploy.yml
│
├── scripts/
│   ├── aws-health-check.sh
│   ├── eks-health-check.sh
│   └── cost-check.sh
│
├── evidence/
│   ├── before/
│   └── after/
│
└── LICENSE
```

---

# Skills Demonstrated

This project demonstrates practical experience in:

* AWS
* CloudOps
* DevOps
* SRE
* Amazon EKS
* Kubernetes
* Terraform
* Infrastructure as Code
* GitHub Actions
* CI/CD
* DevSecOps
* IAM
* AWS Networking
* Cloud Security
* Cloud Cost Optimization
* FinOps
* Observability
* Prometheus
* Grafana
* Automation
* Reliability Engineering
* Technical Documentation

---

# Project Roadmap

## Phase 1 — Environment Design

* Define the fictional client environment
* Design the AWS architecture
* Define the EKS architecture
* Define the CI/CD architecture
* Define the assessment criteria
* Define realistic issues to evaluate

## Phase 2 — Infrastructure

* Build the AWS infrastructure
* Configure the required AWS services
* Deploy EKS
* Deploy sample workloads
* Configure CI/CD
* Configure monitoring

## Phase 3 — Assessment

* Perform AWS health check
* Perform EKS health check
* Perform CI/CD health check
* Perform security assessment
* Perform cost assessment
* Record findings

## Phase 4 — Remediation

* Fix selected AWS issues
* Fix Kubernetes issues
* Improve CI/CD security
* Improve observability
* Apply cost optimizations

## Phase 5 — Validation

* Validate remediation
* Capture evidence
* Compare before and after
* Document results

## Phase 6 — Portfolio

* Finalize assessment report
* Finalize architecture documentation
* Finalize remediation documentation
* Add evidence
* Publish the project

---

# Disclaimer

This repository is a portfolio and demonstration project.

The client, application, infrastructure, findings, and configurations are created for demonstration purposes.

No confidential information, production credentials, proprietary code, or employer/customer infrastructure is included.

---

# About

I am a CloudOps / DevOps / SRE engineer focused on building reliable, secure, scalable, and cost-efficient cloud platforms.

My areas of focus include:

* AWS
* Kubernetes / EKS
* Terraform
* CI/CD
* DevSecOps
* CloudOps
* SRE
* Observability
* FinOps
* Automation

---

## Reliable. Secure. Automated. Cost-Optimized.
