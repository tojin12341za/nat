# Create an SNAT entry {#task_491135 .task}

This topic describes how to create an SNAT entry. The SNAT function enables ECS instances without public IP addresses in a VPC to access the Internet.

A NAT Gateway is created and the NAT Gateway is associated with an Elastic IP Address \(EIP\). For more information, see [Create a NAT Gateway](../reseller.en-US/Quick Start/Create a NAT Gateway.md#) and [Associate an EIP](../reseller.en-US/Quick Start/Associate an EIP.md#).

**Note:** If your account has purchased a bandwidth package before January 26, 2018, make sure there is an available public IP address in the bandwidth package.

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **NAT Gateways**.
3.  Select the region of the NAT Gateway.
4.   On the NAT Gateways page, find the target NAT Gateway instance and click **Configure DNAT** in the **Actions** column. 
5.   On the SNAT Table page, click **Create SNAT Entry**. 
6.   On the Create SNAT Entry page, configure the SNAT entry according to the following information and click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    | **VSwitch Granularity** |
    | **VSwitch** |Select the VSwitch where the ECS instances that require the Internet access are located. All ECS instances that belong to the specified VSwitch can access the Internet through the SNAT function. **Note:** If an ECS instance is already associated with a public IP address \(for example, it is allocated with a public IP address, associated with an EIP, or configured with DNAT IP mapping\), the ECS instance accesses the Internet by using the associated public IP address instead of the SNAT function of NAT Gateway. To uniformly manage the public IP addresses of ECS instances in a VPC, see [Attach an ENI to an ECS that is allocated with an public IP address](../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md#), [Attach an ENI to an ECS instance associated with an EIP](../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md#), and [Attach an ENI to an ECS instance configured with DNAT IP mapping](../reseller.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md#).

 |
    | **VSwitch CIDR Block** |Display the CIDR block of the selected VSwitch.|
    | **Public IP** |Select the public IP address that is used to access the Internet. **Note:** The IP that is already being used in a DNAT entry cannot be selected.

 |
    | **Entry Name** |Enter a name for the SNAT entry to be created. The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, underscores \(\_\), and hyphens \(-\). The name must start with a letter.

 |
    | **ECS Granularity** |
    | **Available ECS Instances** |Select an ECS instance in the VPC that needs to access the Internet. The selected ECS instance will access the Internet by using the specified public IP address. Make sure that the following conditions are met:

    -   The ECS instance is running.
    -   The ECS instance is not associated with any public IP addresses or EIPs.
 |
    | **ECS CIDR Block** |Displays the CIDR block of the selected ECS instance.|
    | **Public IP** |Select the public IP address that is used to access the Internet. **Note:** The IP that is already being used in a DNAT entry cannot be selected.

 |
    | **Entry Name** |Enter a name for the SNAT entry to be created. The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, underscores \(\_\), and hyphens \(-\). The name must start with a letter or a Chinese character.

 |


