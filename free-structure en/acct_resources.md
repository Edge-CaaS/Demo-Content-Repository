---

copyright:

  years: 2018, 2019
lastupdated: "2019-08-29"

keywords: service instances, resource group, resource

subcollection: resources

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}


# What is a resource?
{: #resource}

A resource is anything that you can create from the catalog that is managed by and contained within a [resource group](/docs/resources?topic=resources-rgs). Some examples include apps, service instances, container clusters, storage volumes, and virtual servers. When you add a resource to your account from the catalog, you can assign the resource to a resource group. 

Access to resources is managed by using {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) access control. The services that support the use of [IAM roles for access](/docs/iam?topic=iam-userroles#iamusermanrol) and organization within a resource group are referred to as IAM-enabled services.

Services that are managed by using {{site.data.keyword.Bluemix_notm}} IAM and belong to a resource group have several benefits. Some of the benefits include the ability to connect to apps and services in any Cloud Foundry space, which means you can connect apps and services from different locations. Because resource groups are not scoped by location, you can provision apps and services from different locations into the same resource group. You can also use fine-grained access control down to an individual instance within a resource group.

Not all services support the use of resource groups and IAM currently. All service instances that are added to Cloud Foundry orgs and spaces when they're created from the catalog are distinctly different from IAM-enabled services. These services are called Cloud Foundry services. Cloud Foundry services have no connection to resource groups and use [Cloud Foundry roles for access management](/docs/iam?topic=iam-cfaccess#cfroles). As services enable support for IAM and resource groups, you're notified, you're notified about the ability to [migrate existing Cloud Foundry instances to a resource group](/docs/resources?topic=resources-migrate).
