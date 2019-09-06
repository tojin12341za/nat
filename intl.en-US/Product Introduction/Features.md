# Features {#concept_sdh_thy_ydb .concept}

NAT Gateway provides SNAT, DNAT, and bandwidth sharing functions.

## SNAT {#section_qsq_vhy_ydb .section}

NAT Gateway supports SNAT, allowing ECS instances without a public IP address in a VPC to access the Internet.

In addition, SNAT can operate as a simple firewall that protects backend ECS instances. An external terminal can access an ECS instance after the ECS instance actively establishes a connection with the external terminal. An untrustworthy external terminal cannot access a backend ECS instance if no connection is established.

## DNAT {#section_rsq_vhy_ydb .section}

NAT Gateway supports DNAT and maps a public IP address to a private IP address. Then, the ECS instance with the public IP address can provide public service.

DNAT supports both port mapping and IP mapping.

## Bandwidth sharing {#section_ssq_vhy_ydb .section}

You can associate an NAT Gateway with an EIP and add the EIP to [Internet Shared Bandwidth](https://www.aliyun.com/product/cbwp?spm=5176.8142029.388261.320.3836dbcc85aZVp). After an EIP is added to an Internet Shared Bandwidth, the original billing method of the EIP loses effect, and only the instance fee of the EIP is charged.

