# 同账号VPC互连 {#concept_wrx_vbr_ydb .concept}

本教程指引您使用高速通道连接同一个账号下的两个VPC。

**说明：** 如果您首次使用高速通道实现两个VPC互通，推荐您使用云企业（CEN），详情参见[教程概览](../../../../../cn.zh-CN/快速入门/教程概览.md#)。

## 教程示例 {#section_ock_bcr_ydb .section}

本操作以如下两个VPC为例演示如何使用高速通道实现VPC私网互通。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154089918511702_zh-CN.png)

## 前提条件 {#section_kdw_xbr_ydb .section}

确保要进行互连的VPC或交换机的网段不冲突。

## 步骤一 创建对等连接 {#section_ldw_xbr_ydb .section}

完成以下操作，创建对等连接：

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**专有网络对等连接** \> **VPC互连**。
3.  选择一个地域。

    本教程选择**华北1（青岛）**。

4.  单击**创建对等连接**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154089918511683_zh-CN.png)

5.  配置对等连接。

    本操作使用如下配置：

    **说明：** 如果您要通过高速通道连接中国大陆和境外（含香港）的专有网络，请选择中国联通跨境。跨境互通由中国联通运营。

    -   **连接场景**：选择**VPC互连**。

    -   **创建路由器场景**：选择**同时创建两端**。

        系统会将选择的本端VPC设置为连接发起端，对端VPC设置为接受端，自动连接发起端接收端。

    -   **地域**：选择本端VPC的所属地域，本操作选择**华北1 （青岛）**。

    -   **本端VPC ID**：选择本端VPC即连接发起端，本操作选择**VPC1**。

    -   **对端地域**：选择要连接的VPC的所属地域，本操作选择**华北2 （北京）**。

    -   **对端VPC ID**：选择要连接的VPC，本操作选择**VPC2**。

    -   **带宽值**：选择专有网络互通的带宽，本操作选择**2Mb**。

6.  单击**立即购买**，并完成支付。
7.  回到专有网络对等连接页面，查看已创建的对等连接。

    当发起端和接收端的状态都为已激活时，表示成功建立连接。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154089918611684_zh-CN.png)


## 步骤二 配置路由 {#section_tdw_xbr_ydb .section}

建立对等连接后，您还需要分别为互连的VPC添加路由。

完成以下操作，配置路由：

1.  在专有网络对等连接页面，找到已创建的对等连接。
2.  单击发起端实例下的**路由配置**选项。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154089918611686_zh-CN.png)

3.  单击**添加对端路由**，然后输入要连接的VPC或其交换机的网段，单击**确定**。

    本操作输入对端VPC的网段172.16.0.0/16。

4.  单击接收端实例下的**路由配置**选项。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154089918611700_zh-CN.png)

5.  单击**添加对端路由**，然后输入要连接的VPC或其交换机的网段，单击**确定**。

## 步骤三 配置安全组 {#section_zx1_ndf_hfb .section}

在两个VPC间建立对等连接后，您还需要配置安全组规则，实现两个VPC内的ECS实例的互通。

本操作以下表中的ECS实例和安全组配置为例。

|配置信息|账号A|账号A|
|:---|:--|:--|
|账号ID|AccountID\_A|AccountID\_A|
|ECS实例ID|InstanceID\_A|InstanceID\_B|
|安全组ID|SecurityGroupID\_A|SecurityGroupID\_B|

您可以在[账号中心](https://account.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.39.4cb94bd3LoJmJ3#/secure)查看账号ID。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154089918613186_zh-CN.png)

完成以下操作，配置安全组规则：

1.  登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏，单击**网络和安全** \> **安全组**。
3.  选择实例的地域。
4.  找到目标安全组，然后单击**配置规则**。
5.  在安全组规则页面，单击**添加安全组规则**。
6.  配置安全组规则，根据您的需要选择协议类型并输入端口。其中：

    -   **授权类型**：选择**安全组访问**，并选择**跨账号授权**。
    -   **授权对象**：输入允许访问实例关联的安全组ID。
    -   **账号ID**：输入本账号的ID。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13830/154089918613187_zh-CN.png)


## 步骤四 测试 {#section_hj4_55m_cfb .section}

建立对等连接，并添加路由后，您可以登录到其中一个专有网络的ECS实例上，ping已连接的专有网络中的ECS实例的私网IP。如果可以ping通，则表示两个VPC已经成功连接。

