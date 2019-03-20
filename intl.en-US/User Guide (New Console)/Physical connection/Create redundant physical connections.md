# Create redundant physical connections {#concept_jhf_r5p_hfb .concept}

You can use two physical connections to connect an on-premises IDC to Alibaba Cloud. In this way, a high-quality and highly reliable intranet communication can be established between the on-premises IDC and Alibaba Cloud.

## Example {#section_dys_x5p_hfb .section}

This topic takes the following scenario as an example to describe how to connect an on-premises IDC to Alibaba Cloud through redundant physical connections.

A company has an on-premises IDC \(CIDR block: 172.16.0.0/12\) in Beijing, and has a VPC \(CIDR block: 192.168.0.0/16\) in the China \(Beijing\) region. To solve the issue of Single Points of Failure \(SPOFs\), the company plans to apply for two physical connections that are provided by two different service providers to connect the on-premises IDC to Alibaba Cloud.

## Step 1: Apply for a physical connection interface {#section_wxh_rvp_hfb .section}

Set the name of this first physical connection interface to leasedline1. This topic provides only general configuration information. For detailed configuration information, see [Apply for leased line connection](intl.en-US/User Guide (New Console)/Physical connection/Apply for leased line connection.md#).

1.  Apply for a physical connection interface and pay the initial installation fee.
    -   **Region**: Select the region where the leased line is deployed.
    -   **SP**: Select the service provider of your leased line. In this example, select **China Unicom**.
    -   **Access Point**: Select an access point that is closest in geographical proximity to your on-premises IDC. In this example, select **Qingdao-Laoshan-A-CU**.
    -   **Port Specification**: Select the required port specification. In this example, select **10G**. Note that different specifications incur different resource fees.
    -   **Port Type**: Select the port type of the physical connection. In this example, select **1000Base-LX**.
    -   **Redundant Connection ID**: Select **None**.
2.  Click **Apply for LOA** in the **Actions** column.
3.  Enter your company name, the name of the data center cable installation company, the scheduled installation date and time, and the contact information of data center cable installation technician or representative, and select a construction type.
4.  After your application is approved, download the LOA to view installation information in the console, such as the location of the installation site \(the Alibaba Cloud IDC site\), cabinet location, and port information. At this stage, we recommend that you instruct your installation company to start installation.
5.  After the installation is complete, click **Delivery Report** on the Physical Connection Interfaces page, enter the leased line code and the label numbers of cables at the installation site, and click **OK**. The physical connection interface enters the **Waiting** state.
6.  Alibaba Cloud will connect the cables to the corresponding CSW ports according to the information you provided. After you confirm that the physical connection interface has been deployed, pay the resource fee. When the physical connection interface changes to the **Enabled** state, the leased line connection is completed.

## Step 2: Apply for a second physical connection interface { .section}

Set the name of the second physical connection interface to leasedline2. This topic provides only general configuration information. For detailed configuration information, see [Apply for leased line connection](intl.en-US/User Guide (New Console)/Physical connection/Apply for leased line connection.md#).

1.  Apply for a physical connection interface and pay the initial installation fee.
    -   **Region**: Select the region where the leased line is deployed.
    -   **Access Point**: Select an access point that is closest in geographical proximity to your on-premises IDC. In this example, select **Qingdao-Laoshan-A-CU**.
    -   **SP**: Select the service provider of your leased line. In this example, select **China Unicom**.
    -   **Port Specification**: Select the required port specification. In this example, select **10G**. Note that different specifications incur different resource fees.
    -   **Port Type**: Select the port type of the physical connection. In this example, select **1000Base-LX**.
    -   **Redundant Connection ID**: Select the first physical connection interface you have applied for. Make sure that you have paid the initial installation fee.

        **Note:** 

        -   If the access point of the second physical connection interface is the same as that of the first physical connection interface, select the ID of the first physical connection. Make sure that you have paid the initial installation fee for the first physical connection.
        -   If the access point of the second physical connection interface is different from that of the first physical connection interface, the two connections create a redundant connection by default, so you do not need to select a physical connection ID.
2.  Click **Apply for LOA** in the **Actions** column.
3.  Enter your company name, the name of the data center cable installation company, the scheduled installation date and time, and the contact information of data center cable installation technician and representative, and select a construction type.
4.  After your application is approved, download the LOA to view installation information in the console, such as the location of the installation site \(the Alibaba Cloud IDC site\), cabinet location, and port information. At this stage, we recommend that you instruct your installation company to start installation.
5.  After the installation is complete, click **Delivery Report** on the Physical Connection Interfaces page, enter the leased line code and the label numbers of cables at the installation site, and click **OK**. The physical connection interface enters the **Waiting** state.
6.  Alibaba Cloud will connect the cables to the corresponding CSW ports according to the information you provided. After you confirm that the physical connection interface has been deployed, pay the resource fee. When the physical connection interface changes to the **Enabled** state, the leased line connection is completed.

## Step 3: Create a VBR {#section_xpm_5yp_hfb .section}

To create a VBR, follow these steps:

1.  On the Virtual Border Routers page, click **Create VBR**.
2.  Configure the VBR. The VBR configurations in this example are as follows:
    -   **Account**: Select **Current Account**.
    -   **Name**: Enter vbr1.
    -   **Physical Connection Interface**: Select the first physical connection interface.
    -   **VLANID**: Enter 2333.
    -   **Gateway IP Address on Alibaba Cloud Side**: Enter 10.0.0.1.
    -   **Gateway IP Address on Customer Side**: Enter 10.0.0.2.
    -   **Subnet Mask**: Enter 255.255.255.252.
3.  Repeat the preceding steps to create a VBR named vbr2 for the second physical connection interface.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/22194/155305635334848_en-US.png)


## Step 4: Establish a peering connection {#section_dpd_1zp_hfb .section}

To establish a peering connection between your VBR and your VPC, follow these steps:

1.  On the VPC Peering Connections page, click **Create Peering Connection**.
2.  Configure the peering connection. The configurations in this example are as follows:
    -   **Connection Type**: Select **VBR-to-VPC**.
    -   **Routers to Create**: Select **Initiator and Acceptor**.
    -   **Local Region**: Select the region of the VBR. In this example, select **China \(Beijing\)**.
    -   **Local VBR ID**: Select the created VBR.
    -   **Peer Region**: Select the region to which the VPC belongs. In this example, select **China \(Beijing\)**.
    -   **Peer VPC ID**: Select the VPC to be connected.
    -   **Bandwidth**: In this example, select **100 Mb**.
3.  Go back to the VPC Peering Connections page to view the status of the peering connection. The connection is successfully established if the status of both the acceptor and the initiator is activated.
4.  Repeat the preceding steps to establish a peering connection between the other VBR and the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/22194/155305635334857_en-US.png)


