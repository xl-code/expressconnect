# Limits {#concept_jyz_dxq_ydb .concept}

Note the following limits before you use the Express Connect service.

|Item|Quota|Can I apply for an increase to the quota?|
|:---|:----|-----------------------------------------|
|The maximum number of physical connections that an account can establish at an access point|2|Yes. You can apply for an increase to the quota by opening a ticket.|
|The maximum number of Virtual Border Routers \(VBRs\) that can be created in a physical connection|5|Yes. You can apply for an increase to the quota by using the [quota management](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou) function.|
|The maximum number of idle VBRs \(VBRs without interfaces\) under an account|5|No.|
|The maximum number of VBRs that an account can create for other accounts.|2|No.|
|The maximum number of route entries that can be added to a VBR|48|Yes. You can apply for an increase to the quota by using the [quota management](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou) function.|
|The maximum number of BGP route entries that can be accepted by a VBR|110|Yes. You can apply for an increase to the quota by opening a ticket.|
|The number of BGP route entries that can be advertised on each VBR.|10|Yes. You can apply for an increase to the quota by using the [quota management](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou) function.|
|We recommend that you use private CIDR blocks for a VBR and VPC to communicate with each other. The CIDR blocks cannot conflict with each other.|
|If you use dual physical connections to access Alibaba Cloud, you must configure health checks so that traffic is distributed to the standby link when the active link fails.|

