# ModifyPhysicalConnectionAttribute {#doc_api_Vpc_ModifyPhysicalConnectionAttribute .reference}

调用ModifyPhysicalConnectionAttribute接口修改物理专线的配置。

调用该接口时，请注意：

-   只有处于**Initial**或**Rejected**状态的物理专线可以修改规格和冗余专线ID。
-   无法修改处于**Canceled**、**Allocating**、**AllocationFailed**和**Terminated**状态的物理专线。
-   处于**Rejected**状态的物理专线被修改后会进入**Initial**状态。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyPhysicalConnectionAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyPhysicalConnectionAttribute|要执行的操作。

 取值： **ModifyPhysicalConnectionAttribute**。

 |
|PhysicalConnectionId|String|是|pc-119mfjzm7|物理专线的ID。

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|CircuitCode|String|否|longtel001|运营商的为物理专线提供的电路编码。

 |
|ClientToken|String|否|efefe566754h|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Description|String|否|物理专线的描述信息|物理专线的描述信息。 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|LineOperator|String|否|CT|提供接入物理线路的运营商，取值：

 -   CT：中国电信
-   CU：中国联通
-   CM：中国移动
-   CO：中国其他
-   Equinix：Equinix
-   Other：境外其他

 |
|Name|String|否|物理专线的名称|物理专线的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|PeerLocation|String|否|浙江省---vfjdbg\_21e|本地数据中心的地理位置。

 |
|PortType|String|否|E1 - 2M|物理专线接入端口类型，取值：

 -   100Base-T：百兆电口
-   1000Base-T（默认值）：千兆电口
-   1000Base-LX：千兆单模光口（10千米）
-   10GBase-T：万兆电口
-   10GBase-LR：万兆单模光口（10千米）

 |
|RedundantPhysicalConnectionId|String|否|pc-119mfjzm7|冗余物理专线的ID，该专线的状态必须为**Allocated**、**Confirmed**或**Enabled**。

 |
|bandwidth|Integer|否|5|物理专线接入接口带宽，单位Mbps，取值范围：2-10240。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|013EE132-A109-4247-91B0-099A8FF49AD7|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyPhysicalConnectionAttribute
&PhysicalConnectionId=pc-119mfjzm7
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyPhysicalConnectionAttributeResponse>
  <RequestId>8A6A5EC5-6F6C-4906-9689-56ACE58A13E0"</RequestId>
</ModifyPhysicalConnectionAttributeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8A6A5EC5-6F6C-4906-9689-56ACE58A13E0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidPhysicalConnectionId.NotFound|The PhysicalConnectionId provided does not exist in our records.|该物理专线不存在。|
|400|InvalidLineOperator.Malformd|The LineOperator provided was invalid.|参数LineOperator的值不合法。|
|400|InvalidPeerLocation.Malformd|The PeerLocation provided was invalid.|参数PeerLocation的值不合法。|
|400|InvalidPortType.Malformd|The PortType provided was invalid.|该端口类型不合法。|
|400|InvalidDescription.Malformed|The specifid ?Description? is not valid.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|
|400|InvalidName.Malformed|The specified ?Name? is not valid.|该名称格式不合法。|
|400|InvalidStatus|invalid physical connection status.|物理专线状态不合法。|
|400|InvalidBandwidth|invalid physical connection banwidth.|物理专线的带宽不合法。|
|400|InvalidRedundantPhysicalConnection|redundant physical connection doesn't belong to current user.|该冗余物理专线不属于您的账号。|
|400|InvalidRedundantPhysicalConnectionStatus|invalid redundant physical connection status.|冗余物理专线状态不合法。|
|400|InvalidCircuitCode.Malformed|circuitCode is illegal.|该CircuitCode不合法。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

