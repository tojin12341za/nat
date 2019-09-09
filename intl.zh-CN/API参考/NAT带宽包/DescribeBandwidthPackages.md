# DescribeBandwidthPackages {#doc_api_Vpc_DescribeBandwidthPackages .reference}

使用DescribeBandwidthPackages接口查询指定地域的NAT带宽包。

本接口仅支持在2018年1月26日之前账号下存在NAT带宽包的用户调用。2018年1月26日之前账号下不存在NAT带宽包的用户，请绑定EIP。

详情参见[AssociateEipAddress](~~36017~~)。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeBandwidthPackages&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeBandwidthPackages|要执行的操作。 取值：**DescribeBandwidthPackages**。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BandwidthPackageId|String|否|bwp-bp1xea10o8qxwdfs\*\*\*\*|NAT网关带宽包的ID。

 |
|NatGatewayId|String|否|ngw-bp1uewa15k4iydfre\*\*\*\*|NAT网关的ID。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为**1**。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BandwidthPackages| | |NAT带宽包的详细信息。

 |
|BandwidthPackage| | |NAT带宽包的详细信息。

 |
|Bandwidth|String|5|带宽值，取值范围：**5**~**5000**，单位为Mbps。

 |
|BandwidthPackageId|String|bwp-xxoo123sfwr\*\*\*\*|NAT带宽包的ID。

 |
|BusinessStatus|String|Normal|带宽包的状态。

 -   **Normal**：正常。
-   **FinancialLocked**：欠费锁定状态。
-   **SecurityLocked**：安全风控锁定状态。

 |
|CreationTime|String|2017-06-08T12:20:55|创建时间。

 按照ISO8601标准表示，并需要使用UTC时间。

 格式为：YYYY-MM-DDThh:mmZ。

 |
|Description|String|test123|描述信息。

 描述长度为2~256个字符，实例描述会显示在控制台。不填则为空，默认为空。不能以`http://`和`https://`开头。

 |
|ISP|String|BGP|目前只支持**BGP**。

 |
|InstanceChargeType|String|PostPaid|实例的付费方式。目前仅支持**PostPaid**（按量付费）。

 |
|InternetChargeType|String|PayByBandwidth|网络计费类型。

 -   **PayByTraffic**：按流量计费。

 |
|IpCount|String|1|NAT带宽包中的公网IP数量。

 取值范围：**1**~**50**。

 |
|Name|String|abc|NAT带宽包的名称。

 |
|NatGatewayId|String|ngw-xxoo123ggtf\*\*\*\*|NAT网关ID。

 |
|PublicIpAddresses| | |带宽包中的IP。

 |
|PublicIpAddresse| | |带宽包中的IP。

 |
|AllocationId|String|eip-2zeerraiwb7ujdeds\*\*\*\*|分配ID。

 |
|IpAddress|String|116.xx.xx.28|IP地址。

 |
|UsingStatus|String|Available|使用状态。

 |
|RegionId|String|cn-hangzhou|NAT带宽包所在地域。

 |
|Status|String|Available|带宽包状态。

 |
|ZoneId|String|cn-shanghai-a|NAT带宽包所在的可用区。

 |
|TotalCount|Integer|10|列表条目数。

 |
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含的条目数。

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF"|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeBandwidthPackages
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeBandwidthPackagesResponse>
	  <PageNumber>1</PageNumber>
	  <TotalCount>1</TotalCount>
	  <BandwidthPackages>
		    <BandwidthPackage>
			      <Description></Description>
			      <IpCount>2</IpCount>
			      <ISP>BGP</ISP>
			      <ZoneId>cn-hangzhou-b</ZoneId>
			      <InternetChargeType>PayByTraffic</InternetChargeType>
			      <NatGatewayId>ngw-bp1uewa15k4iyaszaasza****</NatGatewayId>
			      <Name></Name>
			      <CreationTime>2018-03-06T07:33:51Z</CreationTime>
			      <Status>Available</Status>
			      <BandwidthPackageId>bwp-bp1xea10o8qxwaswq****</BandwidthPackageId>
			      <BusinessStatus>Normal</BusinessStatus>
			      <RegionId>cn-hangzhou</RegionId>
			      <InstanceChargeType>PostPaid</InstanceChargeType>
			      <PublicIpAddresses>
				        <PublicIpAddresse>
					          <IpAddress>118.31.xx.xx</IpAddress>
					          <AllocationId>nateip-bp1jb1uijvm9oaqaqaqaq****</AllocationId>
					          <UsingStatus>Idle</UsingStatus>
				        </PublicIpAddresse>
				        <PublicIpAddresse>
					          <IpAddress>118.31.xx.xx</IpAddress>
					          <AllocationId>nateip-bp1dt4hpe8847aceb****</AllocationId>
					          <UsingStatus>UsedBySnatTable</UsingStatus>
				        </PublicIpAddresse>
			      </PublicIpAddresses>
			      <Bandwidth>5</Bandwidth>
		    </BandwidthPackage>
	  </BandwidthPackages>
	  <PageSize>10</PageSize>
	  <RequestId>8909013D-4A64-41A6-93E6-E3FD08A3EAFE</RequestId>
</DescribeBandwidthPackagesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"BandwidthPackages":{
		"BandwidthPackage":[
			{
				"Description":"",
				"IpCount":"2",
				"ISP":"BGP",
				"ZoneId":"cn-hangzhou-b",
				"InternetChargeType":"PayByTraffic",
				"NatGatewayId":"ngw-bp1uewa15k4iyaszaasza****",
				"Name":"",
				"CreationTime":"2018-03-06T07:33:51Z",
				"Status":"Available",
				"BandwidthPackageId":"bwp-bp1xea10o8qxwaswq****",
				"BusinessStatus":"Normal",
				"RegionId":"cn-hangzhou",
				"InstanceChargeType":"PostPaid",
				"PublicIpAddresses":{
					"PublicIpAddresse":[
						{
							"IpAddress":"118.31.xx.xx",
							"AllocationId":"nateip-bp1jb1uijvm9oaqaqaqaq****",
							"UsingStatus":"Idle"
						},
						{
							"IpAddress":"118.31.xx.xx",
							"AllocationId":"nateip-bp1dt4hpe8847aceb****",
							"UsingStatus":"UsedBySnatTable"
						}
					]
				},
				"Bandwidth":"5"
			}
		]
	},
	"PageSize":10,
	"RequestId":"8909013D-4A64-41A6-93E6-E3FD08A3EAFE"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

