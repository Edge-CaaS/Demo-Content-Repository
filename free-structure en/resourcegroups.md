---



copyright:

  years: 2017, 2019
lastupdated: "2019-10-30"

keywords: resource group, account resources, users access to resource groups, create resource group

subcollection: resources

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:note: .note}

# Creating and managing resource groups
{: #rgs}

A resource group is a way for you to organize your account resources in customizable groupings so that you can quickly assign users access to more than one resource at a time. Any account resource that is managed by using {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) access control belongs to a resource group within your account. The only exception is Kubernetes, which doesn't prompt you for a resource group assignment, but access to the service is controlled by using IAM roles. Cloud Foundry services are assigned to orgs and spaces and can't be added to a resource group.

To start managing your resource groups, go to **Manage** &gt; **Account**. Expand **Account resources** and then select **Resource groups**. From there you can view your resource groups, add resources, rename them, manage access, and create new resource groups. For more information about working with resource groups, see [Best practices for organizing resources in resource groups](/docs/resources?topic=resources-bp_resourcegroups).


## Creating a resource group
{: #create_rgs}

If you have a Pay-As-You-Go or Subscription account, you can create multiple resource groups to easily manage quota and view billing usage for a set of resources. You can also group resources to make it easier for you to assign users access to more than one instance at a time. It's important to note that you can rename a resource group, but you can't delete a resource group after it's created.

You must be assigned an IAM policy with the Administrator role on All Account Management services to create additional resource groups. If you have a Lite account or 30-day trial, you can't create extra resource groups, but you can rename your default resource group.

Connections between a resource group and a Cloud Foundry org or space are restricted by your quota. See [What is an alias?](/docs/resources?topic=resources-connect_app#what_is_alias) for more information.
{: note}

1. Go to **Manage** &gt; **Account**. Expand **Account resources** and then select **Resource groups**.
2. Click **Create a resource group**.
3. Enter a name for your resource group.
4. Click **Add**.

## Adding resources to a resource group
{: #add_to_rgs}

Services that are managed with IAM belong to a resource group instead of Cloud Foundry org or space. When you create a service instance for one of these services from the catalog, you're prompted to assign the instance to a resource group. Your resource group selection at the time of creating the instance is final and can't be changed.

For users in your account to be able to create resources from the catalog and assign them to a resource group, they must be assigned two access policies:

* A policy with viewer role or higher on the resources group itself
* A policy with editor role or higher on the service in the account

## Viewing resources within resource groups
{: #view_rg_resources}

To easily view the resources that are contained within a resource group, filter by resource group from your resource list.

## Renaming a resource group
{: #rename_rgs}

Your first resource group is created and named `Default` for you. You can choose to update the name of this group or any other groups that you create.

1. Go to **Manage** &gt; **Account**. Expand **Account resources** and then select **Resource groups**.
2. Select **Rename** from the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu.
3. Enter a unique name and click **Save**.

## Managing resource groups and resources by using the {{site.data.keyword.Bluemix_notm}} CLI
{: #rgs_cli}

The {{site.data.keyword.Bluemix_notm}} CLI has multiple commands that support resource management. For more information, see [Working with resources and resource groups](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_resource#ibmcloud_commands_resource).

## Managing access to your resource groups
{: #rgs_manage_access}

Cloud IAM gives you the flexibility to provide fine-grained user access to resources in your account. You can use Cloud IAM to assign policies to users, which provide user access to all resources in a resource group, a single service type within a resource group, or an individual service instance in the account. Providing users access to resources within a resource group doesn't give them access to manage the resource group itself. You can set access for the ability to view, edit, and manage the actual resource group separately.

For more information, see [Managing access to resources](/docs/iam?topic=iam-iammanidaccser).
