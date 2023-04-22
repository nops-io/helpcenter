---
title: EventBridge Integration
keywords: reporting, integrations
tags: [agents_integrations]
sidebar: mydoc_sidebar
permalink: eventbridge-integration.html
folder: Integrations_and_Agents
---

EventBridge Integration makes it easier for nOps to automate workflows in the client’s environment.

1. TOC
{:toc}

# Integrating with EventBridge

Amazon EventBridge is a serverless event bus that makes it easier to build event-driven applications at scale using events generated from your applications, integrated Software-as-a-Service (SaaS) applications, and AWS services.

With EventBridge integration, nOps will be able to:

* Automate events based on nOps rules.
    
* Trigger automation to reduce the size of underutilized EC2 instances.
    
* Purchase or exchange RI automatically risk-free, if RI utilization is not optimized. To see the nOps list of risk-free commitments, go to **ShareSave Dashboard > List of Opportunities > List of Risk-Free Commitments**.
    
* Turn on and off the EC2 and RDS instances in a group with the Resource Scheduler.
    
* Trigger messages in multiple services other than the event messages.
    

To add nOps as an EventBridge partner, go to **AWS > Amazon EventBridge >** **Partner event sources**, and select **nOps** as one of the options to listen. Click on **Setup** and configure the options.

Once the EventBridge integration is set up, you can create event sources directly from the nOps application and deploy them to any account and region that you’ve connected to nOps.

To integrate your AWS EventBridge with nOps, log in to nOps and click **User Avatar > Organization Settings > Integrations > EventBridge**. In the _Event Bridge_ tab click **\+ Create EventBridge**.

On the **Create New Event Bridge** page:

1.  Create a name for this EventBridge.
    
2.  Select the AWS account you want to deploy the EventBridge into. In the AWS accounts list, you will only see the accounts that you onboard into nOps.
    
3.  Select the region you want to deploy the EventBridge into.
    
4.  Click **Create**.
    

When you click **Create**, nOps will deploy the EventBridge into your selected AWS account and region by creating an event bus in the selected AWS account.

To see the event bus that nOps just created, go to **AWS > Amazon EventBridge > Event buses > Custom event bus**.

The next step is to add an EventBridge target into Webhooks.

Adding EventBridge Target into nOps Webhooks
============================================

nOps has a Webhook for almost every cost optimization rule in the nOps environment.

When you create a Webhook, anytime an associated event is fired a message will be sent to either the endpoint you define or the EventBridge that you create.

To add an EventBridge target into nOps Webhooks, go to **User Avatar > Organization Settings > Integrations > Outgoing Webhooks**. In the _Outgoing Webhooks_ tab, click **\+ Create New Webhook**

In the **Create New Webhook** page:

1.  Create a **name** for the Webhook.
    
2.  Select an **Event**. Notice that the Event option has two fields, in the first field you need to select the event category, and in the second you need to select the actual event.
    
3.  Select an **Endpoint**, it can be either a simple Endpoint (Target URL) or an **EventBridge**. In the scope of this documentation, we are only going to select the EventBridge option. Selecting this option will send the Webhook to your EventBridge.
    
4.  Select an EventBridge from the list. The list consists of all EventBridges that you create in **nOps > Organization Settings > Integrations > EventBridge** tab.
    
5.  Click **Save**.
    

Launch Stack
============

When you create an EventBridge in nOps, nOps will automatically create an event bus in your selected AWS account. To see the event bus that nOps automatically created, go to **AWS > Amazon EventBridge > Event buses > Custom event bus**.

Once, you have configured the webhook, come back to the **nOps > Organization Settings > Integrations > EventBridge** tab and click **Launch Stack** against the EventBridge that you created:

* * *

**Note:** Before you click **Launch Stack**, make sure that you are logged into the AWS account that you used for the EventBridge. You also need to make sure that the account region is the same as the one you specified while creating the EventBridge.

* * *

When you click Launch Stack, you will be redirected to **AWS > CloudFormation > Stacks > Create stack.** All fields on the page will be prefilled.

![](/tmpimg/eb-stackset.png)

_You can follow the link highlighted above to see the CloudFormation template. To see the CloudFormation template right now, see [Scheduler CloudFormation Template](https://s3-us-west-2.amazonaws.com/nops-rules-lambda-sources/scheduler/scheduler.yml)._

Check the acknowledgment box, and click **Create stack**. The EventBridge is now ready and configured.

Add Key in KMS
==============

Allow Scheduler Lambda Function to use encrypted EBS with KMS to get **automatic Stack creation for EventBridge with a single click.** To enable, go to **nOps > Organization Settings > Integrations > EventBridge** and click **Add key in KMS.** You will be redirected to the **Create stack** page in AWS:

![](/tmpimg/eb-kms-stack.png)

* * *

**Note:** To check the template, go to the link highlighted above.

* * *

Simply enter your **KmsArn**, acknowledge, and click **Create stack**.