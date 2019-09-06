# DescribeForwardTableEntries {#doc_api_Vpc_DescribeForwardTableEntries .reference}

调用DescribeForwardTableEntries接口查询已创建的DNAT条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeForwardTableEntries&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeForwardTableEntries|要执行的操作。

 取值： **DescribeForwardTableEntries**。

 |
|ForwardTableId|String|是|ftb-bp1mbjubq34hlcqpa5u3a|DNAT列表的ID。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ExternalIp|String|否|116.xx.xx.28|公网IP地址。

 |
|ExternalPort|String|否|8080|公网端口。取值范围：1-65535。

 |
|ForwardEntryId|String|否|fwd-8vbn3bc8roygjp0gy3xk7|系统分配的DNAT条目ID。

 |
|ForwardEntryName|String|否|ForwardEntry-1|DNAT规则的名称。长度为2-128个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|InternalIp|String|否|192.168.xx.xx|目标私网IP。

 |
|InternalPort|String|否|80|目标私网端口。取值范围：1-65535。

 |
|IpProtocol|String|否|TCP|协议类型。取值：

 -   TCP：转发TCP协议的报文。
-   UDP：转发UDP协议的报文。
-   Any：转发所有协议的报文。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ForwardTableEntries| | |DNAT列表的详细信息。

 |
|ExternalIp|String|139.xxx.xx.79|公网IP地址。

 |
|ExternalPort|String|80|公网端口。

 |
|ForwardEntryId|String|fwd-119smw5tk|DNAT条目的ID。

 |
|ForwardEntryName|String|ForwardEntry-1|DNAT规则的名称。

 |
|ForwardTableId|String|ftb-11tc6xgmv|DNAT条目所属DNAT表的ID。

 |
|InternalIp|String|192.168.1.1|私网IP地址。

 |
|InternalPort|String|any|目标私网端口。取值：1-65535。

 |
|IpProtocol|String|tcp|协议类型。

 |
|Status|String|Available|DNAT条目的状态

 |
|TotalCount|Integer|5|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|A6C4A8B1-7561-4509-949C-20DEB40D71E6|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeForwardTableEntries
&ForwardTableId=ftb-bp1mbjubq34hlcqpa5u3a
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
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

`JSON` 格式

``` {#json_return_success_demo}
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

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|无法执行该操作。DNAT表中有DNAT条目的状态处于Pending或Modifying状态。|
|404|InvalidForwardTableId.NotFound|Specified forwardTableId does not exist|指定的 DNAT 表不存在，请您检查输入参数是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

