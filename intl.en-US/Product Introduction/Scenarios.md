# Scenarios {#concept_wvh_wjy_ydb .concept}

NAT Gateway applies to scenarios where ECS instances of the VPC network need to access Internet or provide public services.

## Scenario 1: Set up a high-availability SNAT Gateway {#section_tlk_zjy_ydb .section}

In an IT system, some ECS instances need to access the Internet. Out of security concerns, public IPs of these ECS instances cannot be exposed on the Internet. In such cases, you can use the SNAT function of NAT Gateway. For more information, see [Create an SNAT entry](../../../../reseller.en-US/Quick Start/Create an SNAT entry.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13982/15434985574441_en-US.png)

## Scenario 2: Provide public services {#section_t21_hrj_32b .section}

The ECS instances of the VPC network can provide public services by configuring IP mapping or port mapping.

