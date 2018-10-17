# Connect a local data center to a VPC through a physical connection {#concept_ssw_lhr_ydb .concept}

As shown in the following figure, this tutorial provides a step-by-step guidance on connecting an on-premises local data center to the Alibaba Cloud VPC by using the physical connection.

## Example {#section_c5n_rhr_ydb .section}

In this tutorial, the VPC and local data center configurations in the following figure are used.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/15397440894207_en-US.jpg)

## Prerequisites {#section_cs5_qhr_ydb .section}

You have submitted a ticket and obtained the geographic position of the access point.

## Step 1: Apply for a leased line {#section_ds5_qhr_ydb .section}

1.  Log on to [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
2.  In the left-side navigation pane, click **Physical Connection** \> **Leased Line**.
3.  Click **Apply for Leased Line Access**.
4.  Configure the leased line. The following are the settings used in this tutorial.
    -   **Leased Line Name**: Enter a name for the leased line. In this tutorial, Beijing\_Local is entered.

    -   **Access Point**: Select the region where the access point of the leased line is located. In this tutorial, **Beijing-Daxing-A** is selected.

    -   **Carrier**: Select a network operator. In this tutorial, **Other \(China\)** is selected.

    -   **Access Port Type**: Select a port used by the leased line. In this tutorial, **100Base-T-100M electrical port** is selected.

    -   **Access Bandwidth**:  Select a bandwidth for the leased line. In this tutorial, **100 Mbit/sport** is selected.

    -   **Peer Address of Leased Line**:  Enter the address of your local data center. For example, No. XX, XX Street, XX District, Beijing

    -   **Redundant Leased Line**: Select an existing leased line as the redundant physical connection. In this tutorial, redundant leased line is not used.

5.   Click **Apply**.

    Return to the Leased line page. The status of the leased line is **Application in Progress**.

6.  After the application is approved, click **Pay Access Fee** to pay the fee. Then the system automatically assigns you a port and a physical connection ID.

    Wait for Alibaba Cloud for reviewing and approving the application. The approving process usually takes two workdays. You can pay the leased line fee when the status of the leased line changes to **Approved**.

7.  After the system finishes port allocation, the status of the leased line changes to **Access Construction in Progress**. You can click **View** to check the leased line details.
8.  Instruct your carrier to connect the leased line to the allocated port. The carrier provides a list of staff who will be sent to the designated Alibaba Cloud data center \(including their names, ID numbers, and phone numbers\).  **Open a ticket** to Alibaba Cloud to inform the after sales staff about the carrier staff list, the acquired connection ID, and when the carrier staff will go to the data center.

    In the following workday, Alibaba Cloud after sales staff will schedule an appointment at the data center for the carrier staff and inform you of the contact information of the reception personnel in the data center on that day. Inform the carrier of the appointment information. After the carrier completes deployment in the Alibaba Cloud data center, Alibaba Cloud after sales staff changes the leased line status to **Waiting for Confirmation**.

9.  After the carrier notifies you that the connection is deployed, find the leased line on the console and click **Confirm**.

    The leased line status then changes to **Normal**. The installation of the leased line is now completed.


## Step 2: Create a VBR on the physical connection {#section_js5_qhr_ydb .section}

Follow these steps to create a VBR:

1.  Log on to [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
2.  In the left-side navigation pane, click **Physical Connection** \> **Virtual Border Router**.
3.  Click **Create VBR**. The following are the settings used in this tutorial.
    -   **Object**: Select **This Account**.

    -   **Name**: Enter a name for the router interface. In this tutorial, "Beijing\_Border\_Router" is entered as the name.

    -   **Description**: Enter a description.

    -   **Leased Line**: Select the leased line created in the Step 1.

    -   **VLAN ID**: Enter a VLAN ID.

    -   **Circuit Code**: Enter the circuit code provided by the operator.

    -   **Addresses**: Configure the IP addresses used to communicate according to the following information:

-   **Alibaba Cloud Side**: The IP address used as the route gateway to route data from VPC to your local data center.  In this tutorial, 10.100.0.1 is used.

-   **Customer Side**: The IP address used as the route gateway to route data from your local data center to VPC.  In this tutorial, 10.100.0.10 is used.

-   **Subnet Mask**: The subnet mask of the specified IP addresses. In this tutorial, 255.255.255.0 is entered.

4.  Click **Confirm Creation**.

    If the status of VBR is **Normal**, it indicates that the VBR has been created successfully. Now you have configured and activated the IP address 10.100.0.1/24 of Alibaba Cloud side. You need to configure the IP address 10.100.0.10/24 of the peer side and do the ping test to check whether the communication is normal.


## Step 3: Connect the VBR to the VPC through router interfaces {#section_ps5_qhr_ydb .section}

Create a router interface for the VPC and VBR separately to create a communication channel for the VPC and VBR.

Follow these steps to create router interfaces:

1.  Log on to [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  Click **Create Router Interface**.
4.  Configure the router interface and complete the payment.

    The following are the settings used in this tutorial.

    -   **Scenario**: Select **Physical Access**.

    -   **Router Creation**: Select **Create Initiator and Receiver**.

    -   **Local Region**: Select the location where the access point of the leased line is reside. In this tutorial, **China \(Beijing\)** is selected.

    -   **Access Point**: Select the access point of the leased line. In this tutorial, Beijing Beijing-Daxing-B is selected.
    -   **Local VBR ID**: Select the VBR created in the step 2.

    -   **Peer Region**: Select the region where the VPC to be connected is located. In this tutorial, **China \(Hangzhou\)** is selected.

    -   **Peer VPC ID**: Select the VPC to be connected.


After the router interface is created, the system creates a router interface for the VRouter and the VBR respectively and initiates the connection.

## Step 4: Configure route entries {#section_us5_qhr_ydb .section}

After creating a router interface, you must configure a route entry to route destined for VPC to the local data center, and configure two route entries for the VBR router interface to route traffic to VPC and VBR respectively. At last, add a route entry in the local gateway to route traffic to VPC.

Add route entry in VPC:

Follow these steps to route the traffic destined for the IDC \(CIDR Block: 172.16.0.0/12\) to the leased line:

1.  On the Router Interface page, find the target VPC router interface and click **Route Configuration**.
2.  In the displayed dialog box, configure the route:
    -   **Destination CIDR Block**: The CIDR block of the local data center. In this example, enter 172.16.0.0/12.
    -   **Next Hop Type**: Select **Router Interface \(To VBR\)**.
    -   **Router Interface**: Select the router interface created for the VPC in the step 3.

Add route entries in VBR

-   Add a rout entry pointing to the leased line

    Follow these steps to route the traffic destined for the IDC \(CIDR Block: 172.16.0.0/12\) to the leased line:

    1.  Log on to [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
    2.  In the left-side navigation pane, click **Physical Connection** \> **Virtual Border Router**.
    3.  Click the ID of the target router interface and click **Add Route Entry**.
    4.  In the displayed dialog box, configure the route:
        -   **Destination CIDR Block**: Enter the CIDR block of the local data center. In this tutorial, 172.16.0.0/12 is entered.
        -   **Next Hop Type**: Select **To leased line**.
        -   **Router Interface**: Select the router interface created for the VBR.
    5.  Click ****OK**** and complete the configuration.

        Then you can access the Alibaba Cloud-side IP address 10.100.0.1 from the local data center.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13831/15397440894209_en-US.png)

-   Add a route entry pointing to the VPC

    Follow these steps to route the traffic destined for the VPC \(CIDR Block: 192.168.0.0/16\) to the VPC:

    1.  Log on to [Express Connect console](https://partners-intl.console.aliyun.com/#/ri).
    2.  In the left-side navigation pane, click **Physical Connection** \> **Virtual Border Router**.
    3.  Click the ID of the target router interface and click **Add Route Entry**.
    4.  In the displayed dialog box, configure the route:
        -   **Destination CIDR Block**: Enter the CIDR Block of the VPC. In this tutorial,192.168.0.0/16 is entered.
        -   **Next Hop Type**: Select **Router Interface \(To VPC\)**.
        -   **Router Interface**: Select the router interface associated with the VPC.
    5.  Click ****OK**** and complete the configuration.

        ![](images/4211_en-US_source.png)


Configure the route of the local data center

Now the route configuration for the Alibaba Cloud side is completed. However, to establish the connection from the IDC to the VPC, you must add a route entry for the gateway of you IDC to route traffic destined for the VPC to the IP address of the Alibaba Cloud side. You can configure a static route or BGP dynamic routing to forward data in the local data center to VBR:

-   Static route

    Example:

    ```
    ip route 192.168.0.0/16 10.100.0.1
    ```

-   Dynamic routing

    You can also use BGP to connect the VBR and the local data center.

    1.  Create a BGP peer group, see [Create BGP peer groups](https://help.aliyun.com/document_detail/57974.html).
    2.  Add BGP peers to the BGP group, see [Create BGP peers](https://help.aliyun.com/document_detail/57975.html).
    3.  Advertise the BGP network in the VBR, see [Advertise BGP network](https://help.aliyun.com/document_detail/58738.html).

        **Note:** Ensure the destination CIDR block of the BGP route entry is the static route that you have configured. In this tutorial, it is 192.168.0.0/16.


When the routing configuration is complete, intranet communication link between the local data center and VPC \(local data center-leased line-VBR-VPC\) is completed and the route can be reached.

**Note:** You can manage the access between the devices of the local data center and cloud products of the Alibaba Cloud by adjusting ECS security group rules or adding RDS whitelist.

## Step 5: Test the performance {#section_kt5_qhr_ydb .section}

See [Test on the network performance of leased line](https://help.aliyun.com/document_detail/58625.html) to test the rate of leased line to meet the business needs.

