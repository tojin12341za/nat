# Overview {#concept_czl_mcz_ydb .concept}

You can use the DNAT function to map a public IP address on the NAT Gateway to a private IP address in the CIDR block of the target ECS instance, so that the ECS instance can provide Internet services.

## DNAT entries {#section_gsb_pcz_ydb .section}

You can create DNAT entries in a DNAT table to implement port-based forwarding. After a DNAT entry is configured, data packets received by the specified public IP address are forwarded to the ECS instance according to the custom mapping rule.

Each DNAT entry consists of the following five parts:

-    **Public IP**: The Elastic IP Address \(EIP\) associated with the NAT Gateway.
-    **Private IP Address**: The private IP address of the ECS instance in the VPC.
-    **Public Port**: The public port used for forwarding traffic.
-    **Private Port**: The private port used for forwarding traffic.
-    **IP Protocol**: The protocol type of the port used for forwarding traffic.

**Note:** If your account purchased a bandwidth package before January 26, 2018, the public IP address is the IP address provided by the bandwidth package.

## Port mapping and IP mapping {#section_mkg_wcz_ydb .section}

The DNAT function includes port mapping and IP mapping:

-   Configure port mapping

    If port mapping is enabled, the NAT Gateway forwards requests from the specified protocol and port to the specified port of the target ECS instance in the VPC. For example,

    |DNAT entry|Public IP address|Public port|Private IP address|Private port|Protocol|
    |:---------|:----------------|:----------|:-----------------|:-----------|:-------|
    |Entry 1|139.224.xx.xx|80|192.168.x.x|80|TCP|
    |Entry 2|139.224.xx.xx|8080|192.168.x.x|8000|UDP|

    Entry 1: The NAT Gateway forwards traffic that is destined for 139.224.xx.xx through port 80 to port 80 of the ECS instance whose private IP address is 192.168.x.x.

    Entry 2: The NAT Gateway forwards traffic that is destined for 39.224.xx.xx through port 8080 to port 8000 of the ECS instance whose private IP address is 192.168.x.x.

-   IP mapping

    If IP mapping is enabled, the NAT Gateway forwards all traffic destined for the public IP address to the target ECS instance. The following is an example:

    |DNAT entry|Public IP address|Public port|Private IP address|Private port|Protocol|
    |:---------|:----------------|:----------|:-----------------|:-----------|:-------|
    |Entry 3|139.224.xx.xx|Any|192.168.x.x|Any|Any|

    Entry 3: The NAT Gateway forwards all requests destined for 139.224.xx.xx to the ECS instance whose private IP address is 192.168.x.x.


