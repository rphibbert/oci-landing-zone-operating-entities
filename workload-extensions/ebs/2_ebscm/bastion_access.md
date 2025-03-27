# Bastion Acess <!-- omit from toc -->

## **Table of Contents** <!-- omit from toc -->

- [**1. Summary**](#1-summary)
- [**2. Setup IAM Configuration**](#2-setup-iam-configuration)
  - [**2.1. Compartments**](#21-compartments)
  - [**2.2 Groups**](#22-groups)
  - [**3.4 Dynamic groups**](#34-dynamic-groups)
  - [**2.3 Policies**](#23-policies)
- [**3. Setup Network Configuration**](#3-setup-network-configuration)

## **1. Summary**

Whilst deploying resources to OCI we may have the situation where the connectivity to the internet or to on-premise is not available.
In order to access the deployed services in this situation we can utilze the Bastion service.

This document will outline the necessary steps to access the EBS Cloud Manager and E-Business Suite environments.

&nbsp; 

## **2. EBS Cloud Manager Deployment**

To deploy EBS Cloud Manager the next step is to create and configure the EBS Cloud Manager compute instance.

The detailed steps for this are documented [here](https://docs.oracle.com/cd/E26401_01/doc.122/f35809/T679330T679339.htm#T680521)

The following are the initial resources for deploying the EBS Cloud Manager compute instance from Marketplace:

| Resource | Name |
| --- | --- |
| Compartment | cmp-lzp-platform-ebscm |
| Virtual Cloud Network | vcn-fra-lzp-m-ebs |
| Subnet | sn-fra-lzp-m-ebs-app |

The following are some of the resources required to be selected in the Oracle E-Business Suite Cloud Manager Configure Script:

| Resource | Name |
| --- | --- |
| Group | grp-lzp-platform-ebscm-admins |
| Load Balancer Visibility Type | Private |
| Load Balancer Subnet | sn-fra-lzp-m-ebs-lb |

> [!NOTE]
> The EBS Landing Zone Extension includes both Security Lists and Network Security Groups so that either may be utilized.


&nbsp;

# License <!-- omit from toc -->

Copyright (c) 2025 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](/LICENSE.txt) for more details.
