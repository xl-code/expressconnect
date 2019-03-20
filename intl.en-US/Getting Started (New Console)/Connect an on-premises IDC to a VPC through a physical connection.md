# Connect an on-premises IDC to a VPC through a physical connection {#concept_ssw_lhr_ydb .concept}

This topic describes how to use Express Connect to implement intercommunication between your on-premises IDC and the Alibaba Cloud VPC.

## Example {#section_c5n_rhr_ydb .section}

This topic uses the VPC and on-premises IDC configurations shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/15530562094207_en-US.jpg)

## Step 1: Apply for a physical connection interface {#section_ds5_qhr_ydb .section}

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left-side navigation pane, choose **Physical Connections** \> **Physical Connection Interfaces**.
3.  Click **Apply for New Interface**.
4.  Configure the interface by setting the following configurations:
    -   **Region**: Select the region where the leased line is deployed. In this example, select **China North 3 \(Zhangjiakou\)**.

    -   **SP**: Select the service provider of your leased line. In this example, select **China Unicom**.

    -   **Access Point**: Select the nearest access point to your on-premises IDC. In this example, select **Zhangjiakou-Xiaoertai-A-Ali**.

    -   **Port Specification**: Select a port specification. In this example, select **10G**. Note that different specifications incur different resource fees.

    -   **Port Type**: Select the port type of the physical connection. In this example, select **1000Base-LX**.

    -   **Redundant Connection ID**: If you want to implement Equal-Cost Multi-Path \(ECMP\) routing through two physical connections, you can select another physical connection to provide redundancy for this physical connection.

        In this example, do not select a redundant physical connection.

5.  Click **Buy Now** and complete the payment for an initial installation fee.
6.  On the Physical Connection Interfaces page, check the physical connection interface you have applied for.

    The physical connection interface is in the **To Apply for LOA** state.

7.  Click **Apply for LOA** in the **Actions** column.
8.  Enter your company name, the name of the data center cable installation company, the scheduled installation date and time, and the contact information of the data center cable installation technician or representative, and select a construction type.
9.  Click **OK**. Your application is then sent to Alibaba Cloud personnel for review, and the physical connection interface enters the **In Application** state.
10. After your application is approved, download the LOA to view installation information in the console, such as the location of the installation site \(the Alibaba Cloud IDC site\), cabinet location, and port information. At this stage, we recommend that you instruct your installation company to start installation.
11. After installation is complete, click **Delivery Report** on the Physical Connection Interfaces page, enter the leased line code and the label numbers of the cables at the installation site, and click **OK**.

    The physical connection interface enters the **Waiting** state.

12. Alibaba Cloud will connect the cables to the corresponding CSW ports according to the information you provided. Alibaba Cloud should complete this step within two working days of you clicking **OK** in the preceding step.

    The physical connection interface enters the **Waiting** state.

13. After you confirm that the physical connection interface has been deployed, pay the resource fee and enable the port.

    When the physical connection interface changes to the **Enabled** state, the leased line connection is completed.

    **Note:** The estimated time frame of completing the LOA application, installation, and on-site assistance from Alibaba Cloud is subject to local laws and authorities.


## Step 2: Create a virtual border router {#section_js5_qhr_ydb .section}

After the leased line connection is completed, you need to create a Virtual Border Router \(VBR\) for it as a forwarding bridge between the VPC and your on-premises IDC.

To create a VBR, perform the following steps:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Click **Create VBR**. In this example, configure the VBR as follows:
    -   **Account**: Select **Current Account**.

    -   **Name**: Enter the VBR name.

    -   **Physical Connection Interface**: Select the physical connection interface created in Step 1.

    -   **VLAN ID**: Enter the VLAN ID. In this example, enter 1678.

    -   **Gateway IP Address on Alibaba Cloud Side**: Enter the gateway from the VPC to your on-premises IDC. In this example, enter 10.0.0.1.

    -   **Gateway IP Address on Customer Side**: Enter the gateway from your on-premises IDC to the VPC. In this example, enter 10.0.0.2.

    -   **Subnet Mask**: Enter the subnet mask of the IP address on Alibaba Cloud side and customer side. In this example, enter 255.255.255.0.

4.  Click **OK**.

## Step 3: Create a peering connection {#section_ps5_qhr_ydb .section}

After the physical connection is established, you also need to establish a peering connection between the VBR associated with the physical connection and the VPC to be connected.

To create a peering connection, perform the following steps:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VBR-to-VPC**.
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
6.  Check the created peering connection. When the initiator and the acceptor are in the **Activated** state, the peering connection is established successfully.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/155305620911742_en-US.png)


## Step 4: Configure VPC routing {#section_us5_qhr_ydb .section}

After establishing a peering connection, you need to add a route entry destined for your on-premises IDC to the VPC.

To forward the traffic destined for your on-premises IDC \(11.11.11.0/24\) to the VBR, perform the following steps:

1.  On the **VPCs** page, locate the intercommunicated VPC, and then click the ID of the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/155305621011743_en-US.png)

2.  In the Network Resources area, click the route table link.
3.  On the Route Tables page, click the route table ID of the VPC, and then click **Add Route Entry**.
4.  Configure the route entry as follows and then click **OK**:
    -   **Destination CIDR Block**: Enter the CIDR block of your on-premises IDC. In this example, enter 10.0.0.0/24.
    -   **Next Hop Type**: Select **Router Interface \(To VBR\)**.
    -   **General Routing**: Select the VBR associated with the physical connection.

## Step 5: Configure VBR routing {#section_sr1_v54_cfb .section}

To configure VBR routing destined for your on-premises IDC and the VPC respectively, perform the following steps:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left-side navigation pane, click **VBR-to-VPC**.
3.  Locate the target VBR, and then click **Route Settings**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/155305621013168_en-US.png)

4.  Click **Add Route Entry**.
5.  In the displayed dialog box, enter the CIDR block of the VPC \(In this example, enter 192.168.0.0/16\), and then click **Confirm**.
6.  Click **Add Route Entry** again.
7.  Enter the CIDR block of your on-premises IDC \(In this example, enter 10.0.0.0/24\), and then click **Confirm**.

## Step 6: Configure routing for your on-premises IDC {#section_mwr_x54_cfb .section}

Now the route configuration for the Alibaba Cloud side is completed. On the physical connection device, you still need to configure a route destined for the VPC. You can configure a static route or BGP route as follows to forward data from your on-premises IDC to VBR:

-   Static route

    Example:

    ```
    ip route 192.168.0.0/16 10.0.0.2
    ```

-   Dynamic route

    You can also forward data between your on-premises IDC and the VBR by configuring BGP. For more information, see [Configure BGP](../intl.en-US/User Guide (New Console)/Virtual border router/Configure BGP.md#).


After the route configuration is completed, the intranet communication link between your on-premises IDC and VPC \(on-premises IDC→physical connection→VBR→VPC\) is established.

**Note:** You can manage the access between your on-premises IDC devices and Alibaba Cloud products by adjusting the ECS security group rules or adding an RDS whitelist.

## Step 7: Test the connection {#section_kt5_qhr_ydb .section}

After the VPC is connected to the on-premises IDC, test the speed of the leased lines to ensure that they can meet service needs.

