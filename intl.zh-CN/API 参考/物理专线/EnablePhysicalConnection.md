# EnablePhysicalConnection {#doc_api_951810 .reference}

使用EnablePhysicalConnection接口开通处于Confirmed状态的物理专线，开通完成后物理专线进入Enabled状态。

调用该接口时，请注意：

-   只允许开通当前处在**Confirmed**状态的物理专线。
-   开通后进入**Enabled**状态。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=EnablePhysicalConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|EnablePhysicalConnection|要执行的操作。

 取值： **EnablePhysicalConnection**。

 |
|PhysicalConnectionId|String|是|pc-119mfjzm7|物理专线的ID。

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|API-20365164-5b0d-460a-83c2-2189972b3349|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=EnablePhysicalConnection
&PhysicalConnectionId=pc-119mfjzm7
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<EnablePhysicalConnectionResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</EnablePhysicalConnectionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidPhysicalConnectionId.NotFound|The PhysicalConnectionId provided does not exist in our records.|该物理专线不存在。|
|400|Forbidden.NotAllowedInState|The request does not allow in this state.|该状态无法执行请求。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

