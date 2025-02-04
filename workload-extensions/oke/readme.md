# **[OKE Landing Zone Extension](#)**   <!-- omit from toc -->
## **An OCI Open LZ [Workload Extensions](#) to Reduce Your Time-to-Production**  <!-- omit from toc -->

 <img src="../../commons/images/icon_oke.jpg" height="100">

## **1. Introduction**
Welcome to the **OKE Landing Zone Extension**.

The OKE Landing Zone Extension is a secure cloud environment, designed with best practices to simplify the on-boarding of OKE workloads and enable the continuous operations of their cloud resources. This reference architecture provides an automated landing zone configuration.
&nbsp;

## **2. Design Overview**
This workload extension uses the [One-OE](https://github.com/oracle-quickstart/terraform-oci-open-lz/tree/master/blueprints/one-oe) Blueprint as the reference Landing Zone and guides the deployment of OKE on top of it.
&nbsp;

## **3. Deployment**

These are the required steps to provision the OKE landing zone extension:

 1. The [One-OE](https://github.com/oracle-quickstart/terraform-oci-open-lz/tree/master/blueprints/one-oe) LZ is a requirement and needs to be deployed before continuing, in this example we are choosing One-Stack Deployment with CIS Level 1 Security Controls + Hub model A (no cost version). Any other OCI landing zone, such as a [CIS landing zone](https://github.com/oci-landing-zones/oci-cis-landingzone-quickstart), [OCI Core Landing Zone](https://github.com/oci-landing-zones/terraform-oci-core-landingzone) or [Multi-OE](https://github.com/oci-landing-zones/oci-landing-zone-operating-entities/tree/master/blueprints/multi-oe/generic_v1/runtime), can be deployed as a baseline landing zone but maybe be required some minor customizations.
 2. Deploy the **foundation infrastructure**. Follow the guide in [Step 1](/1_foundation/)
 3. Create **OKE clusters** in [Step 2](2_oke/)

## Acknowledgments <!-- omit from toc -->
* **Authors**: *Paola Juárez* (Landing Zones Specialist) 
* **Contributors**: *Peter Hrvola* (Landing Zones Specialist), *Bala Sunil* (Landing Zones Specialist), *Alberto Campagna* ( Application Development DevOps Specialist) 
&nbsp;

## License <!-- omit from toc -->

Copyright (c) 2025 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](/LICENSE) for more details.
