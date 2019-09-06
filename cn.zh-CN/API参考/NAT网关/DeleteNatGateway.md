# DeleteNatGateway {#doc_api_Vpc_DeleteNatGateway .reference}

使用DeleteNatGateway接口删除指定的NAT网关。

**说明：** 如果NAT网关尚有未删除的共享带宽包，需要先删除共享带宽包。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteNatGateway&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteNatGateway|要执行的操作。

 取值： **DeleteNatGateway**。

 |
|NatGatewayId|String|是|ngw-bp1uewa15k4iy5770ya89|NAT网关的ID。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Force|Boolean|否|false|是否强制删除NAT网关。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteNatGateway
&NatGatewayId=ngw-bp1uewa15k4iy5770ya89
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteNatGatewayResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteNatGatewayResponse>
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
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|指定的 NatGatewayId 不存在，请您检查填写的 NatGatewayId 是否正确。|
|400|DependencyViolation.BandwidthPackages|There are BandwidthPackages on specified NatGateway not deleted.|Nat网关上有尚未删除的 带宽包，请删除NAT网关下的所有带宽包后再重试操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

