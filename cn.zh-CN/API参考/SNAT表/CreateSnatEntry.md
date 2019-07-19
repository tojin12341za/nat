# CreateSnatEntry {#doc_api_Vpc_CreateSnatEntry .reference}

调用CreateSnatEntry接口在SNAT列表中添加SNAT条目。

调用本接口添加SNAT条目时，请注意：

-   SNAT条目中指定的交换机和ECS实例必须在NAT网关所属的VPC内。
-   每个交换机和ECS实例只能属于一个SNAT条目。
-   如果交换机中存在HAVIP实例，则无法添加SNAT条目。
-   SNAT条目中的公网IP（SnatIp）需满足以下条件：
    -   对于2018年1月26日之前账户下存在NAT带宽包的用户，SnatIp必须是该NAT网关的NAT带宽包中的公网IP地址。
    -   对于2018年1月26日之前账户下不存在NAT带宽包的用户，SnatIp必须是绑定了该NAT网关的弹性公网IP。
    -   一个公网IP不能同时用于DNAT条目和SNAT条目。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateSnatEntry)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateSnatEntry|要执行的操作，取值：**CreateSnatEntry**。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|SnatIp|String|是|47.XX.XX.98|公网IP地址，多个IP之间用逗号隔开。

 |
|SnatTableId|String|是|stb-bp190wu8io1vgev\*\*\*\*|SNAT表ID。

 |
|SnatEntryName|String|否|SnatEntry-1|SNAT条目的名称。长度为2-128个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|SourceCIDR|String|否|10.1.1.0/24|交换机或ECS实例的网段。

 -   交换机粒度：指定交换机的网段（如192.168.1.0/24），当交换机下的ECS实例发起互联网访问请求时，NAT网关会为其提供SNAT服务（代理上网服务）。如果**SnatIp**仅指定了一个公网IP，ECS实例使用指定的公网IP访问互联网；如果**SnatIp**指定了多个公网IP，ECS实例随机使用**SnatIp**中的公网IP访问互联网。
-   ECS粒度：指定ECS实例的地址（如192.168.1.1/32），当ECS实例发起互联网访问请求时，NAT网关会为其提供SNAT服务（代理上网服务）。如果**SnatIp**仅指定了一个公网IP，ECS实例使用指定的公网IP访问互联网；如果**SnatIp**指定了多个公网IP，ECS实例随机使用**SnatIp**中的公网IP访问互联网。

 **说明：** 此参数和**SourceVSwtichId**参数互斥，不能同时出现。如果指定了**SourceVSwitchId**，则不能指定**SourceCIDR**参数。如果指定了**SourceCIDR**参数，则不能指定**SourceVSwitchId**参数。

 |
|SourceVSwitchId|String|否|vsw-bp1nhx2s9ui5o\*\*\*\*|需要公网访问的交换机的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|SnatEntryId|String|snat-kmd6nv8fy\*\*\*\*|SNAT条目ID。

 |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateSnatEntry
&RegionId=cn-hangzhou
&SnatIp=47.XX.XX.98
&SnatTableId=stb-bp190wu8io1vgevx****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateSnatEntryResponse>
  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
  <SnatEntryId>snat-119smw5tkx****</SnatEntryId>
</CreateSnatEntryResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3",
	"SnatEntryId":"snat-kmd6nv8fyx****"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|指定的 SNAT 表不存在，请您检查输入参数是否正确。|
|400|Forbidden.SourceVSwitchId.IncludeHaVip|There is some HaVips under specified VSwitch|该交换机下有关联的HAVIP。|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|该公网IP不合法。|
|400|SNAT\_IP\_POOL\_COUNT\_TOO\_MANY|The Snat pool ip too many.|SNAT IP池的IP达到配额。|
|400|Forbidden.SnatEntryCountLimited|SNAT entry in the specified SNAT table reach it?s limit.|SNAT条目数量已达到配额。|
|400|NOT\_ALLOW\_USE\_SOURCECIDR|The User not in nat\_scope\_unlimited white list. Cannot use SourceCidr param.|内网IP超出VPC网段范围。|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|该交换机不存在，请您检查输入的交换机是否正确。|
|400|INVALID\_PARAMETER|The parameter invalid.|参数不合法。|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|该交换机已配置了 SNAT 规则，请您不要重复设置。|
|404|InvalidSnatIp.NotFound|Specified SnatIp does not found on the NAT Gateway|该公网IP不在NAT网关中。|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|该公网IP已经被DNAT使用，请更换其他公网IP地址或将当前公网IP的DNAT规则删除。|
|400|Forbindden|The specified Instance already bind eip|该实例已经绑定了 EIP，请将 ECS 实例与 EIP 解绑后再添加该端口转发规则。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

