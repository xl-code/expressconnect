# Limits {#concept_jyz_dxq_ydb .concept}

Before using Express Connect, we recommend that you understand the limits.

|Resource|Default limit|
|:-------|:------------|
|Maximum number of VBRs that can be created on a physical connection|5|
|Maximum number of physical connections that an account can access at an access point|2|
|Maximum number of idle VBRs \(VBRs without interfaces\) under an account|5|
|Maximum number of peering connections that can be created for a VPC|10|
|Maximum number of peering connections that can be created for a VBR|10|
|Maximum number of peering connections that can be created by an account|20|
|Maximum number of route entries that can be added to a VBR|48|
|Maximum number of BGP route entries that can be accepted by a VBR|110|
|We recommend that you use private CIDR blocks for a VBR and VPC to communicate with each other. The CIDR blocks cannot conflict with each other.|
|After you use Express Connect to connect VBRs or VPCs, you cannot use CEN any more.|
|If you use dual physical connections to access Alibaba Cloud, you must configure health check so that traffic is distributed to the standby link when the active link fails.|

