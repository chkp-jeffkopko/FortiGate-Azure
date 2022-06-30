---
title: "Distributed Ingress & Egress"
chapter: true
weight: 5
---

# Distributed Ingress & Egress

### Flow Description & Diagram

| #	  | Hop description Outbound                                      |
|-----|---------------------------------------------------------------|
| 1   | 	Web-Tier to Internet 0/ --> GWLBe                            |
| 2   | 	GWLBe magic: GWLB (GENEVE) --> CGNS and return back to GWLBe |
| 3   | 	GWLBe 0/ --> IGW                                             |

| #	  | Hop description Inbound                                       |
|-----|---------------------------------------------------------------|
| 3   | 	IGW Ingress RT Web-Tier --> GWLB                             |
| 2   | 	GWLBe magic: GWLB (GENEVE) --> CGNS and return back to GWLBe |
| 1   | 	GWLBe Spoke 3 VPC--> Local                                   |

![dist](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/dist.png)

### Testing Procedure 

1. SSH to 11WebTierEC2PrivIp with ee-default-keypair 
   - Once logged in:
      1. ping 8.8.8.8 
      2. curl www.google.com 
2. Search for the internal IP of the EC2 Host in Web-Tier Spoke

![dist-log](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/dist-log.png)
