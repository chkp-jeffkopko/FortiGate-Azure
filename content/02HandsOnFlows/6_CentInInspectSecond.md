---
title: "Centralized Ingress (Inspection Second)"
chapter: true
weight: 6
---

# Centralized Ingress (Inspection Second)

### Flow Description & Diagram

| #	   | Hop description                                             |
|------|-------------------------------------------------------------|
1|	Internet to NLB:8022
2|	NLB (NAT) SpokeCIDR --> GWLBe
3|	GWLBe magic: GWLB (GENEVE) --> CGNS and return back to GWLBe
4|	GWLbe Spoke CIDR --> TGW --> Propagated Spokes
5-8|	Reverse Flow

![centingress-inspectafter](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/centingress-inspectafter.png)

### Testing Procedure 

1. SSH to the NLBInspectionSecond:8022 with ee-default-keypair 
2. Search for the NLB IP (10.0.13.0/24) and internal IP of the EC2 Host in databse VPC (10.100.0.x)
   - Port 22 is the traffic you just generated 
   - Port 111 is health checks

![centingress-inspectafter-log](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/centingress-inspectafter-log.png)
