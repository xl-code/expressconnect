# Use Express Connect to achieve nearby access and one-point access to global resources {#concept_hvl_gt5_ydb .concept}

## Overview {#section_ip3_jt5_ydb .section}

Express Connect helps you build high-quality and high-reliability intranet communication between local data centers and VPCs in different regions of Alibaba Cloud. Express Connect has the following key features:

-   VPC interconnection

    Express Connect supports intranet communication between two VPCs regardless of their regions and accounts. Same-region VPC interconnection is free of charge.

    Alibaba Cloud creates a [Router Interface](../../../../reseller.en-US/Product Introduction/Router interfaces.md#) on each VRouter of the two VPCs, respectively, to achieve secure, reliable, fast, and convenient communication between the two VPCs. For more information, see [VPC interconnection](../../../../reseller.en-US/Tutorials/Establish an intranet connection between VPCs under the same account.md#).

-   Physical access

    You can use a leased line to physically connect your local date center to Alibaba Cloud, and create a VBR and router interfaces to achieve communication between the local data center and a VPC in Alibaba Cloud. For more information, see [Physical access](../../../../reseller.en-US/Tutorials/Connect a local data center to a VPC through a physical connection.md#).


## Nearby access {#section_izk_lt5_ydb .section}

When using a leased line to connect a local data center to a VPC, you only need to select an access point nearest to the local data center, and do not need to build a physical line between the local data center and the VPC. 其中接入点分为阿里云自有接入点和合作伙伴接入点。

阿里云自有接入点

You can obtain information about access points through [The map about Express Connect](https://yq.aliyun.com/articles/241520?spm=a2c4e.11153959.blogcont368231.16.33ac6045hxh6eY) or [Leased line access points](https://vpc.console.aliyun.com/expressConnect?spm=a2c4e.11153959.blogcont368231.17.33ac6045hxh6eY&accounttraceid=3512b7e0-7a11-42a7-b7fd-35d79a06c895#/physicalConnection/cn-beijing/apply) on the Express Connect console. If there is an access point in the city where the local data center is located, you can directly apply for leased line access to the access point.

![](images/4239_en-US.png)

合作伙伴接入点

合作伙伴的接入点已经提前和阿里云建立了专线连接，您只需要在本地IDC和合作伙伴接入点间建立专线连接就可以实现本地IDC和云上VPC间的内网互连。 您可以参考高速通道控制台的[合作伙伴信息](https://vpc.console.aliyun.com/expressConnect?spm=a2c4e.11153959.blogcont368231.17.33ac6045hxh6eY&accounttraceid=3512b7e0-7a11-42a7-b7fd-35d79a06c895#/physicalConnection/cn-beijing/partnerApply)，并联系阿里云合作伙伴获取专线接入的相关信息。

If there is no access point in the city where your local data center is located, you can select a nearby access point and establish connection between the local data center and the access point.

For example, a user has a local data center in Beijing and a local data center in Tianjin, respectively, the user can achieve physical access through the following methods:

-   Because there is an access point in Beijing, the user only needs to connect the local data center in Beijing to the Alibaba Cloud Beijing access point.
-   Because there is no access point in Tianjin, but the local data center is near to the Alibaba Cloud Beijing access point, the user can use a leased line to connect the local data center in Tianjin to the Alibaba Cloud Beijing access point.
-   廊坊既没有阿里云的自有接入点，也没有合作伙伴接入点，由于位于廊坊的IDC距离阿里云北京接入点距离较近，该用户可以使用专线把位于廊坊的IDC和阿里云北京接入点连接。

**Note:** In the following figure, only the lines in orange need to be constructed by a carrier.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13864/15382996564240_en-US.png)

## Access global resources from one point {#section_ir5_b55_ydb .section}

By connecting to any one access point, you can connect your resources to Alibaba Cloud VPCs around the globe through the access point.

For example, a user wants to connect a local data center in Beijing to a VPC in Beijing and a VPC in Shenzhen through physical access. The user only need to use a leased line to connect the local data center to the Alibaba Cloud Beijing access point, and create two router interfaces respectively connecting to the two VPCs on the VBR.

**Note:** In the following figure, only the lines in orange need to be constructed by a carrier.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13864/15382996566214_en-US.png)

