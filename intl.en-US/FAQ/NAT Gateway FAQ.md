# NAT Gateway FAQ {#concept_270217 .concept}

-    [Can I configure both DNAT and SNAT rules for a public IP address?](#section_vlv_m2f_2bf) 
-    [How many NAT Gateways can I create?](#section_0wp_8zk_c6u) 
-    [How many DNAT entries can I add to a NAT Gateway?](#section_igf_d4c_mui) 
-    [How many SNAT entries can I add to an SNAT Gateway?](#section_rsx_1cu_8cd) 
-    [How many public IP addresses can be associated with an SNAT entry?](#section_oyo_bvw_tt3) 
-    [Can I view the traffic of each VSwitch in the console of the corresponding NAT Gateway?](#section_vcs_0wp_vsg) 
-    [If an ECS instance is allocated with a public IP address and configured with an SNAT entry, what can I do if I want the ECS instance to access the Internet through the public IP address in the SNAT entry?](#section_534_7dp_bs8) 
-    [If an ECS instance is allocated with a public IP address and configured with an SNAT entry, what can I do if I want the ECS instance to access the Internet through the public IP address in the SNAT entry?](#section_u9j_9ts_jo0) 
-    [If an ECS instance is configured with both DNAT IP mapping and an SNAT entry, what can I do if I want the ECS instance to access the Internet through the public IP address in the SNAT entry?](#section_0wq_838_rp7) 

## Can I configure both DNAT and SNAT rules for a public IP address? {#section_vlv_m2f_2bf .section}

No, a public IP address can only be configured with either DNAT rules or SNAT rules. You must configure a DNAT rule and a SNAT rule for different public IP addresses.

## How many NAT Gateways can I create? {#section_0wp_8zk_c6u .section}

There is no limit on the number of NAT Gateways that an Alibaba Cloud account can create.

## How many DNAT entries can I add to a NAT Gateway? {#section_igf_d4c_mui .section}

You can add up to 100 DNAT entries to a NAT Gateway.

You can find the quota name natgw\_quota\_dnat\_entry\_num on the Quota Management page and apply for increasing the quota.

## How many SNAT entries can I add to an SNAT Gateway? {#section_rsx_1cu_8cd .section}

You can add up to 40 SNAT entries to a NAT Gateway.

You can find the quota name natgw\_quota\_snat\_entry\_num on the Quota Management page and apply for increasing the quota.

## How many public IP addresses can be associated with an SNAT entry? {#section_oyo_bvw_tt3 .section}

You can associate a maximum of 256 public IP addresses to a single SNAT entry.

## Can I view the traffic of each VSwitch in the console of the corresponding NAT Gateway? {#section_vcs_0wp_vsg .section}

No.

But you can associate EIPs with VSwitches and then view the traffic of the VSwitches in the EIP console.

## If an ECS instance is allocated with a public IP address and configured with an SNAT entry, what can I do if I want the ECS instance to access the Internet through the public IP address in the SNAT entry? {#section_534_7dp_bs8 .section}

You can create an ENI and attach the ENI to the ECS instance, convert the public IP address allocated to the ECS instance to an EIP, and associate the EIP with an ENI, so that the ECS instance accesses the Internet through the public IP address in the SNAT entry and traffic from the Internet accesses the ECS instance through the ENI. For more information, see [Attach an ENI to an ECS that is allocated with an public IP address](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md#).

## If an ECS instance is allocated with a public IP address and configured with an SNAT entry, what can I do if I want the ECS instance to access the Internet through the public IP address in the SNAT entry? {#section_u9j_9ts_jo0 .section}

You can create an ENI and attach the ENI to the ECS instance, disassociate the EIP from the ECS instance, and associate the EIP to the ENI, so that the ECS instance accesses the Internet through the public IP address in the SNAT entry, and traffic from the Internet accesses the ECS instance through the ENI. For more information, see [Attach an ENI to an ECS instance associated with an EIP](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md#).

## If an ECS instance is configured with both DNAT IP mapping and an SNAT entry, what can I do if I want the ECS instance to access the Internet through the public IP address in the SNAT entry? {#section_0wq_838_rp7 .section}

You can create an ENI and attach the ENI to the ECS instance, remove the DNAT entry in the NAT Gateway, create a new DNAT entry, and map a public IP address in the NAT Gateway to the ENI, so that the ECS instance accesses the Internet through the public IP address in the SNAT entry and traffic from the Internet accesses the ECS instance through the ENI. For more information, see [Attach an ENI to an ECS instance configured with DNAT IP mapping](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md#).

