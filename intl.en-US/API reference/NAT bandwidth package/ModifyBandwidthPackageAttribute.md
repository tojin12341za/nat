# ModifyBandwidthPackageAttribute {#reference_i44w_xmt_ndb .reference}

Modifies the name and description of a NAT bandwidth package.

**Note:** This API can be called only if you purchased a NAT bandwidth package before January 26, 2018. If your account does not have a NAT bandwidth package purchased before January 26, 2018, you need to associate an EIP. For more information, see [AssociateEipAddress](~~36017~~)

## Debug {#section_lc7_ejt_lbk .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifyBandwidthPackageAttribute| The name of the action. Value:

 ModifyBandwidthPackageAttribute

 |
|BandwidthPackageId|String|Yes|bwp-s6lmotmkk| The ID of the NAT bandwidth package.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the NAT bandwidth package belongs.

 To query the region ID, call DescribeRegions.

 |
|Description|String|No|xxxxxxxx| The description of the NAT bandwidth package.

 The description must be 2 to 256 characters in length. It must start with a letter. It cannot start with `http://` or `https://`.

 |
|Name|String|No|NAT bandwidth package| The name of the NAT bandwidth package.

 The name must be 2 to 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter. It cannot start with `http://` or `https://`.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|DFDDD35D-3F29-4E15-AA28-53F5341F9599|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=ModifyBandwidthPackageAttribute
&BandwidthPackageId=bwp-s6lmotmkkxxxxxxxx
&RegionId=cn-hangzhou
&<CommonParameters>
			
```

 **Response example** 

-   XML format

    ```
    <ModifyBandwidthPackageAttributeResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
    </ModifyBandwidthPackageAttributeResponse>
    					
    ```

-   JSON format

    ```
    {
    	"RequestId":"54ED4074-3F89-4F11-B166-837DD3E20FE3"
    }
    ```


## Error codes {#section_h5w_nx5_vgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidBandwidthPackageId.NotFound|The specified bandwidthPackageId does not exist in our records.|The specified shared bandwidth package does not exist.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The specified name is invalid.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The specified description is invalid.|

[See common errors](https://error-center.aliyun.com/status/product/Vpc)

