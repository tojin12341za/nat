# What is NAT Gateway {#concept_wpm_kfy_ydb .concept}

NAT Gateway is an enterprise-class VPC Internet gateway that provides NAT proxy services \(SNAT and DNAT\), up to 10 Gbps forwarding capacity and cross-zone disaster tolerance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13979/15616360224440_en-US.png)

As an Internet gateway, public IP addresses are required to make NAT Gateway function normally. After creating a NAT Gateway, you can associate an Elastic IP Address \(EIP\) with the NAT Gateway.

**Note:** If your account purchased a NAT bandwidth package before January 26, 2018, you still need to use the bandwidth package to provide public IP addresses. To associate an EIP with the NAT Gateway, please open a ticket.

If you want to use the Internet Shared Bandwidth function, you can add EIPs to an existing Internet Shared Bandwidth in the EIP console or buy an Internet Shared Bandwidth first and then add the EIPs to it. For more information, see [Add EIPs to an Internet Shared Bandwidth instance](../../../../reseller.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Add EIPs to an Internet Shared Bandwidth instance.md#).

