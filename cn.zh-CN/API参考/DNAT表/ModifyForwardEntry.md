# ModifyForwardEntry {#doc_api_Vpc_ModifyForwardEntry .reference}

调用ModifyForwardEntry接口修改指定的DNAT条目。

**说明：** 当DNAT表中有DNAT条目的状态为**Pending**或**Modifying**时，无法修改DNAT条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyForwardEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyForwardEntry|要执行的操作。

 取值：**ModifyForwardEntry**。

 |
|ForwardEntryId|String|是|fwd-8vbn3bc8roygjp0gy3xk7|DNAT条目的ID。

 |
|ForwardTableId|String|是|ftb-8vbx8xu2lqj9qb334h0ow|DNAT列表的ID。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ExternalIp|String|否|116.62.222.28|公网IP地址。

 |
|ExternalPort|String|否|80|公网端口。取值范围：1-65535。

 |
|InternalIp|String|否|10.34.56.78|目标私网IP。

 |
|InternalPort|String|否|80|目标私网端口。取值范围：1-65535。

 |
|IpProtocol|String|否|TCP|协议类型。取值：

 -   **TCP**：转发TCP协议的报文。
-   **UDP**：转发UDP协议的报文。
-   **Any**：转发所有协议的报文。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|24CC85DC-7700-4F09-9624-99E988C7DD03|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyForwardEntry
&ForwardEntryId=fwd-8vbn3bc8roygjp0gy3xk7
&ForwardTableId=ftb-8vbx8xu2lqj9qb334h0ow
&RegionId= cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyForwardEntryResponse>
	  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifyForwardEntryResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidExternalIp.Malformed|The specified ExternalIp is not a valid IP address.|该公网IP不合法。|
|400|InvalidInternalIp.Malformed|The specified InternalIp is not a valid IP address.|该目标私网IP不合法。|
|400|InvalidExternalPort.Malformed|The specified ExternalPort is not a valid port.|该公网端口不合法。|
|400|InvalidInternalPort.Malformed|The specified InternalPort is not a valid port.|该私网端口不合法。|
|400|Forbidden.DestnationIpOutOfVpcCIDR|The specified Destination Ip is Out of VPC CIDR.|该私网IP不在VPC的网段范围内，请您填写在VPC的网段范围内的私网IP。|
|400|InvalidProtocal.ValueNotSupported|The specified IpProtocol does not support.|该协议类型不支持。|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|无法执行该操作。DNAT表中有DNAT条目的状态处于Pending或Modifying状态。|
|400|QuotaExceeded|Forward entry quota exceeded in this route table.|同一个路由表中自定义路由条目不能超过 48 条，可以提交工单申请调整数量。|
|404|InvalidForwardEntryId.NotFound|Specified forward entry ID does not exist|该DNAT条目不存在。|
|404|InvalidExternalIp.NotFound|Specified External Ip address does not found on the VRouter|该公网IP不存在。|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|指定的 DNAT 表不存在，请您检查输入参数是否正确。|
|400|Forbidden.ExternalIp.UsedInSnatTable|The specified ExternalIp is already used in SnatTable|该公网IP已经被SNAT使用，请更换其他公网IP或将当前公网IP的SNAT规则删除。|
|400|Forbidden.Already.Bounded|The specified instance already bounded|实例已经被绑定，请不要重复绑定。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

