# CreateNatGateway {#doc_api_951863 .reference}

使用CreateNatGateway接口创建一个NAT网关。

在调用本接口创建NAT网关时，请注意：

-   目前不支持NAT网关与自建SNAT网关（使用一台ECS作为SNAT网关）在VPC中并存。
-   NAT网关创建后，系统会在VPC的路由表中自动添加一条目标网段为0.0.0.0/0，下一跳为NAT网关的路由条目，用于将流量路由到NAT网关。
-   如果在创建NAT网关前，VPC的路由表中已经存在一条目标网段为0.0.0.0/0的路由条目，请先删除该路由条目。否则，无法创建NAT网关。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateNatGateway)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateNatGateway|要执行的操作。

 取值：**CreateNatGateway**。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpcId|String|是|vpc-bp1di7uewzmtvfuq8ufpv|VPC的ID。

 |
|BandwidthPackage.N.Bandwidth|Integer|否|5|第N个共享带宽包的带宽值，取值范围：5-5000

 **说明：** 本参数仅支持在2017年11月3日之前账号下存在NAT带宽包的用户指定。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。

 |
|BandwidthPackage.N.ISP|String|否|BGP|第n个共享带宽包中的线路ISP类型，默认为BGP（多线）。

 |
|BandwidthPackage.N.IpCount|Integer|否|5|NAT带宽包中的公网IP数量，取值范围：1-50。

 N是第几个带宽包，取值范围：1-4。

 **说明：** 本参数仅支持在2017年11月3日之前账号下存在NAT带宽包的用户指定。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。

 |
|BandwidthPackage.N.Zone|String|否|cn-hangzhou-b|第n个共享带宽包的可用区。不指定该参数时，系统将随机分配一个可用区。

 NAT带宽包的IP与后端ECS不处于同一个可用区，并不影响其连通性；但是位于相同可用区时，可减小延迟。

 **说明：** 本参数仅支持在2017年11月3日之前账号下存在NAT带宽包的用户指定。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。

 |
|ClientToken|String|否|shefffxxddjehfh123|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符。

 |
|Description|String|否|testnat|NAT网关的描述。

 描述在2-256个字符之间，不能以`http://` 和 `https://`开头。

 |
|Name|String|否|fortest|NAT网关的名称。

 名称在\\2,128个字符之间，必须以英文字母或中文开头，不能以`http://`和 `https://`开头，可包含数字，“.”，“\_”或“-”。

 如果没有指定该参数，默认使用网关ID。

 |
|Spec|String|否|small|NAT网关的规格。取值：

 -   Small\(默认值\)：小型
-   Middle：中型
-   Large：大型
-   XLarge.1：超大型

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|NatGatewayId|String|ngw-112za33e4|NAT网关ID。

 由系统生成，全局唯一，是访问实例的唯一标识。

 |
|ForwardTableIds| |ftb-11tc6xgmv|转发条目列表。

 |
|BandwidthPackageIds| |bwp-11odxu2k7|共享带宽包列表。

 |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|用户请求ID。

 |
|SnatTableIds| |stb-SnatTableIds|SNAT表的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateNatGateway
&RegionId=cn-hangzhou
&VpcId= vpc-bp1di7uewzmtvfuq8ufpv
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateNatGatewayResponse>
  <BandwidthPackageIds>bwp-**************</BandwidthPackageIds>
  <forwardTableIds>ftb-**************</forwardTableIds>
  <natGatewayId>ngw-**************</natGatewayId>
  <snatTableIds>stb-**************</snatTableIds>
  <RequestId>E43E51F2-344F-4685-8DF5-30EB298CFA81</RequestId>
</CreateNatGatewayResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"BandwidthPackageIds":[
		"bwp-**************"
	],
	"snatTableIds":[
		"stb-**************"
	],
	"natGatewayId":"ngw-**************",
	"RequestId":"E43E51F2-344F-4685-8DF5-30EB298CFA81",
	"forwardTableIds":[
		"ftb-**************"
	]
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidVPCStatus|vpc incorrect status.|该 VPC 状态非法，请您检查 VPC 状态是否输入正确。|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|MissingParameter.BandwidthPackage|only support one BandwidthPackage be created with NatGateway.|必须指定一个共享带宽包。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|该可用区不存在。|
|404|InvalidZoneId.NotFound|Can not find ZoneId for allocated ip.|该IP的可用区不正确。|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|IP 数量超过上限，可以提交工单申请增加配额。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|该描述不合法。|
|400|ZONE\_NO\_AVAILABLE\_IP|The Zone have no available ip.|该可用区没有可用IP。|
|400|InvalidParameter.BandwidthPackage.n.ISP.ValueNotSupport|The specified ISP of BandwidthPackage is not valid.|该共享带宽包的ISP不合法。|
|400|InvalidNatGatewayId.NotFound|The NatGatewayId not exist.|指定的 NatGatewayId 不存在，请您检查填写的 NatGatewayId 是否正确。|
|400|VswitchStatusError|The VSwitch is creating .|交换机正在创建中。|
|400|VpcStatusError|The Vpc is creating .|正在创建VPC。|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|该规格不合法。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

