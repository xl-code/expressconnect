# Terms {#concept_ybn_hxq_ydb .concept}

|Term| Description|
|:---|:-----------|
|Express Connect| A data transmission channel powered by Alibaba Cloud infrastructure. It provides secure and reliable intranet-like connections between different networks, such as between VPCs, or between VPCs and on-premises IDCs.|
|Virtual Private Cloud \(VPC\)|A customized private network established on Alibaba Cloud. VPCs are logically isolated from each other. You can create and manage instances, such as ECS, Server Load Balancer, and RDS instances, in a VPC.|
|Physical connection|The abstraction of a physical line used to directly connect an on-premises IDC to Alibaba Cloud. Each line a customer uses to access Alibaba Cloud corresponds to a physical connection object.|
|VRouter|The hub of a VPC, connecting all VSwitches in a VPC and serving as a gateway device that connects the VPC to other networks. It forwards network traffic according to route entries.|
|Virtual border router \(VBR\)|You can create multiple virtual border routers on a physical connection. Each VBR is responsible for forwarding the data of a VLAN in Alibaba Cloud. With VBR, you can transmit your data directly to any region of Alibaba Cloud.|
|Router interface \(RI\)|A router interface \(or VRouter interface\) is a virtual network device. It can be attached to a VRouter to create an Express Connect with another VRouter interface, delivering an intranet connection between different networks.|
|Route table|A route table refers to a list of route entries on the VRouter.|
|Route Entry| Each item in a route table is a route entry. It defines the next hop address of the network.|
|Access point|The geographical location of the end, to which the physical leased line connects, on Alibaba Cloud. An access point belongs to a certain region and has two access devices. When a single region has multiple access points, any of these can be used to access Alibaba Cloud VPCs.|

