# Interconnect two VPCs under different accounts {#concept_wrx_vbr_ydb .concept}

This tutorial describes how to use Express Connect to connect two VPCs under different accounts.

**Note:** If this is the first time you are using Express Connect to interconnect two VPCs, we recommend that you use CEN. For more information, see [Tutorial overview](../../../../../reseller.en-US/Quick Start/Tutorial overview.md#).

## Example {#section_ock_bcr_ydb .section}

In cross-account VPC interconnection, you need to create an initiator and an acceptor separately, establish a peering connection, and then configure routes. This tutorial uses the following two VPCs as an example. VPC1 under account A acts as the initiator and VPC2 under account B acts as the acceptor.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154745678711706_en-US.png)

## Prerequisites {#section_kdw_xbr_ydb .section}

-   You have obtained the Alibaba Cloud account ID of the peer VPC and the VRouter ID of the VPC.
-   The Classless Inter-Domain Routing \(CIDR\) blocks of the VPCs or VSwitches that you want to interconnect do not conflict.

## Step 1: Create an initiator {#section_ldw_xbr_ydb .section}

Perform the following steps to create an initiator:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri) using the credentials of account A.
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Click **Create Peering Connection**.
4.  Configure the peering connection.

    Use the following configurations:

    -   **Account**: Select **Different from Peer's**.

    -   **Connection Type**: Select **VPC-to-VPC**.

    -   **Routers to Create**: Select **Create Initiator**.

        Only the initiator can initiate the connection to the acceptor.

    -   **Local Region**: Select the region of the VPC. In this example, select **China \(Qingdao\)**.

    -   **Local VPC ID**: Select the VPC for which the initiator instance is created. In this example, select **VPC1**.

    -   **Peer Region**: Select the region where the VPC to be connected is located. In this example, select **China \(Beijing\)**.

    -   **Specification**: Select a bandwidth for the interconnection. In this example, select **2 Mb**.

5.  Click **Buy Now** and complete the payment.
6.  Go back to the VPC Peering Connections page to check the created initiator instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15474567874203_en-US.png)


## Step 2: Create an acceptor {#section_ugv_m3n_cfb .section}

Perform the following steps to create an acceptor:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri) using the credentials of account B.
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Click **Create Peering Connection**.
4.  Configure the peering connection.

    Use the following configurations:

    -   **Account**: Select **Different from Peer's**.

    -   **Connection Type**: Select **VPC-to-VPC**.

    -   **Routers to Create**: Select **Acceptor Only**.

    -   **Local Region**: Select the region of the VPC. In this example, select **China \(Beijing\)**.

    -   **Local VPC ID**: Select the VPC for which the acceptor instance is created. In this example, select **VPC2**.

    -   **Peer Region**: Select the region where the VPC to be connected is located. In this example, select **China \(Qingdao\)**.

    -   **Specification**: The acceptor bandwidth depends on the initiator bandwidth. In this example, select **Default**.

5.  Click **Buy Now** and complete the payment.
6.  On the VPC Peering Connections page, check the created acceptor instance and note down its ID. In this example, the acceptor instance ID is ri-2zeix2q86uoyisagyz0pn.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15474567874204_en-US.png)


## Step 3: Add the initiator {#section_w2d_l3f_hfb .section}

After creating an initiator and an acceptor, you must add the initiator for the acceptor.

Perform the following steps to add the initiator for the acceptor:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri) using the credentials of account B.
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select the region of the acceptor.

    In this example, select **China \(Beijing\)**.

4.  Find the created acceptor instance and click **Add Initiator**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154745678713085_en-US.png)

5.  On the Add Instance page, select **Another Account** and enter the initiator router interface. In this example, enter ri-m5e33r3n78zyi5573kf85. Click **OK**.

## Step 4: Add the acceptor and establish a peering connection {#section_b4x_zgr_ydb .section}

After you add the initiator and the acceptor, the initiator can actively initiate and establish a peering connection between the two VPCs.

In this example, the connection initiator is VPC1 under account A. Perform the following steps to establish a peering connection:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri) using the credentials of account A.
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select the region of the initiator instance.

    In this example, select **China \(Qingdao\)**.

4.  Click **Add Acceptor**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154745678711720_en-US.png)

5.  On the Add Instance page, select **Another Account** and enter the acceptor router interface. In this example, enter ri-2zeix2q86uoyisagyz0pn. Click **OK**.
6.  Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154745678711689_en-US.png)** \> **Initiate Connection**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154745678713014_en-US.png)

    When the connection is established, the initiator and the acceptor enter the activated state.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154745678711684_en-US.png)


## Step 5: Configure routes {#section_tdw_xbr_ydb .section}

After establishing a peering connection, you need to add a route for each of the two VPCs.

Perform the following steps to configure the routes:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri) using the credentials of account A.
2.  On the VPC Peering Connections page, find the created peering connection.
3.  Find the initiator instance and click **Route Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154745678713123_en-US.png)

4.  Click **Add Route Entry**, enter the CIDR block of the VPC or VSwitch to be connected, and click **Confirm**.

    In this example, enter the CIDR block of the peer VPC: 172.16.0.0/16.

5.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri) using the credentials of account B.
6.  Find the acceptor instance and click **Route Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/154745678711721_en-US.png)

7.  Click **Add Route Entry**, enter the CIDR block of the VPC or VSwitch to be connected, and click **Confirm**.

    In this example, enter the CIDR block of the peer VPC: 192.168.0.0/16.


## Step 6: Configure security groups {#section_zx1_ndf_hfb .section}

After establishing a peering connection between two VPCs, you need to configure security groups to enable the intercommunication of ECS instances in these two VPCs.

This tutorial uses the ECS instances and security groups in the following table as an example.

|Configuration|Account A|Account B|
|:------------|:--------|:--------|
|Account ID|AccountID\_A|AccountID\_B|
|ECS instance ID|InstanceID\_A|InstanceID\_B|
|Security group ID|SecurityGroupID\_A|SecurityGroupID\_B|

You can view the account ID in the [Account Center](https://account.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.39.4cb94bd3LoJmJ3#/secure).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154745678813186_en-US.png)

Perform the following steps to configure the security group rule:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, click **Networks and Security** \> **Security Groups**.
3.  Select the region of the instance.
4.  Find the target security group and then click **Add Rules**.
5.  On the Security Group Rules page, click **Add Security Group Rule**.
6.  Configure the security group rule, select the protocol type, and enter the port range. Then select the authorization type according to the following information.

    |Scenario|Authorization type|Description|
    |:-------|:-----------------|:----------|
    |Cross-region VPC interconnection|CIDR block|The CIDR block of the peer VPC.|
    |Same-region VPC interconnection|Security group|The ID of the security group associated with the peer ECS instance.**Note:** If the VPCs to be interconnected belong to different accounts, select Allow Other Accounts and in the Account ID field, enter the peer account ID.

|

    **Note:** 

    -   If the VPCs to be interconnected are in different regions, select the CIDR block authorization type and enter the CIDR block of the peer VPC. In this example, select the CIDR block authorization type.
    -   If the VPCs to be interconnected are in the same region, select the security group authorization type. In cross-account interconnection, select **Allow Other Accounts** and in the Account ID field, enter the peer account ID.

## Step 7: Test the connection {#section_hj4_55m_cfb .section}

After establishing the peering connection and adding routes, you can log on to an ECS instance of either VPC and ping the IP address of an ECS instance in the other VPC. If the ping succeeds, the connection between the two VPCs is successful.

