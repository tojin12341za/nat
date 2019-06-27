# Overview {#concept_pnw_cdl_32b .concept}

You can use the SNAT function to enable ECS instances without public IP addresses in a VPC to access the Internet.

## SNAT entries {#section_qnw_cdl_32b .section}

You can create SNAT entries in an SNAT table to enable the ECS instance to access the Internet.

Each SNAT entry consists of the following two parts:

-    **ECS Instance**: The ECS instance of the VPC network that needs to use the SNAT function.
-    **Public IP**: The Elastic IP Address \(EIP\) associated with the NAT Gateway.

**Note:** If your account includes a NAT bandwidth package purchased before January 26, 2018, the public IP address is the IP address provided by the bandwidth package.

## VSwitch granularity and ECS granularity {#section_g9i_j7e_7cx .section}

The SNAT function provides the following two kinds of granularity.

-   VSwitch granularity

    If you select the VSwitch granularity, when an ECS instance under the specified VSwitch accesses the Internet, the NAT Gateway uses the specified EIP to provide the SNAT service. By default, all the ECS instances belonging to the VSwitch can use the specified public IP address to access the Internet.

-   ECS granularity

    If you select the VSwitch granularity, when the ECS instance accesses the Internet, the NAT Gateway uses the specified EIP to provide the SNAT service.


**Note:** If an ECS instance is already associated with a public IP address \(for example, it is allocated with a public IP address, associated with an EIP, or configured with DNAT IP mapping\), the ECS instance accesses the Internet by using the associated public IP address instead of the SNAT function of NAT Gateway. To uniformly manage the public IP addresses of ECS instances in a VPC, see [Attach an ENI to an ECS that is allocated with an public IP address](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md#), [Attach an ENI to an ECS instance associated with an EIP](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md#), and [Attach an ENI to an ECS instance configured with DNAT IP mapping](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md#).

