# ModifyBandwidthPackageSpec {#reference_i41w_xmt_ndb .reference}

Modifies the bandwidth of a NAT bandwidth package.

**Note:** This API can be called only if you purchased a NAT bandwidth package before January 26, 2018. If your account does not have a NAT bandwidth package purchased before January 26, 2018, you need to associate an EIP.

[AssociateEipAddress](~~36017~~) .

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifyBandwidthPackageSpec| The name of this action. Value:

 ModifyBandwidthPackageSpec

 |
|BandWidth|Integer|Yes|5| The bandwidth of the NAT bandwidth package. Value range: 5 to 1000.

 |
|BandwidthPackageId|String|Yes|bwp-s6lmotmkk| The ID of the NAT bandwidth package.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT bandwidth package belongs.

 To query the region ID, call DescribeRegions.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|079874CD-AEC1-43E6-AC03-ADD96B6E4907|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=ModifyBandwidthPackageSpec
&Bandwidth=5
&BandwidthPackageId=bwp-s6lmotmkkxxxxxxxx
&RegionId=cn-hangzhou
&<CommonParameters>
			
```

 **Response example** 

-   XML format

    ```
    <ModifyBandwidthPackageSpecResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
    </ModifyBandwidthPackageSpecResponse>
    					
    ```

-   JSON format

    ```
    {
    	"RequestId":"54ED4074-3F89-4F11-B166-837DD3E20FE3"
    }
    ```


## Error codes {#section_bqn_fv5_vgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidBandwidth.ValueNotSupported|The specified value of Bandwidth not supported.|The specified peak bandwidth is not supported.|
|404|BandwidthPackage.FinancialLocked|The specified BandwidthPackage has been Financail Lock.|The specified bandwidth package is locked due to insufficient account balance.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

