# 创建SNAT IP地址池 {#concept_264331 .concept}

您可以在创建SNAT条目时，将多个EIP加入到一个SNAT地址池。VPC ECS实例可以随机通过SNAT地址池中的EIP访问互联网。

## 前提条件 {#section_au7_r96_xlc .section}

-   您已经创建了专有网络和交换机。详细信息，请参见[创建专有网络和交换机](../../../../intl.zh-CN/专有网络和交换机/管理专有网络/创建专有网络.md#section_ufw_rhv_rdb)。
-   您已经申请了待加入到SNAT地址池的EIP。详细信息，请参见[申请EIP](../../../../intl.zh-CN/用户指南/申请EIP/申请新EIP.md#)。

## 背景信息 {#section_doq_73k_duj .section}

NAT网关是一款企业级的VPC公网网关，提供SNAT功能，为VPC内无公网IP的ECS实例提供访问互联网的代理服务。如果您在创建SNAT条目时，只为指定的交换机或ECS实例配置1个EIP。当ECS实例负载激增时，1个EIP无法支撑巨大的访问量。

您可以选择添加多个EIP到一个SNAT地址池中，当VPC ECS实例主动发起对外的访问连接时，VPC ECS实例会随机通过SNAT地址池中的EIP访问互联网。

![SNAT IP地址池](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156802295147136_zh-CN.png)

## 步骤一 创建NAT网关 {#section_kaj_h2e_nto .section}

完成以下操作，创建NAT网关。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  在NAT网关页面，单击**创建NAT网关**。
4.  在购买页面，根据以下信息，配置NAT网关并完成支付。
    -   **地域**：选择需要创建NAT网关的VPC所在的地域。
    -   **VPC ID**：选择需要创建NAT网关的VPC。创建NAT网关后，不能修改VPC。

        **说明：** 若在VPC列表中，找不到目标VPC，请从以下方面进行排查：

        -   查看该VPC是否已经配置NAT网关。一个VPC只能配置一个NAT网关。
        -   查看该VPC中是否存在目标网段为0.0.0.0/0的自定义路由。若存在，需要删除该路由条目。
    -   **规格**：选择NAT网关的规格。NAT网关的规格会影响SNAT功能的最大连接数和每秒新建连接数，但不会影响数据吞吐量。

        **说明：** NAT网关的规格对DNAT功能的连接数和吞吐量没有限制。详细信息，请参见[NAT网关规格](../../../../intl.zh-CN/用户指南/NAT网关规格.md#)。

    -   **计费周期**：选择NAT网关的计费周期。

## 步骤二 将EIP绑定到NAT网关 {#section_7mo_onm_20l .section}

完成以下操作，将EIP绑定到NAT网关。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  找到目标NAT网关实例，单击**操作**列下的**更多操作** \> **绑定弹性公网IP**。
5.  在绑定弹性公网IP页面，完成以下操作，然后单击**确定**。

    -   **从已有EIP列表选取**：您可以从已有EIP列表选择EIP并绑定NAT网关。
    -   **新购EIP并绑定NAT网关**：系统为您创建1个按使用流量计费的按量付费EIP，并绑定到NAT网关。
    **说明：** 一个NAT网关最多可绑定20个EIP（最多可绑定10个按流量计费的EIP，每个按流量计费的EIP的最大峰值不能超过200Mbps），您可以提交工单申请更多配额。

6.  重复以上步骤绑定更多EIP。

## 步骤三 将EIP加入共享带宽 {#section_nes_2cn_dhg .section}

完成以下操作，将EIP加入共享带宽。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**弹性公网IP**。
3.  选择EIP的地域。
4.  在弹性公网IP页面，找到目标EIP，单击**操作**列下的**更多操作** \> **加入共享带宽**。
5.  选择要加入的共享带宽，然后单击**确定**。

## 步骤四 创建SNAT条目 {#section_8i2_1th_793 .section}

完成以下操作，创建SNAT条目，将多个EIP加入到一个SNAT地址池。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  在NAT网关页面，找到目标NAT网关实例，单击**操作**列下的**设置SNAT**。
5.  在SNAT表页面，单击**创建SNAT条目**。
6.  在创建SNAT条目页面，根据以下信息配置SNAT条目，然后单击**确定**。

    以**交换机**为粒度：

    -   **交换机**：选择VPC中的交换机。该交换机下所有ECS实例都将通过SNAT功能进行公网访问。
    -   **交换机网段**：显示该交换机的网段。
    -   **公网IP地址**：选择用来提供互联网访问的公网IP。支持选择多个公网IP，多个公网IP构建SNAT IP地址池。
    -   **条目名称**：输入SNAT条目的名称。
    以**ECS**为粒度：

    -   **可用ECS列表**：选择VPC中的ECS实例。
    -   **ECS网段**：显示该ECS实例的网段。
    -   **公网IP地址**：选择用来提供互联网访问的公网IP。支持选择多个公网IP，多个公网IP构建SNAT IP地址池。
    -   **条目名称**：输入SNAT条目的名称。

## 步骤五 测试访问 {#section_xes_80x_bgv .section}

分别登录两台设置了SNAT规则的ECS实例，查看出网的源IP地址。

![ECS1查看出网的源IP地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156802295147157_zh-CN.png)

![ECS2查看出网的源IP地址](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156802295147158_zh-CN.png)

