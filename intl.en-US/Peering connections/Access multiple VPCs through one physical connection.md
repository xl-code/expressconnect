# Access multiple VPCs through one physical connection {#concept_p1l_rk5_ydb .concept}

You can use a physical connection that is already connected to an access point of Alibaba Cloud to connect multiple VPCs. This topic describes how to use a physical connection to connect your on-premises data center with two VPCs that belong to different accounts.

**Note:** Currently, a physical connection can be used by five VPCs at most. You can open a ticket to increase the quota.

## Scenario {#section_d52_1l5_ydb .section}

This topic takes the network architecture in the following figure as an example. A company registers account A on Alibaba Cloud and creates VPC-A. The company creates a physical connection under account A to connect its on-premises data center \(172.16.0.0/12\) with VPC-A. A subsidiary of the company registers account B on Alibaba Cloud and creates VPC-B under account B. The subsidiary wants to connect VPC-B to the on-premises data center.

Because the company has purchased a physical connection under account A and connected the on-premises data center to an access point of Alibaba Cloud, account B of the subsidiary can also use this physical connection to connect the VPC under account B to the on-premises data center.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/15646388014227_en-US.png)

In this topic, the VPC and physical connection configurations are as follows:

|Account A|Account B|
|:--------|:--------|
|Account ID: 12345678|Account ID: 87654321|
|VPC -   Name: VPC-A
-   Region: China \(Beijing\)
-   VPC ID: vpc-12345678
-   CIDR block: 10.10.0.0/16

 |VPC -   Name: VPC-B
-   Region: China \(Hangzhou\)
-   VPC ID: vpc-87654321
-   CIDR block: 192.168.0.0/16

 |
|Physical connection -   VBR name: VPC-Beijing
-   VBR ID: vbr-12345678
-   Physical connection ID: pc-AAA
-   VLAN ID: 1000

 |None|

## Overview {#section_ary_zzb_mgb .section}

To connect VPC-B under account B to the on-premises data center by using the physical connection and VBR of account A, you only need to establish a peering connection between the VBR and VPC-B.

1.  [Step 1: Create an initiator](#section_gxd_jsr_ggb) 

    In VBR-to-VPC peering connections, the VBR must be the initiator. In this topic, create a router interface for the VBR by using account A and use the router interface as the connection initiator.

2.  [Step 2: Create an acceptor](#section_lpm_wl5_ydb) 

    Create a router interface for the VRouter of the VPC to be connected and use the router interface as the connection acceptor.

3.  [Step 3: Add the acceptor and the initiator to establish a peering connection](#section_ij3_fpb_mgb) 

    Add the acceptor and the initiator respectively for the created router interfaces, and then initiate the connection from the initiator.

4.  [Step 4: Configure route entries](#section_f4d_z45_ydb) 

    Add routes to the connection devices of the VPC, VBR, and on-premises data center respectively to forward traffic.

5.  [Step 5: Perform an acceptance test \(optional\)](#section_njh_gr5_ydb) 

    After the network is connected, you can test the speed of the physical connection to check whether the bandwidth meets your service needs.


## Prerequisites {#section_d34_x3r_ggb .section}

The on-premises data center is connected with VPC-A of account A through the physical connection. For more information, see [../../../../dita-oss-bucket/SP\_72/DNexpressconnect1847151/EN-US\_TP\_13831.md\#](../../../../intl.en-US/Getting Started (New Console)/Connect an on-premises data center to a VPC through a physical connection.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156463880135360_en-US.png)

## Step 1: Create an initiator {#section_gxd_jsr_ggb .section}

To create an initiator, follow these steps:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list) by using the credentials of account A.
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC** and then click **Create Peering Connection**.
3.  Configure the peering connection.

    The configurations in this topic are as follows. For more information, see [Interconnect a VPC and a VBR](../../../../intl.en-US/Peering connections/Interconnect a VPC and a VBR.md#).

    -   **Account type**: Select **Different from Peer's**.
    -   **Connection Type**: Select **VBR-to-VPC**.
    -   **Routers to Create**: Select **Create Initiator**.
    -   **Local Region**: Select the region of the created VBR. In this example, select **China \(Beijing\)**.
    -   **Local Access Point**: Select the access point of the physical connection connected to the VBR.
    -   **Local VBR ID**: Select the created VBR.
    -   **Peer Region**: Select the region to which the target VPC belongs. In this topic, select **China \(Hangzhou\)**.
    -   **Bandwidth**: Select the bandwidth for intranet communication. In this topic, select **2Mb**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/15646388014230_en-US.png)

4.  View the created initiator and record the initiator router interface ID.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156463880137535_en-US.png)

## Step 2: Create an acceptor {#section_lpm_wl5_ydb .section}

After the initiator is created, you need to create an acceptor for the VPC to be connected under account B.

To create an acceptor, follow these steps:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list) by using the credentials of account B.
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC** and then click **Create Peering Connection**.
3.  Configure the peering connection.

    The configurations in this topic are as follows. For more information, see [Interconnect a VPC and a VBR](../../../../intl.en-US/Peering connections/Interconnect a VPC and a VBR.md#).

    -   **Account type**: Select **Different from Peer's**.
    -   **Connection Type**: Select **VBR-to-VPC**.
    -   **Routers to Create**: Select **Acceptor Only**.
    -   **Local Region**: Select the region to which the target VPC belongs. In this topic, select **China \(Hangzhou\)**.
    -   **Local VPC ID**: Select the target VPC to be connected. In this topic, select VPC-B.
    -   **Peer Region**: Select the region to which the created VBR belongs. In this topic, select **China \(Beijing\)**.
    -   **Peer Access Point**: Select the access point of the physical connection connected to the VBR.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156463880235392_en-US.png)

4.  View the created acceptor and record the acceptor router interface ID.

## Step 3: Add the acceptor and the initiator to establish a peering connection {#section_ij3_fpb_mgb .section}

To establish a peering connection between VPC-B and the VBR, follow these steps:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list) by using the credentials of account B.
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Select the region of the acceptor, find the target acceptor, and click **Add Initiator**.
4.  On the Add Instance page, complete the following configurations.
    1.  **Account**: Select **Another Account**.
    2.  **Initiator Router Interface**: Enter the router interface ID of the created initiator, for example, ri-1234567.
    3.  Click **OK**.
5.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list) by using the credentials of account A.
6.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC**.
7.  Select the region of the initiator, find the target initiator, and click **Add Acceptor**.
8.  On the Add Instance page, complete the following configurations.
    1.  **Account**: Select **Another Account**.
    2.  **Acceptor Router Interface**: Enter the ID of the created acceptor router interface, for example, ri-1234567.
    3.  Click **OK**.
9.  Click![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156463880237536_en-US.png) in the **Actions** column and then choose **Initiate Connection**.

    The peering connection is established if both the acceptor and the initiator are in the activated state.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156463880135360_en-US.png)


