# API概览 {#concept_qlc_5nb_12b .concept}

高速通道提供以下接口供您使用。

## 边界路由器 {#section_d5g_44b_12b .section}

|API|说明|
|:--|:-|
|[CreateVirtualBorderRouter](../../../../intl.zh-CN/API参考/边界路由器/CreateVirtualBorderRouter.md#)|调用CreateVirtualBorderRouter新建边界路由器（VBR）。|
|[DescribeVirtualBorderRouters](../../../../intl.zh-CN/API参考/边界路由器/DescribeVirtualBorderRouters.md#)|调用DescribeVirtualBorderRouters接口查询已创建的边界路由器（VBR）。|
|[DescribeVirtualBorderRoutersForPhysicalConnection](../../../../intl.zh-CN/API参考/边界路由器/DescribeVirtualBorderRoutersForPhysicalConnection.md#)|调用DescribeVirtualBorderRoutersForPhysicalConnection查询指定物理专线下的边界路由器（VBR），包括物理专线所有者的VBR和其他账号的VBR。|
|[ModifyVirtualBorderRouterAttribute](../../../../intl.zh-CN/API参考/边界路由器/ModifyVirtualBorderRouterAttribute.md#)|调用ModifyVirtualBorderRouterAttribute修改边界路由器（VBR）的配置。|
|[RecoverVirtualBorderRouter](../../../../intl.zh-CN/API参考/边界路由器/RecoverVirtualBorderRouter.md#)|调用RecoverVirtualBorderRouter恢复被终止的边界路由器（VBR）。|
|[TerminateVirtualBorderRouter](../../../../intl.zh-CN/API参考/边界路由器/TerminateVirtualBorderRouter.md#)|调用TerminateVirtualBorderRouter终止边界路由器（VBR）。|

## 物理专线 {#section_n33_znb_12b .section}

|API|说明|
|:--|:-|
|[CreatePhysicalConnection](../../../../intl.zh-CN/API参考/物理专线/CreatePhysicalConnection.md#)|调用CreatePhysicalConnection接口申请物理专线接入。|
|[CancelPhysicalConnection](../../../../intl.zh-CN/API参考/物理专线/CancelPhysicalConnection.md#)|调用CancelPhysicalConnection接口取消物理专线接入，取消后物理专线进入Canceled状态。|
|[DeletePhysicalConnection](../../../../intl.zh-CN/API参考/物理专线/DeletePhysicalConnection.md#)|调用DeletePhysicalConnection接口删除物理专线。|
|[DescribePhysicalConnections](../../../../intl.zh-CN/API参考/物理专线/DescribePhysicalConnections.md#)|调用DescribePhysicalConnections接口查询指定地域内的物理专线。|
|[EnablePhysicalConnection](../../../../intl.zh-CN/API参考/物理专线/EnablePhysicalConnection.md#)|调用EnablePhysicalConnection接口开通处于Confirmed状态的物理专线，开通完成后物理专线进入Enabled状态。|
|[ModifyPhysicalConnectionAttribute](../../../../intl.zh-CN/API参考/物理专线/ModifyPhysicalConnectionAttribute.md#)|调用ModifyPhysicalConnectionAttribute接口修改物理专线的配置。|
|[TerminatePhysicalConnection](../../../../intl.zh-CN/API参考/物理专线/TerminatePhysicalConnection.md#)|在物理专线开通后调用TerminatePhysicalConnection接口终止物理专线接入。|
|、[ApplyPhysicalConnectionLOA](../../../../intl.zh-CN/API参考/物理专线/ApplyPhysicalConnectionLOA.md#)|调用ApplyPhysicalConnectionLOA申请LOA。|
|[CompletePhysicalConnectionLOA](../../../../intl.zh-CN/API参考/物理专线/CompletePhysicalConnectionLOA.md#)|调用CompletePhysicalConnectionLOA完成施工完竣。|
|[CreatePhysicalConnectionOccupancyOrder](../../../../intl.zh-CN/API参考/物理专线/CreatePhysicalConnectionOccupancyOrder.md#)|调用CreatePhysicalConnectionOccupancyOrder创建资源占用费订单。|
|[CreatePhysicalConnectionSetupOrder](../../../../intl.zh-CN/API参考/物理专线/CreatePhysicalConnectionSetupOrder.md#)|调用CreatePhysicalConnectionSetupOrder创建初装费订单。|
|[DescribePhysicalConnectionLOA](../../../../intl.zh-CN/API参考/物理专线/DescribePhysicalConnectionLOA.md#)|调用DescribePhysicalConnectionLOA查询物理专线LOA信息。|

