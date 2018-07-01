# Scenarios {#concept_wvh_wjy_ydb .concept}

NAT Gateway is suitable for the scenarios where ECS instances of the VPC network need to access Internet or to provide public services.

## Scenarios 1: set up a high-available SNAT gateway. {#section_tlk_zjy_ydb .section}

In a system, there are some ECS instances need to access Internet but prevent Internet from initiating a connection to these instances.  In such cases, you can use the SNAT function of NAT Gateway to set up an SNAT gateway.

## Scenarios 2: provide public services {#section_t21_hrj_32b .section}

The ECS instances of the VPC network can provide public services by configuring IP mapping or port mapping.

