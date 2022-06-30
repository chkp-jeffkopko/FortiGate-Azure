---
title: "Distributed Subnet to Subnet"
chapter: true
weight: 4
---

# Distributed Subnet to Subnet

### Flow Description & Diagram

| #	   | Hop description                                             |
|------|-------------------------------------------------------------|
| 1    | 	SS01 to SS02  MSR --> GWLBe02                              |
| 2    | 	GWLBe magic: GWLB (GENEVE) --> CGNS and return back to GWLBe |
| 3    | 	GWLBe SpokeCIDR --> Local                                    |

![sub2sub](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/sub2sub.png)

### Testing Procedure 

1. Ssh to one of the Shared Services hosts (either NLB :8033 or :8044)
   1. Ping the other SharedServices host 
2. Realize the pings don’t work b/c MSR routes are not in place on the Shared Services Web Tier RTs 
   1. 10.100.4.0/22 Local CIDR needs a new Next Hop in RT for Sub01 & Sub02 
      1. Sub01 route should oppose the 10.100.5.0/24 VPCE 
      2. Sub02 route should oppose the Sub01 VPCE
      
        ![ssrt](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/ssRT.png)
        ![ss-route](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/ss-route.png)
      
3. Search for the internal IP of the EC2 Hosts in shared services Spoke

![sub2sub-log](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/sub2sub-log.png)
