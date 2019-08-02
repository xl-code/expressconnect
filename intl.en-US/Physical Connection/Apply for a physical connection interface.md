# Apply for a physical connection interface {#task_r3h_qfx_dfb .task}

Before you can establish a physical connection, you need to connect the leased line from your service provider to an Alibaba Cloud access point by applying for a physical connection interface in the Express Connect console.

Before you apply for a physical connection interface, note the following restrictions:

-   Physical connections do not support interfaces of SDH 155M CPOS, V.35 or G.703.
-   Alibaba Cloud provides multiple access points in all regions, except the China \(Qingdao\) and US \(Silicon Valley\) regions. Additionally, different access points may have different service provider restrictions. For more information, see [Access points](intl.en-US/Physical Connection/Access points.md#).

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console. 
2.  In the left-side navigation pane, choose **Physical Connections** \> **Physical Connection Interfaces**.
3.  Click **Apply for New Interface**.
4.  Configure the physical connection interface, and complete the payment for an initial installation fee. 

    |Configuration|Description|
    |:------------|:----------|
    |**Region**|Select the region where the leased line is deployed. We recommend that you install the leased line in the region that is the same as your VPC. If you choose a different region, you need to pay an extra fee incurred by cross-region Cloud Enterprise Network \(CEN\) or a peering connection.

 |
    |**SP**|Select the service provider \(telecom carrier\) of the leased line. Different access points are provided for different service providers.

 |
    |**Access Point**| Different access points are provided for different service providers.

 Access points are the on-premises data centers of Alibaba Cloud that are located in multiple regions. Each region has one or more access points. Different access points correspond to different access locations and have different access capabilities. You can open a ticket to obtain detailed information about the location of access points.

 |
    |**Port Specification**|Port specifications include 1G and below, 10G, 40G, and 100G. If you select 40G or 100G, you need to enable a whitelist. **Note:** Different specifications incur different resource occupation fees.

 |
    |**Port Type**|Select the access port type. Available port types vary according to the selected access point. The console displays the available port types.

**Note:** Available port types vary according to the selected access point and service provider. We recommend that you consult the service provider before applying for a port.

 |
    |**Redundant Connection ID**|Select a requested physical connection to provide an Equal-Cost Multi-Path routing \(ECMP\) redundant link for this physical connection. Two physical connections that belong to the same region can be used as redundant physical connections.     -   When accessing different access points, both physical connections naturally provide redundancy to each other.
    -   When both physical connections access the same access point, you need to specify one as the redundancy of the other. Redundant physical connections are allocated to different physical access devices.
 |

5.  Go back to the Physical Connection Interfaces page and check the physical connection interface for which you have applied. 

    The physical connection interface is in the **To Apply for LOA** state.

6.  Click **Apply for LOA** in the **Actions** column.
7.  On the Apply for LOA page, enter the leased line connection information, and click **Add Field Engineer** to add the information of a data center cable installation technician or representative. Multiple technicians can be added. 

    |Configuration|Description|
    |-------------|-----------|
    |**Company Name**|Enter the company name that you set when you registered your account or the name of the account owner.

 |
    |**Construction Company**|Enter the name of your designated data center cable installation company, which is usually your service provider of the leased line or the on-premises data center.|
    |**Construction Type**|Select the required leased line type:     -   MSTP
    -   MPLSVPN
    -   FIBRE
    -   Others
 **Note:** SDH is not supported.

 |
    |**Scheduled Construction Time**|Set the date and time when the data center cable installation technician or representative from the installation company will go to complete the leased line connection at the site of the Alibaba Cloud data center.|
    |**Location**|Optional. Enter the location of your on-premises data center.|
    |**Bandwidth**|Optional. Enter the bandwidth of the leased line. **Note:** The bandwidth value you enter does not affect the fees charged to your account or your usage of the leased line.

 |

8.  Click **OK**. Your application is then sent to Alibaba Cloud personnel for review. 

    The physical connection interface enters the **In Application** state.

9.  After the application is approved, download the LOA in the console. 

    The physical connection interface enters the **Approved LOA** state. Click **View LOA** in the **Actions** column to view the installation information, such as the data center location of Alibaba Cloud, cabinet location, and port information.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21425/156473270139771_en-US.png)

10. At this stage, we recommend that you instruct your installation company to start installation. After installation is complete, click **Delivery Report** on the Physical Connection Interfaces page, enter the leased line code and the label numbers of the cables at the site of the Alibaba Cloud data center, and click **OK**. 

    The physical connection interface enters the **Waiting** state.

11. Alibaba Cloud will connect the cables to the corresponding CSW ports according to the information you provided. Alibaba Cloud should complete this step within two working days of you clicking OK in the preceding step. 

    The physical connection interface enters the **Waiting** state.

12. After you confirm that the physical connection interface has been deployed, pay the resource fee****and****enable the port.
13. After payment, the physical connection interface changes to the **Enabled** state, indicating that the leased line connection is completed. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21425/156473270112047_en-US.png)

    **Note:** The estimated time frame of completing the LOA application, construction, and on-site assistance from Alibaba Cloud is subject to local laws and authorities.


