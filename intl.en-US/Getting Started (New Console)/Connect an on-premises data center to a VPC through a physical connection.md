# Connect an on-premises data center to a VPC through a physical connection {#task_1461586 .task}

This topic describes how to use Express Connect to implement intercommunication between your on-premises data center and an Alibaba Cloud VPC.

This topic uses the VPC and on-premises data center configurations shown in the following figure.

![Apply for a physical connection interface](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/156463899054064_en-US.png)

## Step 1: Apply for a physical connection interface {#section_hj0_3gr_9su .section}

1.  Log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com).
2.  In the left-side navigation pane, choose **Physical Connections** \> **Physical Connection Interfaces**.
3.  Click **Apply for New Interface**.
4.  Configure the interface. Perform the following configurations:
    -   **Region**: Select the region where the leased line is deployed.
    -   **SP**: Select the service provider of your leased line. In this example, select **China Mobile**.
    -   **Access Point**: Select an access point that is closest in geographical proximity to your on-premises data center. In this example, select **Zhangjiakou-Xiaoertai-A-Ali**.
    -   **Port Specification**: Select a port specification. Note that different specifications incur different resource occupation fees.
    -   **Port Type**: Select the access port of the physical connection. In this example, select **1000Base-LX**.
    -   **Redundancy**: If you want to implement Equal-Cost Multi-Path \(ECMP\) routing through two physical connections, you can select another physical connection to provide redundancy for this physical connection.

        In this example, do not select a redundant physical connection.

5.  Click **Buy Now** and complete the payment for an initial installation fee.
6.  Click **OK**. Return to the Physical Connection Interfaces page to check the physical connection interface you have applied for. The physical connection interface is in the **To Apply for LOA** state.
7.  Click **Apply for LOA** in the **Actions** column. On the Apply for LOA page, enter your company name, the name of the data center cable installation company, the scheduled installation date and time, and the contact information of the data center cable installation technician or representative, and select a construction type.
8.  Click **OK**. Your application is then sent to Alibaba Cloud personnel for review. The physical connection interface enters the **In Application** state.
9.  After your application is approved, download the LOA to view installation information in the console, such as the location of the installation site \(the Alibaba Cloud data center site\), cabinet location, and port information.
10. At this stage, we recommend that you instruct your installation company to start installation. After the installation is complete, click **Delivery Report** on the Physical Connection Interfaces page, enter the leased line code and the label numbers of the cables at the installation site, and click **OK**. The physical connection interface enters the **Waiting** state.
11. Alibaba Cloud will connect the cables to the corresponding CSW ports according to the information you provided. Alibaba Cloud should complete this step within two working days of you clicking OK in the preceding step. The physical connection interface enters the **Waiting** state.
12. After you confirm that the physical connection interface has been deployed, pay the resource occupation fee and enable the port. When the physical connection interface changes to the **Enabled** state, the leased line connection is completed. 

    **Note:** The estimated time frame of completing the LOA application, installation, and on-site assistance from Alibaba Cloud is subject to local laws and authorities.


## Step 2: Create a virtual border router {#section_6zy_sct_614 .section}

After the leased line connection is completed, you need to create a Virtual Border Router \(VBR\) for it as a forwarding bridge between the VPC and your on-premises data center.

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Click **Create VBR**. The VBR configurations in this example are as follows:
    -   **Account**: Select **Current Account**.
    -   **Name**: Enter the VBR name.
    -   **Physical Connection Interface**: Select the physical connection interface created in Step 1.
    -   **VLAN ID**: Enter the VLAN ID. In this example, enter 1678.
    -   **Gateway IP Address on Alibaba Cloud Side**: Enter the gateway from the VPC to your on-premises data center. In this example, enter 10.0.0.1.
    -   **Gateway IP Address on Customer Side**: Enter the gateway from your on-premises data center to the VPC. In this example, enter 10.0.0.2.
    -   **Subnet Mask**: Enter the subnet mask of the IP address on Alibaba Cloud side and customer side. In this example, enter 255.255.255.0.
4.  Click **OK**.

## Step 3 Add the VBR and VPC to a CEN instance {#section_dhr_197_uaw .section}

After you create a VBR, you need to add the VBR and the VPC to be connected to a Cloud Enterprise Network \(CEN\) instance.

1.  Log on to the [CEN console](https://cen.console.aliyun.com).
2.  On the Instances page, find the target CEN instance and click the instance ID.
3.  On the Networks tab, click **Attach Network** and add the VBR and VPC to be connected to the CEN instance. For more information, see [Networks](../../../../../intl.en-US/User Guide/Networks.md#).

    ![Attach networks](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/156463899050237_en-US.png)

4.  If you have added routes destined for ECS instances, VPN Gateways, or High-Availability Virtual IP Addresses \(HaVips\) in the VPC, you need to publish these routes to the CEN instance. 

    ![Route table](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/156463899150239_en-US.png)


## Step 5: Configure VBR routing {#section_ma7_keb_pe2 .section}

You need to add a route entry destined for your on-premises data center and the physical connection interface in the VBR. To do so, follow these steps:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**. Find the target VBR and click the instance ID.
3.  Click the **Routes** tab, and then click **Add Route**.
4.  On the Add Route page, configure the route as follows: 
    -   **Destination Subnet**: Enter the CIDR block of the on-premises data center. In this example, enter 10.0.0.0/24.
    -   **Next Hop Type**: Select **Physical Connection Interface**.
    -   **Next hop**: Select the physical connection interface created in Step 1.
5.  Click **OK**.

## Step 6: Configure routing for your on-premises data center {#section_nyz_mf9_l9g .section}

Now the route configuration for the Alibaba Cloud side is completed. On the physical connection device, you still need to configure a route destined for the VPC. You can configure a static route or BGP route as follows to forward traffic from your on-premises data center to VBR:

-   Static route

    Example:

    ``` {#codeblock_9fp_hv9_edd}
    ip route 192.168.0.0/16 10.0.0.2
    ```

-   Dynamic route

    You can also forward traffic between your on-premises data center and the VBR by configuring BGP. For more information, see [Configure BGP](../intl.en-US/Virtual Border Router/Configure BGP.md#).


After the route configuration is completed, the intranet communication link between your on-premises data center and VPC \(on-premises data center→physical connection→VBR→VPC\) is established.

**Note:** You can manage the access to your on-premises data center devices and Alibaba Cloud resources by adjusting the ECS security group rules or adding an RDS whitelist.

## Step 6: Perform a test {#section_1nc_l5y_0nf .section}

After the VPC is connected to the on-premises data center, test the speed of the physical connection to ensure that it can meet service needs. For more information, see [Test the network performance of a physical connection](../intl.en-US/Best Practices/Test the network performance of a physical connection.md#).

