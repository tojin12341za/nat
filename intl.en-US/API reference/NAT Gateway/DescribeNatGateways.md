# DescribeNatGateways {#doc_api_Vpc_DescribeNatGateways .reference}

Queries one or more NAT Gateways in a region.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DescribeNatGateways&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeNatGateways| The name of this action. Value: **DescribeNatGateways**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the NAT Gateway belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|InstanceChargeType|String|No|PostPaid| Optional. The billing method of the NAT Gateway. Currently, only Pay-As-You-Go is supported.

 PostPaid: Pay-As-You-Go

 |
|Name|String|No|NAT Gateway| Optional. The name of the NAT Gateway.

 |
|NatGatewayId|String|No|ngw-bp1uewa15k4iy5770xxxx| Optional. The ID of the NAT Gateway.

 |
|PageNumber|Integer|No|10| Optional. The page number. Default value: 1

 |
|PageSize|Integer|No|1| Optional. The number of entries per page in the case of a paged query result. Maximum value: 50. Default value: 10

 |
|Spec|String|No|Large| Optional. The specification of the NAT Gateway. Valid values:

 -   **Small \(default\)**
-   **Middle**
-   **Large**
-   **XLarge.1**

 |
|VpcId|String|No|vpc-bp15zckdt37pq72zxxxx| Optional. The ID of the VPC.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|NatGateways| | | The details of the NAT Gateway.

 |
|AutoPay|Boolean|true| Indicates whether the NAT Gateway order is paid automatically. Valid values:

 -   false: Automatic payment is not enabled. After an order is placed, you must go to the order center to complete the payment.
-   true: Automatic payment is enabled and the order is paid automatically.

 **Note:** This parameter is required if the value of the **InstanceChargeType** parameter is se to **PrePaid**.

 |
|BandwidthPackageIds| |bwp-s6lmotmkk| The ID of the bandwidth package associated with the NAT Gateway.

 |
|BusinessStatus|String|Normal| The status of the NAT gateway:

 -   **Normal**: The NAT Gateway is normal.
-   **FinancialLocked**: The NAT Gateway is locked because of an overdue bill.
-   **SecurityLocked**: The NAT Gateway is locked due to security reasons.

 |
|CreationTime|String|2017-06-08T12:20:55| The time when the NAT Gateway was created. This parameter uses the ISO 8601 format and the output is UTC+8. Format: YYYY-MM-DDThh:mmZ.

 |
|Description|String|NAT| The description of the NAT Gateway.

 |
|ExpiredTime|String|2017-08-26T16:00Z| The time when the NAT Gateway expires.

 |
|ForwardTableIds| |ftb-uf6gj3mhsg94qsqstfqsx| The ID of the port forwarding table.

 |
|InstanceChargeType|String|PostPaid| The billing method of the NAT Gateway. Currently, only Pay-As-You-Go is supported.

 PostPaid: Pay-As-You-Go

 |
|IpLists| | | The Elastic IP Address \(EIP\) associated with the NAT Gateway.

 |
|IpAddress|String|116.62.222.xx| The IP address of the EIP.

 |
|Name|String|abc| The name of the NAT Gateway.

 |
|NatGatewayId|String|ngw-bp1047e2d4z7kf2kixxxx| The ID of the NAT Gateway.

 |
|RegionId|String|cn-hangzhou| The ID of the region to which the NAT Gateway belongs.

 |
|SnatTableIds| |stb-uf6dalcdu0krz423pv8mq| The ID of the SNAT table of the NAT Gateway.

 |
|Spec|String|Small| The specification of the NAT Gateway.

 |
|Status|String|Initiating| The status of the NAT Gateway. Valid values:

 -   Initiating: The NAT Gateway is being initialized.
-   Available: The NAT Gateway is available.
-   Pending: The NAT Gateway is being configured.

 |
|VpcId|String|vpc-bp15zckdt37pq72xxxx| The ID of the VPC to which the NAT Gateway belongs.

 |
|TotalCount|Integer|10| The total number of entries.

 |
|PageNumber|Integer|10| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeNatGateways
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`XML` format

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

`JSON` format

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

## Errors {#section_exu_1cs_3vg .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified RegionId does not exist.|

