# Configure health check {#concept_i5p_mgb_ydb .concept}

To guarantee smooth switch between two redundant leased lines in case of fault, you must configure the health check. The following figure shows how the health check works:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13859/15382994554028_en-US.png)

Alibaba Cloud sends a ping packet to the customer-side IP address of the local data center from each health check IP address every two seconds. If eight successive ping packets on one leased line fail to give response, the traffic is switched to the other leased line.

## Prerequisites {#section_rxr_dhb_ydb .section}

You have configured ECMP pointing to the on-premises IDC in the VPC. For more information, see [Redundant physical connection](reseller.en-US/User Guide/Redundant leased line access.md#).

## Procedure {#section_o4m_tcg_h2b .section}

Complete these steps to configure health check IP addresses in the router interfaces of the VPC.

**Note:** You only need to configure health check on router interfaces pointing to the VBRs, and do not need to configure health check on router interfaces pointing to the VPCs.

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, click **VPC Connection** \> **Router Interface**.
3.  Click **More** \> **Health Check** in the **Actions** column of the target router interface.
4.  Click **Configuration**, configure the following information in the displayed dialog box, and click **OK**.
    -   **SourceIp**: Enter a free IP address of the VPC as the health check IP address.
    -   **TargetIp**: Enter the customer-side IP address of the local data center.
5.  Repeat the preceding steps to configure the health check IP address for the other router interface.

    **Note:** In multi-VPC scenarios, you must configure health check IP addresses for router interfaces of all VPCs connected to redundant leased lines to guarantee smooth switch between the redundant leased lines.


