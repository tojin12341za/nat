# Specifications of NAT Gateway {#concept_nlc_s1z_ydb .concept}

NAT Gateway provides small, medium, large, and super large-1 specifications. You can select different specifications for NAT Gateway to adjust the performance metrics \(Max Connections and CPS\). However, data throughput is not affected.

## Specifications {#section_3bi_c0u_eh6 .section}

The following table lists the available specifications of NAT Gateway.

|Specification|Max Connections of SNAT|CPS of SNAT|
|:------------|:----------------------|:----------|
|Small|10,000|1,000|
|Medium|50,000|5,000|
|Large|200,000|10,000|
|Super Large-1|1,000,000|30,000|

## Notes {#section_v3p_w5y_3wz .section}

Note the following when you select a specification:

-   There is no correlation between a specification and the number of IP addresses.
-   CloudMonitor only provides monitoring data on the maximum number of connections. It does not provide monitoring data on CPS.
-   The timeout period of an SNAT connection is 900 seconds.
-   To avoid SNAT connection timeout caused by network congestion and public network jitter, make sure that your service application has implemented automatic reconnection. This can provide higher availability.
-   Currently, NAT Gateway does not support packet fragmentation.
-   For the same destination public IP address and port, the number of EIPs that are associated with a NAT Gateway affects the maximum number of connections that the NAT Gateway can handle. If the NAT Gateway is associated with only one EIP, the maximum number of connections is 50,000. If multiple EIPs are associated, this number is 50,000 multiplied by the number of EIPs.
-   ECS instances in a VPC that are not associated with any public IP addresses can access the Internet through a NAT Gateway. If the bandwidth at which the ECS instances access the same public IP address and port is greater than 2 Gbit/s, packets may be discarded due to limited ports. To resolve this issue, we recommend that you associate four to eight EIPs with the NAT Gateway and [create a SNAT pool](https://yq.aliyun.com/articles/533821).

