# 宣告BGP网段 {#concept_lym_fdb_ydb .concept}

您可以通过BGP实现边界路由器（VBR）与本地数据中心的互连。您仅需将与VBR通信的BGP邻居添加到对应的BGP组中，然后在VBR中宣告BGP网段即可在本地数据中心和VBR之间建立BGP动态路由。

**说明：** BGP功能只用于建立用户的本地数据中心与VBR之间的动态路由，如果你需要实现本地数据中心与VPC之间的互连，仍需要在VBR和VPC上配置相应静态路由，详情参见[物理专线接入](../../../../intl.zh-CN/快速入门（新版）/物理专线接入.md#)。

## 前提条件 {#section_gng_rdb_ydb .section}

-   [创建BGP组](intl.zh-CN/用户指南/BGP/管理BGP组.md#section_q2j_hz1_ydb)
-   [创建BGP邻居](intl.zh-CN/用户指南/BGP/管理BGP邻居.md#section_fxm_rbb_ydb)
-   [创建边界路由器](intl.zh-CN/用户指南/边界路由器/创建边界路由器.md#)

## 操作步骤 {#section_j2f_tdb_ydb .section}

1.  登录[高速通道管理控制台](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list)。
2.  在左侧导航栏，单击**物理专线连接** \> **边界路由器**。
3.  单击目标边界路由器的ID链接。
4.  在边界路由器详情页面，单击**宣告BGP网段**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13858/15382994254025_zh-CN.png)

5.  输入需要和本地数据中心互连的VPC或交换机的网段，然后单击**确定**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13858/15382994254027_zh-CN.png)


