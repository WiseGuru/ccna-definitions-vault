---
tags:
  - mnemonics
---

![[AD#AD]]

# RIP
1. AD: 120
2. Metric: Hop count
	1. e.g., if *RouteA* has 2 hops but 10Mbps bandwidth on each link, and *RouteB* is 6 hops but Gigabit across entire link, then *RouteA* will be selected

# EIGRP
1. AD: 90
2. Metric: it's complicated, but roughly, the     *bandwidth (in Kbps)* of the **Slowest Link** + *delay (in microseconds) of all links*
	3. e.g., if there are three links and one of those links is on an ethernet (10Mbps) link, it would be 100 + delay of all links
	4. e.g., if there are seven links and one of those links is on a Gigabit (1,000Mbps) link, it would be 10000 + delay of all links
3. Additional terminology
	1. *Feasible Distance*
		1. The route's metric value to the destination
	2. *Advertised Distance* (aka Reported Distance)
		1. A neighbor's metric value to the route's destination
	3. *Successor*
		1. The route with the lowest metric (*feasible distance*) to the destination
	4. *Feasible Successor*
		1. An alternate route whose **Advertised Distance** is *lower* than the successor route's *feasible distance*

# OSPF
1. AD: 110
2. Metric: **Cost**: *Reference bandwidth* / *interface bandwidth*
	1. Default reference bandwidth is 100Mbps
	2. e.g., a route has three links that are 1Gbs, 100 Mbps, and 10 Mbps
		1. With default reference bandwidth: *Cost* = 1+1+10 = 12
		2. With 10000 reference bandwidth: *Cost* = 10 + 100 + 1000 = 1110