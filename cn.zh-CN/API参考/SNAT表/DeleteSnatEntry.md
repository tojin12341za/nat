# DeleteSnatEntry {#doc_api_Vpc_DeleteSnatEntry .reference}

调用DeleteSnatEntry接口删除指定的SNAT条目。

**说明：** 当SNAT表中有SNAT条目的状态为**Pending**或**Modifying**时，无法删除SNAT条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteSnatEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteSnatEntry|要执行的操作。

 取值：**DeleteSnatEntry**。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|SnatEntryId|String|是|snat-bp1vcgcf8tm0plqcgfl04|SNAT条目ID。

 |
|SnatTableId|String|是|stb-bp190wu8io1vgev80kec7|SNAT表ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|47B80B6A-759A-479C-A565-76D04BDA29F3|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteSnatEntry
&RegionId=cn-hangzhou
&SnatEntryId=snat-bp1vcgcf8tm0plqcgfl04
&SnatTableId=stb-bp190wu8io1vgev80kec7
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteSnatEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteSnatEntryResponse>
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
|400|IncorretSnatEntryStatus|Some Snat entry status blocked this operation..|无法执行该操作。SNAT表中有SNAT条目的状态处于Pending或Modifying状态。|
|404|InvalidSnatEntryId.NotFound|Specified Snat entry ID does not exist|指定的 SNAT 条目不存在，请您检查填写的 SNAT 条目是否正确。|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|指定的 SNAT 表不存在，请您检查输入参数是否正确。|
|404|InvalidSnatEntryId.NotFound|Specified SNAT entry does not exist.|指定的 SNAT 条目不存在，请您检查填写的 SNAT 条目是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

