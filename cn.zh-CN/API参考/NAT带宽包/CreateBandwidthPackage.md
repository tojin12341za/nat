# CreateBandwidthPackage {#doc_api_Vpc_CreateBandwidthPackage .reference}

使用CreateBandwidthPackage接口创建NAT带宽包。

NAT网关上的公网IP和带宽，被封装为NAT带宽包。一个NAT网关最多可创建四个NAT带宽包。

一个NAT带宽包包含：

-   一份共享带宽
-   一组公网IP

**说明：** 本接口仅支持在2017年11月3日之前账号下存在NAT带宽包的用户调用。2017年11月3日之前账号下不存在NAT带宽包的用户，请通过绑定EIP的方式申请公网IP。


## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateBandwidthPackage&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateBandwidthPackage|要执行的操作。

 取值： **CreateBandwidthPackage**。

 |
|Bandwidth|Integer|是|5|NAT带宽包的带宽。

 取值范围：5-1000

 |
|IpCount|Integer|是|2|NAT带宽包中的公网IP数量，取值范围：1-50

 |
|NatGatewayId|String|是|ngw-7mwb327j1|NAT网关的ID。

 |
|RegionId|String|是|cn-hangzhou|NAT带宽包所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|she11234556664566|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Description|String|否|带宽包描述|NAT带宽包的描述信息。 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|ISP|String|否|BGP|目前只支持一种：BGP。

 |
|InternetChargeType|String|否|PayByBandwidth|网络计费类型，取值：

 -   PayByTraffic：按流量计费
-   PayByBandwidth：按带宽计费

 |
|Name|String|否|带宽包名称|NAT带宽包的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|Zone|String|否|cn-shanghai-a|NAT带宽包位于的可用区。

 不指定该参数时，系统将随机分配一个可用区。

 **说明：** NAT带宽包上的IP与后端ECS不处于同一个可用区，并不影响其连通性；但是位于相同可用区时，可减小延迟。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BandwidthPackageId|String|bwp-s6lmotmkk|NAT带宽包的ID。

 |
|RequestId|String|54ED4074-3F89-4F11-B166-837DD3E20FE3|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateBandwidthPackage
&Bandwidth=5
&IpCount=2
&NatGatewayId=ngw-7mwb327j1
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateBandwidthPackageResponse>
	  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
          <BandwidthPackageId>bwp-s6lmotmkk</BandwidthPackageId>
</CreateBandwidthPackageResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"BandwidthPackageId":"bwp-s6lmotmkk",
	"RequestId":"54ED4074-3F89-4F11-B166-837DD3E20FE3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|该 VPC 不存在，请您检查输入的 VPC 是否正确。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|该可用区不存在。|
|404|InvalidZoneId.NotFound|Can not find ZoneId for allocated ip.|该IP的可用区不正确。|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|IP 数量超过上限，可以提交工单申请增加配额。|
|400|QuotaExceeded.BandwidthPackageCountOnNatGateway|BandwidthPackage count limit on one NatGateway exceeded.|超过了共享带宽包上限，一个NAT网关最多可创建四个共享带宽包。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|该描述不合法。|
|400|InvalidParameter.BandwidthPackage.n.ISP.ValueNotSupport|The specified ISP of BandwidthPackage is not valid.|该共享带宽包的ISP不合法。|
|400|ZONE\_NO\_AVAILABLE\_IP|The Zone have no available ip.|该可用区没有可用IP。|
|404|NATGW\_NOT\_EXIST|The NatGateway not exist.|该 NAT 网关不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

