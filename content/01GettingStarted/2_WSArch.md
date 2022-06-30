---
title: "Workshop Logistics"
chapter: true
weight: 2
---

# Workshop Logistics

### Summary Steps

1. Browse to the AWS Event Engine Console and login with an email One-time-password 
   - Gmail is very fast…some corporate emails take a long time to get delivered 
2. Each participant will get their own AWS account with CGNS GWLB architecture deployed in it 
3. Login to the Check Point Smart Management console and set an initial policy to enable traffic flows, and then we’ll walk through each of the flows in this workshop together


### GWLB Reference Architecture Diagram

![ws-arch](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/CHKP-CGNS-GWLB-WorkshopArchitecture-Workshop+Final.drawio.png)

### Notes: 
- There are several different ways to organize your AWS Architecture to take advantage of CloudGuard Traffic inspection with AWS GWLB.  It is important to remember that as long as the traffic has a symmetrical routing path for forward and reverse flow, the architecture will work.
- This diagram may look complicated at first glance because it covers **ALL Traffic Flow Options**.  For each scenario, we'll highlight the components involved in that flow.  Depending on application requirements you may only require a subnet of the flows and accordingly a subnet of this Reference Architecture 
### Learning Objectives
- Learn the difference between Centralized and Decentralized GWLB & GWLBe Architectures
- Understand how each listed flow works
- Understand the differences and advantages/disadvntages of centralized ingress architecture options

{{% notice warning %}}
<p style='text-align: left;'>
The examples and sample code provided in this workshop are intended to be consumed as instructional content. These will help you understand how various Check Point and AWS services can be architected to build a solution while demonstrating best practices along the way. These examples are not intended for use in production environments.
</p>
{{% /notice %}}