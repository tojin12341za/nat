# DescribeBandwidthPackages {#reference_i4w_xmt_ndb .reference}

Queries one or more NAT bandwidth packages in a region.

**Note:** This API can be called only if you purchased a NAT bandwidth package before January 26, 2018. If your account does not have a NAT bandwidth package purchased before January 26, 2018, you need to associate an EIP.

For more information, see [AssociateEipAddress](~~36017~~) .

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeBandwidthPackages| The name of this action. Value:

 DescribeBandwidthPackages

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|BandwidthPackageId|String|No|bwp-bp1xea10o8qxw8lkw2xa1| The ID of the NAT bandwidth package.

 |
|NatGatewayId|String|No|ngw-bp1uewa15k4iy5770ya89| The ID of the NAT Gateway.

 |
|PageNumber|Integer|No|10| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|10| The number of rows per page. Maximum value: 50. Default value: 10.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|BandwidthPackages|N/A|N/A| A list of NAT bandwidth packages.

 |
|└Bandwidth|String|5| The bandwidth value in Mbps. Valid values: 5 to 5000.

 |
|└BandwidthPackageId|String|bwp-xxoo123| The ID of the NAT bandwidth package.

 |
|└BusinessStatus|String|Normal| The status of the bandwidth package.

 Valid values: Normal | FinancialLocked | SecurityLocked.

 |
|└CreationTime|String|2017-06-08T12:20:55| The time at which the bandwidth package was created.

 Standard: ISO861. Format: UTC, YYYY-MM-DDThh:mmZ

 |
|└Description|String|test123| The description of the bandwidth package.

 |
|└ISP|String|BGP| Valid value: BGP.

 |
|└InstanceChargeType|String|PostPaid| The billing method of the instance. Currently, only the Pay-As-You-Go billing method is supported.

 Valid value: PostPaid

 |
|└InternetChargeType|String|PayByBandwidth| The Internet billing method. Valid values:

 -   PayByTraffic: Billing based on traffic

 |
|└IpCount|String|1| The number of public IP addresses in the NAT bandwidth package.

 Value range: 1 to 50.

 |
|└Name|String|xxxxxxx| The name of the NAT Gateway.

 |
|└NatGatewayId|String|ngw-xxoo123| The ID of the NAT Gateway.

 |
|└PublicIpAddresses|N/A|N/A| The IP addresses in the bandwidth package.

 |
|└AllocationId|String|eip-2zeerraiwb7uj6i0d0fo3| The allocation ID.

 |
|└ApAccessEnabled|Boolean|true| Indicates whether AP access is enabled.

 |
|└IpAddress|String|116.62.222.28| The IP address.

 |
|└UsingStatus|String|Available| The usage status.

 |
|└RegionId|String|cn-hangzhou| The region ID.

 |
|└Status|String|Available| The status of the bandwidth package.

 |
|└ZoneId|String|cn-shanghai-a| The zone of the NAT bandwidth package.

 |
|TotalCount|Integer|10| The number of queried entries.

 |
|PageNumber|Integer|10| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF"| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeBandwidthPackages
&RegionId=cn-hangzhou
&<CommonParameters>
			
```

 **Response example** 

-   XML format

    ```
    <DescribeBandwidthPackagesResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>1</TotalCount>
      <BandwidthPackages>
        <BandwidthPackage>
          <Description/>
          <IpCount>2</IpCount>
          <ISP>BGP</ISP>
          <ZoneId>cn-hangzhou-b</ZoneId>
          <InternetChargeType>PayByTraffic</InternetChargeType>
          <NatGatewayId>ngw-bp1uewa15k4iy5770ya89</NatGatewayId>
          <Name/>
          <CreationTime>2018-03-06T07:33:51Z</CreationTime>
          <Status>Available</Status>
          <BandwidthPackageId>bwp-bp1xea10o8qxw8lkw2xa1</BandwidthPackageId>
          <BusinessStatus>Normal</BusinessStatus>
          <RegionId>cn-hangzhou</RegionId>
          <InstanceChargeType>PostPaid</InstanceChargeType>
          <PublicIpAddresses>
            <PublicIpAddresse>
              <IpAddress>118.31.xx.xx</IpAddress>
              <AllocationId>nateip-bp1jb1uijvm9o8z30ejqp</AllocationId>
              <UsingStatus>Idle</UsingStatus>
            </PublicIpAddresse>
            <PublicIpAddresse>
              <IpAddress>118.31.xx.xx</IpAddress>
              <AllocationId>nateip-bp1dt4hpe8847yj4oh10w</AllocationId>
              <UsingStatus>UsedBySnatTable</UsingStatus>
            </PublicIpAddresse>
          </PublicIpAddresses>
          <Bandwidth>5</Bandwidth>
        </BandwidthPackage>
      </BandwidthPackages>
      <PageSize>10</PageSize>
    </DescribeBandwidthPackagesResponse>
    					
    ```

-   JSON format

    ```
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
    				"NatGatewayId":"ngw-bp1uewa15k4iy5770ya89",
    				"Name":"",
    				"CreationTime":"2018-03-06T07:33:51Z",
    				"Status":"Available",
    				"BandwidthPackageId":"bwp-bp1xea10o8qxw8lkw2xa1",
    				"BusinessStatus":"Normal",
    				"RegionId":"cn-hangzhou",
    				"InstanceChargeType":"PostPaid",
    				"PublicIpAddresses":{
    					"PublicIpAddresse":[
    						{
    							"IpAddress":"118.31.xx.xx",
    							"AllocationId":"nateip-bp1jb1uijvm9o8z30ejqp",
    							"UsingStatus":"Idle"
    						},
    						{
    							"IpAddress":"118.31.xx.xx",
    							"AllocationId":"nateip-bp1dt4hpe8847yj4oh10w",
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


## Error codes {#section_ztg_tt5_vgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

