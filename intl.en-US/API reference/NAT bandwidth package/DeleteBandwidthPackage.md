# DeleteBandwidthPackage {#reference_i4w_3xmt_ndb .reference}

Deletes a NAT bandwidth package.

**Note:** This API can be called only if you purchased a NAT bandwidth package before January 26, 2018. If your account does not have a NAT bandwidth package purchased before January 26, 2018, you need to associate an EIP. For more information, see [AssociateEipAddress](~~36017~~).

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DeleteBandwidthPackage| The name of this action. Value:

 DeleteBandwidthPackage

 |
|BandwidthPackageId|String|Yes|bwp-bp1arsrmca9kp7inuc3a1| The ID of the NAT bandwidth package.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|Force|Boolean|No|false| Indicates whether to forcibly delete the NAT bandwidth package.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|7D275A59-1EB0-4775-8A20-2A47055EAC5C|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#codeblock_5oc_xeb_5uf}
https://vpc.aliyuncs.com/?Action=DeleteBandwidthPackage
&BandwidthPackageId=bwp-bp1arsrmca9kpxxxxxxxx
&RegionId=cn-hangzhou
&<CommonParameters>
			
```

 **Response example** 

-   XML format

    ```
    <DeleteBandwidthPackageResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </DeleteBandwidthPackageResponse>
    					
    ```

-   JSON format

    ```
    {
    	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
    }
    ```


## Error codes {#section_vx3_45v_vgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|400|DependencyViolation.ForwardEntry|The specified BandwidthPackageId has dependent resource.|The specified shared bandwidth package is associated with an SNAT/DNAT entry. Delete the SNAT/DNAT entry first.|
|400|DependencyViolation.SnatEntry|The specified BandwidthPackageId has dependent resource.|The specified shared bandwidth package is associated with an SNAT/DNAT entry. Delete the SNAT/DNAT entry first.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

