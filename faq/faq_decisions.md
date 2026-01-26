# FAQ - Decisions

## Technical Questions
## **Contents** <!-- omit from toc -->

- [**1. Security (includes IAM**](#1-security-includes-iam)
- [**2. Network**](#2-network)
- [**3. Operations (includes observability)**](#3-operations-includes-observability)

---

## 1. Security (includes IAM)

### Why do we have a well-defined compartment structure?
Compartments allow for the segregation of resources and access into logical structures, allowning for enforcement of best security best practices.
Compartments play key role in securing OCI tenancies due to their tight integration with OCI IAM, Policy framework and security posture management tools. A well defined compartment structure minimizes the risks of mistakes and misconfigurations.

### Why do we separate workloads into Platforms and Projects?
In general applications fit into two categories: Platform and Projects.
Platforms examples are Kubernetes, VMWare and Exadata are commonly used by many applications and form part of the core of the enterprise setup. Platforms usually have their own operations team and specific networking requirements.
Projects are usually smaller, separated applications or services serving a more specific purpose. 

### Why are there both shared and dedicated workload resources?
The majority of customer applications are environment specific based on the application development lifecycle. Separating applications into their shared and environment specific versions helps to clearly set boundaries for data usage and operational responsibility.

### Why do Identity Domains and Groups improve tenancy security?
Most security frameworks are structured around the segregation of duties to help prevent accidental misconfiguration and limit the available attack surface. High privileged accounts should be managed separately with their own processes to enable secure and proper use.
The blueprints are aligned with industry security best practices like the CIS Benchmark.

### Why do we use Security Zones to limit risk of misconfiguration?
Security Zones work in alongside IAM by specifying operations that are not allowed even if the IAM permissions are granted. This minimizes risk of misconfiguration and ensures that resources in the Security Zones are protected.

### Why do we have Network, Security, and Platform compartments both outside and inside the Environments?
Common compartments host shared services, managed centrally, which will be used across multiple environments and workloads. Examples of these shown below. 
- Network:  Hub VCN, DRG, Firewall, Load Balancers
- Security: Cloud Guard, Vaults & Keys, Security Zones
- Platforms: OKE, OCVS, ExaCS

&nbsp;
Environment compartments host resources within the specified environment, enabling clear separation, tight access control, and effective governance.

---

## 2. Network

### Why do we recommend the Hub & Spoke architecture model?
The Hub & Spoke network architecture enables centralized network management, enhances security, improves traffic visibility, and provides strong isolation and segmentation. It is also highly scalable, making it well suited for any expansion.

### Why are the Internet and NAT Gateways in the Hub VCN and not in the Spoke VCNs?
Internet and NAT Gateways are in the Hub VCN in order to centralize internet ingress and egress for all Spoke VCNs. This design enforces consistent security controls, traffic inspection, and logging. It also reduces the attack surface by preventing direct internet access to the Spoke VCNs. Centralizing gateways simplifies operations, governance, and compliance across all workload environments.

### Why did we create the network packet flow animations on the Network Hubs?
These provide a step-by-step visualization of how the traffic traverses inside the Hub & Spoke architectures, making them an effective learning tool. They are  explanatory assets which help simplify a complex area. By making these animations publicly available, we have enabled knowledge sharing at scale.

### Why do we have a Menu of Network Hub designs?
There is a huge number of potential Network Hub designs but there are also many common elements to the design requirements. 
The Network Hub menu provides standardization of the most common Hub designs. This enables a drastic reduction of effort and time whilst raising quality. Most importantly, the designs work. In addition, the availability of Hubs models enables us to easily tailor the relevant Hub model and address specific customer requirements.

### Why are there custom Route Tables and Security Lists?
They provide fine-grained control over traffic routing and network security at the subnet level. This enables precise traffic flows and reduces the risk of inadvertent security exposure.

### Why use Network Security Groups over Security Lists?
Network Security Groups provide more granular traffic filtering and control than Security Lists and enable the implementation of micro-segmentation for improved security isolation.

### Why do we use a DRG?
The DRG simplifies network architecture by eliminating the need to configure multiple LPGs for VCN interconnection. A single DRG can interconnect hundreds of VCNs (up to 300 VCNs - local and remote). DRG routing policies allow precise control and isolation of traffic between attached networks.

---

## 3. Operations (includes observability)

### Why do you provide runnable designs in JSON format?
The simple answer is that they work. They match the design in the draw.io blueprints.
They are the best tool to learn network, security and observability configuration. They are versionable which provides operational security and governance enabling configuration control.

### Why are JSON Configurations used instead of Code?
With the experience of working with hundreds of customers across EMEA, we've learned that configuration-driven approaches scale better than custom development.
Most teams can manage JSON files. Far fewer can develop and maintain infrastructure code.
Managing Terraform code directly increases cost and complexity. Our declarative JSON-based model simplifies IaC, reduces the need for specialized expertise, and enables faster deployments. All our assets—blueprints, add-ons, and workload extensions—use this consistent configuration approach, accelerating customer onboarding while maintaining control.

### Why We Recommend Automation over manual Console Deployment?
It is possible to implement our Landing Zone designs manually through the OCI Console using our reference architectures (One-OE, Multi-OE, or Multi-Tenancy). But this doesn't scale and introduces operational risk.
Terraform automation lets you deploy and manage the resources in a consistent and repeatable manner. This reduces deployment time, operational costs, and manual effort while also dratically reducing the chance of human error.
For automated depoloyment both OCI Resource Manager (ORM) and Terraform CLI are supported and customers can adopt automation at their own pace. This can be integrated with CI/CD tools like GitHub, GitLab, and Jenkins for full IaC and enterprise-grade pipelines. This ensures consistency, governance, and long-term efficiency.

### Why Use OCI Landing Zone Terraform Modules?
Many customers, partners, and internal teams have built their own Terraform code to help manage Landing Zone deployments, duplicating effort and creating a maintenance overhead.
The OCI Landing Zone Terraform modules are developed supported by the Oracle Product Development teams. These represent Oracle's recommended approach. They're standardized, aligned with CIS benchmarks, and continuously updated. By adopting them, you eliminate custom code maintenance, reduce operational risk, and get a supported, enterprise-grade foundation.

### Why have an IaC automation approach? Landing Zones are a one-time setup, why not implement manually?
Landing Zone setup is rarelt a one time setup as they will evolve over time requiring configuration additions and updates.
Manual setup is possible, but automation reduces deployment time and reduces the chances of human error. IaC provides a single source of truth for the OCI tenancy infrastructure, making it easy to understand, repeat, audit, and scale.

### Why is OCI Resource Manager (ORM) preferred over Terraform CLI?
OCI Resource Manager is a managed Terraform service that securely handles state files, execution, and access control within the OCI tenancy. Actions are performed by authenticated OCI users with proper authorization, reducing security and operational risks. Terraform CLI requires external execution platforms, credential handling, and manual state management, making ORM the more secure and governed option.

### Why are Events and Alarms included in the OCI Operating Entities Blueprints?
Production environments require visibility. Without visibility, you can't ensure reliability, security, or operational readiness.
Our blueprints come with pre-configured events and alarms that monitor the critical core components. This enables early detection, faster response times, and lower operational risk. Events include: Security, Identity, Network, and Load Balancer health. Catching critical conditions before they affect your business.

### Why are VCN Flow Logs essential?
Our blueprints enable VCN Flow Logs by default because they are a fundamental security control.
Flow Logs capture traffic metadata that are needed for threat detection, traffic analysis, and to ensure security compliance. Without them, there will be limited visibility of network access which can be critical in the event of a security incident. Without the detailed forensic network evidence it will very difficult to identify attackers, assess the breach scope, or contain threats effectively.

### Why do we require a dedicated Bucket for Audit Logs
The default 365 day retention of the OCI Audit Logs meets PCI DSS and ISO 27001 requirements. However, some organizations require stricter regulations like for HIPAA, SOC or FINRA.
The blueprints implement a dedicated Object Storage bucket with the appropriate Service Connector for secure, long-term audit log retention. This ensures compliance, supports audit readiness, and preserves forensic data for extended investigations.
