# Limits {#concept_un3_rky_ydb .concept}

This topic describes limits related to the usage of NAT Gateway and EIPs.

## Limits on NAT Gateway {#section_kq2_5ky_ydb .section}

-   Only one NAT Gateway can be configured for a VPC.

-   A public IP address cannot be used as an SNAT entry and a DNAT entry at the same time.

-   If a VPC contains a custom route entry whose the destination CIDR block is 0.0.0.0/0, you must delete the CIDR block before you can create a NAT Gateway.

-   If a VSwitch is added to an SNAT entry, it will be limited by the bandwidth of the selected EIP.

-   Up to 100 DNAT entries can be added to a DNAT table.

-   Up to 40 SNAT entries can be added to an SNAT table.


## Limits on attaching EIPs {#section_wcw_yky_ydb .section}

-   Up to 20 EIPs can be associated with a NAT Gateway. You can open a ticket to increase the quota.

-   Up to 10 Pay-As-You-Go EIPs can be attached to a NAT Gateway. The maximum bandwidth of each Pay-As-You-Go EIP is 200 Mbps.

-   If you purchased a NAT bandwidth package before January 26, 2018, you need to use the bandwidth package to provide public IP addresses. However, if you must attach an EIP to the NAT Gateway, please open a ticket.


