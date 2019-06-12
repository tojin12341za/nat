# 创建SNAT IP地址池 {#concept_264331 .concept}

您可以在创建SNAT条目时，将多个EIP加入到一个SNAT地址池。VPC ECS可以随机通过SNAT地址池中的公网IP访问互联网。

## 前提条件 {#section_au7_r96_xlc .section}

-   您已经创建了专有网络和交换机。详细信息，请参见[创建专有网络和交换机](../../../../../intl.zh-CN/用户指南/专有网络和子网/管理专有网络.md#section_ufw_rhv_rdb)。
-   您已经申请了待加入到SNAT地址池的EIP。详细信息，请参见[申请EIP](../../../../../intl.zh-CN/用户指南/申请EIP/申请新EIP.md#)。

## 背景信息 {#section_doq_73k_duj .section}

NAT网关是一款企业级的VPC公网网关，提供SNAT功能，为VPC内无公网IP的ECS实例提供访问互联网的代理服务。您在使用NAT网关控制台创建SNAT条目时，默认只为指定的交换机配置1个公网IP地址。当ECS实例负载激增时，单个公网IP无法支撑巨大的访问量。

您可以通过CreateSnatEntry接口创建SNAT条目，将多个EIP加入到一个地址池。当VPC ECS主动发起对外的访问连接时，VPC ECS会随机通过SNAT地址池中的公网IP地址访问互联网。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156032486347136_zh-CN.png)

## 步骤一 创建NAT网关 {#section_kaj_h2e_nto .section}

完成以下操作，创建NAT网关：

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  单击**创建NAT网关**。
4.  根据以下信息，配置NAT网关并完成支付。

    |配置|说明|
    |:-|:-|
    |**地域**|选择需要配置NAT网关的VPC所在的地域。|
    |**VPC ID**| 选择需要配置NAT网关的VPC。创建NAT网关后，将不能修改VPC。

 若在VPC列表中，找不到目标VPC，可从以下方面进行排查：

     -   查看该VPC是否已经配置NAT网关。一个VPC只能配置一个NAT网关。

    -   查看该VPC中是否存在目标网段为0.0.0.0/0的自定义路由。若存在，需要删除该路由条目。

 |
    |**规格**| 选择NAT网关的规格。NAT网关的规格会影响SNAT功能的最大连接数和每秒新建连接数，但不会影响数据吞吐量。

 **说明：** NAT网关的规格对DNAT功能的连接数和吞吐量没有限制。详细说明，请参见[NAT网关规格](../intl.zh-CN/用户指南/NAT网关规格.md#)。

 |
    |**计费周期**|选择NAT网关的计费周期。|


## 步骤二 绑定EIP {#section_7mo_onm_20l .section}

完成以下操作，将EIP绑定到NAT网关：

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  找到目标NAT网关实例，然后单击**更多操作** \> **绑定弹性公网IP**。
5.  在弹出的对话框，完成以下操作：
    1.  **公网IP地址**：选择一个弹性公网IP作为NAT网关的公网IP。

         

    2.  **交换机（可选）**：系统会自动添加SNAT规则，使已选交换机下的云产品可以通过EIP访问公网。
6.  重复以上步骤绑定更多EIP。

## 步骤三 加入共享带宽 {#section_nes_2cn_dhg .section}

完成以下操作，加入共享带宽：

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**弹性公网IP**。
3.  选择EIP的地域。
4.  在弹性公网IP页面，找到目标EIP，单击**操作**列下的**更多操作** \> **加入共享带宽**。
5.  选择要加入的共享带宽，然后单击**确定**。

## 步骤四 创建SNAT条目 {#section_b2u_tma_3wd .section}

完成以下操作，创建SNAT条目，将多个EIP加入到一个SNAT地址池。

1.  登录[阿里云OpenAPI Explorer](https://api.aliyun.com)。
2.  在左侧导航栏中，单击**专有网络**。
3.  在搜索框中搜索**CreateSnatEntry**，然后单击**CreateSnatEntry**。
4.  根据以下信息，配置CreateSnatEntry参数，然后单击**发起调用**。

    -   **RegionId**：NAT网关所在的地域ID。
    -   **SnatTableId**：SNAT表ID。
    -   **SnatIp**：添加到SNAT地址池中的公网IP地址，多个IP之间用逗号（,）隔开。
    -   **SourceVSwitchId**（可选）：需要公网访问的交换机的ID。
    -   **SourceCIDR**（可选）：指定的交换机的网段。
    -   **SnatEntryName**（可选）：SNAT条目的名称。
    详细信息，请参见[CreateSnatEntry](../../../../../intl.zh-CN/API参考/NAT网关/CreateSnatEntry.md#)。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156032486347549_zh-CN.png)


如果您已经创建了SNAT条目，您可以通过ModifySnatEntry接口修改指定的SNAT条目。ModifySnatEntry接口参数如下：

-   **RegionId**：NAT网关所在的地域ID。
-   **SnatTableId**：SNAT表ID。
-   **SnatEntryId**：SNAT条目ID。
-   **SnatIp**：添加到SNAT地址池中的公网IP地址，多个IP之间用逗号（,）隔开。
-   **SnatEntryName**：SNAT条目的名称。

详细信息，请参见[ModifySnatEntry](../../../../../intl.zh-CN/API参考/NAT网关/ModifySnatEntry.md#)。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156032486347556_zh-CN.png)

## 步骤五 测试访问 {#section_xes_80x_bgv .section}

分别登录两台设置了SNAT规则的交换机下的ECS实例，查看出网的源IP地址。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156032486347157_zh-CN.png)

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/217943/156032486447158_zh-CN.png)

