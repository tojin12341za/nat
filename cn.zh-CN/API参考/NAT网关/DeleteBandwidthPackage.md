# DeleteBandwidthPackage {#doc_api_Vpc_DeleteBandwidthPackage .reference}

使用DeleteBandwidthPackage接口删除指定的NAT带宽包。

本接口仅支持在2017年11月3日之前账号下存在NAT带宽包的用户调用。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP，详情参见[AssociateEipAddress](~~36017~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DeleteBandwidthPackage)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteBandwidthPackage|要执行的操作。 取值： **DeleteBandwidthPackage**

 |
|BandwidthPackageId|String|是|bwp-bp1arsrmca9kpxxxxxxxx|NAT带宽包的ID。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Force|Boolean|否|false|是否强制删除带宽包。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|7D275A59-1EB0-4775-8A20-2A47055EAC5C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteBandwidthPackage
&BandwidthPackageId=bwp-bp1arsrmca9kpxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteBandwidthPackageResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteBandwidthPackageResponse>

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
|400|DependencyViolation.ForwardEntry|The specified BandwidthPackageId has dependent resource.|该共享带宽包有未删除的SNAT/DNAT表项，请您先删除SNAT/DNAT表项在进行操作。|
|400|DependencyViolation.SnatEntry|The specified BandwidthPackageId has dependent resource.|该共享带宽包有未删除的SNAT/DNAT表项，请您先删除SNAT/DNAT表项在进行操作。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

