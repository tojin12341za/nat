# Limits  {#concept_un3_rky_ydb .concept}

## Limits on NAT Gateway {#section_kq2_5ky_ydb .section}

-   A VPC can have only one NAT Gateway.

-   A public IP cannot be used for both an SNAT entry and a DNAT entry.

-   If the VPC contains a custom route entry of which the destination CIDR block is 0.0.0.0/0, you must delete it before creating a NAT Gateway.

-   If a VSwitch is added to an SNAT entry, it will be limited by the bandwidth of the selected EIP.

-   Up to 100 DNAT entries can be added to a DNAT table.

-   Up to 40 SNAT entries can be added to an SNAT table.


## Limits on EIP binding {#section_wcw_yky_ydb .section}

-   Up to 10 EIPs can be bound to a NAT Gateway. Open a ticket to apply for more.

-   The maximum bandwidth of each EIP is 200 Mbps.

-    If your account has purchased a NAT bandwidth package before January 26, 2018, you still need to use the bandwidth package to provide public IPs. Open a ticket if you want to bind an EIP to the NAT Gateway.


