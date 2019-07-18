# Migrate a VBR in a peering connection to a CEN instance {#concept_778480 .concept}

This topic describes how to migrate a Virtual Border Router \(VBR\) that uses a peering connection to a Cloud Enterprise Network \(CEN\) instance. By using CEN, you can build private network communication channels between VPCs or between VPCs and on-premises data centers. CEN uses automatic route distribution and learning, which can improve the network convergence and the quality and security of cross-network communication, and achieve the interconnection of all network resources.

## Prerequisites {#section_eqb_6jw_1q8 .section}

If you want to use an existing CEN instance, make sure that the overlapping routing function is enabled.

**Note:** If the overlapping routing function is not enabled for a CEN instance, enable the function first.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630333/156344530149935_en-US.png)

## Procedure {#section_jva_nyi_5pq .section}

To migrate a VBR in a peering connection to a CEN instance, follow these steps:

**Note:** Make sure that you have made the necessary preparations before migration.

1.  If you have enabled the health check function for the VBR, we recommend that you first disable the health check function in the Express Connect console.
2.  Log on to the [CEN console](https://cen.console.aliyun.com).
3.  On the Instances page, find the target CEN instance and click the instance ID.
4.  On the Networks tab, click **Attach Network** and add the VBR and VPC to be migrated. For more information, see [Networks](../../../../intl.en-US/User Guide/Networks.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630370/156344530249948_en-US.png)

5.  If the VBR and VPC need to communicate with other resources that belong to different regions, you need to buy a bandwidth package and set an intranet communication bandwidth value.

    For more information, see [Set a cross-region interconnection bandwidth](../../../../intl.en-US/User Guide/Cross-region interconnection bandwidth.md#section_gtq_n5n_tdb).

6.  If you have added routes destined for ECS instances, VPN Gateways, or High-Availability Virtual IP Addresses \(HaVips\) in the VPC, you need to publish these routes to the CEN instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630439/156344530249940_en-US.png)

7.  If an on-premises data center needs to access cloud resources, such as OSS and PrivateZone, perform the configurations through the CEN console.

    For more information, see [Set AnyTunnel services](../../../../intl.en-US/User Guide/Access cloud services/Set AnyTunnel services.md#) and [Set PrivateZone access](../../../../intl.en-US/User Guide/Access cloud services/PrivateZone/Set PrivateZone access.md#).

8.  Log on to the [CEN console](https://cen.console.aliyun.com/cen/detail/cen-0e7i2gmdfs6ymbxgay/route), click the ID of the target CEN instance, and on the **Routes** tab, check the routes. Make sure that the routes do not conflict with each other after you add the VBR and VPC to the CEN instance.

    The static route configured for the peering connection takes precedence over the dynamic route of the CEN instance. Specifically, if a static route is configured for the peering connection, no CEN route that is more detailed than or the same as the static route is allowed to be learnt by the CEN instance. In this case, we recommend that you divide a large route segment into smaller route segments and delete these routes after CEN learns the routes to ensure smooth migration.

    For example, the CEN route 192.168.1.0/24 in the following figure is more detailed than the route 192.168.0.0/16 configured for the peering connection, which constitutes a route conflict.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630370/156344530249949_en-US.png)

    -   You can directly delete the route of the peering connection. Then, the CEN route takes effect automatically. However, this method causes intermittent disconnections.

        The duration of disconnections is in proportion to the number of CEN routes. Therefore, we recommend that you use the following method to smoothly migrate the VPC for important services.

    -   You can divide the peering connection route 192.168.0.0/16 into two smaller route segments, 192.168.1.0/25 and 192.168.1.128/25, which are smaller than the CEN route 192.168.1.0/24.
        1.  Log on to the [Express Connect console](https://expressconnectnext.console.aliyun.com/vbr/cn-hangzhou/detail/vbr-bp1qg7vzlr2kjeak81e28), find the target VBR, click the VBR ID, and then click the **Routes** tab.
        2.  Click **Add Route**. Add two routes that are respectively destined for 192.168.1.0/25 and 192.168.1.128/25 with the next hop type of VPCs.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630370/156344530249950_en-US.png)

        3.  For BGP routing, you need to advertise the CIDR blocks related to 192.168.1.0/25 and 192.168.1.128/25.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630370/156344530249951_en-US.png)

        4.  Delete the peering connection route 192.168.0.0/16.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630370/156344530349952_en-US.png)

        5.  Click **Refresh** and check whether the CEN route has taken effect.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630370/156344530349953_en-US.png)

        6.  Delete the two routes 192.168.1.0/25 and 192.168.1.128/25 in the VBR route table, and delete the advertised BGP routes.
        7.  In the CEN console, configure health checks for the migrated VBR. For more information, see [Configure health check](../../../../intl.en-US/User Guide/Health check.md#section_hv3_qzn_tdb).

