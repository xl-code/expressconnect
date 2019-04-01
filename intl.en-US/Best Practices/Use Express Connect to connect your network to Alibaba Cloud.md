# Use Express Connect to connect your network to Alibaba Cloud {#concept_hvl_gt5_ydb .concept}

## Overview {#section_ip3_jt5_ydb .section}

Express Connect allows you to implement a highly reliable intranet communication between your on-premises data center and Alibaba Cloud VPC, and between VPCs that are based in different regions. Specifically, Express Connect provides the following two key features:

-   VPC-to-VPC connection

    Express Connect supports intranet communication between two VPCs regardless of the regions they are based or the accounts under which they are billed. The connection between two VPCs that are based in the same region is provided free of charge, whereas the connection between two VPCs that are based in different regions incurs fees

    To implement a connection between VPCs, Alibaba Cloud creates a Router Interface \(RI\) on the VRouter of each of the two VPCs, and uses its own backbone transmission network to achieve secure, reliable, and fast communication between the two VPCs. For more information, see [VPC interconnection](../../../../../reseller.en-US/Getting Started (New Console)/Interconnect two VPCs under the same account.md#).

-   Physical connection

    You can use a leased line to physically connect your on-premises data center to Alibaba Cloud. After that, you can create a VBR and RIs to achieve communication between the on-premises data center and a VPC in Alibaba Cloud. For more information, see [Connect an on-premises data center to a VPC through a physical connection](../../../../../reseller.en-US/Getting Started (New Console)/Connect an on-premises IDC to a VPC through a physical connection.md#).


## Access points {#section_izk_lt5_ydb .section}

If you use a leased line to connect an on-premises data center to an Alibaba Cloud VPC, you only need to select an access point that is closest in geographic proximity to your on-premises data center. You do not need to build a physical connection between your on-premises data center and Alibaba Cloud VPC.

Access points include Alibaba Cloud access points and access points provided by Alibaba Cloud partners.

-   Alibaba Cloud access points

    You can view all [access points](https://vpc.console.aliyun.com/expressConnect?spm=a2c4e.11153959.blogcont368231.17.33ac6045hxh6eY&accounttraceid=3512b7e0-7a11-42a7-b7fd-35d79a06c895#/physicalConnection/cn-beijing/apply) of Alibaba Cloud in the Express Connect console. If an access point is available in the city where your on-premises data center is located, you can directly select this access point for the leased line connection.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13864/15541155474239_en-US.png)

-   Access points of Alibaba Cloud partners

    Some access points are also provided by Alibaba Cloud partners, and are connected with Alibaba Cloud through dedicated physical lines. This means that if no Alibaba Cloud access point is available, you can select an access point provided by one of our partners. To obtain the information about your selected physical connection, contact the Alibaba Cloud partner.

    As a best practice, if no Alibaba Cloud access point or access point provided by an Alibaba Cloud partner is available directly in the city where your on-premises data center is located, we recommend that you select an access point that is nearest to the city where your on-premises data center is based.

    For example, the following figure shows two on-premises data center centers \(one in Beijing, one in Langfang\) connected to an Alibaba Cloud access point based in Beijing. Additionally, the figure shows an on-premises data center located in Tianjin that is connected to Alibaba Cloud VPC through a leased line connected to the access point of an Alibaba Cloud partner. Note that the lines in yellow are leased lines that need to be installed by your service provider.

    **Note:** .

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13864/15541155474240_en-US.png)


## Access global resources from one point {#section_ir5_b55_ydb .section}

By connecting to any one access point, you can connect your resources to Alibaba Cloud VPCs around the globe through the access point.

For example, you want to connect an on-premises data center in Beijing to a VPC in Beijing and a VPC in Shenzhen through physical connection. To implement that, you only need to use a leased line to connect the on-premises data center to an Alibaba Cloud Beijing access point, and create two RIs respectively connecting to the two VPCs on the VBR.

**Note:** In the following figure, only the lines in yellow need to be installed by your service provider.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13864/15541155476214_en-US.png)

