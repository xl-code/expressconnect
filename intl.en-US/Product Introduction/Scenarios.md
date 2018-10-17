# Scenarios {#concept_gkk_vwq_ydb .concept}

Express Connect creates private network channels between two VPCs and between a VPC and a local IDC, enhancing the flexibility of network topology as well as the quality and security of cross-network communication.

## Connect two VPCs {#section_ir3_ywq_ydb .section}

You can use Express Connect to achieve private-network communication between two VPCs. Express Connect can avoid the network instability caused by bypassing the public network and eliminate the risk of data theft during transmission.. For more information, see [Establish an intranet connection between VPCs under the same account](../../../../intl.en-US/Tutorials/Establish an intranet connection between VPCs under the same account.md#) and [Establish an intranet connection between VPCs under different accounts](../../../../intl.en-US/Tutorials/Establish an intranet connection between VPCs under different accounts.md#).

## Connect a local IDC with a VPC {#section_jr3_ywq_ydb .section}

If your local IDC needs to communicate with a VPC through a private network, you can use the physical connection function of Express Connect to implement private-network communication on both sides. You can build a physical connection by yourself or contact an Alibaba partner to help you build a physical connection. The communication between the on-premises IDC and the VPC by using the physical connection features high quality, high reliability, and high security. You can use Express Connect to establish intranet communication between two VPCs. Express Connect avoids unstable network quality common in Internet communication and prevents data leakage. For more information, see [Connect a local data center to a VPC through a physical connection](../../../../intl.en-US/Tutorials/Connect a local data center to a VPC through a physical connection.md#).

## Two VPCs share a Nat Gateway {#section_kr3_ywq_ydb .section}

If two VPCs need to use the same NAT Gateway to access the Internet, you can also use Express Connect.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13819/15397427974202_en-US.jpg)

