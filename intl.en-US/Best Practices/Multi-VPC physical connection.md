# Multi-VPC physical connection {#concept_p1l_rk5_ydb .concept}

You can use a leased line that is already connected to an access point of Alibaba Cloud to connect multiple VPCs.

**Note:** Now a leased can be connected to 5 VPCs at most. You can open a ticket to increase the quota.

## Scenario {#section_d52_1l5_ydb .section}

A company has opened account A on Alibaba Cloud and created VPC-A. Account A already opened a leased line that connects the local data center of the company to VPC-A. A subsidiary of the company has open account B on Alibaba Cloud and VPC-B is under account B. The subsidiary wants to connect VPC-B to the local data center.

Because there is already a leased line under account A that connects the local data center to the access point of Alibaba Could, VPC-B under account B of the subsidiary can reuse the leased line and VBR of account A. The company only needs to create a router interface for the VBR under account A and the VPC under account B respectively and connect the two interfaces, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/15382996404227_en-US.png)

In this tutorial, VPC and leased line configurations are as follows:

|Account A|Account B|
|:--------|:--------|
|Account ID: 12345678|Account ID: 87654321|
|VPC-   Name: VPC-A
-   Region: China \(Beijing\)
-   VPC ID: vpc-12345678
-   CIDR block: 10.10.0.0/16

|VPC-   Name: VPC-B
-   Region: China \(Hangzhou\)
-   VPC ID: vpc-87654321
-   CIDR block: 192.168.0.0/16

|
|Physical Connection-   VBR name: VPC-Beijing
-   VBR ID: vbr-12345678
-   Leased line ID: pc-AAA
-   VLAN ID: 1000

|N/A|

## Step 1: Create router interfaces {#section_lpm_wl5_ydb .section}

Create a router interface on the VBR under account A and the VPC under account B respectively, so that the VRouter of the VPC and the VBR can send messages to each other through the router interfaces. For more information, see Router interfaces.

**Note:** The router interface on the VBR must act as the initiator.

**Create the initiator router interface**

Follow these steps to create a router interface for the VBR:

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Router Interface**. Click **Create Router Interface**.
3.  Configure the router interface. This tutorial uses the following configurations.
    -   Scenario: Physical Access.
    -   Router Creation: Create Initiator. 
    -   Router Type: VRouter
    -   Local Region: China \(Beijing\).
    -   Access Point: Beijing-Daxing-A. 
    -   VBR ID: vbr-12345678. 
    -   Peer Region: China \(Hangzhou\).
    -   Peer Router Type: VRouter.
    -   Specification: Large.1\(1Gb\).
4.  Click **Buy Now** to complete the creation.

    Go back to the Router Interface page after about one minute and select the target region. Then you can see the newly created router interface under account A. In this tutorial, the ID of the router interface under account A is ri-AAA.


**Create the receiver router interface**

Follow these steps to create the receiver router interface:

1.  Use account B to log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Router Interface**. Click **Create Router Interface**.
3.  Configure the router interface. This tutorial uses the following configurations.
    -   Billing Method: Pay-As-You-Go.
    -   Scenario: Physical Access. 
    -   Router Creation: Create Receiver. 
    -   Router Type: VRouter
    -   Local Region: China \(Hangzhou\).
    -   VPC ID: vpc-87654321. 
    -   Peer Region: China \(Beijing\).
    -   Peer Access Point: Beijing-Daxing-A.
    -   Peer Router Type: VRouter
4.  Click **Buy Now**.

    Go back to the Router Interface page after about one minute and select the target region. Then you can see the newly created router interface under account B. In this tutorial, the ID of the router interface under account B is ri-BBB.


## Step 2: Initiate a connection {#section_w5q_bn5_ydb .section}

After creating router interfaces, you need to add peer router interfaces and initiate a connection. Only the initiator router interface can initiate a connection.

**Add peer router interface for the VPC under account B**

Follow these steps to create a router interface for the VPC of account B:

1.  Use account B to log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Router Interface**.
3.  Select the region where the target router interface is located and find the target router interface.
4.  Click **Add** in the **Peer Router Interface** column or click **More** \> **Edit Peer Interface**.
5.  In the displayed dialog box, select **Other Account** and enter the account ID \(12345678\), VBR ID \(vbr-AAA\), and router interface ID \(ri-AAA\) of account A.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/15382996404230_en-US.png)

