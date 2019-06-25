# EIP limits FAQ {#concept_270190 .concept}

-    [Why am I unable to associate an EIP with a NAT Gateway in the NAT Gateway console?](#section_hp1_eoj_3e0) 
-    [Does EIP support creating an SNAT IP address pool?](#section_hij_hvv_z0w) 
-    [How many EIPs can I associate with a NAT Gateway?](#section_t0q_127_wm6) 
-    [Why am I unable to reach peak bandwidth after I associate an EIP with a NAT Gateway?](#section_ye9_coy_lky) 

## Why am I unable to associate an EIP with a NAT Gateway in the NAT Gateway console? {#section_hp1_eoj_3e0 .section}

You may be unable to associate an EIP with a NAT Gateway because of the purchase date of a NAT Gateway bandwidth package under your Alibaba Cloud account. If your account has a NAT Gateway bandwidth package that was purchased on or before January 28, 2018, you must use this bandwidth package to provide public IP addresses. If you want to use an EIP even though the NAT Gateway bandwidth package under your account is valid, you must open a ticket to request this service.

## Does EIP support creating an SNAT IP address pool? {#section_hij_hvv_z0w .section}

Yes. Currently, you can only create an SNAT IP address pool by calling API actions. For more information, see [Create an SNAT IP address pool](../../../../reseller.en-US/Best Practices/Create an SNAT IP address pool.md#).

## How many EIPs can I associate with a NAT Gateway? {#section_t0q_127_wm6 .section}

You can associate up to 20 EIPs with a NAT Gateway. If you want to increase the quota, open a ticket.

You can associate up to 10 EIPs billed based on traffic with a NAT Gateway, and the peak bandwidth of each EIP billed based on traffic cannot be larger than 200 Mbps.

## Why am I unable to reach peak bandwidth after I associate an EIP with a NAT Gateway? {#section_ye9_coy_lky .section}

The number of EIPs associated with a NAT Gateway limits the Max Connections of the NAT Gateway. The Max Connections of a NAT Gateway associated with only one EIP is 55,000. If the bandwidth at which the ECS instances access the same public IP address and port is greater than 2 Gbit/s, packets may be discarded due to limited ports. To resolve this issue, we recommend that you associate four to eight EIPs with the NAT Gateway and create a SNAT pool.

