# ModifyExpressCloudConnectionBandwidth {#doc_api_Vpc_ModifyExpressCloudConnectionBandwidth .reference}

调用ModifyExpressCloudConnectionBandwidth修改高速上云服务带宽。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyExpressCloudConnectionBandwidth&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyExpressCloudConnectionBandwidth|要执行的操作。

 取值：**ModifyExpressCloudConnectionBandwidth**。

 |
|EccId|String|是|ecc-xxxxxxxxx|高速上云服务实例ID。

 |
|RegionId|String|是|cn-hangzhou|地域ID。

 |
|Bandwidth|String|否|2|高速上云服务带宽。

 只支持提交工单进行升配。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E6385514-B0CC-48E3-B9F9-F7BFF64460A2|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyExpressCloudConnectionBandwidth
&EccId=ecc-xxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyExpressCloudConnectionBandwidthResponse>
	  <RequestId>E6385514-B0CC-48E3-B9F9-F7BFF64460A2</RequestId>
    </ModifyExpressCloudConnectionBandwidthResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E6385514-B0CC-48E3-B9F9-F7BFF64460A2"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

