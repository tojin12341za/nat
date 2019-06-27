# DDoS基础防护 {#concept_wmq_3yb_nfb .concept}

DDoS攻击是一种针对目标系统的恶意网络攻击行为，会导致被攻击者的业务无法正常访问。阿里云免费为NAT网关提供最高5G的DDoS基础防护，DDoS基础防护服务可以有效防止DDoS攻击。

## DDoS基础防护工作原理 {#section_3c7_w9z_z9q .section}

启用DDoS基础防护功能后，所有来自Internet的流量都将先经过云盾再到达NAT网关，云盾会针对常见的攻击进行清洗过滤。云盾DDoS基础防护可以防御SYN Flood、UDP Flood、ACK Flood、ICMP Flood 和DNS Flood等DDoS攻击。

云盾DDoS基础防护根据NAT网关实例的EIP带宽自动设定清洗阈值和黑洞阈值。当入方向流量达到阈值上限时，触发清洗和黑洞：

-   清洗：当来自Internet的攻击流量超过清洗阈值或符合攻击流量模型特征时，云盾将启动清洗操作，清洗操作包括过滤攻击报文、流量限速、包限速等。
-   黑洞：当来自Internet的攻击流量超过黑洞阈值时，为保护集群安全，流量将会被黑洞处理，即所有入流量全部被丢弃。

## 清洗阈值 {#section_lll_29p_4kz .section}

NAT网关的清洗阈值计算方式如下表：

|EIP带宽|最大bps清洗阈值|最大pps清洗阈值|默认黑洞阈值|
|:----|:--------|:--------|:-----|
|小于等于800 Mbps|800Mbps|12万|1.5 Gbps|
|大于800 Mbps|设定的带宽值|设定的带宽值×150|设定的带宽值×2|

比如EIP带宽为1000Mbps，则最大bps清洗阈值为1000Mbps，最大pps清洗阈值15万，默认黑洞阈值2Gbps。

