# Limits {#concept_jyz_dxq_ydb .concept}

Note the following limits before you use the Express Connect service.

|Item|Default limit|
|:---|:------------|
|The maximum number of VBRs that can be created in a physical connection|5|
|The maximum number of physical connections that an account can access at an access point|2|
|The maximum number of idle VBRs \(VBRs without interfaces\) under an account|5|
|The maximum number of route entries that can be added to a VBR|48|
|The maximum number of BGP route entries that can be accepted by a VBR|110|
|We recommend that you use private CIDR blocks for a VBR and VPC to communicate with each other. The CIDR blocks cannot conflict with each other.|
|If you use dual physical connections to access Alibaba Cloud, you must configure health checks so that traffic is distributed to the standby link when the active link fails.|

