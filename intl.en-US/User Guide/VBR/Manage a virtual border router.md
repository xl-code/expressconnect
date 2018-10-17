# Manage a virtual border router {#concept_bxn_ch1_ydb .concept}

## Modify a VBR {#section_zyb_fh1_ydb .section}

You can modify the name, circuit code and description of a VBR to facilitate maintenance.

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Physical Connection** \> **Virtual Border Router**.
3.  Click **Manage** in the **Actions** column of the target VBR.
4.  In **Basic Information** on the page of VBR details, click **Modify Info**.
5.  Enter the **VRouter Name**, **Circuit Code**, and **VRouter Description** of the VBR, and click **OK**.

## Modify IP addresses {#section_q1n_131_ydb .section}

You can modify the IP addresses of a VBR according to your network design.

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Physical Connection** \> **Virtual Border Router**.
3.  Click **Manage** in the **Actions** column of the target VBR.
4.  Find the target leased line in **Physical Connection Info** on the page of VBR details, and click **Modify Info** in the **Actions** column of the target leased line.
5.  In the displayed dialog box, modify the IP addresses of the VBR according to the following information, and click **OK**.
    -   **Alibaba Cloud-Side**: Enter the IP address used as the gateway to connect to the local data center.
    -   **Customer-Side**: Enter the IP address used as the gateway to connect to the VPC.
    -   **Subnet Mask**: The subnet mask of the Alibaba Cloud-side IP address and the customer-side IP address. Because only two IP addresses are required, you can enter a long subnet mask.

## Delete a VBR {#section_f3c_1j1_ydb .section}

Before deleting a leased line, you need to delete VBRs associated with the leased line. Before this operation, you also need to delete corresponding route entries and router interfaces. For more information, see [Remove a physical connection](reseller.en-US/User Guide/Remove a physical connection.md#).

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, select **Physical Connection** \> **Virtual Border Router**.
3.  Click **Delete** in the **Actions** column of the target VBR, and then click **Confirm** in the displayed dialog box.

