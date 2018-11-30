# Delete peering connections {#concept_fvf_n1q_hfb .concept}

Before you can delete a peering connection, you must first delete the route entries of its initiator and acceptor.

## Step 1: Delete route entries {#section_mvg_lnp_hfb .section}

Perform the following steps to delete the custom route entries:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, click **PVC Peering Connections** \> **VPC-to-VPC**.
3.  Select a region and find your target peering connection.
4.  Click the VPC ID of the initiator. On the VPC Details page, click the VPC ID again.
5.  In the **Network Resources** area, click the route table link. On the displayed Route Tables page, click the route table ID.
6.  Find the custom route entry destined for the local IDC and then click **Delete**.
7.  In the displayed dialog box, click **OK**.
8.  Repeat the preceding steps to delete the route entries of the acceptor.

## Step 2: Delete the peering connection {#section_uzh_gbq_hfb .section}

Perform the following steps to delete the peering connection:

1.  Log on to the [Express Connect](https://partners-intl.console.aliyun.com/#/ri) console.
2.  In the left-side navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select a region and find your target peering connection.
4.  Click **![](images/12053_en-US_source.png)** \> **Suspend Initiator**. In the displayed dialog box, click **Confirm**.
5.  Click **![](images/12053_en-US_source.png)** \> **Suspend Acceptor**. In the displayed dialog box, click **Confirm**.
6.  Click **![](images/12053_en-US_source.png)** \> **Delete**. In the displayed dialog box, click **Confirm**.

