# Billing method {#concept_z13_hty_ydb .concept}

Fees for NAT Gateway are incurred when you create NAT Gateway instances and when traffic is sent over the Internet \(that is, the NAT Gateway is associated with one or more Elastic IP Addresses \(EIPs\) to allow access to the Internet\).

## Instance fee {#section_t2z_2gb_n2b .section}

-   Billing method: Pay-As-You-Go

    Fees are calculated and charged on a daily basis.

-   Billing items: Only the instance retention fee is charged on a NAT Gateway.
-   Price: Different NAT Gateway specifications are provided to meet different customer demands. The instance retention fee varies based on different specifications.

## Internet fee {#section_y53_lty_ydb .section}

After you create a NAT Gateway, you need to associate one or more EIPs with the NAT Gateway so that the NAT Gateway can access the Internet. After the association, the Internet fee of the NAT Gateway is charged according to the billing method of the purchased EIPs.

**Note:** If you purchased a NAT bandwidth package for your account before January 26, 2018, you can still use public IP addresses in the bandwidth package. In this case, the fee of the NAT bandwidth package is the Internet fee of the NAT Gateway. For more information, see [Billing of NAT bandwidth package](../../../../reseller.en-US/Bandwidth Package/Billing of NAT bandwidth package.md#).

If you add EIPs to an Internet Shared Bandwidth, the Internet fee of the NAT Gateway is billed according to the billing method of the Internet Shared Bandwidth. For more information, see [Billing](../../../../reseller.en-US/Pricing/Billing.md#).

