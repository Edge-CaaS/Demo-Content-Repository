---

copyright:

  years: 2015, 2019

lastupdated: "2019-03-11"

keywords: troubleshooting services, troubleshooting resources, service problems, resource problems, error message

subcollection: resources

---


{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}


# Troubleshooting for services and resources
{: #services}

General problems with services and resources might include issues with deleting service instances, or trouble with service migration. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}

## Why can't I delete my service instance?
{: #ts_service_broker}
{: troubleshoot}

You might receive an error message if you try to delete a service instance that is already deleted from the cloud controller.
{:shortdesc}

When you try to delete a service instance, the following error message is displayed:
{: tsSymptoms}

`Gateway timeout`

This problem happens if the service instance is already deleted from the cloud controller.
{: tsCauses}

Create a service instance with the same service name, and bind it to your applications. Then, you can delete the service instance and the applications that use the service.   
{: tsResolve}

## Why was a service instance migrated to the wrong resource group? 
{: #ts_service_instance}
{: troubleshoot}

You might notice that a service instance was migrated to the wrong resource group and can't be reassigned. 
{:shortdesc}

You can't move resources between resource groups after they're assigned.
{: tsSymptoms}

You assigned the instance to the wrong resource group.  
{: tsCauses}

To correct this issue, you can try deleting the instance and creating a new one from the catalog. You can assign it to the correct resource group when you create the new instance.
{: tsResolve}

## Why can't I migrate an eligible Cloud Foundry service instance to a resource group?
{: #ts_migrate_instance}
{: troubleshoot}

As a user in the account, you're having trouble when you migrate an eligible instance. 
{:shortdesc}

You can't migrate an eligible instance. 
{: tsSymptoms}

If you're unable to migrate an eligible instance, you might not have the correct access. 
{: tsCauses}

Users must have specific access to migrate an instance. To check out what access you have, click **Manage** &gt; **Access (IAM)** from the console menu bar, and then click **Users**. Click your name and review your Access policies for assigned IAM roles and Cloud Foundry access to see which orgs you have access to and your assigned Cloud Foundry roles. 
{: tsResolve}

## Why can't I migrate all of my services?
{: #ts_service_migration}
{: troubleshoot}

Not all services are eligible for migration. 
{:shortdesc}

You can't migrate certain services. 
{: tsSymptoms}

You're trying to migrate services that aren't available to be added to resource groups and aren't managed by using Identity and Access Management (IAM). If a service is not eligible, there isn't an option for migration. 
{: tsCauses}

Check services to confirm they're eligible for migration. You receive a notification and see a ![Migrate this service instance to a resource group](images/migrate.svg "Migrate this service instance to a resource group") icon to tell if a service is eligible for migration.
{: tsResolve}
