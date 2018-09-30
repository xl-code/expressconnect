# 跨账号VPC互连 {#concept_wrx_vbr_ydb .concept}

本教程指引您使用高速通道连接两个不同账号的VPC。

## 教程示例 {#section_ock_bcr_ydb .section}

跨账号专有网络互通时，需要分别创建发起端和接收端，然后建立对等连接，最后配置路由。本操作以如下两个VPC为例。账号A的VPC1将作为连接发起端，账号B的VPC2作为连接接收端。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153829877011706_zh-CN.png)

## 前提条件 {#section_kdw_xbr_ydb .section}

-   已获取对方的阿里云账号ID和要连接的VPC的路由器ID。
-   确保要进行互连的VPC或交换机的网段不冲突。

## 步骤一 创建发起端 {#section_ldw_xbr_ydb .section}

完成以下操作，创建发起端：

1.  使用账号A登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  单击**创建对等连接**。
4.  配置对等连接。

    本操作使用如下配置：

    -   **账号类型**：选择**跨账号**。

    -   **连接场景**：选择**VPC互连**。

    -   **创建路由器**：选择**只创建发起端**。

        只有连接发起端才可以主动向接收端发起连接。

    -   **地域**：选择VPC的所属地域，本操作选择**华北1 （青岛）**。

    -   **本端VPC ID**：选择为其创建发起端实例的VPC，本操作选择**VPC1**。

    -   **对端地域**：选择要连接的VPC的所属地域，本操作选择**华北2 （北京）**。

    -   **带宽值**：选择互通的带宽，本操作选择**2Mb**。

5.  单击**立即购买**，并完成支付。
6.  返回专有网络对等连接页面，查看已创建的对等连接。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15382987704203_zh-CN.png)


## 步骤二 创建接收端 {#section_ugv_m3n_cfb .section}

完成以下操作，创建接收端：

1.  使用账号B登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  单击**创建对等连接**。
4.  配置对等连接。

    本操作使用如下配置：

    -   **账号类型**：选择**跨账号**。

    -   **连接场景**：选择**VPC互连**。

    -   **创建路由器**：选择**只创建接收端**。

    -   **地域**：选择VPC的所属地域，本操作选择**华北2 （北京）**。

    -   **本端VPC ID**：选择为其创建接收端实例的VPC，本操作选择**VPC2**。

    -   **对端地域**：选择要连接的VPC的所属地域，本操作选择**华北1（青岛）**。

    -   **带宽值**：接收端的带宽由发起端决定，本操作选择**默认**。

5.  单击**立即购买**，完成支付。
6.  在专有网络对等连接页面，查看已创建的对等连接，并记录已创建的接收端实例ID（本操作的实例ID为ri-2zeix2q86uoyisagyz0pn）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/15382987704204_zh-CN.png)


## 步骤三 添加发起端 {#section_w2d_l3f_hfb .section}

在创建发起端和接收端后，还需要为接收端添加发起端。

完成成以下操作，为已创建的接收端添加发起端：

1.  使用账号B登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  选择发起端实例的地域。

    本操作选择**华北2（北京）**。

4.  找到已经创建的接收端实例，然后单击**添加发起端**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153829877013085_zh-CN.png)

5.  在添加实例页面，选择**跨账号**，然后输入发起端路由器接口（本操作为ri-m5e33r3n78zyi5573kf85）。单击**确定**。

## 步骤四 添加接收端并建立对等连接 {#section_b4x_zgr_ydb .section}

在添加发起端和接收端后，发起端可以主动发起连接在两个VPC之间建立对等连接。

本教程中连接发起端是账号A的VPC。完成成以下操作，建立对等连接：

1.  使用账号A登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  选择发起端实例的地域。

    本操作选择**华北1（杭州）**。

4.  单击**添加接收端**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153829877011720_zh-CN.png)

5.  在添加实例页面，选择**跨账号**，然后输入接收端路由器接口（本操作为ri-2zeix2q86uoyisagyz0pn）。单击**确定**。
6.  单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153829877011689_zh-CN.png)** \> **发起连接**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153829877013014_zh-CN.png)

    连接成功后，发起端和接收端状态会变成已激活。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153829877011684_zh-CN.png)


## 步骤四 配置路由 {#section_tdw_xbr_ydb .section}

建立对等连接后，您还需要分别为互连的VPC添加路由。

完成以下操作，配置路由：

1.  使用账号A登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在专有网络对等连接页面，找到已创建的对等连接。
3.  找到发起端实例，然后单击**路由配置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153829877011686_zh-CN.png)

4.  单击**添加对端路由**，然后输入要连接的VPC或其交换机的网段，单击**确定**。

    本操作输入对端VPC的网段172.16.0.0/16。

5.  使用账号B登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
6.  找到接收端实例，然后单击**路由配置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153829877011700_zh-CN.png)

7.  单击**添加对端路由**，然后输入要连接的VPC或其交换机的网段，单击**确定**。

    本操作输入对端VPC的网段192.168.0.0/16。


## 步骤五 配置安全组 {#section_zx1_ndf_hfb .section}

在两个VPC间建立对等连接后，您还需要配置安全组规则，实现两个VPC内的ECS实例的互通。

本操作以下表中的ECS实例和安全组配置为例。

|配置信息|账号A|账号B|
|:---|:--|:--|
|账号ID|AccountID\_A|AccountID\_B|
|ECS实例ID|InstanceID\_A|InstanceID\_B|
|安全组ID|SecurityGroupID\_A|SecurityGroupID\_B|

您可以在[账号中心](https://account.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.39.4cb94bd3LoJmJ3#/secure)查看账号ID。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/153829877013186_zh-CN.png)

完成以下操作，配置安全组规则：

1.  登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏，单击**网络和安全** \> **安全组**。
3.  选择实例的地域。
4.  找到目标安全组，然后单击**配置规则**。
5.  在安全组规则页面，单击**添加安全组规则**。
6.  配置安全组规则，根据您的需要选择协议类型并输入端口。其中：

    -   **授权类型**：选择**安全组访问**，并选择**跨账号授权**。
    -   **授权对象**：输入允许访问实例关联的安全组ID。
    -   **账号ID**：输入对端账号的ID。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13829/153829877013193_zh-CN.png)


## 步骤六 测试 {#section_hj4_55m_cfb .section}

建立对等连接，并添加路由后，您可以登录到其中一个专有网络的ECS实例上，ping已连接的专有网络中的ECS实例的私网IP。如果可以ping通，则表示两个VPC已经成功连接。

