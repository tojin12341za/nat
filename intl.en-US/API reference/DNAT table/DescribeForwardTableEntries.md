# DescribeForwardTableEntries {#reference_amt_w2p_51rdb .reference}

Queries DNAT entries in a DNAT table.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeForwardTableEntries| The name of this action. Value: 

 DescribeForwardTableEntries

 |
|ForwardTableId|String|Yes|ftb-bp1mbjubq34hlcqpa5u3a| The ID of the DNAT table.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|ForwardEntryId|String|No|fwd-8vbn3bc8roygjp0gy3xk7| The ID of the DNAT entry allocated by the system.

 |
|PageNumber|Integer|No|1| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|10| The number of rows per page. Maximum value:50. Default value: 10.

 |

## Response parameters {#section_hlq_4gp_rdb .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|ForwardTableEntries| | | A list of DNAT entries.

 |
|└ExternalIp|String|139.xxx.xx.79| The public IP address.

 |
|└ExternalPort|String|80| The public port.

 |
|└ForwardEntryId|String|fwd-119smw5tk| The ID of the DNAT entry.

 |
|└ForwardTableId|String|ftb-11tc6xgmv| The ID of the DNAT table to which the DNAT entry belongs.

 |
|└InternalIp|String|192.168.1.1| The private IP address.

 |
|└InternalPort|String|any| The target private port. Value range: 1 to 65535.

 |
|└IpProtocol|String|tcp| The protocol type.

 |
|└Status|String|Available| The status of the DNAT entry.

 |
|TotalCount|Integer|5| The number of queried entries.

 |
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|A6C4A8B1-7561-4509-949C-20DEB40D71E6| The ID of the request.

 |

## Examples { .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeForwardTableEntries
&ForwardTableId=ftb-bp1mbjubq34hlcqpa5u3a
&RegionId=cn-hangzhou
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <DescribeForwardTableEntriesResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>1</TotalCount>
      <PageSize>10</PageSize>
      <RequestId>74F2BAD8-AF35-4C57-81F1-5E33BFB0F5F2</RequestId>
      <ForwardTableEntries>
        <ForwardTableEntry>
          <Status>Available</Status>
          <IpProtocol>any</IpProtocol>
          <ForwardEntryId>fwd-bp18jpb1tlm550di3q5pb</ForwardEntryId>
          <ExternalIp>47.97.xx.xx</ExternalIp>
          <ForwardTableId>ftb-bp15o9aylj19vfvgtnzoy</ForwardTableId>
          <ExternalPort>any</ExternalPort>
          <InternalPort>any</InternalPort>
          <InternalIp>192.168.xx.xx</InternalIp>
        </ForwardTableEntry>
      </ForwardTableEntries>
    </DescribeForwardTableEntriesResponse>
    
    ```

-   JSON format

    ```
    {
    	"PageNumber":1,
    	"TotalCount":1,
    	"PageSize":10,
    	"RequestId":"74F2BAD8-AF35-4C57-81F1-5E33BFB0F5F2",
    	"ForwardTableEntries":{
    		"ForwardTableEntry":[
    			{
    				"ForwardEntryId":"fwd-bp18jpb1tlm550di3q5pb",
    				"IpProtocol":"any",
    				"Status":"Available",
    				"ExternalIp":"47.97.xx.xx",
    				"ForwardTableId":"ftb-bp15o9aylj19vfvgtnzoy",
    				"ExternalPort":"any",
    				"InternalPort":"any",
    				"InternalIp":"192.168.xx.xx"
    			}
    		]
    	}
    }
    ```


## Error codes {#section_sxh_nxb_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|This operation is forbidden because one or more DNAT entries in the DNAT table are in the Pending or Modifying state.|
|404|InvalidForwardTableId.NotFound|Specified forwardTableId does not exist|The specified DNAT table does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

