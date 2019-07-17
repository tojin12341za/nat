# Overview {#concept_pnw_cdl_32b .concept}

NAT Gateways support the SNAT function. This function allows ECS instances that are not associated with public IP addresses in a VPC to access the Internet.

## SNAT entries {#section_qnw_cdl_32b .section}

You can create SNAT entries in a SNAT table to enable ECS instances to access the Internet.

Each SNAT entry consists of the following two parts:

-   **VSwitch or ECS Instance**: The VSwitch or ECS instance that needs to use the SNAT function.
-   **Public IP**: The public IP address used to grant access to the Internet.

    **Note:** 

    -   You can select multiple public IP addresses to build a SNAT IP address pool. When an ECS instance in a VPC initiates an Internet access request, the ECS instance uses a public IP address in the SNAT address pool to access the Internet.
    -   If you purchased a NAT bandwidth package before January 26, 2018, the public IP address is the IP address provided by the bandwidth package.

## VSwitch granularity and ECS granularity {#section_g9i_j7e_7cx .section}

The SNAT function provides the following two types of granularity:

-   VSwitch granularity

    If you select VSwitch granularity to create a SNAT entry, the NAT Gateway provides the Internet proxy service for an ECS instance in the specified VSwitch when the ECS instance initiates an Internet access request. In this way, the ECS instance can use the specified public IP address to access the Internet. By default, all ECS instances in the VSwitch can use the specified public IP address to access the Internet.

    **Note:** If an ECS instance is already associated with a public IP address \(for example, it is assigned a public IP address, associated with an EIP, or configured with DNAT IP mapping\), the ECS instance accesses the Internet by using the associated public IP address instead of the SNAT function of the NAT Gateway. To configure ECS instances in a VPC with the same public IP address, see [Attach an ENI to an ECS that is allocated with an public IP address](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md#), [Attach an ENI to an ECS instance associated with an EIP](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md#), and [Attach an ENI to an ECS instance configured with DNAT IP mapping](../../../../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md#).

-   ECS granularity

    If you select VSwitch granularity to create a SNAT entry, the specified ECS instance uses the specified public IP address to access the Internet. When the ECS instance initiates an Internet access request, the NAT Gateway provides the Internet proxy service for the ECS instance.


