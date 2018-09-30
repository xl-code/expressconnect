# Advertise a BGP network {#concept_lym_fdb_ydb .concept}

You can use BGP to connect a VBR to a local data center. You only need to add BGP peers that communicate with the VBR to the corresponding BGP group, and advertise the BGP network in the VBR, then BGP dynamic routing can be achieved between the local data center and the VBR.

**Note:** BGP can only be used to achieve dynamic routing between a local data center and a VBR. If you need to connect a local data center to a VPC, you still need to configure a static route for the VBR and the VPC respectively. For more information, see [Access a VPC under the same account through a physical connection](../../../../reseller.en-US/Tutorials/Connect a local data center to a VPC through a physical connection.md#).

## Prerequisites {#section_gng_rdb_ydb .section}

-   [Create BGP peer groups](reseller.en-US/User Guide/BGP/Manage BGP peer groups.md#section_q2j_hz1_ydb)
-   [Create BGP peers](reseller.en-US/User Guide/BGP/Manage BGP peers.md#section_fxm_rbb_ydb)
-   [Create a VBR](reseller.en-US/User Guide/VBR/Create a virtual border router.md#)

## Procedure {#section_j2f_tdb_ydb .section}

1.  Log on to the [Express Connect console](https://partners-intl.aliyun.com/login-required#/ri).
2.  In the left-side navigation pane, click **Physical Connection** \> **Virtual Border Router**.
3.  Click the ID of the target VBR.
4.  Click **Advertise BGP Network** on VBR Details page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13858/15382994304025_en-US.png)

5.  Enter the VPC CIDR block or VSwitch CIDR block to be connected with the local data center, and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13858/15382994304027_en-US.png)


