# CreateForwardEntry {#reference_i4w_xmt_ndb5 .reference}

Adds a DNAT entry to a DNAT table.

Each DNAT entry consists of five parts: ExternalIp, ExternalPort, Protocol, InternalIp, InternalPort. After a DNAT entry is added, the NAT gateway forwards the data of the specified protocol received by \[ExternalIp:ExternalPort\] to \[InternalIp:InternalPort\], and returns a response.

Note the following before you call this action:

-   Each combination of ExternalIp, ExternalPort, and Protocol of all DNAT entries must be unique \(that is, a message cannot be forwarded to multiple targets\).

-   Each combination of Protocol, InternalIp, and InternalPort of all DNAT entries must be unique.

-   If any DNAT entry in the DNAT table is in the Pending or Modifying state, a new DNAT entry cannot be added.

-   ExternalIp must meet the following requirements:
    -   A public IP address cannot be used in both SNAT and DNAT entries at the same time.
-   InternalIp must meet the following requirements:
    -   The InternalIp must belong to the CIDR block of the VPC to which the NAT Gateway belongs.
    -   The DNAT entry takes effect only when the InternalIP is used by an ECS instance that is not associated with an EIP. If the InternalIP is used by non-ECS resources such as HaVip, SLB, or RDS, the DNAT entry does not take effect and the Internet traffic cannot be forwarded to the IP address.
    -   A public IP address cannot be used in both SNAT and DNAT entries at the same time.
-   A maximum of 100 DNAT entries can be added to a DNAT table.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|CreateForwardEntry| The name of this action. Value:

 CreateForwardEntry

 |
|ExternalIp|String|Yes|116.xx.xx.28| The public IP address.

 |
|ExternalPort|String|Yes|8080|The public port number. Value range: 1 to 65535.|
|ForwardTableId|String|Yes|ftb-bp1mbjubq34hlcqpa5u3a| The ID of the DNAT table.

 |
|InternalIp|String|Yes|192.168.xx.xx| The target private IP address.

 |
|InternalPort|String|Yes|80|The target private port number. Valid value: 1 to 65535.|
|IpProtocol|String|Yes|TCP| The protocol type. Valid values:

-   TCP: forward TCP packets.

-   UDP: forward UDP packets.

-   Any: forward all packets.


 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|ForwardEntryName|String|No|ForwardEntry-1| The name of the DNAT entry to be created. The name must be 2 to 128 characters in length and start with a Chinese character or a letter. The name cannot start with`http://` or `https://`.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|ForwardEntryId|String|fwd-119smw5tkxxxxxxxx|The ID of the DNAT entry.|
|RequestId|String|A4AEE536-A97A-40EB-9EBE-53A6948A6928|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#codeblock_urx_4ad_c4n}

https://vpc.aliyuncs.com/?Action=CreateForwardEntry
&ExternalIp=116.xx.xx.28
&ExternalPort=8080
&ForwardTableId=ftb-bp1mbjubq34hlxxxxxxxx
&InternalIp=192.168.xx.xx
&InternalPort=80
&IpProtocol=TCP
&RegionId=cn-hangzhou
&<CommonParameters>

```

 **Response example** 

-   XML format

    ``` {#codeblock_6bd_wnc_dve}
    <CreateForwardEntryResponse>
      <ForwardEntryId>fwd-119smw5tkxxxxxxxx</ForwardEntryId>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
    </CreateForwardEntryResponse>
    
    ```

-   JSON format

    ``` {#codeblock_orq_ht4_jp3}
    {
    	"ForwardEntryId":"fwd-119smw5tkxxxxxxxx",
    	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
    }
    ```


## Error codes {#section_pmc_l1b_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|400|InvalidExternalIp.Malformed|The specified ExternalIp is not a valid IP address.|The specified ExternalIp is invalid.|
|400|InvalidInternalIp.Malformed|The specified InternalIp is not a valid IP address.|The specified InternalIp is invalid.|
|400|InvalidExternalPort.Malformed|The specified ExternalPort is not a valid port.|The specified ExternalPort is invalid.|
|400|InvalidInternalPort.Malformed|The specified InternalPort is not a valid port.|The specified InternalPort is invalid.|
|400|Forbidden.DestnationIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|The specified InternalIp is not in the CIDR block of the VPC.|
|400|InvalidProtocal.ValueNotSupported|The specified IpProtocol does not support.|The specified protocol type is not supported.|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|You cannot perform this operation because one or more DNAT entries are in the Pending or Modifying status.|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|The specified DNAT table does not exist.|
|404|InvalidExternalIp.NotFound|Specified External Ip address does not found on the VRouter|The specified ExternalIP does not exist.|
|400|Forbidden.ExternalIp.UsedInSnatTable|The specified ExternalIp is already used in SnatTable|The specified ExternalIp is being used by an SNAT rule. Select a different IP address or delete the SNAT rule that uses this IP address.|
|400|Forbindden|The specified Instance already bind eip|An EIP is already attached to this ECS instance. Detach the EIP from the ECS instance first and then add the forwarding rule.|
|400|Forbidden.InternalIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|The specified InternalIP is not in the CIDR block of the VPC.|
|400|Invalid.natgwNotExist|The specified natgateway not exist.|The specified NAT Gateway does not exist.|
|400|InvalidIp.NotInNatgw|The specified Ip not belong to natgateway.|The specified IP address does not belong to the NAT Gateway.|
|400|MissingParameter|Missing mandatory parameter|The required parameters are missing.|
|500|InternalError|The request processing has failed due to some unknown error.|The request cannot be processed due to unknown errors.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The specified name is invalid. Enter a valid name and try again.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc).

