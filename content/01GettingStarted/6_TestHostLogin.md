---
title: "Test Host Login"
chapter: true
weight: 6
---

# Testing procedure

### Login to test instances 

The test instances are secured by inbound GWLB flows.  To access the instance, you will need to use the Load Balancer DNS names and EC2 Private keys provided in Cloudformation Output

 Use the DNS name above to login via SSH(using Putty or Terminal) with the Private key provided to the following EC2 instances…**be sure to note the special port being used for the DB and Shared Services instances**
   - DB instance:  dnsname:8022 
   - Shared Services instance #1:  dnsname:8033
   - Shared Services instance #2:  dnsname:8044
   - Web-Tier instance:  Public IP as defined by the CFT

#### Test Host & NLB Info
     
| VPC            | EC2 Host | AZ | SSH | Internal Subnet|
|----------------| --- | --- | --- | --- | 
| Database       |	database-EC2-***	| A	| NLB:8022 | 10.100.0.x/24|
| SharedServices |	shared-services-EC2-01-*** |	A |	NLB:8033 | 10.100.4.x/24|
| SharedServices |	shared-services-EC2-02-*** |	B |	NLB:8034 | 10.100.05x/24|
| Web Tier       |	Web-tier-ec2-***	| A |	Public IP from CFT | 10.100.8.x/24|

### ddd  


| NLB           | Listeners --> TargetGroup            | AZ      | Health Check | Internal Subnet                          |
|---------------|--------------------------------------|---------|--------------|------------------------------------------|
| InspectFirst  | 8022 -->  database-EC2-***           | A,B,C   | 111          | 10.0.15.0/24, 10.0.25.0/24, 10.0.35.0/24 |
| -             | 8033 --> shared-services-EC2-01-***  | -       | -            | -                                        | 
| -             | 8044 -->  shared-services-EC2-02-*** | -       | -            | -                                        |
| InspectSecond | 8022 -->  database-EC2-***           | A, B, C | 111          | 10.0.13.0/24, 10.0.23.0/24, 10.0.33.0/24 |
| -             | 8033 --> shared-services-EC2-01-**** | -       | -            | -                                        |
| -             | 8044 --> shared-services-EC2-02-**** | -       | -            | -                                        |

#### CloudGuard Instances

| VPC	      | EC2 Host	| AZ	| SSH	| Internal Subnet|
|-----------| --- | --- | --- | --- | 
| Security	 | Check-Point-Gateway-1	| A	| -	| 10.0.10.x/24|
| Security	 | Check-Point-Gateway-1	| B	| -	| 10.0.20.x/24 |
| Security	 | Check-Point-Gateway-1	| C	| -	| 10.0.30.x/24 |
| Security	 | Gwlb-management-server	| A	| Public IP from CFT	| 10.0.10.x/24|

### Test Internet(outbound) traffic

1. Validate that pings and web requests to the internet are successful from each instance above
   1. **ping 8.8.8.8**
   
    ![ping](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/ping.png)

   2. **curl www.google.com**

    ![curl](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/curl.png)


{{% notice warning %}}
<p style='text-align: left;'>
The examples and sample code provided in this workshop are intended to be consumed as instructional content. These will help you understand how various Check Point and AWS services can be architected to build a solution while demonstrating best practices along the way. These examples are not intended for use in production environments.
</p>
{{% /notice %}}