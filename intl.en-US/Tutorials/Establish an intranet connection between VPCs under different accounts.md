# Establish an intranet connection between VPCs under different accounts {#concept_wrx_vbr_ydb .concept}

This tutorial guides you to use Express Connect to connect two VPCs under different accounts.

**Note:** If you use Express Connect to connect two VPCs for the first time, we recommend that you use CEN. For more information, see [Tutorial overview](../../../../intl.en-US/Quick Start/Tutorial overview.md#).

## Example {#section_ock_bcr_ydb .section}

To connect VPCs under different accounts, you must create the initiator and acceptor respectively, establish a peering connection and configure the routes. This tutorial takes the following two VPCs as an example. VPC1 under account A acts as the initiator and VPC2 under account B acts as the acceptor.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154108716211706_en-US.png)

## Prerequisites {#section_kdw_xbr_ydb .section}

-   You have obtained the Alibaba Cloud account ID of the peer end and the VRouter ID of the VPC to connect.
-   Make sure that the CIDR blocks of the VPCs or VSwitches to be interconnected do not conflict with each other.

## Step 1 Create the initiator {#section_ldw_xbr_ydb .section}

To create the initiator, complete these steps:

1.  Use account A to log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com).
2.  In the left-side navigation pane, click**VPC Peering Connections** \> **VPC-to-VPC**.
3.  Click **Create Peering Connection**.
4.  Configure the peering connection.

    The following are the configurations used in this tutorial.

    -   **Account**: Select **Different Account**.

    -   **Connection Type**: Select **VPC-to-VPC**.

    -   **Router Creation**: Select **Create Initiator Only**.

        Only the initiator can actively initiate the connection.

    -   **Local Region**: Select the region of the VPC. In this tutorial, select **China \(Qingdao\)**.

    -   **VPC ID**: Select the VPC for which the initiator instance is created. In this tutorial, select **VPC1**.

    -   **Peer Region**: Select the region where the VPC to connect is located. In this tutorial, select **China \(Beijing\)**.

    -   **Bandwidth**: Select the bandwidth of the interconnection. In this tutorial, select **2Mb**.

5.  Click **Buy Now** to complete the payment.
6.  Go back to the VPC Peering Connections page to view the created initiator instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15410871624203_en-US.png)


## Step 2 Create the acceptor {#section_ugv_m3n_cfb .section}

To create the acceptor, complete these steps:

1.  Use account B to log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com).
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Click **Create Peering Connection**.
4.  Configure the peering connection.

    The following are the configurations used in this tutorial.

    -   **Account**: Select **Different Account**.

    -   **Connection Type**: Select **VPC-to-VPC**.

    -   **Router Creation**: Select **Create Acceptor Only**.

    -   **Local Region**: Select the region where the VPC is located. In this tutorial, select **China \(Beijing\)**.

    -   **VPC ID**: Select the VPC for which the acceptor instance is created. In this tutorial, select **VPC2**.

    -   **Peer Region**: Select the region where the VPC to connect is located. In this tutorial, select **China \(Qingdao\)**.

    -   **Bandwidth**: The bandwidth of the acceptor is decided by the initiator. In this tutorial, select **Default**.

5.  Click **Buy Now** and complete the payment.
6.  On the VPC Peering Connections page, view the created acceptor instance, and record the ID of the created acceptor instance \(the instance ID in this tutorial is ri-2zeix2q86uoyisagyz0pn\).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15410871624204_en-US.png)


## Step 3 Add the initiator {#section_w2d_l3f_hfb .section}

After creating the initiator and the acceptor, you must add the initiator for the acceptor.

To add the initiator for the acceptor, complete these steps:

1.  Use account B to log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com).
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select the region of the acceptor.

    In this tutorial, select **China \(Beijing\)**.

4.  Find the created acceptor instance and click **Add Initiator**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154108716213085_en-US.png)

5.  On the Add Instance page, select **No**, and enter the initiator router interface \(In this tutorial, the interface ID is ri-m5e33r3n78zyi5573kf85\). Click **OK**.

