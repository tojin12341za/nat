# DeleteForwardEntry {#reference_i4w_xmt_ndb .reference}

Deletes a DNAT entry.

**Note:** You cannot delete a DNAT entry if the DNAT entry in the Pending or Modifying state.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can debug APIs, automatically generate SDK example codes, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DeleteForwardEntry| The name of this action. Value: 

 DeleteForwardEntry

 |
|ForwardEntryId|String|Yes|fwd-8vbn3bc8roygjp0gy3xk7| The ID of the DNAT entry.

 |
|ForwardTableId|String|Yes|ftb-8vbx8xu2lqj9qb334h0ow| The ID of the DNAT table.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DeleteForwardEntry
&ForwardEntryId=fwd-8vbn3bc8roygjp0gy3xk7
&ForwardTableId=ftb-8vbx8xu2lqj9qb334h0ow
&RegionId=cn-hangzhou
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <DeleteForwardEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </DeleteForwardEntryResponse>
    
    ```

-   JSON format

    ```
    <DeleteForwardEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </DeleteForwardEntryResponse>
    
    ```


## Error codes {#section_t5p_42c_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|This operation cannot be performed because one or more DNAT entries are in the Pending or Modifying status.|
|404|InvalidForwardEntryId.NotFound|Specified forward entry ID does not exist|The specified DNAT entry does not exist.|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|The specified DNAT table does not exist.|
|400|IncorretForwardEntryStatus|The Specified forwardEntry is not exist|The specified DNAT entry does not exist.|
|400|MissingParameter|Missing mandatory parameter|Required parameters are missing.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

