Implementation Tasks

* Network Foundation
- Build the topology and apply the IPv4 addressing plan.
- Configure router and switch hostnames and interface descriptions.
- Configure all routed Ethernet and serial interfaces.
- Configure DCE clocking where required.
- Verify Layer 1, Layer 2, and directly connected reachability.

*Switching and VLANs
- Create VLANs 10, 20, 30, 110, 120, 210, and 220.
- Configure access ports for all client devices.
- Configure 802.1Q trunks toward the router-on-a-stick gateways.
- Restrict trunks to the required VLANs.
- Enable PortFast on client-facing switch ports.
- Verify VLAN membership, trunking, spanning tree, and MAC learning.

*DHCP and Inter-VLAN Routing
- Configure router-on-a-stick on R4, R10, R11, and R25.
- Configure DHCP for the Area 10 client VLANs.
- Configure split DHCP scopes for VLANs 110 and 120.
- Configure DHCP for the EIGRP client VLANs.
- Advertise `8.8.8.8` as the client DNS server.
- Verify DHCP leases and local gateway connectivity.

*Multi-Area OSPF
- Configure OSPF Area 0 as the backbone.
- Configure Area 10 as a totally stubby area.
- Configure Area 20 as a totally NSSA.
- Configure Area 30 as a stub area.
- Configure R2 and R3 as Area Border Routers.
- Configure R6 as an NSSA Autonomous System Boundary Router.
- Configure R29 and R32 as OSPF/BGP edge routers.
- Use passive interfaces by default.
- Configure point-to-point OSPF network types on router links.
- Configure a consistent OSPF reference bandwidth.
- Enable OSPF equal-cost multipath routing.

*OSPF Security and Path Control
- Secure OSPF adjacencies with MD5 authentication.
- Configure explicit OSPF interface costs.
- Add redundant Area 0 paths.
- Verify OSPF path selection and failover.
- Validate all OSPF neighbor adjacencies.

*OSPF DR and BDR Election
- Configure the Area 30 Ethernet segment as a broadcast multi-access network.
- Configure R5 as the preferred DR.
- Configure R7 as the preferred BDR.
- Prevent R8 and R9 from participating in DR/BDR elections.
- Verify the DR, BDR, and DROTHER states.

*OSPF Loopbacks, Filtering, and Summarization
- Create five `/24` loopback networks on R4.
- Advertise the R4 loopbacks into Area 10.
- Create five `/24` loopback networks on R5.
- Advertise the R5 loopbacks into Area 30.
- Filter selected Area 10 and Area 30 prefixes at R2.
- Configure inter-area summarization on the ABR.
- Verify that approved prefixes are advertised.
- Verify that filtered prefixes remain inside their source areas.

*Static Routing and OSPF Redistribution
- Configure a primary static route through R10.
- Configure a floating static backup route through R11.
- Monitor the primary path using IP SLA and object tracking.
- Redistribute only approved static prefixes into OSPF.
- Use prefix lists and route maps to control redistribution.
- Apply explicit external metrics and route tags.
- Advertise the static VLAN summary as an N1/E1 route.
- Advertise a test prefix as an N2/E2 route.
- Verify Type 7 to Type 5 LSA translation at R3.

*HSRP High Availability
- Configure HSRP for VLANs 110 and 120.
- Configure R10 as the preferred active gateway.
- Configure R11 as the standby gateway.
- Enable HSRP preemption.
- Track upstream reachability and decrement HSRP priority.
- Synchronize HSRP gateway failover with the active static route.
- Verify gateway and path failover without losing end-to-end connectivity.

*Named EIGRP AS 100
- Deploy named EIGRP AS 100 across R19 through R24 and R32.
- Configure unique EIGRP router IDs.
- Enable EIGRP MD5 authentication using a key chain.
- Configure passive interfaces by default.
- Enable neighbor formation only on router-to-router links.
- Configure maximum paths for redundant forwarding.
- Configure variance for unequal-cost path testing.
- Verify EIGRP successors, feasible successors, and topology entries.

