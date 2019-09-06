# DescribeNatGateways {#reference_i4w_xmt_n1db .reference}

Queries one or more NAT Gateways in a region.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeNatGateways| The name of the action. Valid value: 

 DescribeNatGateways

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|Name|String|No|The name of the NAT Gateway| The name of the NAT Gateway.

 |
|NatGatewayId|String|No|ngw-bp1uewa15k4iy5770ya89| The ID of the NAT Gateway.

 |
|PageNumber|Integer|No|10| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|1| The number of entries per page. Maximum value: 50. Default value: 10.

 |
|VpcId|String|No|vpc-bp15zckdt37pq72zvw3| The ID of the VPC.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|NatGateways|N/A|N/A| A list of NAT Gateways.

 |
|└AutoPay|Boolean|true| Indicates whether automatic payment is enabled. Valid values:

 -   false: Automatic payment is not enabled. After an order is generated, you need to go to the order center to complete the payment.
-   true: Automatic payment is enabled.

 **Note:** This parameter is required when the **InstanceChargeType** value is **PrePaid**.

 |
|└BandwidthPackageIds|N/A|bwp-s6lmotmkk| The IDs of the bandwidth packages attached to the NAT Gateway.

 |
|└BusinessStatus|String|Normal| The status of the NAT Gateway:

 -   **Normal**: Normal
-   **FinancialLocked**: Locked due to insufficient account balance
-   **SecurityLocked**: Locked due to security reasons

 |
|└CreationTime|String|2017-06-08T12:20:55| The time at which the NAT Gateway was created. Standard: ISO8601. Format: YYYY-MM-DDThh:mmZ

 |
|└Description|String|NAT| The description of the NAT Gateway.

 |
|└ExpiredTime|String|2017-08-26T16:00Z| The time at which the NAT Gateway is to expire.

 |
|└ForwardTableIds|N/A|ftb-uf6gj3mhsg94qsqstfqsx| The IDs of port forwarding tables.

 |
|└InstanceChargeType|String|PostPaid| The billing method of the instance. Currently, only the Pay-As-You-Go billing method is supported. Valid value:

 PostPaid: Pay-As-You-Go

 |
|└IpLists| | | The EIPs attached to the NAT Gateway.

 |
|└IpAddress|String|116.62.222.28| The IP address of the EIP.

 |
|└Name|String|The name of the instance| The name of the NAT Gateway.

 |
|└NatGatewayId|String|ngw-bp1047e2d4z7kf2kiy25t| The ID of the NAT Gateway.

 |
|└RegionId|String|cn-hangzhou| NThe ID of the region to which the NAT Gateway belongs.

 |
|└SnatTableIds| |stb-uf6dalcdu0krz423pv8mq| The ID of the SNAT table of the NAT Gateway.

 |
|└Spec|String|Small| The specification of the NAT Gateway.

 |
|└Status|String|Initiating| The status of the NAT Gateway. Valid values:

 -   Initiating: initiating
-   Available: available
-   Pending: being configured

 |
|└VpcId|String|vpc-bp15zckdt37pq72zvw3| The ID of the VPC.

 |
|TotalCount|Integer|10| The number of queried entries.

 |
|PageNumber|Integer|10| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeNatGateways
&RegionId=cn-hangzhou
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <DescribeNatGatewaysResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>1</TotalCount>
      <PageSize>10</PageSize>
      <RequestId>1207C80C-7CAB-4874-A9A0-D19EC9F35490</RequestId>
      <NatGateways>
        <NatGateway>
          <Description/>
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
          <BandwidthPackageIds/>
          <Name/>
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

-   JSON format

    ```
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


## Error codes {#section_w1n_jfv_vgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

