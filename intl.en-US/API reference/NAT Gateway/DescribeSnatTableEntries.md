# DescribeSnatTableEntries {#reference_amt_w2p_rdb .reference}

Queries one or more SNAT entries in a SNAT table.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeSnatTableEntries| The name of this action. Value: 

 Describeforwardtableentries

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|SnatTableId|String|Yes|stb-8vbczigrhop8x5u3twlhd| The ID of the SNAT table.

 |
|PageNumber|Integer|No|1| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|10| The number of rows per page. Maximum value: 50. Default value: 10.

 |
|SnatEntryId|String|No|snat-8vbae8uqh7rjpk7d2kuwt| The ID of the SNAT entry.

 |

## Response parameters {#section_hlq_4gp_rdb .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|SnatTableEntries|N/A|N/A| A list of SNAT entries.

 |
|└SnatEntryId|String|snat-kmd6nv8fy| The ID of the SNAT entry.

 |
|└SnatIp|String|116.62.222.28| The public IP address in the SNAT entry.

 |
|└SnatTableId|String|stb-gz3r3odaw| The ID of the SNAT table to which the SNAT entry belongs.

 |
|└SourceCIDR|String|116.62.222.28/33| The source CIDR block of the SNAT entry.

 |
|└SourceVSwitchId|String|vsw-3xbxxxxx| The ID of the VSwitch that accesses the Internet through the SNAT function.

 |
|└Status|String|Pending| The status of the SNAT entry.

 |
|TotalCount|Integer|1| The number of queried entries.

 |
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|5| The number of entries per page.

 |
|RequestId|String|6D7E89B1-1C5B-412B-8585-4908E222EED5| The ID of the request.

 |

## Examples {#section_dg4_y5r_rdb .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeSnatTableEntries
&RegionId=cn-hangzhou
&SnatTableId=stb-8vbczigrhop8x5u3twlhd
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <DescribeSnatTableEntriesResponse>
      <PageNumber>1</PageNumber>
      <PageSize>10</PageSize>
      <RequestId>6D7E89B1-1C5B-412B-8585-4908E222EED5</RequestId>
      <SnatTableEntries>
        <SnatTableEntry>
          <SnatEntryId>snat-kmd6nv8fy</SnatEntryId>
          <SnatIp>139.xxx.xx.40</SnatIp>
          <SnatTableId>stb-gz3r3odaw</SnatTableId>
          <SourceCIDR>192.168.1.0/24</SourceCIDR>
          <SourceVSwitchId>vsw-yrv0xxxxx</SourceVSwitchId>
          <Status>Available</Status>
        </SnatTableEntry>
        <SnatTableEntry>
          <SnatEntryId>snat-bs5bezbme</SnatEntryId>
          <SnatIp>139.xxx.xx.40</SnatIp>
          <SnatTableId>stb-gz3r3odaw</SnatTableId>
          <SourceCIDR>192.168.3.0/24</SourceCIDR>
          <SourceVSwitchId>vsw-3xbxxxxx</SourceVSwitchId>
          <Status>Available</Status>
        </SnatTableEntry>
      </SnatTableEntries>
    </DescribeSnatTableEntriesResponse>
    
    ```

-   JSON format

    ```
    {
    	"SnatTableEntries":{
    		"SnatTableEntry":[
    			{
    				"Status":"Available",
    				"SourceCIDR":"192.168.1.0/24",
    				"SnatTableId":"stb-gz3r3odaw",
    				"SnatIp":"139.xxx.xx.40",
    				"SnatEntryId":"snat-kmd6nv8fy",
    				"SourceVSwitchId":"vsw-yrv0xxxxx"
    			},
    			{
    				"Status":"Available",
    				"SourceCIDR":"192.168.3.0/24",
    				"SnatTableId":"stb-gz3r3odaw",
    				"SnatIp":"139.xxx.xx.40",
    				"SnatEntryId":"snat-bs5bezbme",
    				"SourceVSwitchId":"vsw-3xbxxxxx"
    			}
    		]
    	},
    	"PageNumber":1,
    	"PageSize":10,
    	"RequestId":"6D7E89B1-1C5B-412B-8585-4908E222EED5"
    }
    ```


## Error codes {#section_h22_5nc_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The specified SNAT table does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

