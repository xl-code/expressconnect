# 多VPC专线接入 {#concept_p1l_rk5_ydb .concept}

您可以复用已接入到阿里云接入点的物理专线，连接多个VPC。本教程指引您如何使用一条已申请的物理专线将本地IDC和不同账号的两个VPC连接起来。

**说明：** 目前一根专线最多可连接5个VPC，可提交工单增加配额。

## 背景信息 {#section_d52_1l5_ydb .section}

本教程以下图的网络拓扑为例。某公司在阿里云上开通了账号A，并创建了专有网络VPC-A。账号A已经申请开通了一条物理专线将该公司的本地数据中心（172.16.0.0/12）和VPC-A连接了起来。该公司的一个子公司在阿里云上开通了一个账号B，账号B下有一个专有网络VPC-B。现在子公司希望将VPC-B与本地IDC连接起来。

由于账号A已经购买了专线并将本地IDC接入到阿里云的接入点上，所以子公司账号B可以复用这根专线，将其账号下的VPC和本地数据中心连接起来。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/15601361684227_zh-CN.png)

本教程中的VPC配置和专线配置如下：

|账号A|账号B|
|:--|:--|
|账号ID：12345678|账号ID：87654321|
|专有网络 -   名称：VPC-A
-   地域：华北2（北京）
-   VPC ID：vpc-12345678
-   CIDR block：10.10.0.0/16

 |专有网络 -   名称：VPC-B
-   地域：华东1（杭州）
-   VPC ID：vpc-87654321
-   CIDR block：192.168.0.0/16

 |
|专线连接 -   VBR名称：专有网络-北京
-   VBR ID：vbr-12345678
-   专线ID：pc-AAA
-   VLAN ID：1000

 |无|

## 教程概览 {#section_ary_zzb_mgb .section}

要将账号B下的VPC-B和本地IDC打通，且复用账号A的物理专线和边界路由器（VBR），您只需要在已创建的VBR和要连接的VPC-B间建立对等连接即可：

