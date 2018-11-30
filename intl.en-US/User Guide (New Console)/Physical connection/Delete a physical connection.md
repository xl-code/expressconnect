# Delete a physical connection {#concept_idv_sc4_hfb .concept}

When you no longer need a physical connection, you can delete it by following the steps provided in this document.

Follow these steps to delete a physical connection:

**Note:** To delete a physical connection, you must use the following sequence.

1.  Delete the route entries configured in the VBR and the VPC router.
2.  Delete related BGP peers and BGP groups if BGP routing is configured.
3.  Delete the peering connection between the VPC and the VBR.
4.  Delete all associated VBRs.
5.  Delete the physical connection.

## Step 1: Delete route entries {#section_mvg_lnp_hfb .section}

Follow these steps to delete the custom route entries in the VPC and VBR:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left navigation pane, click **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Select the region where your VBR-to-VPC connection is located and find the connection.
4.  Click the ID of the acceptor VPC. On the VPC Details page, click the VPC ID again.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/22175/154355166513241_en-US.png)

5.  In the **Network Resources** area, click the route table link. Then click the route table ID.
6.  Locate the custom route entry destined for the local IDC and then click **Delete**.
7.  In the displayed dialog box, click **OK**.
8.  In the left navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs \)**.
9.  Select the region of the VBR and then click the ID of the target VBR instance.
10. Click the **Route Entries** tab.
11. Delete the route entries added in the VBR.

## Step 2: Delete BGP peers and BGP groups {#section_enb_2sp_hfb .section}

If you have configured BGP, follow these steps to delete the BGP configurations associated with the VBR:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select the region of the VBR and then click the ID of the target VBR instance.
4.  Click the **BGP Peers** tab and then delete the created BGP peers.
5.  Click the **BGP Groups** tab and then delete the created BGP groups.
6.  Click the **BGP CIDR Blocks** tab and then delete the added BGP CIDR blocks.

## Step 3: Delete peering connections {#section_xyr_nsp_hfb .section}

Follow these steps to delete the peering connection between the VBR and the VPC:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left navigation pane, click **VPC Peering Connections** \> **VBR-to-VPC**.
3.  Select the region where your VBR-to-VPC connection is located and find the connection.
4.  Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/154355166512053_en-US.png)** \> **Suspend Initiator**. In the displayed dialog box, click **Confirm**.
5.  Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/154355166512053_en-US.png)** \> **Suspend Acceptor**. In the displayed dialog box, click **Confirm**.
6.  Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/154355166512053_en-US.png)** \> **Delete**. In the displayed dialog box, click **Confirm**.

## Step 4: Delete the VBRs {#section_y32_ltp_hfb .section}

Follow these steps to delete the VBRs:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left navigation pane, click **Physical Connections** \> **Virtual Border Routers \(VBRs\)**.
3.  Select the region where the VBR is located.
4.  Find the target VBR and click **Delete**.
5.  In the displayed dialog box, click **Confirm**.

## Step 5: Delete the physical connection interface {#section_xdd_stp_hfb .section}

Complete the following steps to delete the physical connection interface:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, click **Physical Connections** \> **Physical Connection Interfaces**.
3.  Select the region of the physical connection interface.
4.  Find the target physical connection interface and click **Delete**.
5.  In the displayed dialog box, click **Confirm**.

