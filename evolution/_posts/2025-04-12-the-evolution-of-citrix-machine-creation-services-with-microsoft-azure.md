---
layout: post
title: The Evolution of Citrix Machine Creation Services with Microsoft Azure
permalink: "/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/"
categories: [Citrix, UPM, Profiles, Windows, CVAD, Cloud, Azure, evolution]
redirect_from: 
    - /2021/07/08/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure
    - /2021/07/08/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/
    - /2021/07/08/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/AMP
    - /2021/07/08/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/AMP/
description: Tracking the progress of Citrix MCS and Microsoft Azure
image:
  path: /assets/img/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
related_posts:
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-profile-management.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-wem-service.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-wem.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-workspace.md
---

<!--excerpt-->

-  Table of Contents
{:toc .large-only}

There is a lot of constant improvement being executed by the MCS team at Citrix, the release cadence is impressive and the feature enhancements significant. I spend a lot of time in Microsoft Azure with Citrix Cloud with a lot of happy customers. I thought it would be worthwhile keeping a rolling tally of new features with MCS and how it relates to Azure, so that we don't lose sight of how much value add is provided.

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

It is important to be across the options when designing your delivery platform on Azure, many changes have a direct implication on the ongoing operational costs associated with running workloads on/in Azure, as well as availability and global deployment options. Looking at what we have now, vs what was available 12 months ago, many designs and deployments would look remarkably different.

## March 2025

### [Support for creating Azure AD joined and Microsoft Intune enrolled catalogs with prepared images](https://docs.citrix.com/en-us/citrix-daas/install-configure/identity-pools-of-different-machine-identity-join-types/identity-pool-aad-joined-machine-identity#use-powershell)

With this feature, you can now use prepared images to create Azure Active Directory joined and Microsoft Intune enrolled catalogs using Studio and PowerShell commands. This feature is applicable to single and multi-session persistent and non-persistent type MCS catalogs. This implementation significantly reduces the storage and time costs, and simplifies the VM deployment and image update process.

## February 2025

### [Support for provisioning data disk on Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#provision-data-disk)

ou can now create and assign a persistent data disk to an MCS created persistent or non-persistent VM of an MCS machine catalog in Azure. The data disk is used for storage of persistent data like event logs, security traces, and application data.

The data disk must be provisioned from the master image. The properties such as storage type, encryption settings, zones are derived from custom properties or from the OS disk template if the properties are not specified in the custom properties.

## January 2025

### [Filter master images based on hosting unit regions](https://docs.citrix.com/en-us/citrix-daas/install-configure/create-prepared-image-machine-catalogs-azure#create-a-machine-catalog-from-the-machine-catalogs-node)

During machine catalog creation for the Azure platform, Studio can now filter out and exclude master images that belong to different regions other than the hosting unit’s region. This ensures that only images from the same region as the hosting unit are available for selection.

### [MCSIO with only disk cache is no longer supported](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create#configure-cache-for-temporary-data)

The option to configure MCSIO with only disk cache (without memory cache) has been removed across all hypervisor and cloud service environments. When creating machine catalogs with the MCSIO enabled, you must now set a non-zero memory cache size. In addition, you can't edit catalogs configured with only a disk cache until you set a memory cache size.

## December 2024

### [New permission for orphaned resource detection in Citrix DaaS](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections#retrieve-a-list-of-orphaned-resources)

 Previously, only **Full Administrator** or **Cloud Administrator** roles could perform orphaned resource detection. With the introduction of a **Use Host Connection to Detect Orphaned Resources in Hypervisor** permission to the Hosts category, any roles assigned with this permission can now detect orphaned resources.

### [Autoscale powers on hibernated VMs](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#december-2024)

With this feature, in Azure, autoscale can power on hibernated multi-session Remote Desktop Services (RDS) and shared single session VMs with no sessions on it during peak time. The VMs can be of MCS and non-MCS machine catalogs.

### [Support for NVMe-only SKUs in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#create-a-catalog-using-a-service-offering-that-supports-both-scsi-and-nvme)

