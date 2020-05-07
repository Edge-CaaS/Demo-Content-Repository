---

copyright:

  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: organize resources, set up resource groups, best practice, resource group strategy

subcollection: resources

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}


# Best practices for organizing resources in a resource group
{: #bp_resourcegroups}

A resource group is a feature that you use to organize your account [resources](/docs/resources?topic=resources-resource) for access control and billing purposes. If you're familiar with using Cloud Foundry spaces, think of organizing resources in resource groups similarly to the way you organized resources in spaces. A resource is anything that can be created, managed, and contained within a resource group. Users aren't added to resource groups. Only resources can be added.

Currently, not all services support the use of {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) access control and the assignment to a resource group. IAM-enabled services prompt you to assign new service instances to a resource group when you create them from the catalog. Access to the resources within a resource group and the resource group itself are managed by IAM. By using IAM roles, you can provide users access to the resources that are organized within the resource groups. IAM roles can also provide the ability to view, edit, add new service instances to, or manage access to a resource group.

You can also find the list of IAM-enabled services when you assign access to resources from the Identity and Access UI by completing the following steps:
1. Go to **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select any user and click **Access policies**.
3. Select **Assign access** > **Assign access to resources**.
4. Using the **Services** menu, select the service that you want to assign. For all services that don't yet support by using IAM, you can continue to use Cloud Foundry orgs, spaces, and roles.
5. Click **Assign**.

Cloud Foundry orgs, spaces, and roles are distinctly separate from resource groups and IAM roles. A Cloud Foundry role can never grant access to resources within a resource group.
{: note}


## Setting up your resource groups
{: #setuprgs}

All users get a single resource group by default that can be renamed. Assign the editor or administrator role to all account management services to create resource groups. If you have a billable account, you can create more than one resource group for organizing your resources. By organizing resources in different resource groups, you can:

* Make assigning access to a set of resources easier by using a minimal number of policies
* View by resource group usage information for billing purposes

To create a new resource group, complete the following steps:

1. Go to **Manage** > **Account**.
2. Expand **Account resources** and select **Resource groups**.
3. Click **Create a resource group**.
4. Enter a name for your resource group.
5. Click **Add**.

## Adding resources to a resource group
{: #addingtorgs}

Services that are enabled by using IAM access control belong to a resource group instead of Cloud Foundry org or space. When you create a service instance for one of these services from the catalog, you're prompted to assign the instance to a resource group.

Your resource group selection at the time of creating the instance is final and can't be changed.
{: important}

As more services enable the assignment to resource groups and the use of IAM access control, you're notified on your resource list if you have existing Cloud Foundry service instances that are eligible for migration. By [migrating a service instance to a resource group](/docs/resources?topic=resources-migrate), you're creating a new linked instance in a resource group of your choice and the Cloud Foundry instance becomes an alias.


## Assigning access to resource groups and the resources within them
{: #assigning_access_rgs}

You provide access for users or groups of users that are organized in access groups by creating access policies. Access policies set a target, which is typically a service instance or all instances of a service in a resource group, and a role, which defines what type of access is allowed. There are two types of access policies that you need to assign as an account owner to enable the users in your account access to working with resources in resource groups:

* Access to resources within a resource group. Access can be granted to all resources in a group, or only selected services within a group.
* Access to enable the users to manage the group, meaning users can view the group, edit the name of the group, manage access for others to manage the group and most importantly to create and add new service instances to a group.

Review the following table for more information about the two types of access and what each assigned platform IAM role provides a user the ability to do:

|   | Actions for access to manage resource groups | Action on resources in resource groups |
|:-----------------|:--------------|:---------------|
| Viewer role  | View the group and its characteristics, but not the resources in the group | View resources in the group |
| Operator role | Not applicable | Not applicable |
| Editor role | View or edit name or other characteristics of the group, but not the resources in the group | Create, delete, edit, suspend, resume, view, bind, and manage access of resources in the resource group |
| Administrator role |  View, edit, or manage access for the group, but not the resources in the group | Create, delete, edit, suspend, resume, view, bind, and manage access of resources in the resource group |
{: row-headers}
{: class="comparison-table"}
{: caption="Table 1. Access for resource groups" caption-side="top"}
{: summary="This table has row and column headers. The row headers identify the selected role of an access policy. The column headers identify the type of policy whether its assigning access to manage a resource group or access to resources within a resource group. The remaining cells tell you the allowable actions based on the type of policy and the specific role that is selected as defined in the header rows."}

If you want a user to create a new service instance and add it to a resource group, the user must be assigned as a Viewer or higher on the resource group and Editor or above on the service.
{: tip}


## Sample access policies
{: #sample_policies}

Review the following sample access policies to help you determine how you might want to assign access to resources within your account that belong to resource groups.

1. A policy that grants the user the Platform Role “Administrator” on the {{site.data.keyword.Bluemix_notm}} Container Service across the entire account. A policy with these details allows the user access to all instances of this service and allows the user to create instances of the service in any resource group that the user has at least Viewer role on. Users with the Administrator role on any resource can also grant other users access to that resource.
2. A policy that grants the user the Platform Role “Viewer” on a resource group, but not its member resources. A policy with these details allows the user visibility to the resource group, which is required to create instances of any service in this resource group.
3. A policy that grants the user the Platform Role “Editor” on all resources in the resource group. A user with Editor role on a resource can edit or delete that resource.
4. A policy that grants the user the Platform Role “Administrator” on the entire account (all IAM-enabled services). A policy with these details allows the user to perform any platform actions on any resource in the entire account and also includes the ability to perform management actions on the account such as managing the resource groups in the account.

## Use case examples
{: #usecase_examples}

For each of these use cases, if you have a group of users that you want to all have the same level of access, add them to an [access group](/docs/iam?topic=iam-groups). By using access groups, you can use a minimal number of access policies since all members of the access group inherit any access that is assigned to the group.
{: tip}

<ol>
<li><p>I have a small account with only 10 users who all work together on a single project. Some of these users need to manage the account and assign other users access. Some of the users need to provision service instances, which will incur expenses. Other users are application developers who only need to use the service instances from their application components.</p>
<p>All of these users should be granted various roles on the account and the default resource group – there’s no need to create additional resource groups to separate resources or restrict some users from accessing some of the resources. Users can be granted the roles on the account and default resource group that are appropriate to their needs – Administrator on the account for users who need to manage the account and give others access, Editor on the default resource group and its members for users who need to provision service instances, and Writer or Reader on the resource group members for users who only need to use the service instances.</p>
</li>
<li><p>I have an account that includes three different teams who work on three projects. A few users are administrators and need the ability to create new resource groups and assign users access to resource groups. The remaining users only need access to the resource group associated with their project.</p>
<p>I would assign the administrators the Administrator role on all IAM-enabled services. I would assign the remaining users various roles on the resource group and resource group members that are associated with their project – resource group Editor for those who need to create instances, plus resource group member Reader or Writer for those who need to use instances.</p>
</li>
<li><p>I have an account with multiple resource groups. I have some users who are the administrators for Service A across my entire account and need access to all instances of that service as well as the ability to create instances, but these users don’t need access to any other resources in the account.</p>
<p>I would assign these users the Administrator role on Service A at the account level, as well as assigning them Viewer role for all resource groups in the account where they need to create instances.</p>
</li>
<li><p>I have a user in my account who only needs access to a specific resource in one service, for example the ability to write to a Bucket A in IBM Cloud Object Storage. This user shouldn’t see the resource groups in my account or access any other services or any other buckets in this instance of Cloud Object Storage.</p>
<p>I would give this user the Writer role on Bucket A in the specific instance of Cloud Object Storage. You can either grant this policy by using service-specific interfaces (the Cloud Object Storage UI, in this example) or the main Assign Access UI. The service-specific UI is recommended because it allows you to choose from a list of resources, while the Assign Access UI doesn't display resources past the service instance level and you would need to manually enter the CRN to assign policy to those resources.</p>
</li>
<li><p>I'm by using Cloud Foundry orgs and spaces today, but I'm going to start by using resource groups and access groups for my IAM-enabled services. Currently, my users and resources are organized in orgs for lines of business and the spaces are used for different projects within a line of business.</p>
<p>I would use resource groups to organize resources the same way I did with spaces thinking of each resource group as a project space. Then, I would set up separate access groups to give the necessary access to my users for the right project-level resource groups. Access can be given to all resources in a resource group or to even just a select group of resources within a resource group. So, you can set up each access group with different levels of access to resources within a resource group, which gives each group of users the access they require for working with the resources or the resource group itself.</p>
</li>
</ol>