## Step 4 Add the acceptor and establish a peering connection {#section_b4x_zgr_ydb .section}

After adding the initiator and acceptor, the initiator can actively initiate the connection to establish a peering connection between the two VPCs.

In this tutorial, the initiator is the VPC under account A. To establish the peering connection, complete these steps:

1.  Use account A to log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com).
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select the region of the initiator instance.

    In this tutorial, select **China \(Hangzhou\)**.

4.  Click **Add Acceptor**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154108716211720_en-US.png)

5.  On the Add Instance page, select **No**, and enter the acceptor router interface \(In this tutorial, the interface ID is ri-2zeix2q86uoyisagyz0pn\). Click **OK**.
6.  Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108716211689_en-US.png)** \> **Initiate Connection**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154108716213014_en-US.png)

    After the connection is successfully established, the status of the initiator and acceptor becomes activated.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108716211684_en-US.png)


## Step 5 Configure the routes {#section_tdw_xbr_ydb .section}

After establishing the peering connection, you must add routes for the interconnected VPCs.

To configure the routes, complete these steps:

1.  Use account A to log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com).
2.  On the VPC Peering Connections page, find the created peering connection.
3.  Find the initiator instance and click **Route Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154108716213123_en-US.png)

4.  Click **Add Route Entry**, enter the CIDR block of the VPC or VSwitch to connect, and click **Confirm**.

    In this tutorial, enter the CIDR block of the peer VPC, that is, 172.16.0.0/16.

5.  Use account B to log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com).
6.  Find the acceptor instance and click **Route Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154108716211721_en-US.png)

7.  Click **Add Route Entry**, enter the CIDR block of the VPC or VSwitch to connect, and click **Confirm**.

    In this tutorial, enter the CIDR block of the peer VPC, that is 192.168.0.0/16.


## Step 6 Configure security groups  {#section_zx1_ndf_hfb .section}

After establishing the peering connection between the two VPCs, you also need to configure security group rules so that ECS instances in the two VPCs can communicate with each other.

This tutorial uses ECS instances and security group configurations in the following table as an example.

|Configurations|Account A|Account B|
|:-------------|:--------|:--------|
|Account ID|AccountID\_A|AccountID\_B|
|ECS instance ID|InstanceID\_A|InstanceID\_B|
|Security group ID|SecurityGroupID\_A|SecurityGroupID\_B|

You can view the account ID in the [Account Center](https://account.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.39.4cb94bd3LoJmJ3#/secure).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154108716313186_en-US.png)

To configure security groups, complete these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Networks and Security** \> **Security Groups**.
3.  Select the region of the target instance.
4.  Find the target security group and then click **Add Rules**.
5.  On the Security Group Rules page, click **Add Security Group Rule**.
6.  Configure the security group rule, select the protocol type and enter the port range. Then select the authorization type according to the following information.

    |Scenario|Authorization type|Configuration|
    |:-------|:-----------------|:------------|
    |Cross-region VPC interconnection|CIDR block|The CIDR block of the peer VPC.|
    |Same-region VPC interconnection|Security group|The ID of the security group associated with the peer ECS instance.**Note:** If the VPCs to be interconnected belong to different accounts, select to allow other accounts. In the Account ID field, select the peer account ID.

|

    **Note:** 

    -   If the VPCs to be interconnected are in different regions, select the CIDR block authorization type and enter the CIDR block of the peer VPC. In this tutorial, select the CIDR block authorization type.
    -   If the VPCs to be interconnected are in the same region, select the security group authorization type. In cross-account interconnection, select **Allow Other Accounts**. In the Account ID field, select the peer account ID.

## Step 7 Test the connection {#section_hj4_55m_cfb .section}

After establishing the peering connection and adding routes, you can log on to an ECS instance in one VPC, and ping the priviate IP of an ECS instance in the peer VPC. If you can successfully ping the private IP, the two VPCs have been successfully connected.