Add peer router interface for the router interface on the VBR under account A and initiate a connection

Follow these steps to add peer router interface for the router interface on the VBR under account A and initiate a connection:

1.  Use account A to log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Router Interface**.
3.  Click the region where the target router interface is located and find the target router interface.
4.  Click **Add** in the **Peer Router Interface** column or click **More** \> **Edit Peer Interface**.
5.  In the displayed dialog box, select **Other Account** and enter the account ID \(87654321\), VBR ID \(vbr-BBB\), and router interface ID \(ri-BBB\) of account B.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/15382996404231_en-US.png)

6.  Find the router interface of the VBR, and click **Initiate a Connection**.

    The connection is established successfully when the status of the router interfaces ri-AAA and ri-BBB changes to **Active**.


## Step 3: Configure routes {#section_f4d_z45_ydb .section}

After creating the router interfaces, you need to configure routes so that the local data center can communicate with the VPC.

Configure routes on the VBR

Follow these steps to forward the traffic, destined for the on-premises IDC \(CIDR block: 172.16.0.0/12\), from the VBR to the leased line:

1.  Use account A to log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, click **Virtual Border Router**.
3.  Find the target VBR and click **Manage**. Then click **Add Route Entry** on the page of VBR details.
4.  Configure the route. In this tutorial, the route configurations are as follows:

    -   **Destination CIDR Block**: The CIDR block of the local data center. In this tutorial, enter 172.16.0.0/12.
    -   **Next Hop Direction**: Select To VPC and then select the existing leased line.
    Follow these steps to forward the traffic, destined for the VPC \(CIDR block: 192.168.0.0/16\), from the VBR to the VPC:


1.  Use account A to log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, click **Virtual Border Router**.
3.  Find the target VBR and click **Manage**. Then click **Add Route Entry** on the page of VBR details.
4.  Configure a route. In this tutorial, the route configurations are as follows:
    -   **Destination CIDR Block**: The CIDR block of the peer VPC. In this tutorial, enter 192.168.0.0/16.
    -   **Next Hop Direction**: Select To VPC.
    -   **Next Hop**: Select the router interface of the VBR. In this tutorial, select ri-BBB.

**Configure the route on the VPC**

Follow these steps to forward the traffic, destined for the local data center \(CIDR block: 172.16.0.0/12\), from the VPC to the VBR:

1.  Use account B to log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, click **Router Interface**. Find the target router interface and click **Router Configuration**.

    ![](images/4234_en-US.png)

3.  Configure the route. In this tutorial, the route configurations are as follows:
    -   **Destination CIDR Block**: The CIDR block of the local data center. In this tutorial, enter 172.16.0.0/12.
    -   **Next Hop Type**: Select Router Interface.
    -   **Router Interface**: Select the router interface of VPC-B. In this tutorial, select ri-AAA.

**Configure the route on the local data center**

Till now, the route configuration on Alibaba Cloud has been completed. You still need to add a route entry for the VPC CIDR block in the physical access device of the customer. The destination CIDR block is the Alibaba Cloud-side IP address. For example:

```
ip route 192.168.0.0/16 10.100.0.1
```

You can also configure BGP dynamic routing to point traffic to the border router:

1.  Create BGP peer groups. For more information, see [Manage BGP peer groups](../../../../reseller.en-US/User Guide/BGP/Manage BGP peer groups.md#section_q2j_hz1_ydb).
2.  Add BGP peers to the BGP groups, see [Manage BGP peers](../../../../reseller.en-US/User Guide/BGP/Manage BGP peers.md#section_fxm_rbb_ydb).
3.  Advertise BGP network, see [Advertise BGP network](../../../../reseller.en-US/User Guide/BGP/Advertise a BGP network.md#).

    **Note:** Make sure the destination CIDR block of the BGP routing is the same as that of the static route. In this tutorial, it is 192.168.0.0/16.


Till now, all configurations have been completed.

## Step 5: Performance test {#section_njh_gr5_ydb .section}

After the two networks are connected with each other, test the speed of the leased line to ensure it can meet service needs. For more information, see [Test the network performance of a physical connection](reseller.en-US/Best Practices/Method for testing the network performance of the leased line.md#).

