---
title: "Centralized Egress"
chapter: true
weight: 3
---

# Centralized Egress


### Flow Description & Diagram

| #	   | Hop description                                               |
|------|---------------------------------------------------------------|
| 1    | 	DB host to SS host, 0--> TGW                                 |
| 2    | 	TGW Attachment RT 0/ --> Sec VPC                             |
| 3    | 	Sec VPC TGW Attach RT 0/ --> GWLBe                           |
| 4    | 	GWLBe magic: GWLB (GENEVE) --> CGNS and return back to GWLBe |
| 5    | 	GWLBe RT Spoke--> TGW                                        |
| 6    | 	TGW Propagated RT --> SS Spoke/Host                          |
| 1    | 	SS Host to Internet 0/--> TGW                                |
| 2    | 	TGW Attachment RT 0/ --> Sec VPC                             |
| 3    | 	Sec VPC TGW Attach RT 0/ --> GWLBe                           |
| 4    | 	GWLBe magic: GWLB (GENEVE) --> CGNS and return back to GWLBe |
| 5    | 	GWLBe RT 0/ --> NATGW                                        |
| 6    | 	NATGW (egress NAT) 0/ --> IGW                                |
| 7    | 	IGW --> Internet host                                        |
| 8-13 | 	Reverse flow                                                 |

![centegress](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/cent-egress.png)

### Testing Procedure 

1. SSH to any of the hosts in Database or SharedServices Spoke (either NLB + :8022, :8033, :8044)
   1. Ping 8.8.8.8 
   2. Curl www.google.com
2. Search for the internal IP of the EC2 Host you’re sending the ping/curl from

![egress-log](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/egress-log.png)
