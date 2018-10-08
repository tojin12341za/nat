# What is NAT Gateway {#concept_wpm_kfy_ydb .concept}

NAT Gateway is an enterprise-class Internet gateway that provides NAT proxy services \(SNAT and DNAT\), with the forwarding capacity of up to 10 Gbps, and the capability of cross-zone disaster recovery. The position of NAT Gateway in the VPC network topology is as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13979/15389613624440_en-US.png)

As an Internet gateway, NAT Gateway needs to be configured with a public IP to function normally. After creating a NAT gateway, you can bind an EIP to it.

**Note:**  If your account has a NAT bandwidth package before January 26, 2018, you still need to use the bandwidth package to provide public IPs. Open a ticket if you want to bind EIP to the NAT gateway.

