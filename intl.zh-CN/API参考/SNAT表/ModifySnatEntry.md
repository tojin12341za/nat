# ModifySnatEntry {#doc_api_951860 .reference}

调用ModifySnatEntry接口修改指定的SNAT条目。

**说明：** 当SNAT表中有SNAT条目的状态为**Pending**或**Modifying**时，无法修改SNAT条目。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifySnatEntry)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifySnatEntry|要执行的操作。

 取值： **ModifySnatEntry**。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|SnatEntryId|String|是|snat-bp1vcgcf8tm0plqcgfl04|SNAT条目ID。

 |
|SnatIp|String|是|47.XXX.XXX.98|公网IP地址。多个IP之间逗号隔开。

 |
|SnatTableId|String|是|stb-8vbczigrhop8x5u3twlhd|SNAT表ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifySnatEntry
&RegionId=cn-hangzhou
&SnatEntryId=snat-bp1vcgcf8tm0plqcgfl04
&SnatIp=47.XXX.XXX.98
&SnatTableId=stb-8vbczigrhop8x5u3twlhd
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifySnatEntryResponse>
  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifySnatEntryResponse>

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
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|指定的 SNAT 表不存在，请您检查输入参数是否正确。|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|该公网IP不合法。|
|404|InvalidSnatEntryId.NotFound|Specified SNAT entry does not exist.|指定的 SNAT 条目不存在，请您检查填写的 SNAT 条目是否正确。|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|该交换机已配置了 SNAT 规则，请您不要重复设置。|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|该公网IP已经被DNAT使用，请更换其他公网IP地址或将当前公网IP的DNAT规则删除。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

