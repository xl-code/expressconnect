# Apply for leased line access through self-service {#task_r3h_qfx_dfb .task}

You need to connect the leased line from your service provider to an Alibaba Cloud access point before you can establish a physical connection.

Before applying for leased line access, pay attention to the following restrictions:

-   Physical connections do not support interfaces of SDH 155M CPOS, V.35 or G.703.
-   Alibaba Cloud provides one or more access points in each accessible region. Different access points have different service provider restrictions. Before applying for leased line access, you must submit a ticket to obtain an access point and the restriction information of your service provider.

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console. 
2.  In the left-side navigation pane, click **Physical Connections** \> **Physical Connection Interfaces**. 
3.  Click **Apply for New Interface**. 
4.  Set the parameters, and then click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Name**|Enter a name for the leased line.|
    |**Access Point**| Select the nearest access point to your local IDC.

 Access points are Alibaba Cloud IDCs in different regions. Each region has one or more access points. Different access points correspond to different access locations and have different access capabilities. You can submit a ticket to obtain access point information and select the optimal access point.

 |
    |**Service Provider**|Select the service provider of the leased line.|
    |**Port Type**|Select the access port type.|
    |**Bandwidth**|Enter the access bandwidth.|
    |**Location**|Enter the location of your local IDC.|
    |**Redundancy**|Select a requested physical connection to provide an Equal-Cost Multi-Path routing \(ECMP\) redundant link for this leased line. Two physical connections accessing the same region can be used as redundant physical connections.    -   When accessing different access points, both physical connections naturally provide redundancy to each other.
    -   When both physical connections access the same access point, you need to specify one as the redundancy of the other. Redundant physical connections are allocated to different physical access devices.
|

5.  Click **OK**. On the Physical Connection Interfaces page, check the physical connection interface you have applied for. 

    The physical connection interface status is **Applying**.

6.  Wait for Alibaba Cloud to review your application. Normally, the review will be completed on the next workday.
7.  When the physical connection interface status becomes **Approved**, click **Pay for Connection** and complete the payment. 

    The system automatically allocates you a port and a physical connection ID. The physical connection interface status becomes **Connecting**.

8.  Click **View** to view the details, such as IDC location, network location, and port information. 
9.  Notify your service provider of the port information. After conducting a resource survey, the service provider will provide a list of personnel who will be sent to the Alibaba Cloud IDC at the access point, and provide relevant information, such as arrival time and physical connection ID.
10. Submit a ticket to inform Alibaba Cloud after-sales personnel of the information about the leased line deployed by the service provider. On the next workday, Alibaba Cloud after-sales personnel will schedule an access to the IDC for your service provider and give you the contact information of the reception personnel in the IDC.
11. Inform your service provider of the construction time and the reception personnel. 
12. Wait for the service provider to complete the construction. After the service provider completes the construction in the Alibaba Cloud IDC, the physical connection interface status becomes **Pending Confirmation**.
13. After your service provider notifies you that the physical connection is deployed, find the physical connection in the console and click **Confirm**. After confirmation, the physical connection interface status changes to **Enabled**, indicating that the leased line access is completed.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21425/154752583412047_en-US.png)


