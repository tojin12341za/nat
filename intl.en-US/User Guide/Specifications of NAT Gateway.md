# Specifications of NAT Gateway {#concept_nlc_s1z_ydb .concept}

NAT Gateway provides with you different specifications to use. The specification affects the performance metrics \(maximum connections and the number of new connections per second\), but does not influence data throughput.

The following table lists the available specifications.

|Specification|Maximum number of SNAT connections|Number of new SNAT connections established per second|
|:------------|:---------------------------------|:----------------------------------------------------|
|Small|10,000|1,000|
|Medium|50,000|5,000|
|Large|200,000|10,000|
|Super large|1,000,000|30,000|

Note the following when selecting a specification:

-   The specifications only affect the SNAT performance and have no impact on the DNAT performance.

-   No mutual restraint exists between the specification and the number of the IPs.

-   CloudMonitor only provides the monitor data on the maximum number of connections but does not provide monitor data on CPS.

-   The timeout period of an SNAT connection is 900 seconds.

-   To avoid SNAT connection timeout caused by network congestion and public network jitter, make sure that your service application has implemented automatic reconnection. This can provide higher availability.

-   The NAT Gateway does not yet support packet fragmentation.


