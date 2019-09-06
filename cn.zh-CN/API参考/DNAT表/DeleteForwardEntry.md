# DeleteForwardEntry {#doc_api_Vpc_DeleteForwardEntry .reference}

调用DeleteForwardEntry接口删除指定的DNAT条目。

**说明：** 当DNAT表中有DNAT条目的状态为**Pending**或**Modifying**时，无法删除DNAT条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteForwardEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteForwardEntry|要执行的操作。

 取值： **DeleteForwardEntry**。

 |
|ForwardEntryId|String|是|fwd-8vbn3bc8roygjp0gy3xk7|DNAT条目ID。

 |
|ForwardTableId|String|是|ftb-8vbx8xu2lqj9qb334h0ow|DNAT列表ID。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteForwardEntry
&ForwardEntryId=fwd-8vbn3bc8roygjp0gy3xk7
&ForwardTableId=ftb-8vbx8xu2lqj9qb334h0ow
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteForwardEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteForwardEntryResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|无法执行该操作。DNAT表中有DNAT条目的状态处于Pending或Modifying状态。|
|404|InvalidForwardEntryId.NotFound|Specified forward entry ID does not exist|该DNAT条目不存在。|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|指定的 DNAT 表不存在，请您检查输入参数是否正确。|
|400|IncorretForwardEntryStatus|The Specified forwardEntry is not exist|该DNAT条目不存在。|
|400|MissingParameter|Missing mandatory parameter|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

