
# **[EBS Landing Zone Extension](#)**
## **An OCI Open LZ [Workload Extensions](#) to Reduce Your Time-to-Production**
 <img src="../../commons/images/icon_ebs.jpg" height="70">

&nbsp; 

## **1. Introduction**
Welcome to the **EBS Landing Zone Extension**.

The EBS Landing Zone Extension is a secure cloud environment, designed with best practices to simplify the on-boarding of E-Business Suite workloads and enable the continuous operations of their cloud resources. This reference architecture provides an automated landing zone configuration.
&nbsp;

## **2. Design Overview**
This workload extension uses the [One-OE](https://github.com/oracle-quickstart/terraform-oci-open-lz/tree/master/blueprints/one-oe) Blueprint as the reference Landing Zone and guides the deployment of EBS on top of it.
&nbsp;

## **3. Deployment**

These are the required steps to provision the EBS landing zone extension:

 1. The [One-OE](https://github.com/oracle-quickstart/terraform-oci-open-lz/tree/master/blueprints/one-oe) LZ is a requirement and needs to be deployed before continuing, in this example we are choosing One-Stack Deployment with CIS Level 1 Security Controls + Hub model A (no cost version). Any other OCI landing zone, such as a [CIS landing zone](https://github.com/oci-landing-zones/oci-cis-landingzone-quickstart), [OCI Core Landing Zone](https://github.com/oci-landing-zones/terraform-oci-core-landingzone) or [Multi-OE](https://github.com/oci-landing-zones/oci-landing-zone-operating-entities/tree/master/blueprints/multi-oe/generic_v1/runtime), can be deployed as a baseline landing zone but may require some minor customizations.
 2. Deploy the **foundation infrastructure**. Follow the guide in [Step 1](/1_foundation/)
 3. Deploy **EBS Cloud Manager** in [Step 2](2_ebscm/)

## Acknowledgments <!-- omit from toc -->
* **Authors**: *Richard Hibbert* (Landing Zones Specialist) 
* **Contributors**: *Paola Juárez* (Landing Zones Specialist)
&nbsp;

## License <!-- omit from toc -->

Copyright (c) 2025 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](/LICENSE) for more details.