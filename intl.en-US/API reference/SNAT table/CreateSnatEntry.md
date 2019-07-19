# CreateSnatEntry {#doc_api_Vpc_CreateSnatEntry .reference}

Adds a SNAT entry to the SNAT table.

Before you call this API action to add an SNAT entry, note the following:

-   The VSwitch specified in the SNAT entry must belong to the same VPC as the NAT Gateway.
-   Each VSwitch and ECS instance can belong to only one SNAT entry.
-   No SNAT entry can be added if any HAVIP instance exists in the VSwitch.
-   The public IP address \(SnatIp\) in the SNAT entry must meet the following conditions:
    -   If you purchased a NAT bandwidth package before January 26, 2018, SnatIp must be a public IP address in the NAT bandwidth package of the NAT Gateway.
    -   If you did not purchase a NAT bandwidth package before January 26, 2018, SnatIp must be an EIP associated with the NAT Gateway.
    -   A public IP address cannot be used by a DNAT entry and an SNAT entry at the same time.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=CreateSnatEntry) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateSnatEntry|The name of this action. Value: **CreateSnatEntry**.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the NAT Gateway belongs.

 To query the region ID, call [DescribeRegions](~~36063~~).

 |
|SnatIp|String|Yes|47.XX.XX.98|The public IP address. Multiple IP addresses are separated by commas.

 |
|SnatTableId|String|Yes|stb-bp190wu8io1vgev\*\*\*\*|The ID of the SNAT table.

 |
|SnatEntryName|String|No|SnatEntry-1|The name of the SNAT entry to be added. The name must be 2 to 128 characters in length and start with a letter or a Chinese character. The name cannot start with `http://` or `https://`.

 |
|SourceCIDR|String|No|10.1.1.0/24|The CIDR block of the VSwitch or ECS instance.

 -   VSwitch granularity: specifies the CIDR block of the VSwitch \(for example, 192.168.1.0/24\). When an ECS instance in the VSwitch initiates an Internet access request, the NAT Gateway provides the SNAT service \(Internet proxy service\) for the ECS instance. If you specify only one public IP address for the **SnatIp** parameter, the ECS instance uses the specified public IP address to access the Internet. However, if you specify multiple public IP addresses for the **SnatIp** parameter, the ECS instance randomly uses one of the specified public IP addresses to access the Internet.****
-   ECS granularity: specifies the IP address of the ECS instance \(for example, 192.168.1.1/32\). When an ECS instance initiates an Internet access request, the NAT Gateway provides the SNAT service \(Internet proxy service\) for the ECS instance. If you specify only one public IP address for the **SnatIp** parameter, the ECS instance uses the specified public IP address to access the Internet. However, if you specify multiple public IP addresses for the **SnatIp** parameter, the ECS instance randomly uses one of the specified public IP addresses to access the Internet.****

 **Note:** This parameter and the **SourceVSwtichId** parameter cannot be used at the same time. If you have specified the **SourceVSwitchId** parameter, you cannot specify the **SourceCIDR** parameter. If you have specified the **SourceCIDR** parameter, you cannot specify the **SourceVSwitchId** parameter.

 |
|SourceVSwitchId|String|No|vsw-bp1nhx2s9ui5o\*\*\*\*|The ID of the VSwitch that requires access to the Internet.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|SnatEntryId|String|snat-kmd6nv8fy\*\*\*\*|The ID of the SNAT entry.

 |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateSnatEntry
&RegionId=cn-hangzhou
&SnatIp=47.XX.XX.98
&SnatTableId=stb-bp190wu8io1vgevx****
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<CreateSnatEntryResponse>
  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
  <SnatEntryId>snat-119smw5tkx****</SnatEntryId>
</CreateSnatEntryResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3",
	"SnatEntryId":"snat-kmd6nv8fyx****"
}
```

## Errors { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The specified SNAT table does not exist.|
|400|Forbidden.SourceVSwitchId.IncludeHaVip|There is some HaVips under specified VSwitch|One or more HAVIPs already exist under the specified VSwitch.|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|The specified SNAT IP address is invalid.|
|400|SNAT\_IP\_POOL\_COUNT\_TOO\_MANY|The Snat pool ip too many.|The quota for IP addresses in the SNAT IP address pool has been reached.|
|400|Forbidden.SnatEntryCountLimited|SNAT entry in the specified SNAT table reaches its limit.|The quota for SNAT entries has been reached.|
|400|NOT\_ALLOW\_USE\_SOURCECIDR|The User not in nat\_scope\_unlimited white list. Cannot use SourceCidr param.|The specified intranet IP address does not belong to the CIDR block of the VPC.|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exist.|The specified VSwitch does not exist.|
|400|INVALID\_PARAMETER|The parameter is invalid.|The parameter is invalid.|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDR is duplicated.|A SNAT rule has already been configured for this VSwitch.|
|404|InvalidSnatIp.NotFound|The specified SnatIp is not found in the NAT Gateway.|The public IP address is not found in the NAT Gateway.|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table.|This public IP address is being used by a DNAT rule. Select a different public IP address or delete the DNAT rule.|
|400|Forbidden|The specified Instance already bind eip|An EIP is already associated with this ECS instance. Disassociate the EIP from the ECS instance and then add the forwarding rule.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The specified name is invalid. Enter a valid name and try again.|

