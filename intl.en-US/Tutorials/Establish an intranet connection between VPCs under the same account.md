# Establish an intranet connection between VPCs under the same account {#concept_wrx_vbr_ydb .concept}

This tutorial guides you to use Express Connect to connect two VPCs under the same account.

**Note:** If you use Express Connect to connect two VPCs for the first time, we recommend that you use CEN. For more information, see [Tutorial overview](../../../../../intl.en-US/Quick Start/Tutorial overview.md#).

## Example {#section_ock_bcr_ydb .section}

This tutorial takes the following two VPCs as an example to show how to achieve VPC intranet interconnection by using Express Connect.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108711411702_en-US.png)

## Prerequisites {#section_kdw_xbr_ydb .section}

Make sure that the CIDR blocks of the VPCs or VSwitches to be interconnected do not conflict with each other.

## Step 1 Create a peering connection {#section_ldw_xbr_ydb .section}

To create a peering connection, complete these steps:

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select a region.

    In this tutorial, select **China \(Qingdao\)**.

4.  Click **Create Peering Connection**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108711511683_en-US.png)

5.  Configure the peering connection.

    The following are the configurations used in this tutorial.

    -   **Connection Type**: Select **VPC-to-VPC**.

    -   **Router Creation**: Select **Create Initiator and Acceptor**.

        The system sets the local VPC as the initiator and the peer VPC as the acceptor and automatically connect the initiator to the acceptor.

    -   **Local Region**: Select the region where the VPC is located. In this tutorial, select **China \(Qingdao\)**.

    -   **VPC ID**: Select the VPC, that is, the initiator. In this tutorial, select **VPC1**.

    -   **Peer Region**: Select the region where the VPC to connect is located. In this tutorial, select **China \(Beijing\)**.

    -   **Peer VPC ID**: Select the VPC to connect. In this tutorial, select **VPC2**.

    -   **Bandwidth**: Select the bandwidth of the VPC interconnection. In this tutorial, select **2Mb**.

6.  Click **Buy Now** to complete the payment.
7.  Go back to the VPC Peering Connections page to view the created peering connection.

    If both the initiator and the acceptor are in the Activated status, the connection is successfully established.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108711511684_en-US.png)


## Step 2: Configure the routes {#section_tdw_xbr_ydb .section}

After establishing the peering connection, you must add routes for the interconnected VPCs.

To configure the routes, complete these steps:

1.  On the VPC Peering Connections page, find the created peering connection.
2.  Click the **Route Settings** option under the initiator instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108711511686_en-US.png)

3.  Click **Add Route Entry**, enter the CIDR block of the VPC or VSwitch to connect, and click **Confirm**.

    In this tutorial, enter the CIDR block of the peer VPC, that is, 172.16.0.0/16.

4.  Click the **Route Settings** option under the acceptor instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108711511700_en-US.png)

5.  Click **Add Route Entry**, enter the CIDR block of the VPC or VSwitch to connect, and click **Confirm**.

## Step 3: Configure security groups {#section_zx1_ndf_hfb .section}

After establishing the peering connection between the two VPCs, you also need to configure security group rules so that ECS instances in the two VPCs can communicate with each other.

This tutorial uses ECS instances and security group configurations in the following table as an example.

|Configurations|Account A|Account A|
|:-------------|:--------|:--------|
|Account ID|AccountID\_A|AccountID\_A|
|ECS instance ID|InstanceID\_A|InstanceID\_B|
|Security group ID|SecurityGroupID\_A|SecurityGroupID\_B|

You can view the account ID in the [Account Center](https://account.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.39.4cb94bd3LoJmJ3#/secure).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108711513186_en-US.png)

To configure security groups, complete these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Networks and Security** \> **Security Groups**.
3.  Select the region of the target instance.
4.  Find the target security group and then click **Add Rules**.
5.  On the Security Group Rules page, click **Add Security Group Rule**.
6.  Configure the security group rule, select the protocol type and enter the port range.

    **Note:** For cross-region VPC interconnection, select the CIDR block authorization type and enter the CIDR block of the peer VPC.

    If you select the security group authorization type, make sure that the VPCs are in the same region.

    In this tutorial, select the CIDR block authorization type.


## Step 4 Test the connection {#section_hj4_55m_cfb .section}

After establishing the peering connection and adding routes, you can log on to an ECS instance in one VPC, and ping the private IP of an ECS instance in the peer VPC. If you can successfully ping the private IP, the two VPCs have been successfully connected.

