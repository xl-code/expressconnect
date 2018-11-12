# Configure BGP {#concept_ljj_4vx_dfb .concept}

You can establish Border Gateway Protocol \(BGP\) routing between a local IDC and a Virtual Border Router \(VBR\). You only need to add the BGP peers that communicate with the VBR to the corresponding BGP group, and then add the BGP CIDR block in the VBR.

**Note:** Express Connect allows you only to establish BGP routing between a VBR and a local IDC. In the physical connection access process, you still need to add a route destined for the VPC and the physical connection for the VBR. For more information, see [Add route entries](intl.en-US/User Guide/Virtual border router/Add route entries.md#).

## BGP overview {#section_e3x_wwx_dfb .section}

BGP, a dynamic routing protocol based on the TCP protocol, is used to exchange routing and network accessibility information among Autonomous Systems \(ASs\). During physical connection access, you can use BGP to implement intranet interconnection between the local IDC and the VBR. BGP can help you build a hybrid cloud in a more efficient, flexible, and reliable way.

Before configuring GBP, you need to create a BGP group. BGP groups are used to simplify BGP configurations. Adding repeated configurations into a BGP group can make configurations easier. You only need to create a BGP group according to the ASN and add qualified BGP peers into the group. The added BGP peers will inherit the configurations of the BGP group. You do not need to configure the BGP peers separately.

## Limits {#section_ksj_qxx_dfb .section}

The limits on using BGP are as follows:

-   The VBR can establish BGP peers only with the peer local IDC. Static routing is still needed between the VBR and the VPC.
-   The supported BGP version is BGP4.
-   The VBR supports IPv4 BGP, but does not support IPv6 BGP.
-   Up to eight BGP peers can be created under each VBR.
-   Up to 100 dynamic route entries can be added to a BGP peer.
-   The Alibaba Cloud-side Autonomous System Number \(ASN\) is 45104. The customer side can transmit 2-byte or 4-byte ASN.

## Step 1: Create a BGP Group {#section_uks_sxx_dfb .section}

Before configuring BGP routing, you need to create a BGP group according to the requested ASN.

Do the following to create a BGP:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select a region and click the ID of the target VBR.
4.  Click the **BGP Groups** tab page, and then click **Create BGP Group**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/154200595812049_en-US.png)

5.  Configure the BGP group, and then click **OK**.

    |Configuration item|Description|
    |:-----------------|:----------|
    |**Name**|Enter the name of the BGP group.|
    |**Peer AS No.**|Enter the AS number of the local IDC network.|
    |**BGP Key**|Enter the key of the BGP group.|
    |**Description**|Enter a description of the BGP peer group.|


## Step 2: Add a BGP peer {#section_lpj_tyx_dfb .section}

Do the following to add a BGP peer:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select a region and click the ID of the target VBR.
4.  Click the **BGP Peers** tab page, and then click **Create BGP Peer**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/154200595812050_en-US.png)

5.  Configure the BGP peer, and then click **OK**.

    |Configuration item|Description|
    |:-----------------|:----------|
    |**BGP Group**|Select the BGP group to which you want to add the BGP peer.|
    |**BGP peer IP Address**|Enter the IP address of the BGP peer.|


## Step 3: Add the BGP CIDR block {#section_lbw_wzx_dfb .section}

After configuring the BGP peer, you need to add the CIDR block of the local IDC.

Do the following to add the CIDR block of the local IDC:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select a region and click the ID of the target VBR.
4.  Click the **Add BGP CIDR Block** tab page, and then click **Add BGP CIDR Block**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/154200595812051_en-US.png)

5.  Enter the CIDR block to be added, and then click **OK**.

