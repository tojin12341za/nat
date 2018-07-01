# Billing {#concept_z13_hty_ydb .concept}

NAT Gateway is a service entity. It cannot access the Internet itself. Therefore, it must be configured with a public IP \(EIP\). The billing of a NAT Gateway not only includes the fee of the NAT Gateway but also the fee of the public IP.

## Instance fee {#section_aph_lty_ydb .section}

-   Billing method: Pay-As-You-Go

    The billing cycle is on a daily basis.

-   Billing items: Only instance fee is collected for NAT Gateway itself.
-   Price: NAT Gateway provides different specifications to meet different user needs. The price varies based on different specifications.

## Public network fee {#section_y53_lty_ydb .section}

After creating a NAT Gateway, you must bind an EIP to it to access the Internet. Once an EIP is bound, the public network fee of the NAT Gateway is billed on the EIP.

**Note:** If your account has purchased a shared bandwidth package, you can still use the public IP of the bandwidth package. In this case, the public network fee is billed on the bandwidth package. For more information, see [Billing of NAT bandwidth package](../../../../intl.en-US/Bandwidth Package/Billing of NAT bandwidth package.md#).

