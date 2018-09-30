# Scenarios {#concept_gkk_vwq_ydb .concept}

Express Connect creates private network channels between two VPCs and between a VPC and a local IDC, enhancing the flexibility of network topology as well as the quality and security of cross-network communication.

## Connect two VPCs {#section_ir3_ywq_ydb .section}

You can use Express Connect to achieve private-network communication between two VPCs. Express Connect can avoid the network instability caused by bypassing the public network and eliminate the risk of data theft during transmission.. For more information, see [Establish an intranet connection between VPCs under the same account](../../../../reseller.en-US/Tutorials/Establish an intranet connection between VPCs under the same account.md#) and [Establish an intranet connection between VPCs under different accounts](../../../../reseller.en-US/Tutorials/Establish an intranet connection between VPCs under different accounts.md#).

## Connect a local IDC with a VPC {#section_jr3_ywq_ydb .section}

If your local IDC needs to communicate with a VPC through a private network, you can use the physical connection function of Express Connect to implement private-network communication on both sides. You can build a physical connection by yourself or contact an Alibaba partner to help you build a physical connection. The communication between the on-premises IDC and the VPC by using the physical connection features high quality, high reliability, and high security.  您可以使用高速通道实现两个VPC间的的私网通信需求，既可以避免绕行公网带来的网络质量不稳定问题，也可以免去数据在传输过程中被窃取的风险。 For more information, see [Connect a local data center to a VPC through a physical connection](../../../../reseller.en-US/Tutorials/Connect a local data center to a VPC through a physical connection.md#).

## Two vpcs shared Nat gateways {#section_kr3_ywq_ydb .section}

If two VPCs need to use the same NAT gateway to access a public network, you can also use Express Connect.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13819/15382983754202_en-US.jpg)

