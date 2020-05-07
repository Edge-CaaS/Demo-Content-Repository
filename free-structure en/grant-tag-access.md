---

copyright:

  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: tagging, enabling others to tag, tagging permissions

subcollection: resources

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}


# Granting users access to tag resources
{: #access}

As the account owner, you might want to delegate some of the responsibility of tagging resources. To do that, you can grant access to other users in the account to add and remove tags from resources. For users on account to add tags to a resource, they must be assigned the appropriate access. Access to services that belong to a resource group are managed by {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) access policies, and access to services that belong to a Cloud Foundry org and space are managed by Cloud Foundry org and space roles.
{: shortdesc}

## Tagging permissions
{: #tagging-permissions}

Tags are visible to any user in an account. Once a resource is tagged, the tag is visible to all users who have read access to the resource. To add or remove a tag from a resource, certain access roles or permissions are required depending on the resource type. Check out the following table to understand what role is required for each resource type.


| Resource Type | Role |
|--------|---------------|
| IAM-enabled | Editor or Administrator on the resource |
| Cloud Foundry | Developer role on the space that the resource belongs to  |
| Classic infrastructure*| View hardware details permission or view virtual server details permission |
| Cloud Object Storage S3 on classic infrastructure | Storage manage permission |
{: caption="Table 1. Required roles for adding and removing tags" caption-side="top"}
{: summary="This is a simple data table. However, the asterisk indicates that you must read the qualifying note after this table."}

*The taggable resources in classic infrastructure are Virtual Guest, Virtual Dedicated Host, Network Application Delivery Controller, Gateway Member, Subnet, VLAN, and VLAN Firewall (Dedicated).


## Granting access for tagging IAM-enabled resources
{: #iam-managed}

Resources that belong to a resource group are managed by {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) access policies. Complete the following steps to assign the Editor role for a user to tag IAM-enabled resources:

  1. From the {{site.data.keyword.Bluemix_notm}} console, click **Manage > Access (IAM)**, and select **Users**.
  2. Click the name of the user that you are granting access to.
  3. Click **Access policies** > **Assign access**.
  4. Select the **Assign access to resources** option.
  5. From the list of services, select a specific service or **All Identity and Access enabled services**.
  6. From the list of platform access roles, select **Editor**.
  7. Click **Assign**.

## Granting access for tagging Cloud Foundry resources
{: #cf_tag_access}

Resources that belong to a Cloud Foundry org and space are managed by Cloud Foundry org and space roles. Complete the following steps to assign the Developer space role for a user to tag Cloud Foundry resources:

 1. Click **Manage > Access (IAM)**, and select **Users**.
2. Select the name for the user that you want to provide access to.
3. Click **Cloud Foundry access**.
4. Click **Assign Organization**.
5. Expand and select the `Organization` with the service instance that you want to provide the user access to.
6. Select the region.
7. Select the **Developer** space role.
8. Click **Save role**.

## Granting access for tagging classic infrastructure resources
{: #classic-infra}

Complete the following steps to assign the Manager service access role for a user to tag classic infrastructure services:

  1. Click **Manage > Access (IAM)**, and select **Users**.
  2. Click the name of the user that you are granting access to.
  3. Click **Classic infrastructure**
  4. From the **Permissions** tab, expand the **Devices** category.
  5. Select **View Hardware Details** and **View Virtual Server Details**. If you need to assign access to Cloud Object Storage S3, assign the **Storage manage** permission.
  6. Click **Save**.
  7. Click the **Devices** tab.
  8. Select **All bare metal servers** or **All virtual servers** depending on the resource you would like to tag.
