# Delete a peering connection {#concept_fvf_n1q_hfb .concept}

Before you can delete a peering connection, you must delete the route entries of its initiator and acceptor.

## Step 1: Delete route entries {#section_mvg_lnp_hfb .section}

To delete the custom route entries, follow these steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select a region and find your target peering connection.
4.  Click the VPC ID of the initiator. On the VPC Details page, click the VPC ID again.
5.  In the **Network Resources** section, click the route table link. On the displayed **Route Tables** page, click the route table ID.
6.  Find the custom route entry destined for the on-premises data center and then click **Delete**.
7.  In the displayed dialog box, click **OK**.
8.  Repeat the preceding steps to delete the route entries of the acceptor.

## Step 2: Delete the peering connection {#section_uzh_gbq_hfb .section}

To delete the peering connection, follow these steps:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, choose **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select a region and find your target peering connection.
4.  Choose **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/156050008312053_en-US.png)** \> **Suspend Initiator**. In the displayed dialog box, click **Confirm**.
5.  Choose **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/156050008312053_en-US.png)** \> **Suspend Acceptor**. In the displayed dialog box, click **Confirm**.
6.  Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21440/156050008312053_en-US.png)** \> **Delete**. In the displayed dialog box, click **Confirm**.

