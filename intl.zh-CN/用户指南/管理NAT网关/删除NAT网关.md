# 删除NAT网关 {#task_491107 .task}

您可以删除按量付费类型的NAT网关，包年包月类型的NAT网关不支持删除操作。

删除NAT网关前，请确保满足以下条件。

-   NAT网关没有绑定EIP，如有绑定请解绑。详细信息，请参见[解绑EIP](intl.zh-CN/用户指南/管理EIP/解绑EIP.md#)。
-   DNAT列表中没有DNAT条目，如有请删除。详细信息，请参见[删除DNAT条目](intl.zh-CN/用户指南/管理DNAT表/删除DNAT条目.md#)。
-   SNAT列表中没有SNAT条目，如有请删除。详细信息，请参见[删除SNAT条目](intl.zh-CN/用户指南/管理SNAT表/删除SNAT条目.md#)。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  在NAT网关页面，找到目标NAT网关，单击**操作**列下的**更多操作** \> **删除**。
5.  在弹出的对话框中，单击**确定**。 

    **说明：** 您也可以在弹出的对话框中选择**强制删除**，在删除NAT网关后自动删除NAT网关中的DNAT、SNAT条目，并解绑EIP。


**相关文档**  


[DeleteNatGateway](../../../../../intl.zh-CN/API参考/NAT网关/DeleteNatGateway.md#)

