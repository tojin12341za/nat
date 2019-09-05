# ModifyNatGatewayAttribute {#doc_api_Vpc_ModifyNatGatewayAttribute .reference}

Modifies the name and description of a NAT Gateway.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=ModifyNatGatewayAttribute&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyNatGatewayAttribute| The name of this action.

 Value: **ModifyNatGatewayAttribute**

 |
|NatGatewayId|String|Yes|ngw-xxoo123| The ID of the NAT Gateway.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the NAT Gateway belongs.

 To query the region ID, call [DescribeRegions](~~36063~~).

 |
|Description|String|No|fortest| Optional. The description of the NAT Gateway. The description must be 2 to 256 characters in length. It must start with a letter. It cannot start with `http://` or `https://`.

 |
|Name|String|No|nat123| Optional. The name of the NAT Gateway. The name must be 2 to 128 characters in length. It must start with a letter. It can contain numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). It cannot start with `http://` or `https://`.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|AB5F62CF-2B60-4458-A756-42C9DFE108D1| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyNatGatewayAttribute
&NatGatewayId=ngw-xxoo123
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<ModifyNatGatewayAttributeResponse>
	  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifyNatGatewayAttributeResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## Errors {#section_zdi_1n6_gce .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The specified NAT Gateway ID does not exist.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The specified name is invalid.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The specified description is invalid.|

