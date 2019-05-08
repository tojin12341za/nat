# Billing method {#concept_z13_hty_ydb .concept}

Fees for NAT Gateway are incurred when you create NAT Gateway instances and when traffic is sent over the Internet \(that is, the NAT Gateway is associated with one or more Elastic IP Addresses \(EIPs\) to allow access to the Internet\).

## Instance fee {#section_t2z_2gb_n2b .section}

-   Billing method

    NAT Gateway is billed by the Pay-As-You-Go method and fees are calculated and charged on a daily basis.

-   Billing item

    Only an instance fee is charged at the creation of NAT Gateway.

-   Price

    The fee for NAT Gateway varies according to the selected specification.

    **Note:** The following table is provided for reference only. Prices displayed on the purchase page are the actual fees for the selected specification.

    |Region|Specification|
|Small \(USD/day\)|Medium \(USD/day\)|Large \(USD/day\)|Super Large-1 \(USD/day\)|
    |------|-------------|
    |-----------------|------------------|-----------------|-------------------------|
    |China \(Qingdao\), China \(Hangzhou\), China \(Shanghai\), China \(Beijing\), China \(Zhangjiakou\), China \(Shenzhen\), China \(Hohhot\)|1.829|3.505|6.858|12.192|
    |Hong Kong, US \(Virginia\)|2.438|4.572|8.991|15.849|
    |Singapore|2.743|5.334|10.363|18.287|
    |US \(Silicon Valley\)|2.591|5.029|9.601|17.068|
    |Japan \(Tokyo\)|2.926|5.608|10.972|19.507|
    |UAE \(Dubai\)|5.486|10.515|20.573|36.575|
    |Australia \(Sydney\)|3.657|5.334|13.716|24.383|
    |Germany \(Frankfurt\)|3.292|6.309|12.344|21.945|


## Internet fee {#section_y53_lty_ydb .section}

After you create an NAT Gateway, you need to associate one or more EIPs with the NAT Gateway so that the NAT Gateway can access the Internet. After the association, an Internet fee is incurred due to traffic being sent over the Internet. The Internet fee is billed to the associated EIP, instead of the NAT Gateway.

**Note:** If you purchased a shared bandwidth package for your account before January 26, 2018, you can still use the public IP address of the bandwidth package. In this case, the Internet fee is billed to the bandwidth package. For more information, see [Billing of NAT bandwidth package](../../../../reseller.en-US/Bandwidth Package/Billing of NAT bandwidth package.md#).

