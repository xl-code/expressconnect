# VPC互连常见问题 {#concept_h5w_vpb_12b .concept}

## 1.使用高速通道进行通信，数据会经过公网么？ {#section_vd1_ypb_12b .section}

不会。高速通道上的数据只会在阿里云的数据中心内或数据中心之间的物理专线间进行传输，不会经过互联网，从而避免您的数据在传输过程中被窃听，并且能够提供比互联网更好的网络质量。

## 2. 高速通道能否支持跨账号的VPC内网互连？ {#section_wd1_ypb_12b .section}

支持。高速通道支持同一账号或不同账号的VPC之间进行内网互连。关于具体步骤，参见[同账号VPC互连](../../../../intl.zh-CN/专有网络对等连接（关闭新购）/同账号VPC互连.md#)。

## 3. 高速通道能否支持跨地域的VPC内网互连？ {#section_xd1_ypb_12b .section}

支持。高速通道支持相同地域或不同地域的VPC之间进行内网互连。您可以在两侧VPC的路由器上分别创建路由器接口，通过传输网络来搭建高速通道，轻松实现两个VPC之间安全可靠、方便快捷的通信。

## 4.用高速通道进行VPC内网互连，两侧可以互相访问哪些资源？ {#section_yd1_ypb_12b .section}

两侧的ECS实例都可以访问另一侧的ECS实例、负载均衡实例或RDS实例。

-   不支持一侧的负载均衡实例使用另一侧的ECS实例作为后端服务器。
-   不支持ECS访问对侧除了ECS实例/负载均衡实例/RDS实例之外的云产品实例，未来会逐步增加支持。

## 5. 当我购买了某种规格的路由器接口后，如果某时刻业务流量突发，是否可以临时调整？ {#section_a21_ypb_12b .section}

阿里云现在已经支持提高或降低路由器接口的规格，您可以根据业务需要，随时更改发起端路由器接口的规格，变更将实时生效。

## 6. 当我使用高速通道路由器接口时，阿里云会不会对数据的传输做限制？ {#section_c21_ypb_12b .section}

阿里云会根据您购买的路由器接口的规格对应的数据传输能力对数据的传输进行限制。

## 为什么我的账户无法创建对等连接？ {#section_t2n_bjp_m6w .section}

高速通道的对等连接功能于2019年6月20日停止售卖，在此之前使用对等连接的用户，不会受到影响，仍然可以继续使用对等连接，未使用过的用户，将无法创建对等连接。

您可以使用云企业网产品代替对等连接来满足您的需求，详情请参见[迁移介绍](../../../../intl.zh-CN/最佳实践/高速通道对等连接迁移方案/迁移介绍.md#)。

## 每个VPC上最多可建立的对等连接接口数量？ {#section_vt0_ntf_bc9 .section}

默认是10个，您可以在高速通道[配额管理](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou)页面，申请调整名称为**ec\_quota\_vroute\_ri\_num**的配额。

## 每个边界路由器上最多可建立的对等连接接口数量？ {#section_dn2_dp8_31a .section}

默认是10个，您可以在高速通道[配额管理](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou)页面，申请调整名称为**ec\_quota\_vbr\_ri\_num**的配额。

## 每个账户最多可建立的对等连接接口数量？ {#section_drl_v22_buf .section}

默认是20个，您可以在高速通道[配额管理](https://expressconnect.console.aliyun.com/quota/cn-hangzhou//cn-hangzhou)页面，申请调整名称为**ec\_quota\_user\_ri\_num**的配额。

