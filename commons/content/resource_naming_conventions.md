# RESOURCE NAMING CONVENTIONS

## **Table of Contents** <!-- omit from toc -->

- [**1. Introduction**](#1-introduction)
- [**2. Genral**](#2-general-naming-convention)
- [**3. IAM Resources**](#3-iam-resources)
  - [**3.1 Compartments**](#31-compartments)
  - [**3.2 Groups**](#32-groups)
  - [**3.3 Policies**](#33-policies)
- [**4. Network Resources**](#4-network-resources)
  - [**4.1 VCNs**](#41-vcns)
  - [**4.2 Subnets**](#42-subnets)
  - [**4.3 Route Tables**](#43-route-tables)
  - [**4.4 Security Lists**](#44-security-lists)
  - [**4.5 Network Security Groups**](#45-network-security-groups)
  - [**4.6 Internet Gateways**](#46-internet-gateways)
  - [**4.7 NAT Gateways**](#47-nat-gateways)
  - [**4.8 Service Gateways**](#48-service-gateways)
  - [**4.9 Dynamic Routing Gateways**](#49-dynamic-routing-gateways)
  - [**4.10 DRG Attachments**](#410-drg-attachments)
  - [**4.11 DRG Route Distributions**](#411-drg-route-distributions)
  - [**4.12 DRG Route Tables**](#412-drg-route-tables)
  [**5. List of Resource Types**](#5-list-of-resource-types)

&nbsp; 

## 1. Introduction

A resource naming convention helps to identify resources, their type, and location by the name, quickly. If you don't have any naming convention in place, we recommend using the following principles:

1. **Segmented Names**: Segments of the name are separated by "-". Within a name segment do not use &lt;space&gt; and ".".
2. **Intuitive Names**: Where possible intuitive/standard abbreviations should be considered (e.g., use "shared" instead of "shared.cloud.team"). Use simple rules such as "p" for production, or "np" for non-production, for a clear identification of the resource scope.
3. **Intuitive Grouping**: Use the technical scope (e.g., production environment) and functional scope (e.g., LoB, Department) to aggregate resources and resource groups.
4. **Intuitive Hierarchy**: Compartment names should reflect their hierarchy (environment -&gt; projects -&gt; workload layer).

&nbsp; 

## 2. General Naming Convention

One-OE Example:\
&lt;resource_type&gt;-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;workload&gt;


&lt;resource_type&gt;
| Name | Description |
|---|---|
| cmp | IAM: Compartment
| vcn | Network: Virtual Cloud Network


&lt;landing_zone&gt;
| Name | Short Name | Description |
|---|---|---|
| landingzone | lz | Production Landing Zone
| landingzonenp | lznp | Non-Production Landing Zone (optional)

&lt;environment&gt;
| Name | Short Name | Description |
|---|---|---|
| prod | p | Production Environment
| preprod | pp | Pre-Production Environment
| test | t | Test Environment
| dev | d | Development Environment

> [!NOTE]
> The longer names like prod and preprod are used in the naming as this is considered important information, the short name is used in the DNS Labels.

&lt;region&gt;
| Name | Short Name | Description |
|---|---|---|
| Frankfurt | fra | Germany Central (Frankfurt) Region

> [!NOTE]
> The Frankfurt region is used throughout the provided templates.\
> For a list of all the available regions and their short names (Region Key) see [here](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/regions.htm)


&lt;resource_type&gt;
| Name | Short Name | Description |
|---|---|---|
| platform | plat | Platform Workload Resources
| project | proj | Project Workload Resources
| network | net | Network Resources
| security | sec | Security Resources

&lt;workload&gt;
| Name | Description |
|---|---|
| oke | Oracle Kubernetes Engine
| ebs | Oracle E-Business Suite

&lt;access_type&gt;
| Name | Description |
|---|---|
| admin | Administrators
| read | Read Only

&nbsp; 

## 3. IAM Resources

### 3.1 Compartments

#### Naming Convention
cmp-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;workload&gt;

#### Examples
| Name | Short Name | Object Name | Description |
|---|---|---|---|
| cmp-landingzone | cmp-lz-… | CMP-LANDINGZONE-KEY | Enclosing (Production) | 
| cmp-lz-network || CMP-LZ-NETWORK-KEY | Network | 
| cmp-lz-platform || CMP-LZ-PLATFORM-KEY | Platform |
| cmp-lz-project || CMP-LZ-PROJECT-KEY | Project | 
| cmp-lz-prod || CMP-LZ-PROD-KEY | Production Environment | 
| cmp-lz-preprod || CMP-LZ-PREPROD-KEY | Pre-Production Environment | 
| cmp-lz-prod-proj1 || CMP-LZ-PROD-PROJ1-KEY | Production Environment "proj1" Workload | 
| cmp-landingzonenp | cmp-lznp-… | CMP-LANDINGZONENP-KEY | Enclosing (Non-Production) | 

### 3.2 Groups

#### Naming Convention
grp-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;resource_type&gt;-&lt;workload&gt;-&lt;access_type&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| grp-iam-admin | GRP-IAM-ADMIN-KEY | Tenancy IAM Administrators |
| grp-security-admin | GRP-SECURITY-ADMIN-KEY | Tenancy Security Administrators |
| grp-lz-network-admin | GRP-LZ-NETWORK-ADMIN-KEY | Production Landing Zone Network Administrators |
| grp-lz-security-admin | GRP-LZ-SECURITY-ADMIN-KEY| Production Landing Zone Security Administrators |
| grp-lz-platform-admin | GRP-LZ-PLATFORM-ADMIN-KEY | Platform Workload Administrators |
| grp-lz-prod-proj1-admin | GRP-LZ-PROD-PROJ1-ADMIN-KEY | Production Environment, "proj1" Project Workload Administrators |
| grp-lz-preprod-proj1-admin | GRP-LZ-PREPROD-PROJ1-ADMIN-KEY | Pre-Production Environment, "proj1" Project Workload Administrators |

### 3.3 Policies

#### Naming Convention
pcy-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;resource_type&gt;-&lt;workload&gt;-&lt;access_type&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| pcy-services | PCY-SERVICES-KEY | Tenancy Services |
| pcy-iam-admin | PCY-IAM-ADMIN-KEY | Tenancy IAM Administration |
| pcy-security-admin | PCY-SECURITY-ADMIN-KEY | Tenancy Security Administration |
| pcy-lz-network-admin | PCY-LZ-NETWORK-ADMIN-KEY | Production Landing Zone Network Administration |
| pcy-lz-security-admin | PCY-LZ-SECURITY-ADMIN-KEY | Production Landing Zone Security Administration |
| pcy-lz-prod-proj1-admin | PCY-LZ-PROD-PROJ1-ADMIN-KEY | Production Environment, "proj1" Project Workload Administration |
| pcy-lz-preprod-proj1-admin | PCY-LZ-PREPROD-PROJ1-ADMIN-KEY | Pre-Production Environment, "proj1" Project Workload Administration |

&nbsp; 

## 4. Network Resources

### 4.1 VCNs

#### Naming Convention
vcn-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;workload&gt;

#### Examples
| Name | Object Name | DNS Label | Description |
|---|---|---|---|
| vcn-fra-lz-hub | VCN-FRA-LZ-HUB-KEY | vcnfralzhub | Hub Virtual Network |
| vcn-fra-lz-prod-projects | VCN-FRA-LZ-PROD-PROJECTS-KEY | vcnfralzpproj | Production Environment shared Virtual Network |
| vcn-fra-lz-preprod-projects | VCN-FRA-LZ-PREPROD-PROJECTS-KEY | vcnfralzppproj | Pre-Production Environment shared Virtual Network |

### 4.2 Subnets

#### Naming Convention
sn-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;subnet_type&gt;

#### Examples
| Name | Object Name | DNS Label | Description |
|---|---|---|---|
| sn-fra-lz-hub-fw-dmz | SN-FRA-LZ-HUB-FW-DMZ-KEY | snfrahubfwdmz | Hub Subnet for External Firewall |
| sn-fra-lz-prod-web | SN-FRA-LZ-PROD-WEB-KEY | snfrapweb | Production Environment shared Web Subnet |
| sn-fra-lz-preprod-web | SN-FRA-LZ-PREPROD-WEB-KEY | snfrappweb | Pre-Production Environment shared Web Subnet |

> [!NOTE]
> It is not necessary to have "lz" in the DNS Label for the subdomain name. It’s already included in the VCN dns-label eg: snfrahubfwdmz.vcnfra**lz**hub.oraclevcn.com

### 4.3 Route Tables

#### Naming Convention
rt-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;resource_type&gt;-&lt;type&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| rt-fra-lz-hub-ingress | RT-FRA-LZ-HUB-INGRESS-KEY | Hub VCN Ingress Routing |
| rt-fra-lz-prod-prj-gen | RT-FRA-LZ-PROD-PRJ-GEN-KEY | Production Shared VCN, Subnets Generic Routing |
| rt-fra-lz-preprod-prj-gen | RT-FRA-LZ-PREPROD-PRJ-GEN-KEY | Pre-Production Shared VCN, Subnets Generic Routing |

### 4.4 Security Lists

#### Naming Convention
sl-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;resource_type&gt;-&lt;type&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| sl-fra-lz-hub-fw-dmz | SL-FRA-LZ-HUB-FW-DMZ-KEY | Hub External Firewall Subnet Security List |
| sl-fra-lz-prod-prj-gen | SL-FRA-LZ-PROD-PRJ-GEN-KEY | Production Shared VCN, Subnets Generic Security List |
| sl-fra-lz-preprod-prj-gen | SL-FRA-LZ-PREPROD-PRJ-GEN-KEY | Pre-Production Shared VCN, Subnets Generic Security List |

### 4.5 Network Security Groups

#### Naming Convention
nsg-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;workload&gt;-&lt;subnet_type&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| nsg-fra-lz-hub-fw-dmz | NSG-FRA-LZ-HUB-FW-DMZ-KEY | Hub External Firewall Network Security Group |
| nsg-fra-lz-prod-proj1-web | NSG-FRA-LZ-PROD-PROJ1-WEB-KEY | Production Shared VCN, "Proj1" Web Network Security Group |
| nsg-fra-lz-preprod-proj1-web | NSG-FRA-LZ-PREPROD-PROJ1-WEB-KEY | Pre-Production Shared VCN, "Proj1" Web Network Security Group |

### 4.6 Internet Gateways

#### Naming Convention
igw-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| igw-fra-lz-hub | IGW-FRA-LZ-HUB-KEY | Hub VCN Internet Gateway |

### 4.7 NAT Gateways

#### Naming Convention
ngw-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| ngw-fra-lz-hub | NGW-FRA-LZ-HUB-KEY | Hub VCN NAT Gateway |

### 4.8 Service Gateways

#### Naming Convention
sgw-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;-&lt;resource_type&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| sgw-fra-lz-hub | SGW-FRA-LZ-HUB-KEY | Hub VCN Service Gateway |
| sgw-fra-lz-prod-proj | SGW-FRA-LZ-PROD-PROJ-KEY | Production VCN Service Gateway |
| sgw-fra-lz-preprod-proj | SGW-FRA-LZ-PREPROD-PROJ-KEY | Pre-Production VCN Service Gateway |

### 4.9 Dynamic Routing Gateways

#### Naming Convention
drg-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| drg-fra-lz-hub | DRG-FRA-LZ-HUB-KEY | Hub Dynamic Routing Gateway |

### 4.10 DRG Attachments

#### Naming Convention
drgatt-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| drgatt-fra-lz-hub | DRGATT-FRA-LZ-HUB-KEY | Hub VCN DRG Attachment |
| drgatt-fra-lz-prod-projects | DRGATT-FRA-LZ-PROD-PROJECTS-KEY | Production VCN DRG Attachment |
| drgatt-fra-lz-preprod-projects | DRGATT-FRA-LZ-PREPROD-PROJECTS-KEY | Production VCN DRG Attachment |

### 4.11 DRG Route Distributions

#### Naming Convention
drgrd-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| drgrd-fra-lz-hub | DRGRD-FRA-LZ-HUB-KEY | Hub VCN DRG Import Route Distribution |

### 4.12 DRG Route Tables

#### Naming Convention
drgrt-&lt;region&gt;-&lt;landing_zone&gt;-&lt;environment&gt;

#### Examples
| Name | Object Name | Description |
|---|---|---|
| drgrt-fra-lz-hub | DRGRT-FRA-LZ-HUB-KEY | Hub VCN DRG Route Table |
| drgrt-fra-lz-spokes | DRGRT-FRA-LZ-SPOKES-KEY | Spoke VCNs DRG Route Table |

&nbsp;

## 5. List of Resource Types


| RESOURCE TYPE  |  ABREVIATION | 
|---|---|
| Agent | agt | 
| Alarm | al |
| API Gateway |apigw |
| Autonomous Container Database (Dedicated) | adbc 
| Autonomous Database (Transaction Processing) | atp 
| Autonomous Data Warehouse | adw 
| Autonomous Exadata Infrastructure | aei 
| Autonomous JSON Database | ajd 
| Autonomous Database with APEX | apx 
| Bastion Service | bst |
| Bucket | bkt |
| Block Volume | blk |
| Cloud Guard Recipe (cloned) | cg-act, cg-cfg|
| Cloud Guard Responder (cloned) | cg-rsp |
| Cloud Guard Target | cg-tgt |
| Compartment | cmp |
| Container Repository | cir |
| Customer Premise Equipment | cpe |
| Database on VM | db |
| Database Backup | dbb |
| Database Backup Destination | dbbd |
| Database Connection | dbc |
| Database Home | dbh |
| Database Key Store | dks |
| Database Node | dbn |
| Database Pluggable Database | pdb |
| Database Server | dbs |
| Database Software Image | dbi |
| Database System | dbsys |
| DNS Endpoint Forwarder | dnsepf |
| DNS Endpoint Listener | dnsepl |
| Dynamic Group | dgp |
| Dynamic Routing Gateway | drg |
| Dynamic Routing Gateway Attachment | drgatt |
| Event Rule | rul |
| ExaCS Infrastructure | ecsi |
| ExaCS VMCluster Cloud | ecsvmc |
| Exadata Cloud@Customer Infrastructure | ecci |
| Exadata Cloud@Customer VMCluster | eccvmcls |
| Exadata Cloud@Customer Operator Control | eccop |
| Exadata Cloud@Customer Operator Control Assignment | eccopasgn |
| Exadata Cloud@Customer Operator Control Access Request | eccopreq |
| External Database | edb |
| External Container Database | edbc |
| External Pluggable Container Database | epdb |
| External Non-Container Database | edbn |
| External Database Connector | edbc |
| Fast Connect | fc# &lt;# := 1...n&gt; |
| File Storage | fss |
| Function | fun |
| Group | grp |
| Internet Gateway | igw |
| Load Balancer | lb |
| Location (Three-letter region code)| ams, fra, etc. |
| Log | log |
| Log Groups | lgrp |
| NAT Gateway | nat |
| Network Security Group | nsg |
| Notification Topic | nott |
| Managed key | key |
| OCI Function Application | fn |
| Object Storage Bucket | bkt |
| Policy | pcy |
| Routing Table | rt |
| Secret | sec |
| Security List | sl |
| Security Zone Recipe | sz-rcp |
| Security Zone Target | sz-tgt |
| Service Gateway | sgw |
| Service Connector Hub | sch |
| Stream | str |
| Subnet | sn |
| Tenancy | tcy |
| Vault | vlt |
| Virtual Cloud Network | vcn |
| Virtual Machine | vm |
| Vulnerability Scanning Recipe - Container | vss-recc |
| Vulnerability Scanning Recipe - Host | vss-rech |
| Vulnerability Scanning Target | vss-tgt |

&nbsp; 

# License

Copyright (c) 2025 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](https://github.com/oracle-devrel/technology-engineering/blob/main/LICENSE) for more details.
