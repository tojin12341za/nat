# Limits {#concept_un3_rky_ydb .concept}

This topic describes limits related to the usage of NAT Gateway and EIPs.

## Limits on NAT Gateway {#section_kq2_5ky_ydb .section}

-   Only one NAT Gateway can be configured for a VPC.
-   A public IP address cannot be used as an SNAT entry and a DNAT entry at the same time.
-   Up to 100 DNAT entries can be added to a DNAT table. If you want to increase the quota, open a ticket.
-   Up to 40 SNAT entries can be added to an SNAT table. If you want to increase the quota, open a ticket.
-   If a VPC contains a custom route entry whose the destination CIDR block is 0.0.0.0/0, you must delete the CIDR block before you can create a NAT Gateway.
-   If a VSwitch is associated with an SNAT entry, it is limited by the peak bandwidth of the selected EIP.

    If the EIP is added to an Internet Shared Bandwidth, the VSwitch is limited by the peak bandwidth of the Internet Shared Bandwidth.


## Limits on associating EIPs {#section_wcw_yky_ydb .section}

-   You can associate up to 20 EIPs with a NAT Gateway. If you want to increase the quota, open a ticket.
-   You can associate up to 10 EIPs billed based on traffic with a NAT Gateway, and the peak bandwidth of each EIP billed based on traffic cannot be larger than 200 Mbps.
-   For the same destination IP address and port, the number of EIPs set for a NAT Gateway limits the Max Connections for the NAT Gateway. The Max Connections for a NAT Gateway associated with only one EIP is 55,000, and the Max Connections for a NAT Gateway associated with multiple EIPs is N\*55,000.
-   ECS instances in a VPC that are not associated with any public IP addresses can access the Internet through a NAT Gateway. If the bandwidth at which the ECS instances access the same public IP address and port is greater than 2 Gbit/s, packets may be discarded due to limited ports. To resolve this issue, we recommend that you associate four to eight EIPs with the NAT Gateway and create an SNAT IP address pool.
-   If your account includes a NAT bandwidth package purchased before January 26, 2018, you still need to use the bandwidth package to provide public IP addresses. To associate an EIP with the NAT Gateway, open a ticket.