1.  [步骤一：创建连接发起端](#section_gxd_jsr_ggb) 

    在专线接入场景中，VBR必须是连接发起端。本操作中使用账号A为VBR创建一个路由器接口，作为连接发起端。

2.  [步骤二：创建接收端](#section_lpm_wl5_ydb) 

    为要连接的VPC的路由器创建路由器接口，作为连接接收端。

3.  [步骤三：添加接收端和发起端，建立对等连接](#section_ij3_fpb_mgb) 

    为已创建的路由器接口分别添加接收端和发起端，然后由发起端路由器接口发起连接。

4.  [步骤四：配置路由](#section_f4d_z45_ydb) 

    分别在VPC、VBR和本地IDC的接入设备中添加路由，完成流量转发。

5.  [步骤五：验收测试（可选）](#section_njh_gr5_ydb) 

    网络互通后，您可以测试物理专线速率，查看带宽是否满足业务需求。


## 前提条件 {#section_d34_x3r_ggb .section}

本地IDC已经和账号A的VPC-A通过物理专线建立连接，详情参考[物理专线接入](../../../../intl.zh-CN/快速入门/物理专线接入.md#)。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156013616835360_zh-CN.png)

## 步骤一：创建连接发起端 {#section_gxd_jsr_ggb .section}

完成以下操作，创建连接发起端：

1.  使用账号A登录[高速通道管理控制台](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list)。
2.  在左侧导航栏，选择**专有网络对等连接** \> **VBR上连**，然后单击**创建对等连接**。
3.  配置对等连接。

    本操作中的配置如下，详细配置说明，请参考[VBR上联](../../../../intl.zh-CN/专有网络对等连接/VBR上联.md#)。

    -   **账号类型**：选择**跨账号**。
    -   **连接场景**：选择**VBR上连**。
    -   **创建路由器场景**：选择**只创建发起端**。
    -   **地域**：选择已创建的边界路由器（VBR）的所属地域。本操作选择**华北2（北京）**。
    -   **接入点**：选择VBR连接的物理专线所属的接入点。
    -   **本端VBR ID**：选择已创建的VBR 。
    -   **对端地域**：选择要连接的VPC的所属地域。本操作选择**华东1（杭州）**。
    -   **带宽值**：选择私网互通的带宽。本操作选择**2Mb**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/15601361684230_zh-CN.png)

4.  查看已创建的发起端，并记录发起端路由器接口ID。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156013616837535_zh-CN.png)

## 步骤二：创建接收端 {#section_lpm_wl5_ydb .section}

创建发起端后，账号B需要为要连接的VPC创建接收端。

完成以下操作，创建接收端：

1.  使用账号B登录[高速通道管理控制台](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list)。
2.  在左侧导航栏，选择**专有网络对等连接** \> **VBR上连**，然后单击**创建对等连接**。
3.  配置对等连接。

    本操作中的配置如下，详细配置说明，请参考[VBR上联](../../../../intl.zh-CN/专有网络对等连接/VBR上联.md#)。

    -   **账号类型**：选择**跨账号**。
    -   **连接场景**：选择**VBR上连**。
    -   **创建路由器场景**：选择**只创建接收端**。
    -   **地域**：选择要连接的VPC地域。本操作选择**华东1（杭州）**。
    -   **本端VPC ID**：选择要连接的VPC。本操作选择VPC-B。
    -   **对端地域**：选择已创建的VBR的所属地域。本操作选择**华北2（北京）**。
    -   **对端接入点**：选择VBR连接的物理专线的所属接入点。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156013616835392_zh-CN.png)

4.  查看已创建的接收端，并记录接收端路由器接口ID。

## 步骤三：添加接收端和发起端，建立对等连接 {#section_ij3_fpb_mgb .section}

完成以下操作，在VPC和VBR之间建立对等连接：

1.  使用账号B登录[高速通道管理控制台](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list)。
2.  在左侧导航栏，选择**专有网络对等连接** \> **VBR上连**。
3.  选择连接接收端的地域，然后找到目标接收端，单击**添加发起端**。
4.  在添加实例页面，完成以下配置：
    1.  **账号类型**：选择**跨账号**。
    2.  **发起端路由器接口**：输入已创建的发起端路由器接口ID，比如ri-1234567。
    3.  单击**确定**。
5.  使用账号A登录[高速通道管理控制台](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list)。
6.  在左侧导航栏，选择**专有网络对等连接** \> **VBR上连**。
7.  选择连接发起端的地域，然后找到目标发起端，单击**添加接收端**。
8.  在添加实例页面，完成以下配置：
    1.  **账号类型**：选择**跨账号**。
    2.  **发起端路由器接口**：输入已创建的接收端路由器接口ID，比如ri-1234567。
    3.  单击**确定**。
9.  单击发起端实例操作列下的![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156013616937536_zh-CN.png)图标，然后单击**发起连接**。

    当接收端和发起端状态都变为已激活时，表示连接成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13863/156013616835360_zh-CN.png)


## 步骤四：配置路由 {#section_f4d_z45_ydb .section}

建立对等连接后，您还需要分别在VPC、VBR和本地数据中心配置路由。

**配置VBR的路由**

完成以下操作，在VBR中分别添加到IDC和VPC的路由：

1.  使用账号A登录[高速通道管理控制台](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list)。
2.  在左侧导航栏，选择**物理专线连接** \> **边界路由器（VBR）**。
3.  选择VBR的所属地域，然后单击目标VBR的ID。
4.  单击路由条目页签，然后单击**添加路由条目**。
5.  根据以下信息配置路由将VBR上访问IDC（网段：172.16.0.0/12）的流量转发至物理专线：
    1.  **目标网段**：本地IDC的网段。本操作中为172.16.0.0/12。
    2.  **下一跳类型**：选择**物理专线接口**。
    3.  **下一跳**：选择已创建的物理专线。
    4.  单击**确定**。
6.  再次单击**添加路由条目**将VBR上访问VPC（网段：192.168.0.0/16）的流量转发至VPC：

    1.  **目标网段**：要连接的VPC的网段。本操作中为192.168.0.0/16。
    2.  **下一跳类型**：选择**专有网络**。
    3.  **下一跳**：选择要连接的VPC。
    4.  单击**确定**。
    **配置VPC的路由**

    完成以下操作，将VPC中访问IDC（网段：172.16.0.0/12）的流量转发至VBR：

    1.  使用账号B登录[高速通道管理控制台](https://vpc.console.aliyun.com/expressConnect#/connection/cn-hangzhou/list)。
    2.  在左侧导航栏，选择**专有网络对等连接** \> **VBR上连**。
    3.  选择对等连接的地域，找到接收端实例，然后单击**路由配置**。
    4.  单击**添加对端路由**，然后在弹出的对话框中输入本地IDC的网段（本操作中为172.16.0.0/12）。单击**确认**。

**IDC路由配置**

至此，已完成阿里云上的路由配置，本地IDC的专线接入设备还需增加VPC网段的路由，指向专线阿里云侧IP，例如：

``` {#codeblock_lle_gao_30g}
ip route 192.168.0.0/16 10.100.0.1
```

## 步骤五：验收测试 {#section_njh_gr5_ydb .section}

网络互通后，请测试物理专线速率，确保满足业务需求。详细测速方法请参考[物理专线网络性能测试](intl.zh-CN/最佳实践/物理专线网络性能测试方法.md#)。

