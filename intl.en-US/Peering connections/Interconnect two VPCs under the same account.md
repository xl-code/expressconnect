# Interconnect two VPCs under the same account {#concept_wrx_vbr_ydb .concept}

This topic describes how to use Express Connect to connect two VPCs under the same account.

**Note:** 

-   If this is the first time that you are using Express Connect to interconnect two VPCs, we recommend that you use CEN. For more information, see [Tutorial overview](../../../../../intl.en-US/Quick Start/Tutorial overview.md#).

## Example {#section_ock_bcr_ydb .section}

This topic uses the following two VPCs as an example to show you how to fulfill VPC intercommunication by using Express Connect.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/156113013811702_en-US.png)

## Prerequisites {#section_kdw_xbr_ydb .section}

The CIDR blocks of the VPCs or VSwitches that you want to interconnect do not conflict with each other.

## Step 1: Create a peering connection {#section_ldw_xbr_ydb .section}

To create a peering connection, follow these steps:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select a region.

    In this example, select **China \(Qingdao\)**.

4.  Click **Create Peering Connection**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/156113013911683_en-US.png)

5.  Configure the peering connection.

    Use the following configurations:

    -   **Account Type**: Select **Same as Peer's**.
    -   **Connection Type**: Select **VPC-to-VPC**.

    -   **Routers to Create**: Select **Initiator and Acceptor**.

        The system sets the selected local VPC as the connection initiator, sets the peer VPC as the acceptor, and automatically connects the initiator and the acceptor.

    -   **Local Region**: Select the region of the local VPC. In this example, select **China \(Qingdao\)**.

    -   **Local VPC ID**: Select the local VPC, that is, the initiator of the connection. In this example, select **VPC1**.

    -   **Peer Region**: Select the region of the peer VPC. In this example, select **China \(Beijing\)**.

    -   **Peer VPC ID**: Select the peer VPC to be connected. In this example, select **VPC2**.

    -   **Bandwidth**: Select a bandwidth value for the interconnection. In this example, select **2 Mb**.

6.  Click **Buy Now** and complete the payment.
7.  Go back to the VPC-to-VPC page to check the created peering connection.

    When the initiator and the acceptor are both in the activated state, the connection is established.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/156113013911684_en-US.png)


## Step 2: Configure routes {#section_tdw_xbr_ydb .section}

After establishing the peering connection, you need to add a route for each of the two interconnected VPCs.

To configure the routes, follow these steps:

1.  On the VPC-to-VPC page, find the peering connection you created.
2.  Click **Route Settings** under the initiator instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/156113013911686_en-US.png)

3.  Click **Add Route**, enter the destination CIDR block of the VPC or VSwitch that you want to connect, and then click **Confirm**.

    In this example, enter the CIDR block of the peer VPC: 172.16.0.0/16.

4.  Click **Route Settings** under the acceptor instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/156113013911700_en-US.png)

5.  Click **Add Route**, enter the destination CIDR block, that is, the CIDR block of the local VPC or its VSwitch, and then click **Confirm**.

## Step 3: Configure security groups {#section_zx1_ndf_hfb .section}

After establishing the peering connection between the two VPCs, you need to configure security groups to enable the intercommunication of ECS instances in these two VPCs.

This topic uses the ECS instances and security groups in the following table as an example.

|Configuration|Account A|Account A|
|:------------|:--------|:--------|
|Account ID|AccountID\_A|AccountID\_A|
|ECS instance ID|InstanceID\_A|InstanceID\_B|
|Security group ID|SecurityGroupID\_A|SecurityGroupID\_B|

You can view the account ID in the [Account Center](https://account.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.39.4cb94bd3LoJmJ3#/secure).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/156113014013186_en-US.png)

To configure the security group rule, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, choose **Networks and Security** \> **Security Groups**.
3.  Select the region of the instance.
4.  Find the target security group and then click **Add Rules**.
5.  On the Security Group Rules page, click **Add Security Group Rule**.
6.  Configure the security group rule, select the protocol type, and enter the port range.

    **Note:** For cross-region VPC interconnection, select the CIDR block authorization type and enter the CIDR block of the peer VPC.

    If you select the security group authorization type, make sure that the VPCs are in the same region.

    In this example, select the CIDR block authorization type.


## Step 4: Test the connection {#section_hj4_55m_cfb .section}

After establishing the peering connection and adding the routes, you can log on to an ECS instance of either VPC and ping the IP address of an ECS instance in the other VPC. If the ping succeeds, the connection between the two VPCs is successful.

