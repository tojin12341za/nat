# CreateForwardEntry {#doc_api_Vpc_CreateForwardEntry .reference}

使用CreateForwardEntry在DNAT列表中添加DNAT条目。

每条DNAT条目由五部分组成，包括ExternalIp、ExternalPort、protocol、InternalIp和InternalPort。添加DNAT条目后，NAT网关会将ExternalIp：ExternalPort上收到的指定协议的报文转发给InternalIp:InternalPort，并将回复消息原路返回。

调用本接口添加DNAT条目时，请注意：

-   所有DNAT条目的ExternalIp、ExternalPort和Protocol三个字段组成的组合必须互不重复。即不允许将同一个源IP、同一个端口、同一个协议的消息转发到多个目标。
-   所有DNAT条目的Protocol、InternalIp和InternalPort三个字段组成的组合也必须互不重复。
-   当DNAT表中有DNAT条目的状态处于Pending或Modifying状态时，无法添加DNAT条目。
-   DNAT条目中的公网IP（ExternalIp）需满足以下条件：
    -   对于2017年11月3日之前账户下存在NAT带宽包的用户，ExternalIp必须是该NAT网关的NAT带宽包中的公网IP地址。
    -   对于2017年11月3日之前账户下不存在NAT带宽包的用户，ExternalIp必须是绑定了该NAT网关的弹性公网IP。
    -   一个公网IP不能同时用于DNAT条目和SNAT条目。
-   DNAT条目中的内网IP（InternalIp）需满足以下条件：
    -   InternalIp必需属于NAT网关所在的VPC的网段。
    -   只有当InternalIp被一个ECS实例使用且该实例没有绑定EIP时，DNAT条目才生效。若该InternalIp被HAVIP、SLB或RDS等非ECS资源使用，DNAT条目无效，公网流量无法转发到该IP上。
    -   一个公网IP不能同时用于DNAT条目和SNAT条目。
-   一个DNAT表最多可添加100条DNAT条目。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateForwardEntry)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateForwardEntry|要执行的操作。

 取值： **CreateForwardEntry**。

 |
|ExternalIp|String|是|116.xx.xx.28|公网IP地址。

 |
|ExternalPort|String|是|8080|公网端口。取值范围：1-65535

 |
|ForwardTableId|String|是|ftb-bp1mbjubq34hlcqpa5u3a|DNAT列表的ID。

 |
|InternalIp|String|是|192.168.xx.xx|目标私网IP。

 |
|InternalPort|String|是|80|目标私网端口。取值范围：1-65535

 |
|IpProtocol|String|是|TCP|协议类型。取值：

 -   TCP：转发TCP协议的报文。
-   UDP：转发UDP协议的报文。
-   Any：转发所有协议的报文。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ForwardEntryName|String|否|ForwardEntry-1|DNAT规则的名称。长度为2-128个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ForwardEntryId|String|fwd-119smw5tkxxxxxxxx|DNAT条目的ID。

 |
|RequestId|String|A4AEE536-A97A-40EB-9EBE-53A6948A6928|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateForwardEntry
&ExternalIp=116.xx.xx.28
&ExternalPort=8080
&ForwardTableId=ftb-bp1mbjubq34hlxxxxxxxx
&InternalIp=192.168.xx.xx
&InternalPort=80
&IpProtocol=TCP
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateForwardEntryResponse>
  <ForwardEntryId>fwd-119smw5tkxxxxxxxx</ForwardEntryId>
  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</CreateForwardEntryResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ForwardEntryId":"fwd-119smw5tkxxxxxxxx",
	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidExternalIp.Malformed|The specified ExternalIp is not a valid IP address.|该公网IP不合法。|
|400|InvalidInternalIp.Malformed|The specified InternalIp is not a valid IP address.|该目标私网IP不合法。|
|400|InvalidExternalPort.Malformed|The specified ExternalPort is not a valid port.|该公网端口不合法。|
|400|InvalidInternalPort.Malformed|The specified InternalPort is not a valid port.|该私网端口不合法。|
|400|Forbidden.DestnationIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|该私网IP不在VPC的网段范围内，请您填写在VPC的网段范围内的私网IP。|
|400|InvalidProtocal.ValueNotSupported|The specified IpProtocol does not support.|该协议类型不支持。|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|无法执行该操作。DNAT表中有DNAT条目的状态处于Pending或Modifying状态。|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|指定的 DNAT 表不存在，请您检查输入参数是否正确。|
|404|InvalidExternalIp.NotFound|Specified External Ip address does not found on the VRouter|该公网IP不存在。|
|400|Forbidden.ExternalIp.UsedInSnatTable|The specified ExternalIp is already used in SnatTable|该公网IP已经被SNAT使用，请更换其他公网IP或将当前公网IP的SNAT规则删除。|
|400|Forbindden|The specified Instance already bind eip|该实例已经绑定了 EIP，请将 ECS 实例与 EIP 解绑后再添加该端口转发规则。|
|400|Forbidden.InternalIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|该私网IP不在VPC的网段范围内。|
|400|Invalid.natgwNotExist|The specified natgateway not exist.|该NAT网关不存在。|
|400|InvalidIp.NotInNatgw|The specified Ip not belong to natgateway.|该 IP 地址不属于该 NAT 网关。|
|400|MissingParameter|Missing mandatory parameter|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

