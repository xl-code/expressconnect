# Establish an intranet connection between VPCs under different accounts {#concept_wrx_vbr_ydb .concept}

This tutorial illustrates how to use Express Connect to connect two VPCs under different accounts.

## Example {#section_ock_bcr_ydb .section}

The following are two VPCs used in this tutorial.

|Configuration|Account A|Account B|
|:------------|:--------|:--------|
|VPC ID|vpc-12345678（VPC A）|vpc-87654321（VPC B）|
|Region|China \(Beijing\)|China \(Hangzhou\)|
|Router ID|vrt-AAA|1vrt-BBB|
|VPC CIDR Block|192.168.0.0/16|172.16.0.0/12|
|VSwitch CIDR Block|192.168.100.0/24|172.16.100.0/24|

## Prerequisites {#section_kdw_xbr_ydb .section}

-   -   The Alibaba Cloud account IDs and router IDs of the two parties have been obtained.
-   The VSwitch CIDR blocks of the two VPCs cannot conflict with each other.

## Step 1: Create the initiator {#section_ldw_xbr_ydb .section}

Follow these steps to create the initiator router interface in the VPC under account A:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  Click **Create Router Interface**.
4.  Configure the router interface.

    In this tutorial, the following configurations are used:

    -   **Scenario**: Select **VPC Interconnection**.

    -   **Router Creation**: Select **Create Initiator**.

    -   **Local Region**: Select the region where the VPC is located. In this tutorial, select **China \(Beijing\)**.

    -   **VPC ID**: Select the VPC to be connected. In this tutorial, select the ID of VPC A.

    -   **Peer Region**: Select the region where the peer VPC is located. In this tutorial, select **China \(Hangzhou\)**.

    -   **Specification**: Select the specification for the initiator. In this tutorial, select **Large 1**.

5.  Click **Buy Now** to complete the creation.

    Then go back to the Router Interface page after about one minute. Select China \(Beijing\) region. Then you can see the router interface of account A. In this tutorial, ri-AAA is used to represent the router interface ID of account A.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15382987754206_en-US.png)


## Step 2: Create the receiver {#section_npq_lgr_ydb .section}

Follow these steps to create the receiver router interface in the VPC under account B:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  Click **Create Router Interface**.
4.  Configure the router interface.

    In this tutorial, the following configurations are used:

    -   **Scenario**: Select **VPC Interconnection**.

    -   **Router Creation**: Select **Create Receiver**.

    -   **Local Region**: Select the region where the VPC is located. In this tutorial, select **China \(Hangzhou\)**.

    -   **VPC ID**: Select the VPC to be connected. In this tutorial, select the ID of VPC B.

    -   **Peer Region**: Select the region where the peer VPC is located. In this tutorial, select **China \(Beijing\)**.

5.  Click **Buy Now** to complete the creation.

    Then go back to the Router Interface page after about one minute. Select the China \(Hangzhou\) region. Then you can see the router interface of account B. In this tutorial, ri-BBB is used to represent the router interface ID of account B.


## Step 3: Add peer router interfaces and initiate the connection {#section_b4x_zgr_ydb .section}

Follow these steps to add the peer router interface for each router interface and initiate the connection:

1.  Log on to the [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  On the Router Interface page, select **More** \> **Edit Peer Interface** in the **Actions** column of the router interface ri-BBB.
4.  In the displayed dialog box, configure the peer router interface for account B as follows:
    -   **Peer Account ID**: The ID of the peer account.  In this tutorial, enter account A.

    -   **Peer VRouter ID**: The ID of the peer VRouter.  In this tutorial, enter vrt-AAA.

    -   **Peer Router Interface ID**: The ID of the peer router interface.  In this tutorial, enter vrt-AAA.

5.  Repeat the preceding steps to configure the peer router interface for account A.
6.  Return to the router interface page, click **More** \> **Initiate a Connection** in the **Actions** column of the router interface ri-AAA. The connection is established successfully when the status of the router interfaces ri-AAA and ri-BBB changes to **Active**.

## Step 4: Configure the routes {#section_tdw_xbr_ydb .section}

After creating the router interfaces, follow these steps to configure the routes for the two VPCs:

1.  On the Router Interface page, click **Router Configuration** next to the target router interface.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15382987754205_en-US.png)

2.  Click Add Route Entry.
3.  In the displayed dialog box, configure the route according to the following information:
    -   **Destination CIDR Block**: The CIDR Block of the peer VPC.
    -   **Next Hop Type**:  Select **Router Interface**.
    -   **Router Interface**: Select **General Routing** and select a router interface.
4.  Repeat the preceding steps to configure the route for the peer router interface.

    In this tutorial, the router configurations are as follows:

    |Destination CIDR Block|Next Hop Type|Description|
    |:---------------------|:------------|:----------|
    |172.16.100.0/24 \(VSwitch CIDR block of VPC B\)|Router interface of VPC A|Route table configuration of VPC A|
    |192.168.100.0/24 \(VSwitch CIDR block of VPC A\)|Router interface of VPC B|Route table configuration of VPC B|


