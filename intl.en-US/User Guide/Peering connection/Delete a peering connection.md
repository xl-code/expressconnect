# Delete a peering connection {#concept_fvf_n1q_hfb .concept}

Before you can delete a peering connection, you need to delete the route entries of the initiator and the receiver.

## Step 1: Delete route entries {#section_mvg_lnp_hfb .section}

Do the following to remove the defined route entries:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left navigation pane, click **PVC Peering Connections** \> **VPC-to-VPC**.
3.  Select the region where your instance is located and find your target connection.
4.  Click the VPC ID of the initiator. On the VPC Details page, click the VPC ID again.
5.  In the **Network Resources** area, click the route table link and then click the route table ID.
6.  Locate the custom route entry destined for the local IDC and then click **Delete**.
7.  In the displayed dialog box, click **OK**.
8.  Repeat the preceding steps to delete the route entries of the acceptor.

## Step 2: Delete the peering connection {#section_uzh_gbq_hfb .section}

Follow these steps to delete the peeing connection:

1.  Log on to the [Express Connect](https://expressconnectnext.console.aliyun.com) console.
2.  In the left navigation pane, click **VPC Peering Connections** \> **VPC-to-VPC**.
3.  Select the region where your instance is located and find your target connection.
4.  Click **![](images/12053_en-US.png)** \> **Suspend Initiator**. In the displayed dialog box, click **Confirm**.
5.  Click **![](images/12053_en-US.png)** \> **Suspend Acceptor**. In the displayed dialog box, click **Confirm**.
6.  Click **![](images/12053_en-US.png)** \> **Delete**. In the displayed dialog box, click **Confirm**.

