# RemoveBandwidthPackageIps {#doc_api_Vpc_RemoveBandwidthPackageIps .reference}

使用RemoveBandwidthPackageIps接口删除NAT带宽包中的公网IP。

删除公网IP时，需要指定要删除公网IP的列表：

-   不允许将全部公网IP删除。如果请求中的IP列表包括了所有IP，删除失败。
-   如果请求中的IP列表包括了不属于NAT带宽包中的IP，删除失败。
-   如果请求中的IP列表中有IP被DNAT或SNAT条目使用，删除失败。

本接口仅支持在2017年11月3日之前账号下存在NAT带宽包的用户调用。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。

详情参见[AssociateEipAddress](~~36017~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=RemoveBandwidthPackageIps)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveBandwidthPackageIps|要执行的操作。取值：**RemoveBandwidthPackageIps**。

 |
|BandwidthPackageId|String|是|bwp-s6lmotmkkxxxxxxxx|待删除的公网IP的所属的NAT带宽包ID。

 |
|RegionId|String|是|cn-hangzhou|NAT带宽包所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RemovedIpAddresses.N|RepeatList|是|116.xx.xx.28|待删除的公网IP的ID。n必须从1开始，最大为20。

 |
|ClientToken|String|否|SHAww112344jhsxxxx|用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不能超过64个ASCII字符。

 更多关于幂等性的信息，请参考[如何保证幂等性](~~36569~~)。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|7D275A59-1EB0-4775-8A20-2A47055EAC5C|用户请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=RemoveBandwidthPackageIps
&BandwidthPackageId=bwp-s6lmotmkkxxxxxxxx
&RegionId=cn-hangzhou
&RemovedIpAddresses.1=116.xx.xx.28
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveBandwidthPackageIpsResponse>
  <RequestId>7D275A59-1EB0-4775-8A20-2A47055EAC5C</RequestId>
</RemoveBandwidthPackageIpsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"7D275A59-1EB0-4775-8A20-2A47055EAC5C"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|invalidRemovedIpAddresses.NotFound|Some of the specified value of RemovedIpAddress not found in specified BandwidthPackage.|IP列表中的某个IP不在该共享带宽包中，请您检查该IP列表中的IP。|
|400|InvalidIpCount.ValueNotSupported|Can not remove all ips of the bandwidthPackage.|不能移除带宽包里所有的 IP 地址。|
|400|InvalidRemovedIpAddresses.NotFound|Some of remove ip is not natPublicIp.|要移除的IP中有不是NAT网关的公网IP。|
|400|DependencyViolation.ForwardEntry|The ip has been used by ForwardEntry.|IP 地址被端口转发规则引用，请先删除相应规则再进行操作。|
|400|DependencyViolation.SnatEntry|The ip has been used by SnatEntry.|IP 地址被 SNAT 规则引用，请先删除相应规则再进行操作。|
|404|BandwidthPackage.FinancialLocked|The specified BandwidthPackage has been Financail Lock.|该带宽包被欠费锁定。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

