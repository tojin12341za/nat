# Billing of NAT bandwidth package {#concept_u2s_hvc_zdb .concept}

 A NAT bandwidth package encapsulates public IPs and bandwidth resource. A bandwidth package consists of one or more public IPs. Therefore, the fee of a NAT bandwidth package includes the public IP retention fee and traffic fee.

## Billing methods {#section_fxd_lvc_zdb .section}

NAT bandwidth package supports Pay-As-You-Go billing. The NAT bandwidth package fee is billed on an hourly basis and is deducted in real time. Partial hours are billed as full hours. In a billing cycle, partial hours are billed as full hours.

## Billing items {#section_frq_wwc_zdb .section}

The NAT bandwidth package fee includes public IP retention fee and traffic fee.

-   Public IP fee = IP price × number of IPs × retention time

-   Traffic fee = Traffic price × amount of outgoing traffic

    -   Only the outgoing traffic \(from Alibaba Cloud to the Internet\) is billed, and the incoming traffic is not billed.

    -   Modifying the peak bandwidth does not affect the unit price. However, we recommend that you configure the bandwidth based on your actual needs to avoid generating excessive charged traffic due to program error or malicious access.


The following table shows the traffic prices and IP charges for each region.

**Note:** The price here is a reference, take the price on the purchase page as standard.

|Region| IP retention fee \(USD/hour/per IP\)|Traffic price \(USD/GB\)|
|:-----|:------------------------------------|:-----------------------|
|China \(Qingdao\)|0.003|0.113|
|China \(Hangzhou\), China \(Shanghai\), China \(Beijing\), China \(Zhangjiakou\), China \(Shenzhen\)|0.003|0.125|
|Hong Kong|0.009|0.156|
|Singapore|0.125|0.081|
|US \(Virginia\)|0.005|0.078|
|US \(Silicon Valley\)|0.005|0.078|
|Japan \(Tokyo\)|0.005|0.12|
| India \(Mumbai\)|0.009|0.447|
|Australia \(Sydney\)|0.006|0.13|
|Malaysia \(Kuala Lumpur\)|0.112|0.13|
|Germany \(Frankfurt\)|0.006|0.07|

