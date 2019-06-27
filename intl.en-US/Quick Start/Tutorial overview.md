# Tutorial overview {#concept_anp_q5y_ydb .concept}

This tutorial provides a step-by-step guide on how to configure SNAT and DNAT so that ECS instances in a VPC can communicate with the Internet through NAT Gateway.

## Prerequisites {#section_096_mcx_zp0 .section}

Before you begin, make sure that the following conditions are met:

-   A VPC and a VSwitch are created. For more information, see [Create a VPC and a VSwitch](../../../../reseller.en-US/User Guide/VPC and subnets/Manage a VPC.md#section_ufw_rhv_rdb).
-   An ECS instance of the VPC network is created. For more information, see [Create an instance by using the wizard](../../../../reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).

## Procedure {#section_fo9_u4q_8nb .section}

An ECS instance without any public IP address is used in this example. The configuration flow chart is as follows:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13986/156160117948598_en-US.png)

1.  Create a NAT Gateway

    NAT Gateway is an enterprise-class VPC Internet gateway that provides NAT proxy services. You must create a NAT Gateway before configuring SNAT and DNAT entries.

    For more information, see [Create a NAT Gateway](reseller.en-US/Quick Start/Create a NAT Gateway.md#).

2.  Associate an EIP with a NAT Gateway

    A NAT Gateway can work normally only after it is associated with a public IP address. After you create a NAT Gateway, you can associate an Elastic IP Address \(EIP\) with the NAT Gateway.

    For more information, see [Associate an EIP](reseller.en-US/Quick Start/Associate an EIP.md#).

3.  Create a DNAT entry

    NAT Gateway supports DNAT, which maps a public IP address to an ECS instance so that the ECS instance can provide Internet services. DNAT supports both port mapping and IP mapping.

    For more information, see [Create a DNAT entry](reseller.en-US/Quick Start/Create a DNAT entry.md#).

4.  Create an SNAT entry

    NAT Gateway supports SNAT, which allows ECS instances without a public IP address in a VPC to access the Internet.

    For more information, see [Create an SNAT entry](reseller.en-US/Quick Start/Create an SNAT entry.md#).


