# 为绑定了EIP的ECS实例统一公网出口IP {#concept_711105 .concept}

VPC内的ECS实例通过公网IP访问互联网，统一ECS实例的公网出口IP，有利于您更高效的管理互联网业务。本文为您介绍如何为绑定了EIP的ECS实例统一公网出口IP。

## 背景信息 {#section_5fr_xw0_tg7 .section}

NAT网关提供SNAT功能，为VPC内无公网IP的ECS实例提供访问互联网的代理服务。如果VPC内某些ECS实例绑定了EIP，这些ECS实例会优先通过绑定的EIP访问互联网，而VPC内的其他ECS实例通过NAT网关的SNAT功能代理访问互联网，造成VPC内ECS实例的公网出口IP不一致，不利于统一管理业务。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570281/156091252249564_zh-CN.png)

您可以通过为ECS实例绑定弹性网卡来解决ECS实例公网出口IP不统一的问题。

如下图，您可以为ECS实例单独分配一块弹性网卡，并将EIP绑定到弹性网卡，以实现互联网通过弹性网卡主动访问ECS实例，ECS实例优先通过NAT网关访问互联网。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156091252249551_zh-CN.png)

## 前提条件 {#section_h16_yrt_s8s .section}

-   您已经创建了专有网络和交换机。详细信息，请参见[创建专有网络和交换机](../../cn.zh-CN/用户指南/专有网络和子网/管理专有网络.md#section_ufw_rhv_rdb)。
-   您已经创建了NAT网关并在NAT网关中创建了SNTA条目。详细信息，请参见[创建NAT网关](../cn.zh-CN/用户指南/管理NAT网关实例.md#)和[创建SNAT条目](../cn.zh-CN/.md#)。
-   您已经创建了ECS实例，且您的ECS实例绑定了EIP。详细信息，请参见[使用向导创建实例](../../cn.zh-CN/实例/创建实例/使用向导创建实例.md#)和[绑定ECS实例](../../cn.zh-CN/用户指南/绑定云资源/绑定ECS实例.md#)。

## 步骤一 创建弹性网卡 {#section_o0f_8z1_yy6 .section}

完成以下操作，为ECS实例创建弹性网卡。

1.  登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏，单击**网络与安全** \> **弹性网卡**。
3.  选择弹性网卡的地域。

    **说明：** 弹性网卡的地域必须与ECS实例的地域相同。

4.  在网卡列表页面，单击**创建弹性网卡**。
5.  在创建弹性网卡页面，根据以下信息配置弹性网卡，然后单击**确定**。
    -   **网卡名称**：输入弹性网卡的名称。
    -   **专有网络**：选择ECS实例所在的专有网络。
    -   **交换机**：选择ECS实例所在可用区的交换机。
    -   **主私网IP**（可选）：输入弹性网卡的主私网IPv4地址。此IPv4地址必须属于交换机的CIDR网段中的空闲地址。如果您没有指定，创建弹性网卡时将自动为您分配一个空闲的私网IPv4地址。
    -   **安全组**：选择当前专有网络的一个安全组。
    -   **描述**（可选）：输入对弹性网卡的描述。

## 步骤二 绑定弹性网卡 {#section_wim_o2h_o37 .section}

完成以下操作，为ECS实例绑定弹性网卡。

1.  登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏中，选择**网络与安全** \> **弹性网卡**。
3.  选择弹性网卡的地域。
4.  在网卡列表页面，找到目标弹性网卡，单击**操作**列下的**绑定实例**。
5.  在弹出的对话框中，选择要绑定的ECS实例，然后单击**确定**。

## 步骤三 解除EIP与ECS实例的绑定 {#section_4xl_wtb_54i .section}

完成以下操作，解除EIP与ECS实例的绑定。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com)
2.  在左侧导航栏，单击**弹性公网IP**。
3.  选择弹性公网IP的地域。
4.  在弹性公网IP页面，找到目标弹性公网IP，单击**操作**列下的**解绑**。
5.  在弹出的对话框中，单击**确定**。

## 步骤四 EIP绑定弹性网卡 {#section_n7o_cgd_03c .section}

完成以下操作，将EIP绑定弹性网卡。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com)
2.  在左侧导航栏，单击**弹性公网IP**。
3.  选择弹性公网IP的地域。
4.  在弹性公网IP页面，找到目标弹性公网IP，单击**操作**列下的**绑定**。
5.  在绑定弹性公网IP页面，根据以下信息绑定EIP至弹性网卡，然后单击**确定**。
    -   **IP地址**：显示弹性公网IP地址。
    -   **实例类型**：选择辅助弹性网卡。
    -   **资源组**（可选）：选择该弹性公网IP所属的资源组。
    -   **绑定模式**（可选）：选择弹性公网IP绑定模式。
    -   **辅助弹性网卡**：选择要绑定的辅助弹性网卡。

## 步骤五 测试网络连通性 {#section_eb3_nk5_90p .section}

完成以下操作，测试互联网是否可以通过绑定弹性网卡的EIP访问ECS实例。本操作以本地Linux设备远程连接Linux实例为例。

**说明：** 远程连接Linux实例，Linux实例的安全组必须放行SSH（22）端口。详细信息，请参见[添加安全组规则](../../cn.zh-CN/安全/安全组/添加安全组规则.md#)。

1.  登录本地Linux设备。
2.  执行`ssh root@公网IP`命令，然后输入Linux实例的登录密码，查看是否可以远程连接到实例。

    若界面上出现`Welcome to Alibaba Cloud Elastic Compute Service !`时，表示您已经成功连接到实例。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156091252349595_zh-CN.png)


完成以下操作，测试ECS实例是否可以通过NAT网关的SNAT功能主动访问互联网。本操作以在linux实例上查看公网出口IP为例。

1.  登录ECS实例。
2.  执行`curl https://myip.ipip.net`查看公网出口IP。

    若公网出口IP与NAT网关SNAT条目中的IP一致，即ECS实例优先通过NAT网关的SNAT功能主动访问互联网。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156091252349596_zh-CN.png)