## Step 5: Configure routes {#section_zx3_l1s_2gb .section}

After establishing the peering connections, you must configure a route in the VPC that points to the on-premises IDC in the VPC, and configure two routes pointing to the VPC and the on-premises IDC respectively. Lastly, you must add a route pointing to the VPC in the access device of the on-premises IDC.

To configure the routes, follow these steps:

1.  To configure routes for a VBR:
    1.  On the VBR details page, click the **Routes** tab page, and then click **Add Route**.
    2.  Add a route directing to the VPC:
        -   **Destination Subnet**: Enter the CIDR block of the VPC. In this example, enter 192.168.0.0/16.
        -   **Next Hop Type**: Select **VPC**.
        -   **Next Hop**: Select the VPC.
    3.  Add a route pointing to the physical connection:
        -   **Destination Subnet**: Enter the CIDR block of the on-premises IDC. In this example, enter 172.16.0.0/12.
        -   **Next Hop Type**: Select **Physical Connection Interface**.
        -   **Next Hop**: Select the physical connection interface.
    4.  Repeat the preceding steps to configure routes for the other VBR.
2.  To configure a route for the VPC:
    1.  On the VPC Peering Connections page, find the created peering connection, and click the VPC ID of the acceptor to open the VPC Details page. Here, you can view the ID of the route table.
    2.  On the [Route Tables](https://vpcnext.console.aliyun.com/vpc/cn-qingdao/route-tables) page, click the target route table ID, and then click **Add Route Entry**.
    3.  Configure a route:
        -   **Destination CIDR Block**: Enter the CIDR block of the on-premises IDC. In this example, enter 172.16.0.0/12.
        -   **Next Hop Type**: Select **Router Interface \(To VBR\)**.
        -   **Next Hop**: Select **Load Balancing Routing**, and then select the created VBR.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/22194/155305635334889_en-US.png)

    4.  Configure a route for the on-premises IDC.

        You can configure a static route or BGP dynamic routing to forward data between the on-premises IDC to VBR:

        -   Static route

            Example:

            ```
            ip route 192.168.0.0/16 10.100.0.1
            ```

        -   Dynamic routes

            You can also use BGP to forward data between the on-premises IDC and the VBR. For more information, see [Configure BGP](intl.en-US/User Guide (New Console)/Virtual border router/Configure BGP.md#).

            **Note:** The advertised CIDR block must be the CIDR block of the VPC that will be used to communicate with the on-premises IDC. In this example, enter 192.168.0.0/16.


## Step 6: Configure health checks {#section_fmf_v44_2gb .section}

You must configure the health check settings for redundant physical connections. Alibaba Cloud sends a ping packet once every two seconds from each health check IP address to the customer-side IP address of the on-premises IDC. If eight ping packets on one physical connection are sent in succession, and all packets fail to respond, the traffic is switched to the other physical connection.

To configure the health check, follow these steps:

1.  On the VBR-to-VPC page, locate the created peering connection, and then click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/155305635412053_en-US.png)** \> **Health Check**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/22194/155305635434791_en-US.png)

2.  Click **Configure**, complete the following configurations and then click **OK**.
    -   **Source IP**: Enter an idle IP of the VSwitch in the connected VPC.
    -   **Destination IP**: Enter the interface IP address of the network device of the on-premises IDC.
3.  Repeat the preceding steps to configure a health check for the other peering connection.

