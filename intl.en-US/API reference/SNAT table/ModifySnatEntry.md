# ModifySnatEntry {#reference_i4w3_xmt_ndb .reference}

Modifies an SNAT entry.

**Note:** You cannot modify an SNAT entry that is in the Pending or Modifying state.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifySnatEntry| The name of this action. Value: 

 ModifySnatEntry

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|SnatEntryId|String|Yes|snat-bp1vcgcf8tm0plqcgfl04| The ID of the SNAT entry.

 |
|SnatIp|String|Yes|47.XXX.XXX.98|The public IP address. Separate multiple IP addresses with commas.|
|SnatTableId|String|Yes|stb-8vbczigrhop8x5u3twlhd| The ID of the SNAT table.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=ModifySnatEntry
&RegionId=cn-hangzhou
&SnatEntryId=snat-bp1vcgcf8tm0plqcgfl04
&SnatIp=47.XXX.XXX.98
&SnatTableId=stb-8vbczigrhop8x5u3twlhd
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <ModifySnatEntryResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
    </ModifySnatEntryResponse>
    
    ```

-   JSON format

    ```
    {
    	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
    }
    ```


## Error codes {#section_lsq_bsc_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The specified SNAT table does not exist.|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|The specified SnatIp is invalid.|
|404|InvalidSnatEntryId.NotFound|Specified SNAT entry does not exist.|The specified SNAT entry does not exist.|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|SNAT rules have already been configured for this VSwitch.|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|The specified public IP address is already being used by a DNAT rule. Select a different IP address or delete the DNAT rule that uses this IP address.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

