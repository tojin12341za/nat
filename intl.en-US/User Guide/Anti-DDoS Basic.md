# Anti-DDoS Basic {#concept_wmq_3yb_nfb .concept}

A DDoS attack is a type of malicious network attack against the target system. As a result, the system cannot be accessed normally. Alibaba Cloud provides up to 5 Gbps basic anti-DDoS protection for NAT Gateway.

## Anti-DDoS Basic overview {#section_3c7_w9z_z9q .section}

After you enable Anti-DDos Basic, all traffic from the Internet must first go through Alibaba Cloud Security before arriving at NAT Gateway. Anti-DDoS Basic scrubs and filters common DDoS attacks and protects your services against attacks such as SYN flood, UDP flood, ACK flood, ICMP flood, and DNS Query flood.

Anti-DDoS Basic sets the scrubbing threshold and blackholing threshold according to the EIP bandwidth of NAT Gateway. When the inbound traffic reaches the threshold, scrubbing or blackholing is triggered:

-   Scrubbing: When the attack traffic from the Internet exceeds the scrubbing threshold or matches certain attack traffic model, Alibaba Cloud Security starts scrubbing the attack traffic. The scrubbing includes packet filtration, traffic speed limitation, packet speed limitation and more.
-   Blackholing: When the attack traffic from the Internet exceeds the blackholing threshold, blackholing is triggered and all inbound traffic is dropped.

## Scrubbing threshold {#section_lll_29p_4kz .section}

The scrubbing thresholds of NAT Gateway are calculated as follows.

|EIP bandwidth|Maximum traffic scrubbing threshold \(bits/s\)|Maximum traffic scrubbing threshold \(packets/s\)|Default blackholing threshold|
|:------------|:---------------------------------------------|:------------------------------------------------|:----------------------------|
|Less than or equal to 800 Mbps|800 Mbps|120,000|1.5 Gbps|
|More than 800 Mbps|Configured bandwidth|Configured bandwidth × 150|Configured bandwidth × 2|

If the EIP bandwidth is 1,000 Mbps, the maximum traffic scrubbing threshold \(bits/s\) is 1,000 Mbps, the maximum traffic scrubbing threshold \(packets/s\) is 150,000 and the default blackholing threshold is 2 Gbps.

