# DeleteSnatEntry {#reference_4i4w_xmt_ndb .reference}

Deletes an SNAT entry.

**Note:** You cannot delete an SNAT entry if the SNAT entry in the Pending or Modifying state.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DeleteSnatEntry| The name of this action. Value: 

 DeleteSnatEntry

 |
|RegionId|String|Yes|cn-hangzhou| The region ID of the NAT Gateway where the SNAT entry is to be deleted.

 To query the region ID, call DescribeRegions.

 |
|SnatEntryId|String|Yes|snat-bp1vcgcf8tm0plqcgfl04| The ID of the SNAT entry to be deleted.

 |
|SnatTableId|String|Yes|stb-bp190wu8io1vgev80kec7| The ID of the SNAT table from which the SNAT entry is to be deleted.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|:------------|:----------|
|RequestId|String|47B80B6A-759A-479C-A565-76D04BDA29F3|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DeleteSnatEntry
&RegionId=cn-hangzhou
&SnatEntryId=snat-bp1vcgcf8tm0plqcgfl04
&SnatTableId=stb-bp190wu8io1vgev80kec7
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <DeleteSnatEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </DeleteSnatEntryResponse>
    
    ```

-   JSON format

    ```
    {
    	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
    }
    ```


## Error codes {#section_ejy_dwc_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|400|IncorretSnatEntryStatus|Some Snat entry status blocked this operation..|You cannot perform this operation because one or more SNAT entries are in the Pending or Modifying state.|
|404|InvalidSnatEntryId.NotFound|Specified Snat entry ID does not exist|The specified SNAT entry does not exist.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The specified SNAT table does not exist.|
|404|InvalidSnatEntryId.NotFound|Specified SNAT entry does not exist.|The specified SNAT entry does not exist.|

[View common error codes](https://error-center.aliyun.com/status/product/Vpc)

