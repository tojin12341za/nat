# NAT bandwidth package FAQ {#concept_270180 .concept}

-    [Why cannot I buy a NAT bandwidth package in the NAT Gateway console?](#section_bfi_b1c_dzq) 
-    [How many NAT bandwidth packages can be associated with a NAT Gateway?](#section_zye_aty_rlc) 
-    [What is the difference between a NAT bandwidth package and an Internet Shared Bandwidth?](#section_r8u_xbe_6og) 
-    [What is the difference between public IP addresses in a NAT bandwidth package and EIPs?](#section_ht8_tnb_0nf) 
-    [Can I create an SNAT IP address pool for a NAT bandwidth package?](#section_0z3_fez_245) 
-    [Does the peak bandwidth value in a NAT bandwidth package apply to both inbound and outbound traffic?](#section_w6i_gu2_747) 

## Why cannot I buy a NAT bandwidth package in the NAT Gateway console? {#section_bfi_b1c_dzq .section}

If your account did not include a NAT bandwidth package before January 26, 2018, you can only associate EIPs with a NAT Gateway. For more information, see [Associate and disassociate EIPs](../../../../intl.en-US/User Guide/Associate and disassociate EIPs.md#).

## How many NAT bandwidth packages can be associated with a NAT Gateway? {#section_zye_aty_rlc .section}

By default, you can associate 4 NAT bandwidth packages with a NAT Gateway.

You can find the quota name natgw\_quota\_bandwidth\_packages\_num on the Quota Management page and apply for increasing the quota.

## What is the difference between a NAT bandwidth package and an Internet Shared Bandwidth? {#section_r8u_xbe_6og .section}

NAT bandwidth packages can be associated only with a NAT Gateway,

whereas Internet Shared Bandwidth can be associated with several cloud resources, including, for example, ECS and SLB instances.

## What is the difference between public IP addresses in a NAT bandwidth package and EIPs? {#section_ht8_tnb_0nf .section}

Public IP addresses cannot be disassociated from a NAT bandwidth package after they are associated with the package.

In contrast, EIPs can be associated with, and disassociated from, NAT bandwidth packages at any time.

## Can I create an SNAT IP address pool for a NAT bandwidth package? {#section_0z3_fez_245 .section}

Yes, you can create an SNAT IP address pool by calling the relevant API actions. For more information, see [Create an SNAT IP address pool](https://yq.aliyun.com/articles/533821).

## Does the peak bandwidth value in a NAT bandwidth package apply to both inbound and outbound traffic? {#section_w6i_gu2_747 .section}

The peak bandwidth value of a NAT bandwidth package applies only to the outbound traffic. However, inbound traffic is also indirectly affected by this limit.

