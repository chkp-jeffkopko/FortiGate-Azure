---
title: "Initial Setup"
chapter: true
weight: 5
---

# Initial Setup (Credentials and Check Point Security Policy Setup)

### CloudFormation and Credentials

To get started with this workshop, you'll first need to gather some information from the CloudFormation stack that was used to build the Workshop Architecture.

1. Login to the AWS Console and navigate to the CloudFormation Console
2. Within the **Stacks** listing, deselect **View Nested** and choose the stack you created or the stack beginning with mod-module-1-###### 

    ![stack-nest](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/stack-nest.png)
![stack-choice](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/stack-choice.png)

4. Navigate to **Stack Outputs** and record all the credentials, keys, and values.  We will need these later in the workshop

    ![stack-output](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/stack-output.png)
![stack-output2](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/stack-output2.png)
### Check Point Security Policy Setup
Now, we need to login to the Check Point Web SmartConsole to setup an initial security policy for the workshop, which will allow us to test all traffic flows.

### <span style="color:red"> **SECURITY DISCLAIMER – this is a sample policy for this WORKSHOP ONLY and it NOT SUITABLE for a production environment!!!!** </span>

1. From the CloudFormation Output, locate the Public IP provided for the Check Point Security Management Server 
2. Login to the Check Point SmartConsole application via web console SmartClient: 
      - Username: **admin**    Password: **qwe123!**
      - Web SmartConsole at **https://publicIP/smartconsole**
   
      ![smartconsole-web](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/smartconsole-web.png)
      - R81.10 SmartConsole Windows application > Use Public IP from above 
        - If you need to install SmartConsole on Windows you can download [HERE](https://supportcenter.checkpoint.com/supportcenter/portal/role/supportcenterUser/page/default.psml/media-type/html?action=portlets.DCFileAction&eventSubmit_doGetdcdetails=&fileid=121500)
        
          ![smartconsole-login](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/smartconsole-login.png)
3. Once logged in, Verify that the CloudGuard Network Security Gateways have been discovered by the Security Management Server

    ![smartconsole-gwlisting](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/gwlisting.png)
4. Now we, can create an initial Check Point Security Policy.  Navigate to the Security Policies tab in SmartConsole
5. Create a new rule above the default Cleanup rule

   ![secpolicy-create](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-create.png)

    - The result should look like this…in this example we gave the rule the name **Allow Outbound**
   
   ![secpolicy-new1](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-new1.png)
   
6. Modify the new rule to allow the network **10.100.0.0/16** outbound access to **ANY**
   - Give your rule a name if preferred(not required)
   - Add a new network object that represents **10.100.0.0/16** to the Source field
   
     ![secpolicy-nwobject](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-nwobject.png)
     ![secpolicy-objectdetail](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-objectdetail.png)
   
   - Result should look like this:
     - Modify the rule so that Destination is **ANY**
     - Set Action to **Accept**
     - Set Track to **Log**
     
     ![secpolicy-newrule](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-newrule.png)

7. Using the same procedure as above, create another rule that allows Inbound traffic to the following networks:
   - 10.100.0.0/16
   - 10.0.15.0/24
   - 10.0.25.0/24
   - 10.0.36.0/24
   - Set the Cleanup Rule to **Log**
   
   ![secpolicy-allrules](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-allrules.png)

8. Install Policy to push the new security policy to the Security Gateways

![secpolicy-install](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-install.png)
![secpolicy-publishinstall](https://chkp-gwlb-ws01.s3.us-west-2.amazonaws.com/images/secpolicy-publishinstall.png)



    

{{% notice warning %}}
<p style='text-align: left;'>
The examples and sample code provided in this workshop are intended to be consumed as instructional content. These will help you understand how various Check Point and AWS services can be architected to build a solution while demonstrating best practices along the way. These examples are not intended for use in production environments.
</p>
{{% /notice %}}