# API概览 {#concept_qlc_5nb_12b .concept}

高速通道提供以下接口供您使用。

## 边界路由器 {#section_d5g_44b_12b .section}

|API|说明|
|:--|:-|
|[CreateVirtualBorderRouter](https://help.aliyun.com/document_detail/124791.htm)|调用CreateVirtualBorderRouter新建边界路由器（VBR）。|
|[DescribeVirtualBorderRouters](https://help.aliyun.com/document_detail/109032.html?)|调用DescribeVirtualBorderRouters接口查询已创建的边界路由器（VBR）。|
|[DescribeVirtualBorderRoutersForPhysicalConnection](https://help.aliyun.com/document_detail/109033.html)|调用DescribeVirtualBorderRoutersForPhysicalConnection查询指定物理专线下的边界路由器（VBR），包括物理专线所有者的VBR和其他账号的VBR。|
|[ModifyVirtualBorderRouterAttribute](https://help.aliyun.com/document_detail/109035.html)|调用ModifyVirtualBorderRouterAttribute修改边界路由器（VBR）的配置。|
|[RecoverVirtualBorderRouter](https://help.aliyun.com/document_detail/109042.html?)|调用RecoverVirtualBorderRouter恢复被终止的边界路由器（VBR）。|
|[TerminateVirtualBorderRouter](https://help.aliyun.com/document_detail/109041.html?)|调用TerminateVirtualBorderRouter终止边界路由器（VBR）。|

## 物理专线 {#section_n33_znb_12b .section}

|API|说明|
|:--|:-|
|[CreatePhysicalConnection](https://help.aliyun.com/document_detail/109008.html?)|调用CreatePhysicalConnection接口申请物理专线接入。|
|[CancelPhysicalConnection](https://help.aliyun.com/document_detail/109010.html?)|调用CancelPhysicalConnection接口取消物理专线接入，取消后物理专线进入Canceled状态。|
|[DeletePhysicalConnection](https://help.aliyun.com/document_detail/109016.html?)|调用DeletePhysicalConnection接口删除物理专线。|
|[DescribePhysicalConnections](https://help.aliyun.com/document_detail/109011.html?)|调用DescribePhysicalConnections接口查询指定地域内的物理专线。|
|[EnablePhysicalConnection](https://help.aliyun.com/document_detail/109015.html?)|调用EnablePhysicalConnection接口开通处于Confirmed状态的物理专线，开通完成后物理专线进入Enabled状态。|
|[ModifyPhysicalConnectionAttribute](https://help.aliyun.com/document_detail/109013.html?)|调用ModifyPhysicalConnectionAttribute接口修改物理专线的配置。|
|[TerminatePhysicalConnection](https://help.aliyun.com/document_detail/109014.html?)|在物理专线开通后调用TerminatePhysicalConnection接口终止物理专线接入。|
|[../../../../dita-oss-bucket/SP\_22/DNVPC11886329/ZH-CN\_TP\_134132.md\#](../../../../intl.zh-CN/API参考/物理专线/ApplyPhysicalConnectionLOA.md#)|调用ApplyPhysicalConnectionLOA申请LOA。|
|[CompletePhysicalConnectionLOA](https://help.aliyun.com/document_detail/112124.html?)|调用CompletePhysicalConnectionLOA完成施工完竣。|
|[CreatePhysicalConnectionOccupancyOrder](https://help.aliyun.com/document_detail/120031.html?)|调用CreatePhysicalConnectionOccupancyOrder创建资源占用费订单。|
|[CreatePhysicalConnectionSetupOrder](https://help.aliyun.com/document_detail/112126.html?)|调用CreatePhysicalConnectionSetupOrder创建初装费订单。|
|[DescribePhysicalConnectionLOA](https://help.aliyun.com/document_detail/112127.html?)|调用DescribePhysicalConnectionLOA查询物理专线LOA信息。|

## 高速上云服务 {#section_sv0_n81_w9n .section}

|API|说明|
|---|--|
|[CreateExpressCloudConnection](../../../../intl.zh-CN/API参考/高速上云服务/CreateExpressCloudConnection.md#)|调用CreateExpressCloudConnection申请高速上云服务。|
|[ModifyExpressCloudConnectionAttribute](../../../../intl.zh-CN/API参考/高速上云服务/ModifyExpressCloudConnectionAttribute.md#)|调用ModifyExpressCloudConnectionAttribute修改高速上云服务连接。|
|[ModifyExpressCloudConnectionBandwidth](../../../../intl.zh-CN/API参考/高速上云服务/ModifyExpressCloudConnectionBandwidth.md#)|调用ModifyExpressCloudConnectionBandwidth修改高速上云服务带宽。|
|[DescribeExpressCloudConnections](../../../../intl.zh-CN/API参考/高速上云服务/DescribeExpressCloudConnections.md#)|调用DescribeExpressCloudConnections查询某个区域的高速上云服务列表。|
|[AssociatePhysicalConnectionToVirtualBorderRouter](../../../../intl.zh-CN/API参考/边界路由器/AssociatePhysicalConnectionToVirtualBorderRouter.md#)|调用AssociatePhysicalConnectionToVirtualBorderRouter将VBR关联物理专线。|
|[UnassociatePhysicalConnectionFromVirtualBorderRouter](../../../../intl.zh-CN/API参考/边界路由器/UnassociatePhysicalConnectionFromVirtualBorderRouter.md#)|调用UnassociatePhysicalConnectionFromVirtualBorderRouter解绑VBR和物理专线。|

