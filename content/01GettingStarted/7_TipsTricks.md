---
title: "Tips and tricks"
chapter: true
weight: 7
---

# Tips and Tricks

### Helpful Items 

- [AWS Blogs for GWLB ](https://aws.amazon.com/blogs/networking-and-content-delivery/category/networking-content-delivery/elastic-load-balancing/gateway-load-balancer/) 
- [Check Point SK for GWLB Architectures](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk174447&partition=Basic&product=CloudGuard)
- Repetitive testing tool for AL2 CLI: [Apache Benchmark](https://httpd.apache.org/docs/2.4/programs/ab.html) 
```commandline
yum install httpd-tools
for i in {1..100}; do ab -n 1000 -c 100 http://www.google.com; done
```

![ab](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/ab.png)

### Gateway Load Balancer Limitations & Considerations

1. Flow Stickiness 
   1. Currently GWLB flow hashing default 5 Tuple (TCP) and 4 Tuple (UDP)
      - Multi layered protocols may be hashed differently 
   2. Currently flows are sticky for their lifetime.  If an appliance crashes, the application must re-establish TCP flow 
2. FLOW idle timeouts 
   1. Currently fixed and unchangable 
      - 350s for TCP 
      - 120s for UDP 
3. No VPN 
   -  Currently Check Point does not support VPN with GWLB architectures 
4. Cost 
   - GWLB & GWLBe both have per hour per AZ costs & a Data charge


{{% notice warning %}}
<p style='text-align: left;'>
The examples and sample code provided in this workshop are intended to be consumed as instructional content. These will help you understand how various Check Point and AWS services can be architected to build a solution while demonstrating best practices along the way. These examples are not intended for use in production environments.
</p>
{{% /notice %}}