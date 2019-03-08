# 绑定和解绑EIP {#concept_uy3_f2z_ydb .concept}

创建NAT网关后，您还需要为NAT网关配置公网IP。您可以通过绑定弹性公网IP（EIP）的方式为NAT网关配置公网IP。

**说明：** 

对于2018年1月26日之前账号下存在NAT带宽包的用户，默认无法使用EIP绑定NAT网关的功能。如需使用EIP绑定NAT网关功能，请提交工单。

## 绑定EIP {#section_zx4_l2z_ydb .section}

确保在绑定EIP前，您已经创建NAT网关和EIP。

完成以下操作，将EIP绑定到NAT网关：

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  找到目标NAT网关实例，然后单击**更多操作** \> **绑定弹性公网IP**。
5.  在弹出的对话框，完成以下操作：
    1.  **公网IP地址**：选择一个弹性公网IP作为NAT网关的公网IP。

         

    2.  **交换机（可选）**：系统会自动添加SNAT规则，使已选交换机下的云产品可以通过EIP访问公网。
6.  重复以上步骤绑定更多EIP。

## 解绑EIP {#section_gy4_l2z_ydb .section}

在解绑EIP前，确保该EIP没有被任何SNAT或DNAT条目占用。

完成以下操作，解绑EIP：

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  找到目标NAT网关实例，然后单击**更多操作** \> **解绑弹性公网IP**。
5.  选择要解绑的EIP，然后单击**确定**。

