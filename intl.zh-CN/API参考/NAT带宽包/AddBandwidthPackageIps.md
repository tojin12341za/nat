# AddBandwidthPackageIps {#doc_api_Vpc_AddBandwidthPackageIps .reference}

使用AddBandwidthPackageIps接口在NAT带宽包中增加公网IP。

本接口仅支持在2017年11月3日之前账号下存在NAT带宽包的用户调用。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。

详情参见[AssociateEipAddress](~~36017~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=AddBandwidthPackageIps)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddBandwidthPackageIps|要执行的操作。

 取值： **AddBandwidthPackageIps**。

 |
|RegionId|String|是|cn-hangzhou|NAT带宽包所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|IpCount|String|是|2|NAT带宽包中的公网IP数量，取值范围：1-50。

 |
|BandwidthPackageId|String|是|bwp-s6lmotmkkxxxxxxxx|NAT带宽包的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|EC0B5C51-7F40-44D6-A642-1DE764B547EC|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=AddBandwidthPackageIps
&BandwidthPackageId=bwp-s6lmotmkkxxxxxxxx
&IpCount=2
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddBandwidthPackageIpsResponse>
  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</AddBandwidthPackageIpsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidIpCount.ValueNotSupported|The specified value of IpCount not supported.|参数IpCount的值不合法。|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|IP 数量超过上限，可以提交工单申请增加配额。|
|404|BandwidthPackage.FinancialLocked|The specified BandwidthPackage has been Financail Lock.|该带宽包被欠费锁定。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

