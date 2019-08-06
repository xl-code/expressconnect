# Configure BGP {#concept_ljj_4vx_dfb .concept}

You can establish Border Gateway Protocol \(BGP\) routing between an on-premises data center and a Virtual Border Router \(VBR\). To do so, you only need to add BGP peers that communicate with the VBR to the corresponding BGP group, and then advertise the BGP CIDR blocks in the VBR.

**Note:** Express Connect allows you to establish BGP routing only between a VBR and an on-premises data center. When you create a physical connection, you still need to add a route entry destined for the physical connection and a route entry destined for the VPC in the VBR. For more information, see [Add route entries](reseller.en-US/Virtual Border Router/Add route entries.md#).

## BGP overview {#section_e3x_wwx_dfb .section}

BGP is a dynamic routing protocol based on TCP. It is mainly used to exchange routing and network accessibility information among Autonomous Systems \(ASs\). When you create a physical connection, you can use BGP to implement an intranet connection between the on-premises data center and the VBR. BGP can be used to build hybrid clouds in a more efficient, flexible, and reliable manner.

Before configuring BGP, you need to create a BGP group. BGP groups are used to simplify BGP configurations. Combining repeated configurations into a BGP group can make configurations easier. You only need to create a BGP group according to the Autonomous System Number \(ASN\) and add qualified BGP peers to the group. The added BGP peers will inherit the configurations of the BGP group. You do not need to configure the BGP peers separately.

## Limits {#section_ksj_qxx_dfb .section}

BGP has the following limits:

-   VBR can only establish BGP peers with the peer on-premises data center. Static routing is still required between the VBR and the VPC.
-   BGP only supports the BGP4 version.
-   VBR supports IPv4 BGP, but does not support IPv6 BGP.
-   The number of BGP peers created under each VBR cannot exceed 8.
-   The number of dynamic route entries that are added to a BGP peer cannot exceed 100.
-   The ASN of Alibaba Cloud is 45104. It supports the transmission of 2-byte or 4-byte ASNs from the customer side.

## Step 1: Create a BGP Group {#section_uks_sxx_dfb .section}

Before configuring BGP routing, you need to create a BGP group based on the requested ASN.

To create a BGP group, follow these steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select a region and click the ID of the target VBR.
4.  Click the **BGP Groups** tab, and then click **Create BGP Group**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/156507295112049_en-US.png)

5.  Configure the BGP group, and then click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Name**|Enter a name for the BGP group to be created.|
    |**Peer ASN**|Enter the ASN of the on-premises data center network.|
    |**BGP Key**|Enter the key of the BGP group.|
    |**Description**|Enter a description of the BGP group.|


## Step 2: Add a BGP peer {#section_lpj_tyx_dfb .section}

To add a BGP peer, follow these steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select a region and click the ID of the target VBR.
4.  Click the **BGP Peers** tab, and then click **Create BGP Peer**.

    ![BGP neighbors](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/156507295212050_en-US.png)

5.  Configure the BGP peer, and then click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**BGP Group**|Select the BGP group to which you want to add the BGP peer.|
    |**BGP peer IP Address**|Enter the IP address of the BGP peer.|

    ![The status of the BGP peer.](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/156507295253875_en-US.png)

    A BGP peer can be in the following states:

    -   **Idle**: Indicates that BGP is in the idle state, which is the first state that a newly added BGP peer enters. In the Idle state, BGP waits for a start event. After the start event appears, BGP initializes resources, resets the ConnectRetry timer, initiates a TCP connection, and then enters the Connect state.
    -   **Connect**: In the Connect state, BGP initiates the first TCP connection. If the ConnectRetry timer depletes before the TCP connection is established, a new TCP connection is initiated and the BGP peer remains in the Connect state.
        -   If the new TCP connection is successful, the BGP peer enters the OpenSent state.
        -   If the new TCP connection fails, the BGP peer enters the Active state.
    -   **Active**: In the Active state, BGP starts a new TCP connection. If the ConnectRetry timer depletes, the state moves to Connect.
        -   If the TCP connection is successful, the BGP peer enters the OpenSent state.
        -   If the TCP connection fails, the BGP peer remains in the Active state and a new TCP connection is initiated.
    -   **OpenSent**: In this state, an Open message has been sent. BGP is awaiting for an Open message from the peer. After the OPEN message is received from the peer, BGP checks both OPEN messages for errors.
        -   If an error occurs, the system sends an error message and BGP returns to the Idle state.
        -   If the Open messages do not have any errors, BGP sends a Keepalive message and resets the Keepalive timer. The connection state is moved to OpenConfirm.
    -   **OpenConfirm**: In this state, BGP waits for a Keepalive packet.
        -   If BGP receives a Keepalive packet, the state changes to Established, which indicates that the BGP neighbor relationship is established.
        -   If the TCP connection is interrupted, the BGP peer returns to the Idle state.
    -   **Established**: In this state, the BGP neighbor relationship is established. BGP peers exchange routes via Update messages. The Hold Timer is reset.
    -   **UnEstablished**: Indicates that the neighbor relationship is not established.

## Step 3: Advertise the BGP CIDR block {#section_lbw_wzx_dfb .section}

After configuring the BGP peer, you need to advertise the CIDR block of the on-premises data center. After BGP configuration is completed, the VBR automatically learns the CIDR block of the on-premises data center.

To advertise the CIDR block of the on-premises data center, follow these steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, choose **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select a region and click the ID of the target VBR.
4.  Click the **Advertised BGP Subnets** tab, and then click **Advertise BGP Subnet**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/156507295212051_en-US.png)

5.  Enter the CIDR block to be advertised, and then click **OK**.

