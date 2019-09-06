# Terms {#concept_tms_kly_ydb .concept}

This topic describes basic concepts of NAT Gateway.

|Term|Description|
|:---|:----------|
|NAT Gateway|NAT Gateway is an enterprise-class public network gateway that provides Internet proxy services \(SNAT and DNAT\) with up to 10 Gbps forwarding capability. It also features high availability in a region and disaster recovery across zones.|
|DNAT table|A DNAT table is a configuration table used for configuring DNAT. You can map a public IP address in a NAT bandwidth package to an ECS instance. DNAT supports IP mapping and port mapping.|
|SNAT table|An SNAT table is a configuration table used for configuring SNAT entries. You can configure SNAT entries for a VSwitch or for an ECS instance. -   Configure SNAT entries for a VSwitch: All ECS instances in the VSwitch use the specified public IP address to access the Internet.
-   Configure SNAT entries for an ECS instance: The ECS instance uses the specified public IP address to access the Internet.

 |
|EIP|Elastic IP Address \(EIP\) is a public IP address resource that can be independently purchased and owned. You can associate an EIP with an ECS instance of the VPC network, a private SLB instance of the VPC network, an ENI of the VPC network, and a NAT Gateway, or a HAVIP.|

