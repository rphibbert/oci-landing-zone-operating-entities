# FAQ

## **Table of Contents** <!-- omit from toc -->

- [**1. General**](#1-general)
- [**2. DevOps**](#2-devops)
- [**3. IAM**](#3-iam)
- [**4. Network**](#4-network)
- [**5. Security**](#5-security)
- [**6. Observability**](#6-observability)

&nbsp;

## 1. General

### What are OCI Landing Zones?
OCI Landing Zones are a standardised framework and set of OCI resources that provides a best-practice foundation to build a secure, scalable, and governed OCI tenancy, enabling consistent onboarding of workloads and teams.

### Apart from having a great Drawios, Why having runnable designs (in jsons format) instead ad-hoc power points?
the simple answer is: they work. They match the design in the draw.io blueprints, the best tool to learn network, they're versionable which provides operational security and governance over time (what changed)....


&nbsp;

## 2. DevOps

### Why are JSON Configurations used instead of Code?
After working with hundreds of customers across EMEA, we've learned that configuration-driven approaches scale better than custom development. Most teams can manage JSON files. Far fewer can develop and maintain infrastructure code.
Managing Terraform code directly increases cost and complexity. Our declarative JSON-based model simplifies IaC, reduces the need for specialized expertise, and enables faster deployments. All our assets—blueprints, add-ons, and workload extensions—use this consistent configuration approach, accelerating customer onboarding while maintaining control.

### Why We Recommend Automation Over Console Deployment?
You can implement our Landing Zone designs manually through the OCI Console using our reference architectures (One-OE, Multi-OE, or Multi-Tenancy). But this doesn't scale and introduces operational risk.
Terraform automation lets you deploy and manage hundreds of resources consistently and repeatably. This cuts deployment time, operational costs, and manual effort while reducing human error.
We support both OCI Resource Manager (ORM) and Terraform CLI so customers can adopt automation at their own pace. Plus, you can integrate with CI/CD tools like GitHub, GitLab, and Jenkins for full IaC and enterprise-grade pipelines. This ensures consistency, governance, and long-term efficiency.

### Why Use OCI Landing Zone Terraform Modules?
Over the years, many customers, partners, and internal teams have built their own Terraform code for Landing Zones—duplicating effort and creating maintenance overhead.
OCI Landing Zone Terraform modules are developed by OCI Landing Zone Product Developer teams, led by Nelson Chen. These represent Oracle's recommended approach. They're standardized, aligned with CIS benchmarks, and continuously updated. By adopting them, you eliminate custom code maintenance, reduce operational risk, and get a supported, enterprise-grade foundation.

### Why an IaC automation approach? Landing Zone is a one-time setup, why not manual?
Manual setup is possible, but automation reduces deployment time and avoids human errors. IaC provides a single source of truth for the OCI tenancy infra, making it easy to understand, repeat, audit, and scale. something manual approaches cannot reliably support.

### Why is OCI Resource Manager (ORM) preferred over Terraform CLI?
OCI Resource Manager is a managed Terraform service that securely handles state files, execution, and access control within the OCI tenancy. Actions are performed by authenticated OCI users with proper authorization, reducing security and operational risks. Terraform CLI requires external execution platforms, credential handling, and manual state management, making ORM the more secure and governed option.

&nbsp; 

## 3. IAM

### Why do we use compartments?
Compartments allow to natively reflect best security practices for segregation of duties and resources into logical structure, minimising risk of misconfiguration

### Why do we have Platforms and Projects for workloads?


### Why do we have common Network, Security, and Platform compartments both outside and inside workload environments?
Common compartments host shared services used across multiple workloads (e.g., shared OKE/OCVS). Workload-level compartments host environment-specific resources, enabling clear separation, tighter access control, and better governance.

### Why do we have common Network compartments outside workload environments, and network compartments inside workload env?
Common network compartments holds shared networking components (e.g., Hub VCN, DRG, Firewall) managed centrally. Workload-level network compartments host environment-specific network resources, enabling clear traffic separation, controlled network flows, and segregated access between central network teams and workload owners.

&nbsp;

## 4. Network

### Why do we recommend the Hub & Spoke architecture model?
It enables centralized network management, enhances security, improves traffic visibility, and provides strong isolation and segmentation. Additionally, it is highly scalable, making it well suited for growing and complex environments.

### Why Internet or NAT Gateway are in the Hub and not in the Spokes?
Internet and NAT Gateways are in the Hub VCN to centralize internet ingress and egress for all Spoke VCNs. This design enforces consistent security controls, traffic inspection, and logging. It also reduces the attack surface by preventing direct internet access from Spoke VCNs. Centralizing gateways simplifies operations, governance, and compliance across all workload environments.

### Why did we created the network packet flow animations on the Network Hubs?
They provide step-by-step visualization of how traffic traverses inside the Hub & Spoke architecture, making them an effective self-learning tool, as well as explanatory assets for differnet usecases (customers) presentations. By making these animations publicly available, we enable knowledge sharing at scale.

### Why do we have Network Hubs Menu?
Because we saw reinvention of the wheel over and over in so many SRs, 100 Hubs for 100 similar scenarios (customers), and it was the only way to bring this to an end and create the standardised Hub models. Less effort, less time, more quality. And it works! In addition, the availability of Hubs models, allows us to easily build bespoke Hub models that address specific customer requirements.

### Why (do we have) runnable network?
the simple answer is: they work. They match the design, the best tool to learn network, they're versionable which provides operational security and governance over time (what changed)....

### Why use custom Route Tables and Security Lists?
They provide fine-grained control over traffic routing and network security at the subnet level, enabling precise traffic flows and reducing the risk of inadvertent security exposure.

### Why use Network Security Groups over Security Lists?
They provide more granular traffic filtering and control than security lists and enable the implementation of micro-segmentation for improved security isolation.

### Why to use DRG?
DRG simplifies network architecture by eliminating the need to configure multiple LPGs for VCN interconnection. A single DRG can interconnect hundreds of VCNs (up to 300 VCNs - local and remote). DRG routing policies allow precise control and isolation of traffic between attached networks.

### Why IGs in the Hub and not in the spokes?


### Why did we created the flow animations on the network hubs?
because it's the ultimate tool to self-learn network, step by step, without consuming our teams, and it's available to the whole world, it's the ultimate approach to scale our knowledge.


&nbsp; 

## 5. Security

&nbsp; 

## 6. Observability

### Why Events and Alarms Are Included in Our OCI Operating Entities Blueprints
Production environments need visibility. Without it, you can't ensure reliability, security, or operational readiness.
Our blueprints come with pre-configured events and customizable alarms that monitor critical core components. This means early detection, faster response times, and lower operational risk. We cover security, identity, network, and load balancer health events—catching critical conditions before they affect your business.

### Why VCN Flow Logs Are Essential
Our blueprints enable VCN Flow Logs by default because they're a fundamental security control.
Flow Logs capture traffic metadata that you need for threat detection, traffic analysis, and compliance. Without them, you're flying blind during incidents. No network forensic evidence means you can't identify attackers, assess breach scope, or contain threats effectively. This can drag investigations out for months and create serious business risk.

### Why We Require a Dedicated Bucket for Audit Logs
The default 365-day retention for OCI Audit Logs meets PCI DSS and ISO 27001 requirements. But some organizations face stricter regulations—HIPAA, SOC, FINRA.
Our blueprints implement a dedicated Object Storage bucket with the appropriate Service Connector for secure, long-term audit log retention. This ensures compliance, supports audit readiness, and preserves forensic data for extended investigations.

&nbsp; 

# License

Copyright (c) 2026 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](https://github.com/oracle-devrel/technology-engineering/blob/main/LICENSE) for more details.
