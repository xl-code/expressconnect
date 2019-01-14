# Connect a local IDC to a VPC through a physical connection {#concept_ssw_lhr_ydb .concept}

This tutorial describes how to use Express Connect to implement intercommunication between your local IDC and the Alibaba Cloud VPC.

## Example {#section_c5n_rhr_ydb .section}

This tutorial uses the VPC and local IDC configurations shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/15474568334207_en-US.jpg)

## Prerequisites {#section_cs5_qhr_ydb .section}

You have submitted a ticket and obtained the geographic position of the access point.

## Step 1: Apply for a physical connection interface and complete leased line access {#section_ds5_qhr_ydb .section}

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, click **Physical Connections** \> **Physical Connection Interfaces**.
3.  Click **Apply for New Interface**.
4.  Configure the interface. Perform the following configurations:
    -   **Name**: Enter the name of the physical connection interface.

    -   **Access Point**: Select the nearest access point to your local IDC. In this example, select **ap-cn-zhangjiakou-xrt-A**.

    -   **Service Provider**: Select your physical connection provider. In this example, select **China Mobile**.

    -   **Port Type**: Select the access port of the physical connection. In this example, select **1 Gbit/s Electrical Port**.

    -   **Bandwidth**: Enter a bandwidth value \(unit: Mbps\) based on your specific service needs. In this example, enter **2**.

    -   **Location**: Enter the address of your local IDC.

    -   **Redundancy**: If you want to implement Equal-Cost Multi-Path \(ECMP\) routing through two physical connections, you can select another physical connection to provide redundancy in this physical connection.

        In this example, do not select a redundant physical connection.

5.  Click **OK**. On the Physical Connection Interfaces page, check the physical connection interface you have applied for.

    The physical connection interface status is **Applying**.

6.  Wait for Alibaba Cloud to review your application. Normally, the review will be completed on the next workday. When the physical connection interface status becomes **Approved**, click **Pay for Connection** and complete the payment.

    The system automatically allocates you a port and a physical connection ID.

7.  The physical connection interface status becomes **Connecting**. Click **View** to view the details, such as IDC location, cabinet location, and port information.
8.  Notify your service provider of the port information. After conducting a resource survey, the service provider will provide a list of personnel who will be sent to the Alibaba Cloud IDC at the access point, and provide relevant information, such as arrival time and physical connection ID. **Open a new ticket** to inform Alibaba Cloud after-sales personnel of the information about the leased line to be deployed by the service provider.
9.  On the next workday, Alibaba Cloud after-sales personnel will schedule a visit to the IDC for your service provider and give you the contact information of the reception personnel in the IDC. You need to notify your service provider of the preceding information. After the service provider completes deployment in the Alibaba Cloud IDC, Alibaba Cloud after-sales personnel will change the physical connection interface status to **Pending Confirmation**.
10. After your service provider notifies you that the physical connection is deployed, find the physical connection in the console and click **Confirm**.

    When the physical connection interface status changes to **Enabled**, the physical connection is completed.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/154745683411740_en-US.png)


## Step 2: Create a virtual border router {#section_js5_qhr_ydb .section}

After the physical connection is established, you need to create a Virtual Border Router \(VBR\) for it as a forwarding bridge between the VPC and your local IDC.

To create a VBR, perform the following steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Click **Create VBR**. In this example, configure the VBR as follows:
    -   **Account**: Select **Current Account**.

    -   **Name**: Enter the VBR name.

    -   **Physical Connection Interface**: Select the physical connection interface created in Step 1.

    -   **VLAN ID**: Enter the VLAN ID. In this example, enter 1678.

    -   **Gateway IP Address on Alibaba Cloud Side**: Enter the gateway from the VPC to your local IDC. In this example, enter 10.0.0.1.

    -   **Gateway IP Address on Customer Side**: Enter the gateway from your local IDC to the VPC. In this example, enter 10.0.0.2.

    -   **Subnet Mask**: Enter the subnet mask of the IP address on Alibaba Cloud side and customer side. In this example, enter 255.255.255.0.

