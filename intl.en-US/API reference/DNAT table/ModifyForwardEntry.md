# ModifyForwardEntry {#reference_i4w_xmt_ndb4 .reference}

Modifies a DNAT entry.

**Note:** You cannot modify a DNAT entry if the DNAT entry is in the Pending or Modifying state.

## Debug {#section_ejr_hzb_wgb .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifyForwardEntry| The name of this action. Value: 

 ModifyForwardEntry

 |
|ForwardEntryId|String|Yes|fwd-8vbn3bc8roygjp0gy3xk7|  The ID of the DNAT entry.

 |
|ForwardTableId|String|Yes|ftb-8vbx8xu2lqj9qb334h0ow| The ID of the DNAT table.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|ExternalIp|String|No|116.62.222.28| The public IP address.

 |
|ExternalPort|String|No|80|The public port. Value range: 1 to 65535.|
|InternalIp|String|No|10.34.56.78|The target private IP address.|
|InternalPort|String|No|80|The target private port. Value range: 1 to 65535.|
|IpProtocol|String|No|TCP| The protocol type. Valid values:

-   TCP: forward TCP packets.

-   UDP: forward UDP packets.

-   Any: forward all packets.


 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|24CC85DC-7700-4F09-9624-99E988C7DD03|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=ModifyForwardEntry
&ForwardEntryId=fwd-8vbn3bc8roygjp0gy3xk7
&ForwardTableId=ftb-8vbx8xu2lqj9qb334h0ow
&RegionId= cn-hangzhou
&<CommonParameters>

```

**Response example**

-   XML format

    ```
    <ModifyForwardEntryResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
    </ModifyForwardEntryResponse>
    
    ```

-   JSON format

    ```
    {
    	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
    }
    ```


## Error codes {#section_hrn_41c_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|400|InvalidExternalIp.Malformed|The specified ExternalIp is not a valid IP address.|The specified public IP address is invalid.|
|400|InvalidInternalIp.Malformed|The specified InternalIp is not a valid IP address.|The specified InternalIp is invalid.|
|400|InvalidExternalPort.Malformed|The specified ExternalPort is not a valid port.|The public port is invalid.|
|400|InvalidInternalPort.Malformed|The specified InternalPort is not a valid port.|The private port is invalid.|
|400|Forbidden.DestnationIpOutOfVpcCIDR|The specified Destination Ip is Out of VPC CIDR.|The specified InternalIp is not in the CIDR block of the VPC.|
|400|InvalidProtocal.ValueNotSupported|The specified IpProtocol does not support.|The specified protocol type is not supported.|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|You cannot perform this operation because one or more DNAT entries in the DNAT table are in the Pending or Modifying state.|
|400|QuotaExceeded|Forward entry quota exceeded in this route table.|The quota for custom route entries in the route table has been reached. To increase the quota, open a ticket.|
|404|InvalidForwardEntryId.NotFound|Specified forward entry ID does not exist|The specified DNAT entry does not exist.|
|404|InvalidExternalIp.NotFound|Specified External Ip address does not found on the VRouter|The specified ExternalIp does not exist.|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|The specified DNAT table does not exist.|
|400|Forbidden.ExternalIp.UsedInSnatTable|The specified ExternalIp is already used in SnatTable|This specified ExternalIp is being used by an SNAT rule. Select a different IP address or delete the SNAT rule that uses this IP address.|
|400|Forbidden.Already.Bounded|The specified instance already bounded|The specified instance is already attached.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

