# What is NAT Gateway? {#concept_wpm_kfy_ydb .concept}

NAT Gateway is an enterprise-class VPC Internet gateway that provides NAT proxy services \(SNAT and DNAT\), up to 10 Gbps forwarding capacity and cross-zone disaster tolerance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13979/15560102934440_en-US.png)

As an Internet gateway, public IP addresses are required to make NAT Gateway fucntion normally. After creating a NAT Gateway, you can bind an Elastic IP Address \(EIP\) to the NAT Gateway.

**Note:** If your account has purchased a NAT bandwidth package before January 26, 2018, you still need to use the bandwidth package to provide public IP addresses. To associate an EIP to the NAT Gateway, open a ticket.

If you want to use the Internet Shared Bandwidth function, you can add EIPs to the existing shared bandwidth in the EIP console or buy a shared bandwidth first and then add the EIPs to it. For more information, see [Add EIPs to Internet Shared Bandwidth](../../../../reseller.en-US/User Guide/Add EIPs to Internet Shared Bandwidth.md#).

