# Features {#concept_sdh_thy_ydb .concept}

NAT Gateway provides SNAT and DNAT functions.

## SNAT {#section_qsq_vhy_ydb .section}

NAT Gateway supports SNAT \(Source NAT\), allowing you to associate a public IP with a VSwitch. Then, the ECS instances in the VSwitch can use the public IP to access the Internet.

In addition, SNAT can serve as a simple firewall that protects backend ECS instances. An external terminal can access an ECS instance after the ECS instance actively establishes a connection with the external terminal. An untrustworthy external terminal cannot access a backend ECS instance if no connection is established.

## DNAT {#section_rsq_vhy_ydb .section}

NAT Gateway supports DNAT \(Destination NAT\), allowing you to map a public IP to a private IP. Then, the ECS instance with the public IP can provide public service.

DNAT supports both port mapping and IP mapping.

