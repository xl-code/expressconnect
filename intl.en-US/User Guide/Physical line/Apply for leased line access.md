# Apply for leased line access {#concept_br5_xvz_xdb .concept}

## Overview {#section_bjb_1wz_xdb .section}

A leased line is the abstraction of the network line established between an access point of Alibaba Cloud and a local data center. You must use a leased line of the carrier to connect the local data center to the Alibaba Cloud access point to set up the physical connection.

## Limits {#section_kpw_bwz_xdb .section}

-   Physical Connection does not support interfaces of SDH 155M CPOS, V.35 or G.703.
-   Alibaba Cloud provides one or more access points in each accessible region. Different access points have different carrier restrictions. Before applying for leased line access, open a ticket to obtain the access point and carrier restriction information. 

1.  登录[高速通道管理控制台](https://partners-intl.aliyun.com/login-required#/ri)。
2.  在左侧导航栏，单击**物理专线连接** \> **物理专线**。
3.  单击右上角的**申请专线接入**。
4.  在合作伙伴申请页面，选择一个阿里云的合作伙伴帮助您完成物理专线接入。

## Procedure {#section_qw3_twz_xdb .section}

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Physical Connection** \> **Leased Line**.
3.  In the upper-right corner, click **Apply for Leased Line Access**.
4.  Configure the following information on the self application page:

    |Configuration|Description|
    |:------------|:----------|
    |**Leased Line Name**|Enter the name of the leased line.|
    |**Access Point**|Select the region where your local data center is located. Access points are Alibaba Cloud data centers in different regions.  There is one or more access points in each region. Different access points have different locations and different access capabilities. Open a ticket to obtain access point information to select the optional access point.|
    |**Carrier**|Select the carrier that provides the leased line for you.**ap-cn-beijing-cp-A** only supports China Telecom. **ap-cn-beijing-dx-B** only supports China Unicom.

**ap-cn-shanghai-bs-A**, **ap-cn-shanghai-pd-A**, and **ap-cn-shanghai-pd-B** only support China Telecom, and **ap-cn-shanghai-bs-B** only supports China Unicom.

**ap-cn-shenzhen-lh-A** only supports China Telecom.

Open a ticket for detailed information.

|
    |**Access Port Type**|Select according to your actual needs.|
    |**Bandwidth for Access**|Select according to your actual needs.|
    |**Peer Address of Leased Line**|Enter the location of your local data center.|
    |**Redundant Leased Line**|Select a previously applied leased line to form redundancy with the leased line.|

5.  After you finish self application, the leased line status is **Application in Progress**. Alibaba Cloud will contact you to verify the application within two workdays.
6.  After the application is approved, the leased line status changes to **Approved**. Now click **Pay Access Fee** to complete the payment.
7.  After you make the payment, the leased line status changes to **Allocating Resources**. After another three minutes, the status of the leased line changes to **Access Construction in Progress**. Now click **View** on the right side to view information about leased line construction. Inform your carrier of the port information and ask the carrier to connect the leased line. After completing investigation, the carrier will provide you a file containing names of personnel dispatched to the data center of the access point and related information, time of on-site construction, leased line ID and so on.  At this time, you need to open a ticket to inform Alibaba Cloud aftersales personnel of information about leased line laying by construction personnel of the carrier.
8.  After the construction is completed, the leased line status changes to **Awaiting Confirmation**. Click **Confirm** and the leased line status changes to **Normal**.

    **Note:** After the leased line access is completed, the leased line status changes to Normal, and the connection is established.  If the leased line status is **Rejected**, you need to apply again.


