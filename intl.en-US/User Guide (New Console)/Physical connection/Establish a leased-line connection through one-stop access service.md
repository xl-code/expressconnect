# Establish a leased-line connection through one-stop access service {#task_uh5_54x_dfb .task}

You need to connect the leased line of your service provider to an Alibaba Cloud access point before you can establish a leased-line connection. You can quickly establish a leased-line connection through one-stop access service.

**Note:** Physical connections do not support interfaces of SDH 155M CPOS, V.35 or G.703.

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。 
2.  In the left navigation pane, click **Physical Connections** \> **Physical Connection Interfaces**. 
3.  Click **One-Stop Service**. 
4.  Set the related parameters. 

    |Configuration item|Description|
    |:-----------------|:----------|
    |**Bandwidth**|Select a bandwidth for the leased-line access.|
    |**Access City**|Select the city where your local IDC is located.|
    |**Access Address**|Enter the address of your local IDC.|
    |**Interface Type**|Select the access port type.|
    |**Service Provider**|Select the service provider of the leased line.|
    |**Alibaba Cloud Region**|Select the Alibaba Cloud region that you want to access.|
    |**Multi-Line Access**|Select whether to apply for multiple leased lines as Equal-Cost Multi-Path routing \(ECMP\) redundancy links.|
    |**Leased Line Type**|Select a leased line type as follows:    -   **Layer2 Leased Line \(MSTP\)**: traditional physical connection access.
    -   **Layer3 Leased Line \(MPLS-VPN\)**: MPLS-VPN access.
|
    |**Contact Name**|Enter the name of the contact responsible for the leased-line access.|
    |**Mobile Phone No.**|Enter the mobile phone number of the contact phone responsible for the leased-line access.|
    |**E-mail**|Enter the E-mail box of the contact responsible for the leased-line access.|

5.  Click **Submit**. On the Physical Connection Interfaces page, check the physical connection interface you have applied for. 

    The physical connection interface status is **Applying**.

6.  After the service provider notifies you that the connection is deployed, find the leased line on the console and click **Confirm**. After confirmation, the physical connection interface status changes to **Enabled**, indicating that the leased-line access is completed.

