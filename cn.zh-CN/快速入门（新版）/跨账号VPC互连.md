# 跨账号VPC互连 {#concept_wrx_vbr_ydb .concept}

本教程指引您如何使用高速通道实现不同账号下的两个VPC互通。

## 教程示例 {#section_ock_bcr_ydb .section}

本操作以如下两个VPC为例。跨账号专有网络互通时，需要分别创建连接发起端和接收端，然后在建立对等连接，最后配置路由。本教程中，账号A的VPC1将作为连接发起端，账号B的VPC2作为连接接收端。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153792830311706_zh-CN.png)

## 前提条件 {#section_kdw_xbr_ydb .section}

-   已获取对方的阿里云账号ID和要连接的VPC的路由器ID。
-   确保要进行互连的VPC或交换机的网段不冲突。

## 步骤一 创建发起端 {#section_ldw_xbr_ydb .section}

账号A需要为互连的VPC创建连接发起端实例。

完成以下操作，创建发起端：

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  单击**创建对等连接**。
4.  配置对等连接。

    本操作使用如下配置：

    **说明：** 如果您要通过高速通道连接中国大陆和境外（含香港）的专有网络，请选择中国联通跨境。跨境互通由中国联通运营。

    -   **账号类型**：选择**跨账号**。

    -   **连接场景**：选择**VPC互连**。

    -   **创建路由器**：选择**只创建发起端**。

        只有连接发起端才可以主动向接收端发起连接。

    -   **地域**：选择要互通的VPC的所属地域，本操作选择**华北1 （青岛）**。

    -   **本端VPC ID**：选择要互通的VPC，本操作选择**VPC1**。

    -   **对端地域**：选择要连接的VPC的所属地域，本操作中选择**华北2 （北京）**。

    -   **带宽值**：选择专有网络互通的带宽，本操作选择**2Mb**。

5.  单击**立即购买**，并完成支付。
6.  回到专有网络对等连接页面，查看已创建的对等连接。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15379283034203_zh-CN.png)


## 步骤二 创建接收端 {#section_ugv_m3n_cfb .section}

账号B需要为要互连的VPC创建接接收端实例。

完成以下操作，创建接收端：

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  单击**创建对等连接**。
4.  配置对等连接。

    本操作使用如下配置：

    **说明：** 如果您要通过高速通道连接中国大陆和境外（含香港）的专有网络，请选择中国联通跨境。跨境互通由中国联通运营。

    -   **账号类型**：选择**跨账号**。

    -   **连接场景**：选择**VPC互连**。

    -   **创建路由器**：选择**只创建接收端**。

        只有连接发起端才可以主动向接收端发起连接。

    -   **地域**：选择VPC的所属地域，本操作选择**华北2 （北京）**。

    -   **本端VPC ID**：选择要连接的VPC，本操作选择**VPC2**。

    -   **对端地域**：选择要连接的VPC的所属地域，本操作中选择**华北1（青岛）**。

    -   **带宽值**：接受端的带宽由发起端决定，本操作选择**默认**。

5.  单击**立即购买**，并完成支付。
6.  在专有网络对等连接页面，查看已创建的对等连接，并记录已创建的接受端实例ID（本操作的实例ID为ri-2zec2ufrp2cdyz687wo8s）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15379283034204_zh-CN.png)


## 步骤三 建立对等连接 {#section_b4x_zgr_ydb .section}

在创建好发起端和接收端后，发起端可以主动发起连接，在两个VPC之间建立对等连接。

本教程中连接发起端是账号A的VPC。使用账号A登录阿里云控制台后，完成成以下操作，建立对等连接：

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  选择发起端实例的地域。

    本操作选择**华北1（杭州）**。

4.  单击**添加接收端**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153792830311720_zh-CN.png)

5.  完成以下操作添加接收端：

    1.  **账号类型**：选择跨账号。
    2.  **接收端账号Uid**：要接收端VPC的所属账号ID。
    3.  **接收端路由器**：接收端VPC的路由器ID。
    4.  **接收端路由器**：接收端的实例ID。
    5.  单击**确定**。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153792830311721_zh-CN.png)

6.  
## 步骤四 配置路由 {#section_tdw_xbr_ydb .section}

建立对等连接后，您还需要分别为互连的VPC添加路由。

完成以下操作，配置路由：

1.  在专有网络对等连接页面，找到已创建的对等连接。
2.  单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153792830311689_zh-CN.png)** \> **发起端路由配置**

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153792830311686_zh-CN.png)

3.  单击**添加对端路由**，然后要连接的VPC或其交换机的网段，单击**确定**。

    本操作输入对端VPC的网段172.16.0.0/16。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153792830311699_zh-CN.png)

4.  单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153792830311689_zh-CN.png)** \> **接收端路由配置**

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153792830311700_zh-CN.png)

5.  单击**添加对端路由**，然后要连接的VPC或其交换机的网段，单击**确定**。

    本操作输入对端VPC的网段192.168.0.0/16。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153792830311699_zh-CN.png)


## 步骤五 测试 {#section_hj4_55m_cfb .section}

建立对等连接，并添加路由后，您可以登录到其中一个专有网络的ECS实例上，ping已连接的专有网络中的ECS实例的私网IP。如果可以ping通，则表示两个VPC已经成功连接。

