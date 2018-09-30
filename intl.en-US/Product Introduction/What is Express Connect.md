# What is Express Connect {#concept_ipg_pry_xdb .concept}

Express Connect creates private network channels between two VPCs and between a VPC and an on-premises IDC, enhancing the flexibility of network topology as well as the quality and security of cross-network communication. Express Connect also avoids unstable network quality common in public networks and prevents data leakage.

## Functions {#section_fhs_vmq_ydb .section}

Express Connect provides the following functions:

-   Build an intranet connection between two VPCs

    Express Connect supports intranet communication between two VPCs in the same region or different regions, and under the same account or different accounts.

    Alibaba Cloud creates a Route interface on the VRouter of each VPC. It then uses the two interfaces and its own backbone transmission network to build Express Connect, easily realizing secure, reliable, convenient, and fast communication between the two VPCs.

-   Build an intranet connection between two a VPC and a local IDC

    You can connect an on-premises IDC to a VPC through Physical connection on the physical layer, and create Virtual border router and Router interface to connect the on-premises IDC to the VPC.


## Architecture {#section_ykv_ymq_ydb .section}

Based on the layer-3 overlay technology and switch virtualization technology under the Software Defined Network \(SDN\) architecture, Alibaba cloud isolates the ports of the physical leased lines of a customer and abstracts the ports into virtual border routers \(VBRs\). Using main-stream tunneling technology, Alibaba Cloud encapsulates the packets of the customer in VSwitches and then uses the tunneling technology to further encapsulate the packets and transmit them to the VPC.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13811/15382982764200_en-US.jpg)

## Compare Express Connect with public network {#section_pbm_44q_ydb .section}

VPC is an isolated network environment. Communication between two VPCs or between a VPC and local IDC is achieved by different networks.

The communication quality, cost, and security of the way by using a public network is inferior to those of the way by using Express Connect, as shown in the following table:

|Items|Public network| Express Connect|
|:----|:-------------|:---------------|
|Communication quality and availability|The quality of long-distance public network communication is affected by a variety of factors, making it hard to ensure latency stability and low packet loss rate.|Alibaba Cloud's high-quality infrastructure delivers enhanced link quality and availability:-   Delay jitter does not exceed 20%
-   Encapsulation success rate is not lower than 99.8%
-   Availability is not lower than 99.95%
-   Packet loss rate is lower than  0.2%

|
|Cost|You must pay traffic fee or bandwidth fee for using a public network.| The fee for cross-region communication is more affordable.

 Additionally, same-region VPC intercommunication is free of charge.

 |
|Security|There is risk of data leakage on a public network.|Based on the virtualization technology of Alibaba Cloud, Express Connect isolates different communication links, so the security is enhanced.|

