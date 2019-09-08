# DescribeNatGateways {#doc_api_Vpc_DescribeNatGateways .reference}

使用DescribeNatGateways接口查询已创建的NAT网关。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeNatGateways&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeNatGateways|要执行的操作。 取值： **DescribeNatGateways**。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|InstanceChargeType|String|否|PostPaid|实例的付费方式。目前仅支持按量付费。

 PostPaid：后付费，即按量付费。

 |
|Name|String|否|NAT网关名称|NAT网关的名称。

 |
|NatGatewayId|String|否|ngw-bp1uewa15k4iy5770xxxx|NAT网关的ID。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|1|分页查询时每页的行数，最大值为50，默认值为10。

 |
|Spec|String|否|Large|NAT网关的规格。取值：

 -   **Small\(默认值\)**：小型
-   **Middle**：中型
-   **Large**：大型
-   **XLarge.1**：超大型

 |
|VpcId|String|否|vpc-bp15zckdt37pq72zxxxx|VPC的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|NatGateways| | |NAT网关的详细信息。

 |
|AutoPay|Boolean|true|是否自动付费，取值：

 -   false：不开启自动付费，生成订单后需要到订单中心完成支付。
-   true：开启自动付费，自动支付订单。

 **说明：** **InstanceChargeType**参数的值为 **PrePaid**时，该参数必选。

 |
|BandwidthPackageIds| |bwp-s6lmotmkk|NAT网关绑定的带宽包ID。

 |
|BusinessStatus|String|Normal|NAT网关的状态：

 -   **Normal**：正常
-   **FinancialLocked**：欠费锁定状态
-   **SecurityLocked**：安全风控锁定状态

 |
|CreationTime|String|2017-06-08T12:20:55|创建时间。按照ISO8601标准表示，并需要使用UTC时间。格式为：YYYY-MM-DDThh:mmZ

 |
|Description|String|NAT|NAT网关的描述。

 |
|ExpiredTime|String|2017-08-26T16:00Z|NAT网关的过期时间。

 |
|ForwardTableIds| |ftb-uf6gj3mhsg94qsqstfqsx|端口转发表ID。

 |
|InstanceChargeType|String|PostPaid|实例的付费方式。目前仅支持按量付费。

 PostPaid：后付费，即按量付费。

 |
|IpLists| | |NAT网关绑定的弹性公网IP。

 |
|IpAddress|String|116.62.222.xx|弹性公网IP的地址。

 |
|Name|String|abc|实例名称。

 |
|NatGatewayId|String|ngw-bp1047e2d4z7kf2kixxxx|NAT网关的ID。

 |
|RegionId|String|cn-hangzhou|NAT网关的所在地域ID。

 |
|SnatTableIds| |stb-uf6dalcdu0krz423pv8mq|NAT网关的SNAT表ID。

 |
|Spec|String|Small|NAT网关的规格。

 |
|Status|String|Initiating|NAT的网关的状态，取值：

 -   Initiating：初始化中
-   Available：可用
-   Pending：配置中

 |
|VpcId|String|vpc-bp15zckdt37pq72xxxx|所属的VPC ID。

 |
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含的条目数。

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|用户请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeNatGateways
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeNatGatewaysResponse>
	  <PageNumber>1</PageNumber>
	  <TotalCount>1</TotalCount>
	  <PageSize>10</PageSize>
	  <RequestId>1207C80C-7CAB-4874-A9A0-D19EC9F35490</RequestId>
	  <NatGateways>
		    <NatGateway>
			      <Description></Description>
			      <Spec>Small</Spec>
			      <IpLists>
				        <IpList>
					          <IpAddress>118.31.65.181</IpAddress>
					          <AllocationId>eip-bp1xyg5ipmh3nledxywxf</AllocationId>
					          <UsingStatus>UsedBySnatTable</UsingStatus>
				        </IpList>
				        <IpList>
					          <IpAddress>47.97.187.34</IpAddress>
					          <AllocationId>eip-bp19eue77u20cffjcu4ea</AllocationId>
					          <UsingStatus>UsedByForwardTable</UsingStatus>
				        </IpList>
			      </IpLists>
			      <ForwardTableIds>
				        <ForwardTableId>ftb-bp15o9aylj19vfvgtnzoy</ForwardTableId>
			      </ForwardTableIds>
			      <VpcId>vpc-bp15k6sx6fhdz2jw4daz0</VpcId>
			      <NatGatewayId>ngw-bp1047e2d4z7kf2kiy25t</NatGatewayId>
			      <CreationTime>2018-01-10T09:48:29Z</CreationTime>
			      <BandwidthPackageIds></BandwidthPackageIds>
			      <Name></Name>
			      <Status>Available</Status>
			      <BusinessStatus>Normal</BusinessStatus>
			      <RegionId>cn-hangzhou</RegionId>
			      <SnatTableIds>
				        <SnatTableId>stb-bp1tyr0o48w6wymur4gvn</SnatTableId>
			      </SnatTableIds>
			      <InstanceChargeType>PostPaid</InstanceChargeType>
		    </NatGateway>
	  </NatGateways>
</DescribeNatGatewaysResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"1207C80C-7CAB-4874-A9A0-D19EC9F35490",
	"NatGateways":{
		"NatGateway":[
			{
				"Description":"",
				"Spec":"Small",
				"IpLists":{
					"IpList":[
						{
							"IpAddress":"118.31.65.181",
							"AllocationId":"eip-bp1xyg5ipmh3nledxywxf",
							"UsingStatus":"UsedBySnatTable"
						},
						{
							"IpAddress":"47.97.187.34",
							"AllocationId":"eip-bp19eue77u20cffjcu4ea",
							"UsingStatus":"UsedByForwardTable"
						}
					]
				},
				"ForwardTableIds":{
					"ForwardTableId":[
						"ftb-bp15o9aylj19vfvgtnzoy"
					]
				},
				"VpcId":"vpc-bp15k6sx6fhdz2jw4daz0",
				"NatGatewayId":"ngw-bp1047e2d4z7kf2kiy25t",
				"CreationTime":"2018-01-10T09:48:29Z",
				"BandwidthPackageIds":{
					"BandwidthPackageId":[]
				},
				"Name":"",
				"Status":"Available",
				"BusinessStatus":"Normal",
				"RegionId":"cn-hangzhou",
				"SnatTableIds":{
					"SnatTableId":[
						"stb-bp1tyr0o48w6wymur4gvn"
					]
				},
				"InstanceChargeType":"PostPaid"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