*Named EIGRP AS 200
- Deploy named EIGRP AS 200 between R23 and R25.
- Configure authenticated EIGRP adjacency.
- Advertise VLANs 210 and 220.
- Configure route summarization toward the EIGRP core.
- Verify client reachability through AS 200.

*EIGRP Loopbacks and Summarization
- Create five `/24` loopback networks on R24.
- Advertise all R24 loopbacks in EIGRP AS 100.
- Configure interface summarization as `172.24.8.0/21`.
- Verify the EIGRP summary and local discard route.

*EIGRP Redistribution
- Configure R23 as the boundary between EIGRP AS 100 and AS 200.
- Perform controlled two-way redistribution.
- Configure seed metrics for redistributed routes.
- Apply route maps and route tags.
- Prevent redistributed routes from being advertised back into their source process.
- Propagate the default route from AS 100 into AS 200.
- Verify connectivity between both EIGRP domains.

*OSPF–EIGRP Integration
- Configure R32 as the OSPF–EIGRP boundary router.
- Redistribute selected EIGRP branch prefixes into OSPF.
- Apply prefix lists, route maps, metrics, and tags.
- Prevent route feedback between OSPF and EIGRP.
- Advertise a default route from R32 toward EIGRP AS 100.
- Verify connectivity between OSPF and EIGRP clients.

*Enterprise iBGP
- Deploy enterprise BGP AS 65000 across R29, R30, R31, and R32.
- Configure loopback-based iBGP peering.
- Provide underlay reachability between all BGP loopbacks.
- Build the complete four-router iBGP full mesh.
- Configure `next-hop-self`.
- Enable BGP community exchange.
- Configure iBGP multipath where supported.
- Verify all six iBGP sessions.

*External BGP
- Configure eBGP between AS 65000 and AS 65002.
- Configure eBGP between AS 65000 and AS 65001.
- Configure dual eBGP sessions between AS 65000 and the Internet AS 65003.
- Configure five `/24` loopbacks on R34.
- Advertise the R34 loopbacks from AS 65002.
- Configure five `/24` loopbacks on R35.
- Advertise the R35 loopbacks through AS 65001.
- Configure outbound prefix filtering.
- Configure maximum-prefix protection.
- Verify external route propagation and AS paths.

*BGP Internet Policy
- Configure the Internet router with loopback `8.8.8.8/32`.
- Originate `8.8.8.8/32` and `0.0.0.0/0` in BGP.
- Configure R30 as the preferred Internet exit.
- Configure R31 as the backup Internet exit.
- Use local preference to control outbound path selection.
- Advertise approved enterprise aggregate routes externally.
- Prevent unrestricted BGP-to-OSPF redistribution.
- Inject an OSPF default route from the BGP edge.
- Propagate the default route through OSPF and both EIGRP domains.

*End-to-End Validation
- Verify OSPF, EIGRP, iBGP, and eBGP neighbor relationships.
- Verify routing tables and protocol topology databases.
- Test connectivity between all OSPF client VLANs.
- Test connectivity between all EIGRP client VLANs.
- Test connectivity between OSPF and EIGRP clients.
- Test access from all client VLANs to `8.8.8.8`.
- Test reachability to R34 and R35 external loopbacks.
- Verify DHCP, VLAN, trunk, HSRP, IP SLA, and tracking states.
- Verify OSPF LSA types, summaries, filtering, and external routes.
- Verify EIGRP summaries, route tags, and redistribution.
- Verify BGP best-path selection, next-hop resolution, and prefix filtering.

*Failure and Convergence Testing
- Fail the R6–R10 primary static path.
- Verify floating static activation through R11.
- Verify synchronized HSRP gateway failover.
- Fail an OSPF backbone link and confirm reconvergence.
- Fail an EIGRP successor path and inspect the feasible successor.
- Fail the R30 primary Internet path.
- Verify BGP convergence to the R31 backup exit.
- Confirm that clients retain access to internal networks and `8.8.8.8`.
