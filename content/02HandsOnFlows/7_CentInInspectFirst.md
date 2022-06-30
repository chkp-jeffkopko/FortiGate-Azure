---
title: "Centralized Ingress (Inspection First)"
chapter: true
weight: 7
---

# Centralized Ingress (Inspection First)


### Flow Description & Diagram

| #	   | Hop description                                             |
|------|-------------------------------------------------------------|
1|	Internet to NLB:8022
2|	Ingress RT NLB --> GWLBe
3|	GWLBe magic: GWLB (GENEVE) --> CGNS and return back to GWLBe
4|	GWLBe Sec VPC --> Local (NLB)
5|	NLB (NAT) Spoke CIDR --> TGW --> Propagated Spokes
6-10|	Reverse Flow

![centingress-inspectbefore](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/centingress-inspectbefore.png)

### Testing Procedure 

1. SSH to the NLBInspectionFirst:8033 with ee-default-keypair 
2. Search for your Public IP address or the internal IP of the destination EC2 Host

![centingress-inspectbefore-log](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/centingress-inspectbefore-log.png)


