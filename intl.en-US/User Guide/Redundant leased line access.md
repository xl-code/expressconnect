# Redundant leased line access {#concept_twb_lj1_ydb .concept}

You can use redundant leased lines to connect your local data center to your VPC. Redundant physical connection provides intranet communication featuring high quality and high reliability. Alibaba Cloud supports up to four leased lines to achieve ECMP.

## Scenarios  {#section_rjj_4j1_ydb .section}

This tutorial uses the following scenario to illustrate how to connect a local data center to a VPC on Alibaba Cloud by using redundant leased lines:

A company has a local data center \(CIDR block: 172.16.0.0/12\) in Beijing, and has a VPC \(CIDR block: 192.168.0.0/16\) in the region of China \(Hangzhou\) \(CIDR block: 192.168.0.0/16\). To solve single point of failure \(SPOF\), the company plans to apply for two leased lines provided by two different carriers separately to connect the local data center to the access point of Alibaba Cloud in Beijing.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13851/15349337483977_en-US.png)

## Step 1 Apply for the first physical line {#section_phg_tj1_ydb .section}

Follow these steps to apply for the first leased line:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation pane, select **Physical Connection** \> **Leased Line**.
3.  Click **Apply for Leased Line Access**. 您可以直接联系阿里云合作伙伴，阿里云合作伙伴将会为您提供一站式服，也可以选择自助申请，本操作以自助申请为例。
4.  Configure the leased line. The following are configurations used in this tutorial. For more information, see [Apply for leased line access](intl.en-US/User Guide/Physical line/Apply for leased line access.md#).
    -   **Leased Line Name**: Enter a name for the leased line. In this tutorial, Beijing\_Local\_1 is entered.
    -   **Access Point**: Select the access point closest to the local data center. In this tutorial, select **China North 2 \(Beijing\)** \> **ap-cn-beijing-dx-A**.
    -   **Carrier**: Select the carrier that provides the leased line. In this tutorial, **Other \(China\)** is selected.
    -   **Access Port Type**: Select a port used by the leased line. In this tutorial, **100Base-LR-10G Single-Mode Optical Port \(10km\)** is selected.
    -   **Bandwidth for Access**: Select a bandwidth for the leased line. In this tutorial, **100** is entered.
    -   **Peer Address of Leased Line**: Enter the address of your local data center. For example, No. XX, XX Street, XX District, Beijing.
    -   **Redundant Leased Line**: You do not need to select because this is the first leased line.
5.  Click **Apply**. On the Leased Line page, the status of the leased line is **Application in Progress**.

    Alibaba Cloud will examine and approve your application, which is generally approved the next workday. After the application is approved, the leased line status changes to **Approved**.

6.  After the application is approved, click **Pay Access Fee**. Then the system automatically assigns you a port and a leased line ID. In this tutorial, the leased line ID is “pc- 123xyz”.

## Step 2 Apply for the second leased line {#section_k3m_lhj_p2b .section}

Follow these steps to apply for the second leased line:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation pane, select **Physical Connection** \> **Leased Line**.
3.  Click **Apply for Leased Line Access**. 您可以直接联系阿里云合作伙伴，阿里云合作伙伴将会为您提供一站式服，也可以选择自助申请，本操作以自助申请为例。
4.  Configure the second leased line. The following are configurations used in this tutorial. For more information, see [Apply for leased line access](intl.en-US/User Guide/Physical line/Apply for leased line access.md#).
    -   **Leased Line Name**: Enter a name for the leased line. In this tutorial, Beijing\_Local\_2 is entered.
    -   **Access Point**: Select the access point closest to the local data center. In this tutorial, select **China North 2 \(Beijing\)** \> **ap-cn-beijing-dx-A**.
    -   **Carrier**: Select the carrier that provides the leased line. In this tutorial, **Other \(China\)** is selected.
    -   **Access Port Type**: Select a port used by the leased line. In this tutorial, **100Base-LR-10G Single-Mode Optical Port \(10km\)** is selected.
    -   **Bandwidth for Access**: Select a bandwidth for the leased line. In this tutorial, **100** is entered.
    -   **Peer Address of Leased Line**: Enter the address of your local data center. For example, No. XX, XX Street, XX District, Beijing.
    -   **Redundant Leased Line**: 

        **Note:** You can select any access point in the same region as the first leased line. If you select the same access point as the first leased line, select the first leased line as the redundant leased line \(Make sure that the installation fee of the first leased line has been paid\); If you select an access point different from that of the first leased line, the two lines are naturally redundant and you do not need to select the **Redundant Leased Line**.

5.  Next, complete the application and wait for approval, just as for the first line. After the approval, pay the fee to receive the port location.

## Step 3 Complete leased line construction {#section_ckt_2l1_ydb .section}

Follow these steps to complete the construction of the two leased lines:

1.  After the system complete port allocation and the status of the leased lines change to **Access Construction in Progress**, click **View** on the right side to view information about leased line construction, such has data center location, network cabinet location, and port information.
2.  Inform your carrier of the port information and ask the carrier to connect the leased line. After completing investigation, the carrier will provide you a file containing names of personnel dispatched to the data center of the access point and related information, time of on-site construction, leased line ID and so on. At this time, you need to submit a ticket to inform Alibaba Cloud aftersales personnel of information about leased line laying by the construction personnel of the carrier.

    In the following workday, Alibaba Cloud after sales staff will schedule an appointment at the data center for the carrier staff, and inform you of the contact information of the reception personnel in the data center on that day. Inform the carrier of the appointment information. After the carrier completes deployment in the Alibaba Cloud data center, Alibaba Cloud after sales staff changes the leased line status to **Awaiting Confirmation**.

3.  Click **Confirm** when the carrier informs you that the leased line construction has been completed. The leased line access is completed when the leased line status changes to **Normal**.

## Step 4 Create a VBR for each leased line {#section_rkf_pl1_ydb .section}

Complete these steps to create a VBR for each leased line:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation pane, select **Physical Connection** \> **Virtual Border Router**.
3.  Click **Create VBR**.
4.  Create a VBR for the first leased line. The following configurations are used in this tutorial. For more information, see [Create a virtual border router](intl.en-US/User Guide/VBR/Create a virtual border router.md#).

    VBR 1:

    -   **Object**: Select **This Account**.
    -   **Name**: VBR\_1
    -   **Description**: Leased\_Line\_1
    -   **Leased Line**: Select the first leased line. In this tutorial, select **pc-123xyz**.
    -   **VLAN ID**: 0 \(0 indicates that layer-3 router interfaces are directly used\)
    -   **Circuit Code**: Enter the circuit code provided by the carrier.
    -   **IP Address**: Set according to the following information:

        **Alibaba Cloud-Side**: Enter the IP address used as the gateway to connect to the local data center. In this tutorial, enter 10.100.0.1.

        **Customer-Side**: Enter the IP address used as the gateway to connect to the VPC. In this tutorial, enter 10.100.0.10.

        **Subnet Mask**: The subnet mask for the Alibaba-side IP address and the customer-side IP address. In this tutorial, enter 255.255.255.0.

5.  Repeat the preceding steps to create a VBR for the second leased line, namely “VBR\_2”.

## Step 5 Create router interfaces {#section_mcm_tm1_ydb .section}

To achieve redundant leased line access, you need to create a pair of router interfaces between each pair of VBR and VPC, so that the VPC and the VBR can forward messages to each other through the router interfaces. Follow these steps to create router interfaces:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  Click **Create Router Interface**.
4.  Create a router interface for VBR\_1 and the VPC according to the following information. For more information, see [Create a router interface](intl.en-US/User Guide/VRouter interface/Create a router interface.md#).
    -   **Billing Method**: Select a billing method. In this tutorial, select **Pay-As-You-Go**
    -   **Scenario**: Select **Physical Access**.
    -   **Router Creation**: Select **Create Initiator and Receiver**. The system sets the router interface of the local side as the initiator, and automatically connects the initiator to the receiver.
    -   **Local Region**: Select the region where the access point of the leased line is located. In this tutorial, select **China \(Beijing\)**.
    -   **Access Point**: Select the access point of the leased line. In this tutorial, select **Beijing-Daxing-A**.
    -   **VBR ID**: Select VBR\_1.
    -   **Peer Region**: Select the region where your VPC is located. In this tutorial, select **China \(Hangzhou\)**.
    -   **Peer VPC ID**: Select your VPC.

After the router interface is created, the system creates a router interface for the VRouter of the VPC and VBR\_1 respectively and initiates the connection.

Repeat the preceding steps to create a router interface for VBR\_2 and the VRouter of the VPC respectively.

## Step 6 Configure IP addresses for health check {#section_tfq_nn1_ydb .section}

The strategy for health check of redundant leased lines is: Alibaba Cloud sends a ping message from each source IP address to the customer-side IP address of each VBR every two seconds. If eight ping packets on one leased line consecutively fail to receive response, the traffic will be forwarded to the other leased line. Complete these steps to configure the source IP address for health check in the router interface of VPC.

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  Find the router interface of VPC created in step 4. Click **More** \> **Health Check** in the **Actions** column.
4.  Click **Configuration**, configure the following information in the displayed dialog box, and click **OK**.
    -   **SourceIp**: Enter a free IP address of the VPC as the health check IP address.
    -   **TargetIp**: Enter the customer-side IP address of the local data center.
5.  Repeat the preceding steps to configure the health check IP address for the other router interface.

    **Note:** In multi-VPC scenarios, you must configure health check IP addresses for router interfaces of all VPCs connected to redundant leased lines to guarantee smooth switch between the redundant leased lines.


## Step 7 Configure routes {#section_zmk_f41_ydb .section}

After creating the router interfaces, you need to configure a route pointing to the on-premises IDC for the router interfaces newly created on the VPC, and configure routes pointing to the VPC and the corresponding leased line respectively for each newly created router interface on the two VBRs. At last you need to add a route pointing to the VPC on the access device of the on-premises IDC. Therefore, the interconnection between the on-premises IDC and the VPC is achieved.

Configure the route on the VPC

Follow these steps to forward traffic destined for on-premises IDC \(CIDR block: 172.16.0.0/12\) to the VBR:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  Select the region where the VPC is located.
3.  Click **Route Configuration** in the **Actions** column of the target router interface. Click **Add Route Entry** on the page of VBR details.
4.  In the displayed dialog box, configure the route according to the following information. For more information, see [Add a route entry](intl.en-US/User Guide/VBR/Add a route entry.md#).
    -   **Destination CIDR Block**: The CIDR Block of the local data center. In this example, enter 172.16.0.0/12.
    -   **Next Hop Type**: Select **Router Interface \(To VBR\)**.
    -   **Route Type**: Select **ECMP Routing**.
    -   **Router Interface**: Select the two router interfaces created on the VPC in step 4.

        ![](images/3985_en-US.png)

5.  Click **OK**.

Configure routes on the VBR

Add a route pointing to the leased line

Follow these steps to route the traffic destined for the IDC \(CIDR Block: 172.16.0.0/12\) to the leased line:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation pane, click **Physical Connection** \> **Virtual Border Router**.
3.  Select the region where the VBR is located.
4.  Click **Manage** in the **Actions** column of VBR\_1 to enter the page of VBR details. Click **Add Route Entry**.
5.  In the displayed dialog box, configure the route entry according to the following information. For more information, see [Add a route entry](intl.en-US/User Guide/VBR/Add a route entry.md#).
    -   **Destination CIDR Block**: The CIDR Block of the local data center. In this tutorial, enter 172.16.0.0/12.
    -   **Next Hop Direction**: Select **To Leased Line**.
    -   **Next Hop**: Select the router interface pointing to the local data center created in step 4.
6.  Click **OK** to complete the configuration. Then you can access the Alibaba-side IP address 10.100.0.1 from the local data center.

Add a route entry pointing to the VPC

Follow these steps to route the traffic destined for the VPC \(CIDR Block: 192.168.0.0/16\) to the VPC:

1.  Log on to the [Express Connect console](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list).
2.  In the left-side navigation pane, click **Physical Connection** \> **Virtual Border Router**.
3.  Select the region where the VBR is located.
4.  Click **Manage** in the **Actions** column of VBR\_1 to enter the page of VBR details. Click **Add Route Entry**.
5.  In the displayed dialog box, configure the route entry according to the following information. For more information, see [Add a route entry](intl.en-US/User Guide/VBR/Add a route entry.md#).
    -   **Destination CIDR Block**: The CIDR Block of the VPC. In this tutorial, enter 192.168.0.0/16.
    -   **Next Hop Direction**: Select **To VPC**.
    -   **Next Hop**: Select the router interface pointing to the VPC created in step 4.

Repeat the preceding steps to configure routes pointing to the VPC and the local data center respectively for VBR\_2.

Configure the route on the local data center

Till now, the route configuration on Alibaba Cloud has been completed. However, to establish the connection from the IDC to the VPC, you must add a route entry for the gateway of you IDC to route traffic destined for the VPC to the IP address of the Alibaba Cloud side. You can configure a static route or BGP dynamic routing to forward data in the local data center to VBR:

-   Static routes

    Example:

    ```
      ip route 192.168.0.0/16 10.100.0.1
      ip route 192.168.0.0/16 10.100.1.1
    ```

-   Dynamic routes

    You can also use BGP to connect the VBR and the local data center.

    1.  Create a BGP peer group, see [Create BGP peer groups](intl.en-US/User Guide/BGP/Manage BGP peer groups.md#section_q2j_hz1_ydb).
    2.  Add BGP peers to the BGP group, see [Create BGP peers](intl.en-US/User Guide/BGP/Manage BGP peers.md#section_fxm_rbb_ydb).
    3.  Advertise the BGP network in the VBR, see [Advertise BGP network](intl.en-US/User Guide/BGP/Advertise a BGP network.md#).

        **Note:** Ensure the destination CIDR block of the BGP route entry is the static route that you have configured. In this tutorial, it is 192.168.0.0/16.


## Step 8 Test the performance {#section_imb_zq1_ydb .section}

After the VPC is connected to the local data center, test the speed of the leased lines to ensure that they can meet service needs. For more information, see [Test the network performance of a physical connection](../../../../intl.en-US/Best Practices/Method for testing the network performance of the leased line.md#).