Previously, MCS supported only SCSI storage controller type. With this feature, MCS also supports the NVMe storage controller type to support the new VM SKUs on Azure. For information on NVMe, see the Microsoft documentation [General FAQ for NVMe](https://learn.microsoft.com/en-us/azure/virtual-machines/enable-nvme-faqs). For information on creating an MCS machine catalog using a service offering that:

-  supports both SCSI and NVMe
-  supports only NVMe

## November 2024

### [Image management is now Generally Available](https://docs.citrix.com/en-us/citrix-daas/install-configure/image-management)

Image management functionality is now generally available for Azure and VMware virtualization environments. Also, the Images node now allows you to share image versions across hosting units within the same hosting connection in Azure. This implementation ensures consistency and uniformity of images across different host units, enhancing deployment flexibility and operational efficiency. You can also use PowerShell commands.

### [Support to configure secondary VMs scale up or scale down list for MCS-created catalogs on Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure)

Web Studio now enables the administrators to define secondary VMs to scale up and scale down the MCS-created catalogs on Azure. Based on the usage of CPU and memory resources, if the CPU or memory usage exceeds a certain threshold, the system will automatically use the secondary VMs to handle the load. Alternatively, if the usage falls below a certain level, the system will automatically shut down some VMs to conserve resources.

### [Studio: Support for provisioning persistent VMs on Windows Server OS using Full Copy Clone](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create#select-a-desktop-experience)

Studio now supports provisioning persistent VMs on Windows Server OS using the Full Copy Clone approach. This approach improves data recovery and migration capabilities and can help reduce IOPS after machines are created.

## October 2024

### [Enroll persistent machines of hybrid Azure AD joined type into Microsoft Intune for co-management](https://docs.citrix.com/en-us/citrix-daas/install-configure/create-machine-identities-joined-catalogs/create-microsoft-intune-enabled-catalogs#create-co-management-enabled-catalogs)

During machine catalog creation, you can now enroll persistent machines of the hybrid Azure AD joined type into Microsoft Intune (with Configuration Manager) for co-management. This feature applies to single and multi-session, persistent VMs and on all hypervisors and cloud services, ensuring uniform device management across your infrastructure. This feature is applicable only to VDA version `2407 and later`.

### [Service accounts for machine identity management](https://docs.citrix.com/en-us/citrix-daas/install-configure/service-accounts)

To simplify and enhance the management of machine identities including computer accounts in on-premises Active Directory, Azure AD joined devices and Intune enrolled devices, MCS has a new mechanism for managing on-premises Active Directory and Azure Active Directory (Azure AD) identity service accounts.

-  For Active Directory, there is a new Service Account mechanism where a saved Service Account can be used.
-  For Azure AD (EntraID), Azure AD identity Service Principal Names (SPN) can be used.

### [Export a machine profile to an ARM template spec](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#export-a-machine-profile-to-a-json-file)

You can now export the machine profile used by a catalog into an ARM template spec. Now you can easily reuse an existing machine profile as a template and modify it for future provisioning needs.

### [Reboot schedules for hibernated VMs](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#october-2024)

Ticks the box for this list as MCS can provision Hibernate enabled VMs in Azure, this new capability is a direct follow on from the provision phase.

You can configure reboot schedules for hibernated VMs if the Delivery Group is hibernation enabled. In the reboot cycle, the VMs are resumed and, then shut down. The reboot schedule can be set as weekly, daily, monthly, and once. You can configure multiple schedules. Note that VMs resuming from hibernation can take few mins.

### [Support for creating a host connection using Azure Managed Identity](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager#create-a-host-connection-using-azure-managed-identity)

Goodbye Service Principals. Hello managed Identities.

You can create a host connection to Microsoft Azure Resource Manager using Azure Managed Identity. Currently, you can create the host connection using only PowerShell commands.

### [Support for Boot Integrity Monitoring](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#boot-integrity-monitoring)

You can enable Boot Integrity Monitoring for MCS machine catalog VMs (persistent and non-persistent VMs) using a machine profile (VM or template spec) that has GuestAttestation extension installed. Boot Integrity Monitoring is only supported for Trusted Launch and Confidential VMs that use Secure Boot and virtual Trusted Platform Module(vTPM).

If your VM has Secure Boot and vTPM enabled, and GuestAttestation extension installed, Microsoft Defender for Cloud can remotely validate that your VM boots correctly.

### [Filter empty resource groups](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager#filter-empty-resource-groups)

You can filter out empty resource groups while selecting a master image, machine profile, or prepared image during the machine catalog creation. You can do this using a PowerShell command `Get-HypInventoryItem`.

### [Support for creating preformatted WBC disk catalogs in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#create-a-preformatted-wbc-disk-catalog)

you are able to utilize a preformatted WBC disk for newly created catalogs. This action significantly reduces the time required to start each VM of an MCS or MCS provisioned Citrix Provisioning machine catalog. To implement this functionality, create an Azure catalog with WBC enabled and include an additional custom property `PreformatWriteBackCache` as `True`.

You can update an existing catalog using the `Set-ProvScheme` command to update the WBC disk size.

This feature is compatible with the Image management workflow where MCS separates the mastering phase from the overall provisioning workflow. 

### [Delete WBC disk at shutdown for MCS provisioned Citrix Provisioning catalogs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#delete-wbc-disk-at-shutdown-for-mcs-provisioned-citrix-provisioning-catalogs)

Some more PVS by MCS love. You now have the option to delete the write-back cache (WBC) disk after you shut down the VM for MCS provisioned Citrix Provisioning catalogs in Azure. This helps to save cost when you do not need a persistent WBC disk. This feature is also applicable to an existing catalog.

### [Support for creating a network security group](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager#use-a-pre-created-network-security-group)

You can now create a Deny-All network security group for image preparation instead of requesting Citrix to create and modify a network security group automatically. Edit the custom properties of the hosting unit using a PowerShell command `Set-Item` to include the parameter `NsgForPreparation` to provide the Deny-All network security group.

### [Support for using Azure temporary disk as a WBC disk for existing MCS machine catalogs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure#use-temporary-disk-as-wbc-disk-for-existing-catalogs)

You can now use Azure Temporary disk as a write-back cache (WBC) disk for existing MCS machine catalogs and existing VMs. Use the `Set-ProvScheme` PowerShell command to update existing catalogs. This implementation saves storage cost because Azure temporary disk is free of charge (nothing is really `free` in Azure, you are paying for an instance type that comes with temp SSD - not all do.) 

## September 2024

### [Validate permissions on host connection in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager#validate-permissions-on-host-connection)

Previously, in Azure environments, you could validate only the host connection credentials (client id or application id) used to create a connection to Azure.

With this feature, you can:

-  Get the list of permissions assigned to your host connection credential
-  Get the list of operations that can be performed with the permissions assigned 
-  Information on the permissions required
-  Information on how to add the desired permissions

This helps to troubleshoot and get necessary permissions ahead of time.

### [Support for creating Azure AD joined catalogs enrolled in Microsoft Intune for non-persistent VMs](https://docs.citrix.com/en-us/citrix-daas/install-configure/create-machine-identities-joined-catalogs/create-microsoft-intune-enabled-catalogs)

You can now create Azure AD joined catalogs enrolled in Microsoft Intune for non-persistent single-session and multi-session. 

This feature is applicable only to VDA version `2407 and later`.

## August 2024

### [Persist BDM storage type as standard SSD in Azure](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#august-2024)

PVS in an MCS blog... but its PVS by MCS so you make the list.

For Citrix Provisioning catalogs that are created using MCS in Azure, the BDM storage type is configured as standard SSD by default. This option is considered as a cost-saving measure and cannot be modified.

### [Convert legacy MCS catalogs to machine profile-based catalogs in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure#convert-legacy-mcs-catalogs-in-azure-to-machine-profile-based-catalogs)

you can now convert non-machine profile-based machine catalogs to machine profile-based machine catalogs in Full Configuration in Azure environments. This new capability allows you to upgrade legacy MCS catalogs to the recommended machine profile-based catalogs.

Moving to machine profile based Catalog allows for enhanced capability and flexibility in Azure deployments.

### [Support for backup VM sizes configuration](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create#configure-backup-vm-sizes)

Another feature request addressed by Citrix. For those who have been through situations where machines cannot be provisioned/powered on due to a lack of capacity, this feature is long awaited.

Azure can run out of capacity for a specific VM size. If you use Azure Spot VMs (surely no one does this in prod...), then the VMs are evicted at any time based on Azure capacity needs. In the case of insufficient capacity on Azure or a Spot VM power-on failure, MCS now falls back on the backup VM sizes.

You can provide a list of backup VM sizes using a custom property `BackupVmConfiguration`. MCS tries to fall back on the VM sizes in the order that is specified in the list. If MCS fails to fall back to any instance in the list of backup VM sizes provided, you get an error message. This feature is supported only for a catalog that uses a machine profile and is applicable to both persistent and non-persistent MCS machine catalogs.

## July 2024

### [Configure required Azure host connection permissions](https://github.com/citrix/citrix-mcs-sdk-samples/tree/main/Azure/Hosting%20Connection/Role)

Previously, the host connection test validated whether the credential is good to connect to the hypervisor. The test did not perform validation on actual permissions that you might need to perform relevant MCS operations such as power management, VM creation, and more.

You can now easily configure all the minimum permissions required for a service principal or user account in Azure tied to a host connection to perform all MCS operations using an ARM template. This ARM template automates the following:

-  Creation of an Azure Role with minimal permissions necessary for operations.
-  Assignment of this role to an existing Azure Service Principal at the subscription level.

You can deploy this ARM template using the Azure Portal or PowerShell commands.

### [Increased limit of replicas per image version in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#configure-azure-compute-gallery)

Azure has increased the maximum count of replicas for a gallery image single version to 100. With this limit increase, you can now set the property `SharedImageGalleryReplicaMaximum` to a maximum value of 100 while creating an MCS machine catalog using the Azure Compute Gallery image.

### [Managing prepared images with the Images node](https://docs.citrix.com/en-us/citrix-daas/install-configure/image-management)

An **Images** node is now available in Web Studio, letting you prepare an MCS image (prepared image) from a single source image and deploy it across various MCS machine catalogs. This node facilitates complete image lifecycle management, enabling you to create image definitions, versions, and catalogs.

Images prepared using this node can only be used in Azure and VMware environments. Alternatively, you can also create catalogs with prepared images using the **Machine Catalogs** node.

### [Support for Azure's nested virtualization](https://azure.microsoft.com/en-us/blog/nested-virtualization-in-azure/)

With this feature, if you configure the master VM with nested virtualization enabled, then all VMs in the MCS machine catalog created using that master VM have nested virtualization enabled. This feature is applicable to both persistent and non-persistent VMs. You can update an existing MCS machine catalog and existing VMs to have nested virtualization through image update.

Currently, only Dv3 and Ev3 VM sizes support nested virtualization.

### [Support for on-demand capacity reservation in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#create-a-catalog-of-on-demand-capacity-reservation-vms)

You can create an MCS machine catalog of Azure VMs with on-demand capacity reservation using a machine profile (VM or template spec). This feature is applicable to persistent and non-persistent machine catalogs. You can update an existing machine catalog and existing VMs to have or remove on-demand capacity reservations.

For more information on Azure on-demand capacity reservation, see the [Microsoft documentation On-demand Capacity Reservation](https://learn.microsoft.com/en-us/azure/virtual-machines/capacity-reservation-overview)

### [Option to update write-back cache settings post creation for Machine Creation Service (MCS) catalogs](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#july-2024)

You now have the option to update the memory and disk cache size of the write-back cache, when Machine Creation Service (MCS) Storage Optimization (MCSIO) is enabled, after the catalog is created for MCS catalogs.

### [Option for manually managing the service principal's role for Azure AD joined device management](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager#enable-azure-ad-joined-device-management)

Citrix enhanced the **Enable Azure AD joined device management option** for greater flexibility. Previously, you had to sign in to Azure and allow Citrix to assign the **Cloud Device Administrator** role to the connection's service principal on your behalf. This design worked only when your Azure account had permission to grant this role.

With this enhancement, if your Azure account doesn't have the required permission, you can now choose Don't sign in to Azure when enabling Azure AD joined device management. This allows you to manually assign the role to the connection's service principal in the Azure portal.

## June 2024

### [Simplified subnet updates for machine catalogs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#edit-a-catalog)

Previously, to change the subnet settings of a machine catalog, you had to delete and recreate it. With this feature, you can now achieve the same functionality by editing the catalog. Note that only new virtual machines created under the catalog will be on the newly associated subnets. This enhancement reduces the need for catalog deletion and associated tasks.

### [Support for creating resource groups during Azure catalog creation (for PVS)](https://docs.citrix.com/en-us/provisioning/2402-ltsr/configure/citrix-provisioning-catalog-in-studio#create-a-citrix-provisioning-catalog-using-the-citrix-studio-interface)

I know, it's not MCS, but it still falls under "Provisioning" so I am adding it.

Previously, when creating Azure catalogs using Full Configuration, you had to create the resource groups using PowerShell commands. With this feature, you can now seamlessly create a resource group as part of catalog creation in Web Studio. This enhancement simplifies the overall creation workflow.

## May 2024

### [Azure GPU hibernation support (Preview)](https://learn.microsoft.com/en-us/azure/virtual-machines/hibernate-resume#supported-vm-sizes)

You now have the option to support hibernation for Azure machine SKUs that support GPU

### [Support for creating and managing Azure confidential VMs using Full Configuration](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#azure-confidential-vms-preview)

Azure confidential VMs provide a strong, hardware-enforced boundary to help meet your security needs. With the Full Configuration user interface, you can now create and manage confidential VMs on Azure

### [Cost optimization [Preview]](https://docs.citrix.com/en-us/citrix-daas/monitor/cost-optimization)

I am going to dump this one here as even though it's not provisioning, there is an obvious dotted line towards it, and this feature is really, really cool.

## April 2024

### [Change disk encryption in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure#change-disk-encryption)

You can now change the disk encryption in Azure virtualization environments. You can do the following:

-  Create an MCS machine catalog with a disk encryption set (DES) that is different from the master image DES.
-  Change the disk encryption type from one DES key to another DES key of an existing MCS machine catalog and existing VMs.
-  Update an MCS machine catalog and VM that was not previously CMEK enabled to have customer-managed encryption key (CMEK) encryption (DES), disk encryption at host, or double encryption.
-  Update an existing MCS machine catalog and VM to be non-encrypted that was previously encrypted.
-  Enable disk encryption with private endpoint (an MCS machine catalog that used a host connection enabled with `ProxyHypervisorTrafficThroughConnector`).

### [Support for modifying the page file settings](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#modify-page-file-settings)

You can now modify the page file settings of the newly added VMs to an existing catalog without updating the master image. This is currently an Azure only feature.

To modify the page file settings, you need `VDA version 2311` or later. You can modify the page file settings using the PowerShell commands.

## March 2024

### [Simplified subnet updates for machine catalogs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#edit-a-catalog)

Previously, to change the subnet settings of a machine catalog, you had to delete and recreate it. You can now achieve the same functionality by editing the catalog. Note that only **new** virtual machines created under the catalog will be on the newly associated subnets. This enhancement reduces the need for catalog deletion and associated tasks

### [Support for updating more Azure VM settings using machine profiles (Full Configuration)](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#march-2024)

With Full Configuration, you can now update a wider range of settings for MCS-provisioned Azure VMs through machine profiles, which include:

-  Machine size
-  License type
-  Availability Zone
-  Dedicated Host Group ID

After you update the machine profile, Full Configuration compares the current settings with the new ones. If differences exist, you'll be prompted to confirm which to apply. This design ensures transparent and efficient VM setting updates.

### [Support for Changing write-back cache properties for MCS-provisioned Azure VMs (Full Configuration)](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#march-2024)

For Azure VMs provisioned using Machine Creation Services (MCS), you can now change their write-back cache (WBC) properties using Full Configuration, such as **Disk cache size**, **Memory cache size,** and **Enable storage cost saving**. 

In addition, when you select a new machine size or machine profile for those VMs, Full Configuration validates WBC settings to prevent conflicts, such as exceeding the memory limit of the new selection. If conflicts occur, you'll be prompted to re-configure WBC settings.

## February 2024

### [Image information on the Machine Catalogs page](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#february-2024)

Another example of the product teams listening to requests. You can now view the following image information through the **Template Properties** of the machine catalog:

-  Operating system
-  Machine identity service
-  Machine Creation Service storage
-  Filepath for `pagefile.sys` for Azure deployments

This enhancement provides better clarity on the image information and ensures that the administrators have all the information about the machine catalog in one place.

### [Use Disk Encryption Set ID (DES ID) of the master image to encrypt all the disks of catalog VMs](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#february-2024)

 In Azure environments, previously, the Disk Encryption Set ID (DES ID) of an MCS machine catalog was derived from a machine profile or custom properties. With this feature, a machine catalog can also derive the DES ID from the master image to encrypt all the disks of the VMS in a catalog.

### [Update MCS tags to detect orphaned resources after migration](https://support.citrix.com/article/CTX573477/efficiently-manage-orphaned-azure-resources-with-citrix)

When you migrate from on-premises configuration to a cloud site, or from your cloud configuration to another cloud site, the orphaned resources aren't detected correctly because of the old site id tag. With this feature, using a PowerShell command, you can update the MCS site id tags of a persistent catalog, after migration so that orphaned resources can be detected correctly. Currently, this feature is applicable to Azure.

### [Validate configuration before creating an MCS machine catalog](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create#validate-configuration-before-creating-an-mcs-machine-catalog)

With this feature, you can now validate configuration settings before creating an MCS machine catalog using the parameter `-validate` in `New-ProvScheme` command. After you run this PowerShell command with the parameter, you get an appropriate error message if there's an incorrect parameter used or a parameter has conflict with another parameter. You can then use the error message to resolve the issue and successfully create an MCS machine catalog using PowerShell.

Currently, this feature is applicable to Azure, GCP, and VMware virtualization environments.

For anyone who has played with automating Catalog creations, this is a welcome feature.

### [Azure support for using spot VMs with MCS](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#create-a-catalog-using-azure-spot-vms)

Azure Spot VMs allow you to take advantage of Azure's unused computing capacity at significant cost savings. However, due to its eviction policy, Azure Spot VMs are good for only some **non-critical** applications and desktops.

With this feature, you can create an MCS machine catalog of Azure Spot VMs using a machine profile (VM or template spec). You can update an existing catalog to have Azure Spot VMs as the newly created VMs or switch to have standard Azure VMs. You can also update existing VMs to be Azure Spot VMs.

Be careful with Spot VMs.

### [Support for capturing diagnostic settings from a machine profile](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#capture-diagnostic-settings-on-vms-and-nics-from-a-machine-profile)

In Azure environments, MCS now supports capturing of diagnostic settings on VMs and NICs from a machine profile while creating or updating an MCS machine catalog, or updating existing VMs. With this implementation, the diagnostic data can be seamlessly transmitted to designated Azure destination endpoints, such as Log Analytics workspaces or Event Hubs, for in-depth analysis and visualization.

### [MCS support for managing different versions of a machine catalog](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#manage-versions-of-a-machine-catalog)

With this feature, you can manage the configuration versions of a machine catalog using PowerShell commands. Each configuration change using the `Set-ProvScheme` results in a new configuration version. You can:

-  See the list of versions.
-  Use any previous version to update a machine catalog.
-  Manually delete a version if it isn't used by a VM.
-  Change the number of maximum versions to be retained by a machine catalog.

## January 2024

### [Azure catalogs support for inheriting DES settings from master images (Full Configuration)](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#create-a-machine-catalog-using-an-azure-resource-manager-image-in-the-full-configuration-interface)

 Previously, Full Configuration set the Azure catalogs' default DES settings only based on **machine profiles**. With this enhancement, in the following cases, Full Configuration sets an Azure catalog's default DES settings directly based on the **master image**:

-  If a machine profile isn't selected
-  If the profile specifies a Platform Managed Key (PMK)

## November 2023

### [Support for creating Citrix Provisioning catalogs using Full Configuration interface](https://docs.citrix.com/en-us/provisioning/current-release/configure/citrix-provisioning-catalog-in-studio)

You can now create a Citrix Provisioning catalog using the Full Configuration interface and PowerShell (Drive the bus from Studio rather than the PVS Setup Wizard). This implementation provides the following advantages:

-  A single unified console to manage both MCS and Citrix Provisioning catalogs.
-  Have new features for Citrix Provisioning catalogs, such as identity management solutions, on-demand provisioning, and so on.

Currently, this feature is available **only** for Azure workloads. This feature is pretty cool and works well, but currently only supports initial creation of a Catalog. You must use existing processed for image updates etc via the PVS methdology.

### [A single option to retain VM and system disk during power cycles](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#november-2023)

Starting an existing VM on Azure is now faster than launching a new one, making it a more efficient choice to retain VMs across power cycles. In response to this change, Citrix has combined the options **Retain VMs across power cycles** and **Retain system disk during power cycles** into a single option **Retain VM and system disk during power cycles**. This means that when you select this option to reduce VM restart times by retaining system disks, your VMs are retained as well.

### [New capability in Full Configuration to filter machine sizes based on Encryption at Host property in machine profiles (Azure VMs specific)](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#november-2023)

Once you choose a machine profile with Encryption at Host enabled during Azure machine catalog creation or management, only machine sizes that support this feature are displayed.

### [Image information on the Machine Catalogs page](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#november-2023)

You can now view the following image information through the Template Properties of the machine catalog:

-  Operating system
-  Machine identity service
-  Machine Creation Service storage
-  Filepath for pagefile.sys for Azure deployments.

This enhancement provides better clarity on the image information and ensures that the administrators have all the information about the machine catalog in one place.

### [Ignore orphaned resources with specific tag](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#november-2023)

In Azure environments, a customer-managed resource tagged with all Citrix tags is detected as an orphaned resource. With this feature, if you add another tag `CitrixDetectIgnore` with value as true to that resource, then the resource is ignored while detecting orphaned resources.

### [Solution for SCCM duplicated GUID issue](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#november-2023)

After creating multiple VMs using MCS, the System Center Configuration Manager (SCCM) displayed only one VM on its console because of duplicated GUIDs. This issue is now resolved by adding a step in the image preparation. This step deletes the existing certificates and GUID information within master image. The step is enabled by default.

Not azure specific, but will impact Azure provisioned VMs.

### [Repair the identity information of active computer accounts](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#repair-the-identity-information-of-active-computer-accounts)

With this feature, you can reset the identity information of active computer accounts that have identity-related problems. You can choose to reset only the machine password and trust keys, or reset all configuration of the identity disk. This implementation is applicable to both persistent and non-persistent machine catalogs. Currently, the feature is supported only for Azure and VMware virtualization environments.

### [Get encryption at host information associated with a machine profile](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#retrieve-encryption-at-host-information-from-a-machine-profile)

In Azure environments, with this feature, you can now know whether encryption at host is enabled for a machine profile input (VM or template spec) using PowerShell commands.

### [Support for Azure confidential VMs (Preview)](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#azure-confidential-vms-preview)

Azure confidential computing VMs ensures that your virtual desktop is encrypted in memory and protected in use. With this feature, you can now use MCS to create a catalog with Azure confidential VMs. You must use the machine profile workflow to create such a catalog. You can use both VM and ARM template spec as a machine profile input.

### [Ability to change memory and disk cache size](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#change-cache-configuration-on-an-existing-machine-catalog)

With this feature, you can now change the memory and disk cache size of the Write-back cache (when MCSIO is enabled) using a PowerShell command without creating a new machine catalog. This implementation helps you to have the optimized cache configuration that is suitable for your business needs. This feature is applicable to:

-  GCP and Microsoft Azure environments, and
-  a non-persistent catalog with MCSIO enabled

### [Support for creating a customer-managed encryption key enabled catalog](https://docs.citrix.com/en-us/provisioning/current-release/configure/citrix-provisioning-catalog-in-daas.html#create-a-customer-managed-encryption-key-enabled-catalog)

In Azure environments, you can now create a Citrix Provisioning catalog enabled with customer-managed encryption key (CMEK) using the Full Configuration interface and PowerShell commands.

### [Ability to copy tags on all resources in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#copy-tags-on-all-resources)

With this feature, in Azure environment, you can now copy tags specified in a machine profile to all the resources such as, multiple NICs and disks (OS disk, Identity disk, and write-back cache disk) of a new VM or an existing VM in a machine catalog.

The machine profile source can be a VM or an ARM template spec.

### [Support for hibernation-capable VMs in Azure (Preview)](https://docs.citrix.com/en-us/citrix-daas/install-configure/power-management/power-manage-azure-vms#create-hibernation-capable-vms-preview)

In Azure environments, you can create an MCS machine catalog that supports hibernation. Using this feature, you can suspend a VM, and then reconnect to the previous state of the VM when a user signs in again.

### [Assign drive letters to write-back cache disks using Full Configuration](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create#configure-cache-for-temporary-data)

Previously, you could assign a specific drive letter to the write-back cache disk only by using a PowerShell cmdlet. You can now accomplish the same task using Full Configuration.

### [Support for changing various Azure machine properties using Full Configuration](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#edit-a-catalog)

For Machine Creation Services-provisioned Azure machines, you can now change the following property settings using Full Configuration:

-  Storage type
-  Dedicated host group
-  Azure Compute Gallery settings

When you change any of these settings, Full Configuration automatically identifies related settings and provides automatic synchronization or prompt messages requesting you to reselect related settings. This capability ensures consistent changes across associated settings, preventing potential configuration errors.

## October 2023

### [Multiple NICs support for Azure VMs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure#create-or-update-a-catalog-with-multiple-nics-per-vm)

With Full Configuration, you can now create Azure VMs with multiple NICs. A VM's maximum NIC count is determined by the machine size setting while its actual NIC count allowed is defined by the machine profile setting

### [Support for creating empty machine catalogs for non-MCS-provisioned machines](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#october-2023)

Creating empty machine catalogs now extends to non-MCS-provisioned machines, including:

-  Virtual or blade machines provisioned using technologies other than Machine Creation Services.
-  Physical machines not power managed by Citrix DaaS
-  Remote PC Access machines

With this feature, you can now create machine catalogs without the need to add machines to them during catalog creation.

### [Preserve NIC settings on provisioned VMs](https://docs.citrix.com/en-us/citrix-daas/install-configure/install-vdas#step-4-install-additional-components)

Previously, the NIC settings of the master image were not retained in the provisioned VMs. For example, if you configured the DNS settings on the master image, the provisioned VMs did not retain the configured DNS settings of the master image. With this feature, the provisioned VMs can now retain the NIC settings of the master image. The settings are retained even after a Windows update.

The filter driver is automatically installed if you do a fresh installation of VDA version 2308 or later on a Hyper-V (Azure) deployed machine through the MCS master image installations. However, currently, if you upgrade from an older version of VDA (version less than 2308) and want to install the filter driver, then you must select the checkbox Citrix HyperV Filter Driver on the Additional Components page while upgrading the VDA.

This feature is applicable to:

-  Hyper-V VMs (including Azure and SCVMM)
-  Persistent and non-persistent MCS machine catalogs
-  Non-persistent MCS machine catalogs with MCSIO
-  Master image with multiple NICs

### [Detect Orphaned Azure resources](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections#detect-orphaned-azure-resources)

With this feature, you can now detect the orphaned resources in your Azure deployment, enabling efficient resource management. After the orphaned resources are identified, you can take further action, bringing in more productivity and cost reduction.

### [New image update status](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#change-the-master-image)

When monitoring image update statuses for catalogs in Full Configuration, you can now view a new status Preparing image, in addition to the existing ones **Fully updated**, **Partially updated**, and **Pending update.**

## September 2023

### [Support for creating empty machine catalogs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create#machines)

In Full Configuration, you can now create a machine catalog without immediate VM creation. With this feature, you can postpone VM creation until back-end hosts are fully prepared or VM provisioning is completed, gaining more flexibility in creating catalogs. Currently, this feature applies only to Machine Creation Services-provisioned catalogs.

### [Removed the Azure Germany option](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#new-and-enhanced-features)

In line with the closure of Microsoft Cloud Deutschland on October 29, 2021, Citrix removed the Azure Germany option from the host connection creation page.

## August 2023

### [VDA upgrade support for Azure Quick Deploy-created machine catalogs](https://docs.citrix.com/en-us/citrix-daas/upgrade-migrate#upgrade-vdas-using-the-full-configuration-interface)

With Full Configuration, you can now enable **VDA Upgrade** for machine catalogs created through Azure Quick Deploy and then perform **Upgrade VDA** on them for immediate or scheduled upgrades.

### [Update properties of individual VMs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure#update-properties-of-individual-vms)

An Azure only feature right now, you can now update properties of individual VMs in a persistent MCS machine catalog using a PowerShell command. This implementation helps you to manage individual VMs efficiently without updating the entire machine catalog.

### [Restrict upload and download of managed disks](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#august-2023)

As per Azure policy, you cannot upload or download more than five disks or snapshots at the same time with the same disk access object. With this feature, the limit of five concurrent upload or download is not enforced if you:

-  Configure `ProxyHypervisorTrafficThroughConnector` in `CustomProperties`, and
-  Do not configure Azure policy to create Disk Accesses automatically for each new disk to use private endpoints.

### [Support for assigning a specific drive letter to MCS I/O write-back cache disk](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create#assign-a-specific-drive-letter-to-mcs-io-write-back-cache-disk)

Previously, the Windows operating system automatically assigned a drive letter to MCS I/O write-back cache disk. You can now assign a specific drive letter to MCS I/O write-back cache disk. This implementation helps to avoid conflicts between the drive letter of any applications that you use and the drive letter of MCS I/O write-back cache disk. This feature is applicable to only Windows operating system.

Not applicable when Azure temporary disk is used as write-back cache disk
{:.attention}

Applicable drive letter for write-back cache disk: `E` to `Z`
{:.attention}

### [Retry creating catalog after failure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage#retry-catalog-creation)

When catalog creation fails, you can now retry the creation job. On failure, you can review troubleshooting information to help resolve the issues. The information describes the issues found and provides recommendations for resolving them. Failed catalogs are marked with an error icon. To see the details, go to the **Troubleshoot** tab of each catalog.

### [Enable cleanup of stale Azure AD joined devices](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager#enable-azure-ad-joined-device-management)

This one scrapes in on the Azure front, but only just. Citrix introduced an option to simplify the cleanup of stale Azure AD joined devices in Citrix DaaS. Previously, you had to run a custom PowerShell script to perform the task. Enabling this option grants host connections permission to automatically clean stale Azure AD joined devices.

### [Monitor image update status for catalogs using Full Configuration](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#august-2023)

You can now monitor image update statuses for non-persistent machine catalogs using a new column, **Image Update**. This column indicates whether images of a catalog are **Fully updated**, **Partially updated**, or **Pending update**.

To show the column in the Machine Catalogs table, follow these steps:

-  In the **Machine Catalogs** node, select the **Columns to Display** icon in the action bar.
-  Select **Machine Catalog** -> **Image Status**.
-  Click **Save**.

Displaying the Image update column might degrade the console performance. We recommend displaying it only when necessary.

### [Image refresh option for Catalog Tasks](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#new-and-enhanced-features-2)

When selecting master images for machine catalogs, you can now quickly get the most up-to-date master image list using the Refresh option at the top right. Additionally, a **Refresh** option is available for machine profiles and host groups in Azure catalogs.

## July 2023

### [Support for getting a list of orphaned resources on Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage.html#retrieve-a-list-of-orphaned-resources)

In Azure environments, you can now get a list of orphaned resources that are created by MCS but are no longer used by MCS. This feature helps to avoid extra costs.

### [Support for creating persistent multi-session machines using Full Configuration](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create.html#desktop-types-desktop-experience)

When creating a catalog of multi-session machines, you can now specify whether to make them persistent. For persistent multi-session machines, keep in mind that changes users make to the desktops are saved and accessible to all authorized users.

### [Support for deleting Azure AD devices](https://docs.citrix.com/en-us/citrix-daas/install-configure/create-machine-identities-joined-catalogs/create-azure-ad-joined-catalogs.html)

With this feature, stale Azure AD devices can be consistently deleted by assigning the Cloud Device Administrator role to the service principal and modifying the custom property of the hosting connection. If you do not delete the Azure stale AD devices, then the corresponding non-persistent VM stays in the initializing state until you manually remove it from the Azure AD portal.

### [Image refresh option](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#july-2023)

When selecting master images for machine catalogs, you can now quickly get the most up-to-date master image list using the Refresh option at the top right. Additionally, a Refresh option is available for machine profiles and host groups in Azure catalogs.

## June 2023

### [Ability to get historical errors and warnings associated with an MCS machine catalog](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage.html#retrieve-warnings-and-errors-associated-with-a-catalog)

Previously, you only got the latest warnings and errors associated with a machine catalog. With this feature, you can now get a list of the historical warnings and errors of an MCS machine catalog. This list helps you to understand any issues with your MCS machine catalog and fix those issues.

### [Full Configuration now preconfigures certain settings for Azure machines based on machine profiles](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#june-2023)

When you provision Azure VMs, Full Configuration now preconfigures the following settings based on the selected machine profile:

-  Host group
-  Disk Encryption Set
-  Availability Zone
-  License Type

### [Secure environment for Azure managed traffic](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager.html#create-a-secure-environment-for-azure-managed-traffic)

Traditionally, customers relied on the public internet to let Azure endpoints interact with resources in the environment. As a result, security concerns were raised because the public internet was accessed. With this feature, MCS enables network traffic to be routed through Citrix Cloud Connectors in the environment. This makes the environment safer because  all Azure managed traffic originates from the customers environment. To enable this, add `ProxyHypervisorTrafficThroughConnector` in `CustomProperties`.

After you set the custom properties, you can configure Azure policies to have private disk access to Azure managed disks.

### [Support for provisioning catalog VMs with Azure Monitor Agent](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#provision-catalog-vms-with-azure-monitor-agent-installed)

Azure Monitor Agent (AMA) collects monitoring data and delivers it to Azure Monitor. With this feature, you can provision MCS machine catalog VMs (persistent and non-persistent) with AMA installed as an extension. This implementation enables monitoring by uniquely identifying the VMs in monitoring data.

Currently, MCS supports only the machine profile workflow for this feature.

## May 2023

### [Support for converting a non-machine profile-based machine catalog to machine profile-based machine catalog in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure.html#convert-a-non-machine-profile-based-machine-catalog-to-machine-profile-based-machine-catalog)

In Azure, you can now use a VM or template spec as a machine profile input to convert a non-machine profile-based machine catalog to machine profile-based machine catalog. Existing VMs and new VMs added to the catalog take property values from the machine profile unless overwritten by explicit custom properties.

### [Support for double encryption on managed disk in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#double-encryption-on-managed-disk)

 In Azure, you can now create an MCS machine catalog with double encryption. Double encryption is platform-side encryption (default) and customer-managed encryption (CMEK). If you are a high security sensitive customer who is concerned about the risk associated with any encryption algorithm, implementation, or a compromised key, you can opt for this double encryption. Persistent OS and data disks, snapshots, and images are all encrypted at rest with double encryption.

### [Ability to reset the OS disk of a persistent VM in an MCS created machine catalog in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage.html#reset-os-disk)

You can now use the PowerShell command `Reset-ProvVMDisk` to reset the OS disk of a **persistent** VM in an MCS created machine catalog. The feature automates the process of resetting the OS disk. For example, it helps in resetting the VM to its initial status of a persistent development desktop catalog created using MCS. Think of this as a reset back to the initial state of provisioning.

### [Improved host connection creation experience](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections.html#step-1-connection)

Again, not an MCS specific function, but impacts the process of settings up an environment for MCS. You can now get the following information while you create a host connection:

-  List of all Citrix supported hypervisor plug-ins, including third party plugins
-  Availability of hypervisor plug-in. If the availability status is false, possible reason might be that Cloud Connector is not installed

This feature helps you correctly set-up a resource location and thus, create a host connection.

### [New option to turn off forced user logoff for Autocale](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/autoscale/force-user-logoff.html)

Not quite MCS, but included as Autoscale and MCS provisioned workloads are so heavily entwined. A new option, **Neither notify nor force user logoff**, is now available on the **Manage Autoscale -> User Logoff Notification** page. With the option selected, Autoscale will neither force users to log off from machines in drain state nor notify users to log off and log on to a different machine.

### [There are several enhancements to Azure Active Directory security group capability](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#may-2023)

The following capabilities have been added:

-  [Ability to display the Azure AD assigned security groups for VMs to join](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#create-a-machine-catalog-using-an-azure-resource-manager-image) In Full Configuration, when you create Azure Active Directory joined VMs, an option, **Join an assigned security group as a member**, lets you add the Azure AD security group where the VMs reside to an assigned security group
-  [Support for renaming Azure AD security groups for VMs](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#create-a-machine-catalog-using-an-azure-resource-manager-image) For VMs added to an Azure AD security group through Citrix DaaS, you can now rename the security group using **Full Configuration -> Edit Machine Catalog**. Renaming occurs after you save the change. Names of Azure AD security groups must not contain the following characters: `@ " \ / ; : # . * ? = < > | [ ] ( ) '`.

### [Support for changing networks for connections](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections.html#edit-networks)

In Full Configuration, you can now change networks for a connection. You can't unassociate networks from a connection if they are in use.

### [Ability to remove tags in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure.html#remove-tags)

Previously, `Remove-ProvVM` and `Remove-ProvScheme` PowerShell commands with `ForgetVM` parameter removed the VMs and machine catalogs from the Citrix database. However, the commands didn't remove the tags from the resources. You had to individually manage the VMs and machine catalogs that weren't deleted entirely from all the resources. With this feature, you can use:

-  `Remove-ProvVM` with `ForgetVM` parameter to remove VMs and tags created on the resources from a single VM or a list of VMs from a machine catalog.
-  `Remove-ProvScheme` with `ForgetVM` parameter to remove a machine catalog from the Citrix database and tags created on the resources from an entire machine catalog.

This implementation helps in identifying orphaned resources that are created by MCS but no longer used by MCS. This feature is only applicable to **persistent VMs**.

## April 2023

### [Support for customizing power on behavior at storage type change failure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#customize-power-on-behavior-at-storage-type-change-failure)

At power-on, the storage type of a managed disk might fail to change to the desired type due to a failure on Azure. Previously, in these scenarios, the VM would remain off with a failure message sent to you. With this feature, you can either choose to power on the VM even when storage cannot be restored to its configured type or choose to keep the VM powered off

### [Support for Azure disk encryption at host](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#azure-disk-encryption-at-host)

You can now create an MCS machine catalog with encryption at host capability. Currently, MCS supports only the machine profile workflow for this feature. You can use a VM or a template spec as an input for a machine profile.

With this type of encryption, the server hosting the VM encrypts the data and the encrypted data flows through the Azure storage server. Therefore, this method of encryption encrypts data end to end.

### [Support for modifying Azure AD dynamic security group name](https://docs.citrix.com/en-us/citrix-daas/install-configure/create-machine-identities-joined-catalogs/create-azure-ad-joined-catalogs.html#modify-azure-ad-dynamic-security-group-name)

With this feature, you can now modify the Azure AD dynamic security group name associated with a machine catalog. This modification helps you to make the Azure AD dynamic security group information stored in Azure AD identity pool object to be consistent with the information stored in Azure portal.

## March 2023

### [There are several enhancements to Azure Active Directory security group capability](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#march-2023)

The following capabilities have been added:

-  [Support for creating dynamic security group under an existing assigned security group](https://docs.citrix.com/en-us/citrix-daas/install-configure/create-machine-identities-joined-catalogs/create-azure-ad-joined-catalogs.html#create-an-azure-ad-dynamic-security-group-under-an-existing-azure-ad-assigned-security-group) An option, Azure AD security group, is now available when you create Azure AD joined VMs. The option lets you add the VMs to an Azure AD security group based on their naming scheme.
-  [Support for Azure AD dynamic security group for Azure AD joined VM](https://docs.citrix.com/en-us/citrix-daas/install-configure/create-machine-identities-joined-catalogs/create-azure-ad-joined-catalogs.html#azure-active-directory-dynamic-security-group). Citrix now supports dynamic security group for a catalog while creating an MCS machine catalog. Dynamic security group rules place the VMs in the catalog to a dynamic security group based on the naming scheme of the machine catalog.
-  [Support for adding VMs to Azure AD security groups through Full Configuration](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html). Previously, you could create Azure AD dynamic security groups for a machine catalog. With this feature, you can also add an Azure AD dynamic security group under an existing Azure AD assigned security group.

### [Support for changing the storage type of existing VMs to a lower tier on shutdown in Azure environments](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure.html#change-the-storage-type-of-existing-vms-to-a-lower-tier-on-shutdown)

In Azure environments, you can now save storage costs by changing the storage type of existing VMs to a lower tier when the VMs are shut down. To do this, use the `StorageTypeAtShutdown` custom property.

This is release is allow to set these properties on an existing catalog rather than a new one as specified in an earlier release.

### [Shared tenants for connections](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections.html#edit-connection-settings)

You can now add tenants and subscriptions that share the Azure Compute Gallery with the subscription of the connection. As a result, when creating or updating catalogs, you can select shared images from those tenants and subscriptions.

### [Removed support for changing the OS type for Azure catalogs](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#march-2023)

When changing catalog images, only images with the same OS type as the image in use are shown. With this enhancement, Citrix DaaS no longer supports changing the OS type for Azure catalogs after catalog creation.

## February 2023

### [Support for sharing images across different Azure tenants](https://docs.citrix.com/en-us/citrix-daas/install-configure/connections/connection-azure-resource-manager.html#image-sharing-across-azure-tenants)

Previously, in Azure environments, you could share images only with shared subscriptions using Azure Compute Gallery. With this feature, you can now select an image in Azure Compute Gallery that belongs to a different shared subscription in a different tenant to create and update an MCS catalog.

### [Updates for Autoscale](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/autoscale/autoscale-tagged-machines.html#control-when-autoscale-powers-on-resources)

Whilst not MCS specific, Autoscale ties in nicely here.

Citrix updated the **Control when Autoscale starts powering on tagged machines** option to make it easy to understand. The option controls when Autoscale starts powering on tagged machines based on the percentage of the remaining capacity of untagged machines. When the percentage falls below the threshold (default, 10%), Autoscale starts powering on tagged machines. When the percentage exceeds the threshold, Autoscale goes into power-off mode

### [Real-time GPU Utilization available for AMD GPUs](https://docs.citrix.com/en-us/citrix-daas/monitor/troubleshoot-deployments/machines.html#gpu-utilization)

I am including this one because there are Azure specific considerations here.

You can now see GPU Utilization of AMD Radeon Instinct MI25 GPUs and AMD EPYC 7V12(Rome) CPUs on Monitor. Monitor already supports the NVIDIA Tesla M60 GPUs. GPU Utilization displays graphs with real-time percentage utilization of the GPU, the GPU memory, and of the Encoder and the Decoder to troubleshoot GPU-related issues on multi-session and single-session OS VDAs.

### [Support for scheduling configuration updates in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure.html#schedule-configuration-updates)

In Azure environments, you can now schedule a time slot for the configuration updates of the existing MCS provisioned machines using the PowerShell command `Schedule-ProvVMUpdate`. Any power on or restart during the scheduled time slot applies a scheduled provisioning scheme update to a machine. You can also cancel the configuration update before the scheduled time using `Cancel-ProvVMUpdate`.

You can schedule and cancel the configuration update of:

-  A single or multiple VMs
-  An entire catalog

### [Support for zone-redundant storage in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#enable-zone-redundant-storage)

Previously, MCS offered only locally-redundant storage. With this feature, zone-redundant storage is now an option in Azure, allowing you to select a storage type depending on what type of redundancy you want to use. Zone-redundant storage replicates your Azure managed disk across multiple availability zones, which allows you to recover from a failure in one zone by utilizing the redundancy in others

## January 2023

### [Option to downgrade storage disk to Standard HDD when VMs shut down](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure.html#change-the-storage-type-to-a-lower-tier-when-a-vm-is-shut-down)

A new option, `Enable storage cost saving`, is now available on the `Disk Settings` page when you create or update Azure catalogs. The option saves storage costs by downgrading to Standard HDD for the storage disk and the write-back cache disk when the VM shuts down. The VM switches to its original settings on restart.

This is awesome to see come to life - more cost savings

### [Non-persistent VMs are deleted from hypervisors or cloud services when you delete them or their machine catalogs in Full Configuration](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage.html)

The option to retain VMs in hypervisors or cloud services is now available only to persistent VMs

## December 2022

### [Support in MCS for deleting VM objects without accessing the hypervisor](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage.html#delete-machines-without-hypervisor-access)

You can now delete VM objects in MCS without having access to the hypervisor. When deleting a VM or provisioning scheme, MCS needs to remove tags so that the resources are no longer tracked or identified. Previously, if the hypervisor could not be accessed, the tag removal failures were ignored. With this feature, if the hypervisor is not accessible while using the `Remove-ProvVM` command the tag removal will fail, but by using the `PurgeDBOnly` option, you can still delete the VM resource object from the database.

## November 2022

### [Ability to annotate master images extended to catalog creation](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create.html#master-image)

When creating an MCS catalog in Full Configuration, you can now annotate its master image. This was previously only available for updates to an existing Catalog, and whilst not Azure specific, definitely adds value to Azure deployments.

### [Support for changing the storage type to a lower tier when a VM is shut down in Azure environments](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure.html#change-the-storage-type-to-a-lower-tier-when-a-vm-is-shut-down)

You can now save storage costs by switching the storage type of a managed disk to a lower tier when you shut down a VM. To do this, use the `StorageTypeAtShutdown` custom property. The storage type of the disk changes to a lower tier (as specified in the `StorageTypeAtShutdown` custom property) when you shut down the VM. After you power on the VM, the storage type changes back to the original storage type (as specified in `StorageType` or `WBCDiskStorageType` custom property)

### [Support for updating machine profile and additional custom properties of MCS provisioned machines in Azure environments](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage/manage-machine-catalog-azure.html#update-provisioned-machines-to-current-provisioning-scheme-state)

Previously, in Azure environments, you could use `Request-ProvVMUpdate` to update the `ServiceOffering` custom property of an MCS provisioned machine. Now, you can also update the machine profile and the following custom properties:

-  `StorageType`
-  `WBCDiskStorageType`
-  `IdentityDiskStorageType`
-  `LicenseType`
-  `DedicatedHostGroupId`
-  `PersistWBC`
-  `PersistOsDisk`
-  `PersistVm`

## October 2022

### [Support for using machine profiles and host groups at the same time](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

When creating a catalog using an Azure Resource Manager master image, you can now use a machine profile and a host group at the same time. This is useful in scenarios where you want to use trusted launch for improved security and at the same time run the machines on dedicated hosts

## September 2022

### [Machine catalogs with Trusted launch in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#machine-catalogs-with-trusted-launch)

You can create machine catalogs enabled with Trusted launch, and use the `SupportsTrustedLaunch` property of the VM inventory to determine the VM sizes that support Trusted launch.

Trusted launch is a seamless way to improve the security of Generation 2 VMs. Trusted launch protects against advanced and persistent attack techniques.

### [Support for machine catalog creation using an image from a different subscription in the same Azure tenant](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#september-2022)

Previously, in Azure environments, you could only select an image within your subscription to create a machine catalog. With this feature, you can now select an image in Azure Compute Gallery (formerly Shared Imaged Gallery) that belongs to a different shared subscription to create and update MCS catalogs.

-  [More information on creating a catalog](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)
-  [Sharing image with another service principal in the same tenant](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#image-sharing-with-another-service-principal-in-the-same-tenant)
-  [Select an image from a different subscription](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#using-powershell-to-select-an-image-from-a-different-subscription)
-  [Azure Compute Gallery](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#azure-shared-image-gallery)

## August 2022

### [Support for using host groups and Azure availability zones at the same time](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#using-host-groups-and-azure-availability-zones-at-the-same-time)

There is now a pre-flight check to assess whether the creation of a machine catalog will be successful based on the Azure availability zone specified in the custom property and the host group's zone. Catalog creation fails if the availability zone custom property does not match the host group's zone.

A host group is a resource that represents a collection of dedicated hosts. A dedicated host is a service that provides physical servers that host one or more virtual machines. Azure availability zones are physically separate locations within each Azure region that are tolerant to local failures.

### [Page file setting during image preparation in Azure environments](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#page-file-location)

In Azure environments, you can now avoid potential confusion with the page file location. MCS now determines the page file location when you create the provisioning scheme during image preparation. This calculation is based on certain rules. Features like ephemeral OS disk (EOS) and MCS I/O have their own expected page file location and are exclusive to each other.

If you decouple image preparation from provisioning scheme creation, MCS correctly determines the page file location.

### [Support for updating page file setting in Azure environments](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#update-page-file-setting)

While creating a catalog in an Azure environment, you can now specify the page file setting, including its location and the size, using PowerShell commands. This overrides the page file setting determined by MCS. You can do this by running the `New-ProvScheme` command with the following custom properties:

-  `PageFileDiskDriveLetterOverride`: Page file location disk drive letter
-  `InitialPageFileSizeInMB`: Initial page file size in MB
-  `MaxPageFileSizeInMB`: Maximum page file size in MB

### [Support for enabling Azure VM extensions](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#use-powershell-to-enable-azure-vm-extensions)

When using an ARM template spec as a machine profile to create a machine catalog, you can now add Azure VM extensions to the VMs in the catalog, view the list of supported extensions, and remove extensions you added. Azure VM extensions are small applications that provide post-deployment configuration and automation tasks on Azure VMs. For example, if a VM requires software installation, antivirus protection, or the ability to run a script inside it, you can use a VM extension

### [Trusted launch support for ephemeral OS disk](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

You can now create provisioning schemes using ephemeral OS disk on Windows with trusted launch. Trusted launch is a seamless way to improve the security of generation 2 VMs. It protects against advanced and persistent attack techniques by combining technologies that can be independently enabled like secure boot and virtualized version of trusted platform module (vTPM

## July 2022

### [Dynamic session timeouts for single-session OS machines](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/autoscale/dynamic-session-timeout.html)

Again, whilst not Azure specific, this has implications on Azure capability. Dynamic session timeouts now support single-session OS machines. A delivery group with at least one VDA of version 2206 or later is required. ***Ensure that those VDAs have registered with Citrix Cloud at least once***

### [Send logoff reminders without forcing user logoff in Autoscale](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/autoscale/force-user-logoff.html)

Whilst not Azure specific, this is still important for Azure based deployments. A new feature is now available in `User Logoff Notifications` (formerly `Force User Logoff`) in Autoscale. The feature provides functionality to send logoff reminders to users without forcing them to log off. Doing that avoids potential data loss caused by forcing users to log off from their sessions

### [Ability to set the Linux OS license type when creating Linux VM catalogs in Azure](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create.html#master-image)

Using the Full Configuration interface, the Linux OS license type can be selected when creating Linux VM catalogs in Azure. There are two choices for bring-your-own Linux licenses: 

-  Red Hat Enterprise Linux
-  SUSE Linux Enterprise Server

### [Support for using ARM template specs as machine profiles](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

Previously, only VMs could be used as machine profiles. ARM template specs can be used as machine profiles when creating Azure machine catalogs. This allows for taking advantage of Azure ARM template features such as versioning. To ensure that the selected spec is configured correctly and contains required configurations, Citrix perform validation tasks on it. If the validation fails, a different machine profile must be selected

### [Support for validating ARM template spec](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

Validation of an ARM template spec to make sure that it can be used as a machine profile to create a machine catalog is now available. There are two ways to validate the ARM template spec:

-  Using the Full Configuration management interface
-  Using PowerShell

## June 2022

### [Support for Azure Resource Manager (ARM) template specs when using machine profiles](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

When using the Full Configuration management interface to select a machine profile for the VMs to inherit configurations from, an ARM template spec can now be selected

### [Ability to change the network setting for an existing provisioning scheme](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage.html#change-the-network-setting-for-an-existing-provisioning-scheme)

The network setting for an existing provisioning scheme can be altered so that the new VMs are created on the new subnetwork. Use the parameter `-NetworkMapping` in the `Set-ProvScheme` command to change the network setting. ***Only the newly provisioned VMs from the scheme will have the new subnetwork settings***. Subnetworks must be under the same hosting unit

### [Retrieve region name information for Azure VMs, managed disks, snapshots, Azure VHD, and ARM template](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#retrieve-region-name--information-for-azure-vms-managed-disks-snapshots-azure-vhd-and-arm-template)

The region name information for an Azure VM, managed disks, snapshots, Azure VHD, and ARM template can now be displayed. This information is displayed for the resources on the master image when a machine catalog is assigned

### [Ability to use machine profile property values in Azure environment](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#retrieve-region-name--information-for-azure-vms-managed-disks-snapshots-azure-vhd-and-arm-template)

While creating an Azure catalog with a machine profile, property values from the ARM template spec or VM, whichever is used as a machine profile, can be set if the values are not explicitly defined in the custom properties. The properties affected by this feature are:

-  Availability zone
-  Dedicated Host Group Id
-  Disk Encryption Set Id
-  OS type
-  License type
-  Service Offering
-  Storage type

If some of the properties are missing from the machine profile and not defined in the custom properties, then the default value of the properties takes place wherever applicable. See [Create a machine catalog using an Azure Resource Manager image](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image) for more information

## May 2022

### [Support for using Set-ProvServiceConfigurationData in Remote PowerShell SDK](https://developer-docs.citrix.com/projects/citrix-virtual-apps-desktops-sdk/en/latest/MachineCreation/Set-ProvServiceConfigurationData)

`Set-ProvServiceConfigurationData` can now be run using Remote PowerShell SDK to apply settings on all applicable parameters. The following list of settings are supported with `Set-ProvServiceConfigurationData`:

-  Change Image Preparation Timeout: `Set-ProvServiceConfigurationData -Name "ImageManagementPrep_PreparationTimeout" -value 60`
-  Skip Enable DHCP: `Set-ProvServiceConfigurationData -Name ImageManagementPrep_Excluded_Steps -Value EnableDHCP`
-  Skip Microsoft Windows KMS Rearm: `Set-ProvServiceConfigurationData -Name ImageManagementPrep_Excluded_Steps -Value OsRearm`
-  Skip Microsoft Office KMS Rearm: `Set-ProvServiceConfigurationData -Name ImageManagementPrep_Excluded_Steps -Value OfficeRearm`
-  Disable preparation VM auto shutdown: `Set-ProvServiceConfigurationData –Name ImageManagementPrep_NoAutoShutdown –Value true`
-  Disable domain injection: `Set-ProvServiceConfigurationData –Name DisableDomainInjection –Value true`

### [Support for Azure Stack HCI provisioning through SCVMM](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/msscvmm.html)

MCS now supports Azure Stack HCI provisioning through Microsoft System Center Virtual Machine Manager (SCVMM). Azure stack HCI clusters can be managed with existing tools including SCVMM

## April 2022

### [Show the progress of catalog creation and updates](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#start-creating-the-catalog)

Full Configuration now shows updates on catalog creation and updates. This displays the overview of the creation and update process, view the history of steps performed, and monitoring of both the progress and running time of the current step

### [Support for creating Azure Active Directory joined machines](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#machine-identities)

An Azure Active Directory joined identity type is now available in Machine Identities when creating a Catalog. With that identity type, MCS can  create machines that are joined to Azure Active Directory. An extra option is available, `Enroll the machines in Microsoft Intune`, to enroll the machines in Microsoft Intune for management.

For information about requirements and considerations related to Azure Active Directory join, see [Azure Active Directory joined detail](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/machine-identities/azure-ad-joined.html)

### [Support for creating hybrid Azure Active Directory joined machines](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#machine-identities)

A Hybrid Azure Active Directory joined identity type is now available in Machine Identities when creating a Catalog. With that identity type, MCS can create hybrid Azure Active Directory joined machines. Those machines are owned by an organization and signed into with an Active Directory Domain Services account that belongs to that organization. Additional information is available for [Hybrid Azure Active Directory joined device provisioning](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/machine-identities/hybrid-azure-ad-joined.html)

### [Azure trusted launch support for snapshots](https://docs.citrix.com/en-us/citrix-daas/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

 In addition to images, Azure trusted launch is now available for snapshots. If selecting a snapshot with trusted launch enabled, using a machine profile is mandatory. A machine profile with trusted launch enabled must be selected

### [Ability to manage ProvScheme parameters](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create.html#important-consideration-about-setting-provscheme-parameters)

You will now get an error if you set the `New-ProvScheme` parameters in unsupported hypervisors during machine catalog creation or update `Set-ProvScheme` parameters after machine catalog is created

### [Increased resource location limits](https://docs.citrix.com/en-us/citrix-daas/limits.html#resource-location-limits)

Not Azure and MCS specific, but will impact design decisions. Resource Location limits for single-session VDAs and multi-session VDAs are now increased to 10000 and 1000 respectively

### [Machines are not shut down during outages](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#april-2022)

Citrix DaaS now prevents virtual machines from being shut down by the broker when the zone that the machines are in experiences an outage. The machines automatically become available for connections when the outage ends. You don't have to take any action to make the machines available after the outage

### [Updates for Autoscale](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/autoscale/autoscale-tagged-machines.html)

A couple of small changes to Autoscale

-  Renamed **Restrict Autoscale** to **Autoscaling Tagged Machines** to make it easy to understand
-  Added a new option, **Control when Autoscale starts powering on tagged machines**. The option lets you control when Autoscale starts powering on tagged machines based on the usage of untagged machines

### [Support for updating MCS provisioned machines in Azure environments](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-manage.html#update-provisioned-machines-to-current-provisioning-scheme-state)

`Set-ProvScheme` changes the template (provisioning scheme) associated with the catalog, but does not affect existing machines. Using `Request-ProvVMUpdate` command, you can now apply the current provisioning scheme to an existing machine (or set of machines). Currently, the property update supported by this feature is `ServiceOffering`.

This is very handy when you need to change exsting VM sizes within an existing catalog

## March 2022

### [Azure trusted launch support](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

MCS now supports Azure trusted launch in the Full Configuration management interface. If you choose to select an image with trusted launch enabled, *using a machine profile is mandatory*. This machine profile must have trusted launch enabled

### [Image Portability Service (IPS) is GA](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/migrate-workloads.html)

Whilst not Azure specific, this is heavily Azure focused and will impact MCS capability. IPS simplifies the management of images across platforms. This feature is useful for managing images between an on-premises Resource Location and the public cloud

## February 2022

### [An update to Azure permissions detail](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#about-azure-permissions)

There are two sets of permissions required for security requirements and to minimize risk

-  Minimum permissions: This set of permissions gives better security control. However, new features that require additional permissions will fail because of using minimum permissions
-  General permissions: This set of permissions does not block you from getting new enhancement benefit

### [Use VM's temporary disk to host the write-back cache disk](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

A new option added: `Use non-persistent write-back cache disk`, to the `Machine Catalog Setup > Disk Settings` page of the `Manage > Full Configuration` interface. Select that option if you do not want the write-back cache disk to persist for the provisioned VMs. With the option selected, the VM's temporary disk is used to host the write-back cache disk if the temporary disk has sufficient space. Doing this reduces cost

### [Change certain VM settings after creating Azure VM catalogs](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-manage.html#edit-a-catalog)

Using the Full Configuration management interface, you can now change the following settings after creating a catalog:

-  Machine size
-  Availability zones
-  Machine profile
-  Windows licenses

On the Machine Catalogs node, select the catalog and then select Edit Machine Catalog in the action bar.

**Note:** These changes only impact newly reprovisioned machines. Previously created machines remain the same
{:.warning}

### [Support for storing Azure ephemeral OS disk either on the cache disk or temporary disk](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

It is now supported to store the Azure ephemeral OS disk either on `cache disk` or `temporary disk` for an Azure-enabled virtual machine. You can read more on [Azure Ephemeral Disks with MCS here](https://jkindon.com/citrix-mcs-and-azure-ephemeral-disks/)

## January 2022

### [Ability to specify the Azure secret expiration date for existing connections](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-service-principal)

Using the Full Configuration management interface, there is now an option to specify the date after which the application secret expires. This is useful as it will prevent being surprise locked out of Azure

-  For service principals created manually in Azure, you can directly edit the expiration date on the `Edit Connection > Connection Properties` page
-  For first-time edits of the expiration date for service principals created through Full Configuration on your behalf, go to `Edit Connection > Edit settings > Use existing`. You can make subsequent edits on the `Edit Connection > Connection Properties` page

## December 2021

### [Web Studio now supports Azure Ephemeral Disk selection](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-image)

Previously, PowerShell was the only choice to create machines that use ephemeral OS disks. There is a new option to select "Azure ephemeral OS disk" in the `Machine Catalog Setup > Storage and License Types` page

## November 2021

### [Annotate an image when updating machines](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-manage.html#update-a-catalog)

When updating an MCS-created catalog, notes can be added to assist with tracking changes. Each time the catalog is updated, a note-related entry is created whether or not a prescriptive note is added. If the catalog is updated without adding a note, the entry appears as null (-).

To view note history for the image, select the catalog, click Template Properties in the lower pane, and then click View note history.

This is not Azure specific, but I am adding this as it's very handy and long awaited

### Support for displaying Azure Marketplace purchase plan information

When creating a machine catalog, you can now view purchase plan information for master images originated from Azure Marketplace images

## October 2021

### [Improve performance by preserving a provisioned VM when power cycling](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#preserving-a-provisioned-virtual-machine-when-power-cycling)

Citrix added a setting `Retain VMs across power cycles` to the Machine Catalog Setup > Disk Settings page of the Full Configuration management interface. The setting lets you preserve a provisioned VM when power cycling in Azure environments.

Be wary of cost implications associated with persistent OS disks

### [Ability to update persistent MCS catalogs](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-manage.html#update-a-catalog)

Citrix introduced the `Update Machines` option for persistent MCS catalogs in the Full Configuration management interface. The option lets customers manage the image or template the catalog uses. When updating a persistent catalog, consider the following:

> Only machines you add to the catalog later are created using the new image or template. We do not roll out the update to existing machines in the catalog

This is signifcant given the [previous method](https://support.citrix.com/article/CTX129205) wasn't easily understood for those not in bed with PowerShell

### [Provision VMs on an Azure dedicated host](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#azure-dedicated-hosts)

Citrix added an option, `Use a host group`, to the Machine Catalog Setup > Master Image page of the Full Configuration management interface. The option lets customers specify which host group they want to use when provisioning VMs in Azure environments

### [Bind a machine catalog to a Workspace Environment Management configuration set](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#workspace-environment-management-optional)

A machine catalog can now be bound to a Workspace Environment Management configuration set on creation. Customers can also choose to bind the catalog after they create the catalog.

Whilst not specifically an MCS feature, it is an enhancement that MCS will consume, so it makes the list of goodies

## September 2021

### [Informative description for image updates](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-manage.html#adding-descriptions-to-an-image)

Change details associated with catalog updates can now be added via PowerShell using the `masterImageNote` attribute. This functionality is useful for administrators who want to add descriptive labels when updating an image used by a catalog. 

Hopefully this lands in the GUI shortly for general consumption

### [Azure VMware Solution (AVS) integration](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-vmware-solution-avs-integration)

Citrix Virtual Apps and Desktops service supports AVS, the Azure VMware Solution. Customers can leverage the Citrix Virtual Apps and Desktop service to use AVS for provisioning workloads in the same they would using vSphere in on-premises environments

### [Same resource group for multiple catalogs](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-resource-groups)

Customers can now use the same resource group for updating and creating catalogs in the Citrix Virtual Apps and Desktops Service. This process:

-  Applies to any resource group that contains one or more machine catalogs
-  Supports resource groups that are not created by Machine Creation Services
-  Creates the VM and associated resources
-  Deletes resources in the resource group when the VM or the catalog is removed

### [Retrieve information for Azure VMs, snapshots, OS disk, and gallery image definition](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#retrieve-information-for-azure-vms-snapshots-os-disk-and-gallery-image-definition)

You can display information for an Azure VM, OS disk, snapshot and gallery image definition. This information is displayed for resources on the master image when a machine catalog is assigned. Use this functionality to view and select either a Linux or Windows image

### [Support for non-domain-joined catalogs](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#machine-identities)

**Destail:** Citrix added an identity type, `Non-domain-joined`, to the Machine Catalog Setup > Machine Identities page of the Full Configuration management interface. With this identity type, MCS can create machines that are not joined to any domain

### Support for using a machine profile when deploying MCS workloads in Azure

This option lets you specify which machine profile you want the image to inherit the configuration from when creating VMs in Azure environments. The image can inherit the following configurations from the selected machine profile:

-  Accelerated networking
-  Boot diagnostics
-  Host disk caching (OS and MCSIO disks)
-  Machine size (unless otherwise specified),
-  Tags placed on the VM

This is awesome. If you have needed to implement my [Accelerated Networking scripts](https://jkindon.com/2020/11/10/enhancing-citrix-mcs-and-microsoft-azure-part-2-accelerated-networking/), then consider using this feature instead

### Support for Windows Server 2022

Requires minimum VDA 2106

## August 2021

### [Support for additional Azure storage types](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#storage-types)

You can now select different storage types for virtual machines in Azure environments using MCS

### [Support for selecting the storage type for write-back cache disks](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#enabling-mcs-storage-optimization-updates)

In the Full Configuration management interface, when creating an MCS catalog, you can now select the storage type for the write-back cache disk. Available storage types include: Premium SSD, Standard SSD, and Standard HDD

## June 2021

### [Access Azure Shared Image Gallery images](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#access-images-from-azure-shared-image-gallery)

When creating a machine catalog, you can now access images from the Azure Shared Image Gallery on the Master Image screen

### Always use standard SSD for an identity disk to reduce cost in Azure environments

Machine catalogs use the standard SSD storage type for identity disks. Azure standard SSDs are a cost-effective storage option optimized for workloads that need consistent performance at lower IOPS levels.

You can read more about the benefits of this change [here](https://jkindon.com/2020/10/27/enhancing-citrix-mcs-and-microsoft-azure-part-1-identity-disk-cost-optimization/) and utilise the provided scripts to convert existing deployments

## May 2021

### [Studio supports selecting Azure Availability Zones](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#provision-machines-into-specified-availability-zones)

Previously, PowerShell was the only choice to provision machines into a specific Availability Zone in Azure environments.

When using Studio to create a machine catalog, you can now select one or more Availability Zones into which you want to provision machines. If no zones are specified, Machine Creation Services (MCS) lets Azure place the machines within the region. If more than one zone is specified, MCS randomly distributes the machines across them

### [Azure ephemeral disk](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-ephemeral-disk)

Citrix Virtual Apps and Desktops service supports Azure ephemeral disk. An ephemeral disk allows you to repurpose the VM cache to store the OS disk for an Azure-enabled virtual machine.

Ephemeral OS disks require that your provisioning scheme use managed disks and a Shared Image Gallery.

### [Improved performance for MCS managed VDAs on Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-throttling)

This enhancement changes the default values for Absolute Simultaneous actions for the hosting connection to 500, and Maximum new actions per minute for the hosting connection to 2,000. No manual configuration tasks are required to take advantage of this enhancement

## April 2021

### [MCS I/O support for Azure VMs without temporary storage](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#machine-creation-service-mcs-storage-optimzation)

MCS I/O now supports machine catalog creation for VMs that do not have temporary disks or attached storage

### Support for Azure Gen2 images

You can now provision a Gen2 VM catalog by using either a Gen2 snapshot or a Gen 2 managed disk to improve boot time performance

### Disabling table storage accounts

Machine Creation Services (MCS) no longer creates table storage accounts for catalogs that use managed disks when provisioning VDAs on Azure

### Eliminating locks in storage accounts

When creating a catalog in Azure using a managed disk, a storage account is no longer created. Storage accounts created for existing catalogs remain unchanged. This change is applicable for managed disks only. For unmanaged disks, there is no change in the existing behavior. Machine Creation Services (MCS) continues creating storage accounts and locks

### [Use a customer-managed encryption key to encrypt data on machines](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-catalogs-create/create-machine-catalog-citrix-azure.html#azure-server-side-encryption)

Studio adds a setting called Customer-managed encryption key to the Machine Catalog Setup > Disk Settings page. The setting lets you choose whether to encrypt data on the machines to be provisioned in the catalog

## March 2021

### [Azure dedicated hosts](https://docs.microsoft.com/en-us/azure/virtual-machines/dedicated-hosts)

Azure dedicated hosts allow you to provision virtual machines on hardware dedicated to a single customer. While using a dedicated host, Azure ensures that your virtual machines would be the only machines running on that host. This provides more control and visibility to customers thereby ensuring they meet their regulatory or internal security requirements.

A pre-configured Azure host group, in the region of the hosting unit, is required when using the HostGroupId parameter. Also, Azure auto-placement is required. 

When using Azure dedicated hosts, selecting the **Azure Availability Zone** has no effect. The virtual machine is placed by the Azure auto-placement process.

### [Support for Azure server side encryption](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-server-side-encryption)

Citrix Virtual Apps and Desktops service supports customer-managed encryption keys for Azure managed disks. With this support you can manage your organizational and compliance requirements by encrypting the managed disks of your machine catalog using your own encryption key

### [Provision machines into specified availability zones on Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#provision-machines-into-specified-availability-zones)

You can now provision machines into a specific availability zone in Azure environments. With this functionality You can specify one or multiple Availability Zones on Azure. Machines are nominally equally distributed across all provided zones if more than one zone is provided The virtual machine and the corresponding disk are placed in the specified zone (or zones)

### [Azure Shared Image Gallery](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-shared-image-gallery)

Citrix Virtual Apps and Desktops service supports Azure Shared Image Gallery as a published image repository for MCS provisioned machines in Azure. Administrators have the option of storing an image in the gallery to accelerate the creation and hydration of OS disks. This process improves the boot and application launch times for non-persistent VMs

## February 2021

### [Support for Azure Gen2 images](https://docs.microsoft.com/en-us/azure/virtual-machines/generation-2)

You can now provision managed disks using Gen2 VMs in Azure environments to improve boot time performance

### [Extended support for Citrix Managed Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/#citrix-managed-azure)

Citrix Managed Azure is now available in the following Citrix Virtual Apps and Desktops service editions: Standard for Azure, Advanced, Premium, and Workspace Premium Plus

### [Support for placing master images in Azure Shared Image Gallery](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-master-image)

Studio now provides you an option to place master images in Azure Shared Image Gallery (SIG). SIG is a repository for managing and sharing images. It lets you make your images available throughout your organization.

Citrix recommend that you store a master image in SIG when creating large non-persistent machine catalogs because doing that enables faster reset of VDA OS disks

### [Retain system disk for MCS machine catalogs in Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#enabling-mcs-storage-optimization-updates)

Studio now lets you control whether to retain system disks for VDAs during power cycles. Ordinarily, the system disk is deleted on shutdown and recreated on startup. This ensures that the disk is always in a clean state but results in longer VM restart times. If system writes are redirected to the cache and written back to the cache disk, the system disk remains unchanged.

To avoid unnecessary disk recreation, use the Retain system disk during power cycles option, available on the Machine Catalog Setup > Disk Settings page. Enabling the option reduces VM restart times but increases your storage costs. The option can be useful in scenarios where an environment contains workloads with sensitive restart times

### [Studio now supports creating MCS machine catalogs with persistent write-back cache disk](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#enabling-mcs-storage-optimization-updates)

Previously, PowerShell was your only choice to create a catalog with persistent write-back cache disk. You can now use Studio to control whether the write-back cache disk persists for the provisioned VMs in Azure when you are creating a catalog. If disabled, the write-back cache disk is deleted during each power cycle to save storage costs, causing any data redirected to the disk to be lost.

To retain the data, enable the Use persistent write-back cache disk option, available on the Machine Catalog Setup > Disk Settings page.

## January 2021

### [Azure Shared Image Gallery](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#configure-shared-image-gallery)

**Details:**  Citrix Virtual Apps and Desktops service supports Azure Shared Image Gallery as a published image repository for MCS provisioned machines in Azure. Administrators have the option of storing an image in the gallery to accelerate the creation and hydration of OS disks from the master image. This process improves the boot and application launch times for non-persistent VMs

## December 2020

### [Standard SSD disk type support for Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-master-image)

**Details:**  Studio now adds support for standard SSD disk type. Azure standard SSDs are a cost-effective storage option optimized for workloads that need consistent performance at lower IOPS levels

## October 2020

### [Use direct upload for Azure managed disks](https://azure.microsoft.com/en-us/blog/introducing-the-preview-of-direct-upload-to-azure-managed-disks/)

**Details:**  Direct upload eliminates the need to attach an empty managed disk to a virtual machine. Directly uploading to an Azure managed disk simplifies the workflow by enabling you to copy an on-premises VHD directly for use as a managed disk. Supported managed disks include Standard HDD, Standard SSD, and Premium SSD

### [Single Resource Group in Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html)

**Details:** You can now create and use a single Azure resource group for updating and creating catalogs in Citrix Virtual Apps and Desktops. This enhancement applies to both the full scope and narrow scope service principals. The previous limit of 240 VMs per 800 managed disks per Azure Resource Group has been removed. There is no longer a limit on the number of virtual machines, managed disks, snapshots, and images per Azure Resource Group

## September 2020

### Support for a new machine type

**Details:** This release adds support for the NV v4 and the DA v4 series of AMD machines, when configuring Premium Disks for a machine catalog

## August 2020

### [Improved boot performance for Azure system disks](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#improve-boot-performance)

**Details:** This release supports improved boot performance for Citrix Cloud implementations using Azure when MCSIO is enabled. With this support, you can retain the system disk. This provides the following advantages:

-  VMs and applications now boot and launch with performance similar to how the golden image is served
-  Reduction in API quota consumption, deleting and creating the system disk, and state transition delay caused when you delete a VM