## Step 4: Configure route entries {#section_f4d_z45_ydb .section}

After establishing the peering connection, you must configure routes in the VPC, VBR, and on-premises data center.

**Add route entries in VBR**

To add a route entry to the on-premises data center and VPC respectively, follow these steps:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list) by using the credentials of account A.
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select the region of the VBR and then click the instance ID of the target VBR.
4.  Click the Routes tab and then click **Add Route**.
5.  Follow these steps to add a route that forwards the traffic destined for the on-premises data center \(CIDR block: 172.16.0.0/12\) from the VBR to the physical connection:
    1.  **Destination Subnet**: the CIDR block of the on-premises data center. In this topic, enter 172.16.0.0/12.
    2.  **Next Hop Type**: Select **Physical Connection Interface**.
    3.  **Next hop**: Select the created physical connection.
    4.  Click **OK**.
6.  Click **Add Route** to add one more route that forwards the traffic destined for the VPC \(CIDR block: 192.168.0.0/16\) from the VBR to the VPC.

    1.  **Destination Subnet**: Enter the IP address range of VPC-B. In this topic, enter 192.168.0.0/16.
    2.  **Next Hop Type**: Select **VPC**.
    3.  **Next Hop**: Select the VPC to be connected. In this topic, select VPC-B.
    4.  Click **OK**.
    **Add a route in VPC**

    Follow these steps to add a route that forwards the traffic, destined for the on-premises data center \(CIDR block: 172.16.0.0/12\), from the VPC to the VBR:

    1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list) by using the credentials of account B.
    2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC**.
    3.  Select the peer connection region, find the acceptor, and then click **Route Settings**.
    4.  Click **Add Route** and in the displayed dialog box, enter the CIDR block of the on-premises data center \(172.16.0.0/12 in this topic\). Click **Confirm**.

**Configure a route for the on-premises data center**

After you configure routes on Alibaba Cloud, you need to add a route entry for the VPC CIDR block in the physical connection device of the on-premises data center. The destination CIDR block is the Alibaba Cloud-side IP address. For example:

``` {#codeblock_lle_gao_30g}
ip route 192.168.0.0/16 10.100.0.1
```

## Step 5: Perform an acceptance test \(optional\) {#section_njh_gr5_ydb .section}

After VPC-B is connected to the on-premises data center, test the speed of the physical connection to ensure that your service needs are met. For more information, see [Method for testing the network performance of a physical connection](intl.en-US/Best Practices/Test the network performance of a physical connection.md#).

