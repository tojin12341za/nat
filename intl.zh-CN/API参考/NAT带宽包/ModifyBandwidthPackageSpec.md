# ModifyBandwidthPackageSpec {#doc_api_Vpc_ModifyBandwidthPackageSpec .reference}

使用ModifyBandwidthPackageSpec接口修改指定NAT带宽包的带宽。

本接口仅支持在2017年11月3日之前账号下存在NAT带宽包的用户调用。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。

详情参见[AssociateEipAddress](~~36017~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyBandwidthPackageSpec)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyBandwidthPackageSpec|要执行的操作。

 取值： **ModifyBandwidthPackageSpec**。

 |
|Bandwidth|String|是|5|NAT带宽包的带宽。取值范围：5-1000。

 |
|BandwidthPackageId|String|是|bwp-s6lmotmkkxxxxxxxx|NAT带宽包的ID。

 |
|RegionId|String|是|cn-hangzhou|NAT带宽包所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|079874CD-AEC1-43E6-AC03-ADD96B6E4907|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyBandwidthPackageSpec
&Bandwidth=5
&BandwidthPackageId=bwp-s6lmotmkkxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyBandwidthPackageSpecResponse>
  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifyBandwidthPackageSpecResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"54ED4074-3F89-4F11-B166-837DD3E20FE3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidBandwidth.ValueNotSupported|The specified value of Bandwidth not supported.|指定的带宽峰值不支持。|
|404|BandwidthPackage.FinancialLocked|The specified BandwidthPackage has been Financail Lock.|该带宽包被欠费锁定。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

