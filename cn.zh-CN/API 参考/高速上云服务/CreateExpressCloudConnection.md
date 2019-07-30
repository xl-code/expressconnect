# CreateExpressCloudConnection {#doc_api_Vpc_CreateExpressCloudConnection .reference}

调用CreateExpressCloudConnection申请高速上云服务。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateExpressCloudConnection&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateExpressCloudConnection|要执行的操作。

 取值：**CreateExpressCloudConnection**。

 |
|Bandwidth|Integer|是|2|高速上云连接的带宽， 单位Mbps。

 取值：**2|4|6|8|10|20|50|100|200|500|1000|10000|40000**

 |
|IdcSP|String|是|CU|IDC的网络服务商。

 |
|PeerLocation|String|是|XX区XX大厦XX栋5楼|本地数据中心的地理位置。

 需要精确到楼层。

 |
|RegionId|String|是|cn-hangzhou|高速上云服务实例所在的地域ID。

 |
|ContactMail|String|否|XX@example.com|申请高速上云连接的联系人邮件。

 |
|ContactTel|String|否|152XXXXXXXX|申请高速上云服务的联系人电话。

 |
|Description|String|否|高速上云服务|高速上云服务的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|IDCardNo|String|否|32\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*|申请高速上云服务的联系人身份证号。

 |
|Name|String|否|doctest|高速上云服务的实例名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://` 或`https://`开头。

 |
|PeerCity|String|否|杭州|所在城市。

 |
|PortType|String|否|100Base-T|物理专线接入端口类型，取值：

 -   100Base-T：百兆电口
-   1000Base-T（默认值）：千兆电口
-   1000Base-LX：千兆单模光口（10千米）
-   10GBase-T：万兆电口
-   10GBase-LR：万兆单模光口（10千米）

 |
|RedundantEccId|String|否|ecc-d\*\*\*\*|冗余高速上云服务专线实例ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|EccId|String|ecc-xxx\*\*\*\*\*|新建的高速上云服务实例ID。

 |
|RequestId|String|C004F022-1CC2-4958-9937-675513A2CD7E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateExpressCloudConnection
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateExpressCloudConnectionResponse>
    <EccId>ecc-bp1t9osmuln1vxfpt6gy8</EccId>
    <RequestId>C004F022-1CC2-4958-9937-675513A2CD7E</RequestId>
</CreateExpressCloudConnectionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"EccId":"ecc-bp1t9osmuln1vxfpt6gy8",
	"RequestId":"C004F022-1CC2-4958-9937-675513A2CD7E"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

