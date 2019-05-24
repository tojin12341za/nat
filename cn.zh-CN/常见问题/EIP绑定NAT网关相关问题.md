# EIP绑定NAT网关相关问题 {#concept_270190 .concept}

-   [为什么在NAT网关控制台不能绑定EIP？](#section_hp1_eoj_3e0)
-   [EIP支持创建SNAT IP地址池吗？](#section_hij_hvv_z0w)
-   [一个NAT网关可以绑定多少个EIP？](#section_t0q_127_wm6)
-   [NAT网关绑定EIP，为什么流量达不到带宽峰值？](#section_ye9_coy_lky)
-   [ECS实例同时绑定EIP和NAT网关，为什么不是通过NAT网关绑定的公网IP访问互联网？](#section_x58_rws_uyl)

## 为什么在NAT网关控制台不能绑定EIP？ {#section_hp1_eoj_3e0 .section}

对于2017年11月3日23：59分之前账号下存在NAT带宽包的全部用户，仍然为NAT带宽包的使用方式。默认无法使用EIP绑定NAT网关的功能，如需使用EIP绑定NAT网关功能请提交工单。

## EIP支持创建SNAT IP地址池吗？ {#section_hij_hvv_z0w .section}

支持。目前只支持通过API创建SNAT IP地址池。详细信息，请参见[创建SNAT IP地址池](../../../../cn.zh-CN/最佳实践/创建SNAT IP地址池.md#)。

## 一个NAT网关可以绑定多少个EIP？ {#section_t0q_127_wm6 .section}

一个NAT网关最多绑定20个EIP，可提交工单申请更多配额。

一个NAT网关最多绑定10个按流量计费的EIP，且按流量计费的EIP的最大峰值不能大于200Mbps。

## NAT网关绑定EIP，为什么流量达不到带宽峰值？ {#section_ye9_coy_lky .section}

NAT网关绑定的EIP数限制NAT网关的最大并发数，绑定单个EIP最大连接数为55000，当ECS通过NAT网关访问公网上同一个目的IP和端口的带宽大于2Gbps时，建议您为NAT网关绑定4-8个EIP并构建SNAT IP地址池，避免单个EIP的端口数量限制可能产生的丢包。

## ECS实例同时绑定EIP和NAT网关，为什么不是通过NAT网关绑定的公网IP访问互联网？ {#section_x58_rws_uyl .section}

当ECS实例同时绑定了EIP和NAT网关时，数据均通过EIP转发。解绑EIP后，才能通过NAT网关绑定的公网IP访问互联网。

