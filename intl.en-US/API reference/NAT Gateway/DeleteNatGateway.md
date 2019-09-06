# DeleteNatGateway {#reference_i4w1_xmt_ndb .reference}

Deletes a NAT Gateway.

**Note:** If the NAT Gateway is associated with a shared bandwidth package, you must delete the shared bandwidth package first.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DeleteNatGateway| The name of this action. Value:

 DeleteNatGateway

 |
|NatGatewayId|String|Yes|ngw-bp1uewa15k4iy5770ya89| The ID of the NAT Gateway.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|Force|Boolean|No|false| Indicates whether to forcibly delete the NAT Gateway.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DeleteNatGateway
&NatGatewayId=ngw-bp1uewa15k4iy5770ya89
&RegionId=cn-hangzhou
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <DeleteNatGatewayResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </DeleteNatGatewayResponse>
    
    ```

-   JSON format

    ```
    {
    	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
    }
    ```


## Error codes {#section_ix1_jyv_vgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The specified NatGatewayId does not exist.|
|400|DependencyViolation.BandwidthPackages|There are BandwidthPackages on specified NatGateway not deleted.|The NAT Gateway is associated with one or more shared bandwidth packages. Delete all shared bandwidth packages first.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

