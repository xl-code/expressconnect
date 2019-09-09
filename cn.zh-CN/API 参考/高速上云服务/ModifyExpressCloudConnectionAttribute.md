# ModifyExpressCloudConnectionAttribute {#doc_api_Vpc_ModifyExpressCloudConnectionAttribute .reference}

调用ModifyExpressCloudConnectionAttribute修改高速上云服务连接。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyExpressCloudConnectionAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyExpressCloudConnectionAttribute|要执行的操作。

 取值：**ModifyExpressCloudConnectionAttribute**。

 |
|EccId|String|是|ecc-bp1t9osmuln\*\*\*\*\*\*\*|高速上云连接实例ID。

 |
|RegionId|String|是|cn-hangzhou|地域ID。

 |
|Description|String|否|ECC|高速上云服务说明。

 |
|Name|String|否|doctest|高速上云服务实例名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E6385514-B0CC-48E3-B9F9-F7BFF64460A2|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyExpressCloudConnectionAttribute
&EccId=ecc-bp1t9osmuln*******
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyExpressCloudConnectionAttributeResponse>
	  <RequestId>E6385514-B0CC-48E3-B9F9-F7BFF64460A2</RequestId>
    </ModifyExpressCloudConnectionAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E6385514-B0CC-48E3-B9F9-F7BFF64460A2"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

