
# **[OIC Landing Zone Extension](#)**
## **An OCI Open LZ [Workload Extensions](#) to Reduce Your Time-to-Production**
 <img src="../../commons/images/icon_oic.png" height="70">

&nbsp; 

## **1. Introduction**
Welcome to the **OIC Landing Zone Extension**.

The OIC Landing Zone Extension is a secure cloud environment, designed with best practices to simplify the on-boarding of Oracle  workloads and enable the continuous operations of their cloud resources. This reference architecture provides an automated landing zone configuration.
&nbsp;

## **2. Design Overview**
This workload extension uses the [One-OE](https://github.com/oci-landing-zones/terraform-oci-open-lz/tree/master/blueprints/one-oe) Blueprint as the reference Landing Zone and guides the deployment of OIC on top of it.

&nbsp;

## **3. Deployment**

These are the required steps to provision the OIC landing zone extension:

 1. It's required to already have deployed an OCI Landing Zone. In this guide we will build on top of the One-OE LZ with Hub model A Light option. Any other OCI landing zone, such as a [CIS landing zone](https://github.com/oci-landing-zones/oci-cis-landingzone-quickstart), [OCI Core Landing Zone](https://github.com/oci-landing-zones/terraform-oci-core-landingzone) or [Multi-OE](https://github.com/oci-landing-zones/oci-landing-zone-operating-entities/tree/master/blueprints/multi-oe/generic_v1/runtime), can also used as a baseline landing zone as well.
 2. Deploy the base infrastructure from the [Step 1 - OIC Extension](1_oic_extension/)
 3. Deploy **OIC** in [Step 2 - OIC](2_oic/)

## License <!-- omit from toc -->

Copyright (c) 2025 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](/LICENSE) for more details.