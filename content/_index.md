---
title: "Fortinet FortiGate SDWAN"
chapter: true
weight: 1
---

# Fortinet FortiGate Workshop on Azure

### Welcome!

In this workshop you will learn how to deploy Fortinet's FortiGate NGFW on Azure in several different use cases 

### Learning Objectives
- Learn thing 1
- Learn thing 2
- Learn thing 3

# About TEChnical Recipes

[![Launch Button](https://raw.githubusercontent.com/FortinetSecDevOps/technical-recipe-azure-sdwan/main/images/rocket.jpg)</br>Launch Now](https://github.com/FortinetSecDevOps/technical-recipe-azure-sdwan/actions/workflows/lab-provision.yml)

> Clicking the ***Launch Now*** button opens the Github Actions tab, ***click*** the "Run Workflow" button on the *right-hand* side, enter your email address and ***click*** the lower "Run Workflow" button.

>The workflow starts the TEChnical Recipe environment provisioning process. An email is sent to the provided email address when the environment provisioning process is complete. The email contains environment details, including all required access credentials and links, as well as environment duration period. When the environment duration period has passed the environment and all resources will be removed.

***

TEChnical Recipes provide the learner with the opportunity to put into practice newly developed skills in an easy to launch environment that can be used for customer engagements.  At a minimum a TEChnical Recipe will include the following:

* A use case description
* An integrated lab and demo environment

  * Informational call-outs for key points to discuss or highlight to a customer
  * Questions that could be asked while giving the TEChnical Recipe as a demo
  * Points of value that relate the business value to the technical feature
* A reference architecture(s)

Optional components may be included for certain use cases

The TEChnical Recipe will not be a completely, self-contained learning experience for a single product.  A TEChnical Recipe will cover features and often multiple products where they relate to the use case of interest.  

Deployments will be automated for those tasks that are not salient to the learning or demonstration activity in the use case.  For example, for a TEChnical Recipe focused on Indicators of Compromise, the system may deploy a FortiGate and FortiAnalyzer with configurations for these systems.  However, the leaner will have to configure the Event Handlers for IOC setup.  

## Azure SDWAN TEChnical Recipe

Introduction:
As enterprises adopt the cloud as the new core for application hosting, remote sites require secure, reliable connectivity with an optimal user experience to access those cloud and SaaS applications.  In fact, cloud access is SD-WAN's primary use case for IaaS and SaaS-hosted services.  Fortinet's Cloud On-Ramp capabilities using SD-WAN are differentiated in the following ways: 

* Integrated Security and SD-WAN policy configuration and workflows
* Unique ability to provide scale up performance for higher bandwidth into cloud environments
* Decentralized orchestration for better survivability and easier deployment of SD-WAN overlays
* Single OS for consistent policy and overlay deployment on all software-defined networks (SDNs)

The purpose of this TEChnical Recipe is to familiarize the learner with routing, data-plane, and architectural concepts specific to the Azure Cloud environment.  Other TEChnical Recipes are available to cover SD-WAN feature deployment.

## TEChnical Recipe Main Objectives

* Deploy the SDWAN architecture using Terraform
* Configure Azure components
  * Load Balancer
  * VNET Peering
  * Route Server
  * vWAN and vWAN Hub
* Understand the different available architecture options

***
***

{{% notice warning %}}
<p style='text-align: left;'>
The examples and sample code provided in this workshop are intended to be consumed as instructional content. These will help you understand how various Fortinet and Azure services can be architected to build a solution while demonstrating best practices along the way. These examples are not intended for use in production environments without full understanding of how they operate.
</p>
{{% /notice %}}