4.  Click **OK**.

## Step 3: Create a peering connection {#section_ps5_qhr_ydb .section}

After the physical connection is established, you also need to establish a peering connection between the VBR associated with the physical connection and the VPC to be connected.

To create a peering connection, perform the following steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Click **Create Peering Connection**.
4.  Configure the peering connection.

    Perform the following configurations:

    -   **Belongs to Current Account**: Select **Yes**.

    -   **Connection Type**: Select **VBR-to-VPC**.

    -   **Routers to Create**: Select **Initiator and Acceptor**.

        In physical connection scenarios, the initiator of a peering connection must be a VBR.

    -   **Local Region**: Select the region where the VBR is located. In this example, select **China \(Zhangjiakou-Beijing Winter Olympics\)**.

    -   **Local Access Point**: Select the access point of the physical connection. In this example, select **ap-cn-zhangjiakou-xrt-A**.

    -   **Local VBR ID**: Select the created VBR. In this example, select **VBR1**.

    -   **Peer Region**: Select the region where the peer VPC is located. In this example, select **China \(Zhangjiakou-Beijing Winter Olympics\)**.

    -   **Peer VPC ID**: Select the peer VPC. In this example, select **VPC1**.

    -   **Bandwidth**: Select the bandwidth for intercommunication. In this example, select **1Gb**.
5.  Click **Buy Now** and complete the payment.
6.  Check the created peering connection. When the initiator and the acceptor are in **Activated** status, the peering connection is established successfully.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/154745683411742_en-US.png)


## Step 4: Configure VPC routing {#section_us5_qhr_ydb .section}

After establishing a peering connection, you need to add a route entry destined for your local IDC to the VPC.

To forward the traffic destined for your local IDC \(11.11.11.0/24\) to the VBR, perform the following steps:

1.  On the VPCs page, locate the intercommunicated VPC, and then click the ID of the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/154745683411743_en-US.png)

2.  In the Network Resources area, click the route table link.
3.  On the Route Tables page, click the route table ID of the VPC, and then click **Add Route Entry**.
4.  Configure the route entry as follows and then click **OK**:
    -   **Destination CIDR Block**: Enter the CIDR block of your local IDC. In this example, enter 10.0.0.0/24.
    -   **Next Hop Type**: Select **Router Interface \(To VBR\)**.
    -   **General Routing**: Select the VBR associated with the physical connection.

## Step 5: Configure VBR routing {#section_sr1_v54_cfb .section}

To configure VBR routing destined for your local IDC and the VPC respectively, perform the following steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, click **VBR-to-VPC**.
3.  Locate the target VBR, and then click **Route Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/154745683413168_en-US.png)

4.  Click **Add Route Entry**.
5.  In the displayed dialog box, enter the CIDR block of the VPC \(In this example, enter 192.168.0.0/16\), and then click **Confirm**.
6.  Click **Add Route Entry** again.
7.  Enter the CIDR block of your local IDC \(In this example, enter 10.0.0.0/24\), and then click **Confirm**.

## Step 6: Configure routing for your local IDC {#section_mwr_x54_cfb .section}

Now the route configuration for the Alibaba Cloud side is completed. On the physical connection device, you still need to configure a route destined for the VPC. You can configure a static route or BGP route as follows to forward data from your local IDC to VBR:

-   Static route

    Example:

    ```
    ip route 192.168.0.0/16 10.0.0.2
    ```

-   Dynamic route

    You can also forward data between your local IDC and the VBR by configuring BGP. For more information, see [Configure BGP](../reseller.en-US/User Guide (New Console)/Virtual border router/Configure BGP.md#).


After the route configuration is completed, the intranet communication link between your local IDC and VPC \(local IDC→physical connection→VBR→VPC\) is established.

**Note:** You can manage the access between your local IDC devices and Alibaba Cloud products by adjusting the ECS security group rules or adding an RDS whitelist.

## Step 7: Test the connection {#section_kt5_qhr_ydb .section}

After the VPC is connected to the local data center, test the speed of the leased lines to ensure that they can meet service needs.

