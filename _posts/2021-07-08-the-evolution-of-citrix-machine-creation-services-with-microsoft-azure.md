---
layout: post
title: The Evolution of Citrix Machine Creation Services with Microsoft Azure
permalink: "/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/"
subtitle: Tracking the progress of Citrix MCS and Microsoft Azure
#cover-img: /assets/img/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/mcs-evolution.png
thumbnail-img: /assets/img/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/mcs-evolution.png
share-img: /assets/img/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/mcs-evolution.png
tags: [Citrix, UPM, Profiles, Windows, CVAD, Cloud, Azure]
categories: [Citrix, UPM, Profiles, Windows, CVAD, Cloud, Azure]
---

![The Evolution of Citrix Machine Creation Services with Microsoft Azure]({{site.baseurl}}/assets/img/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/mcs-evolution.png)

There is a lot of constant improvement being executed by the MCS team at Citrix, the release cadence is impressive and the feature enhancements significant. I spend a lot of time in Microsoft Azure with Citrix Cloud with a lot of happy customers. I thought it would be worth to keep a rolling tally of new features with MCS and how it relates to Azure, so that we don't lose sight of how much value add is provided.

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

It is important to be across the options when designing your delivery platform on Azure, many changes have a direct implication on the ongoing operational costs associated with running workloads on/in Azure, as well as availability and global deployment options. Looking at what we have now, vs what was available 12 months ago, many designs and deployments would look remarkably different.

There is a lot of constant improvement being executed by the MCS team at Citrix, the release cadence is impressive and the feature enhancements significant. I spend a lot of time in Microsoft Azure with Citrix Cloud with a lot of happy customers. I thought it would be worth to keep a rolling tally of new features with MCS and how it relates to Azure, so that we don't lose sight of how much value add is provided.

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

It is important to be across the options when designing your delivery platform on Azure, many changes have a direct implication on the ongoing operational costs associated with running workloads on/in Azure, as well as availability and global deployment options. Looking at what we have now, vs what was available 12 months ago, many designs and deployments would look remarkably different.

## September 2021

| **Feature** | **Detail**
|---|---|
| Support for using a machine profile when deploying MCS workloads in Azure | This option lets you specify which machine profile you want the image to inherit the configuration from when creating VMs in Azure environments. The image can inherit the following configurations from the selected machine profile:<br>- Accelerated networking<br>-  Boot diagnostics<br>- Host disk caching (OS and MCSIO disks)<br>- Machine size (unless otherwise specified),<br>- Tags placed on the VM<br><br>This is awesome. If you have needed to implement my [Accelerated Networking scripts](https://jkindon.com/2020/11/10/enhancing-citrix-mcs-and-microsoft-azure-part-2-accelerated-networking/), then consider using this feature instead
| Support for Windows Server 2022 | Requires minimum VDA 2106

## August 2021

| **Feature** | **Detail**
|---|---|
| [Support for additional Azure storage types](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#storage-types) | You can now select different storage types for virtual machines in Azure environments using MCS
| [Support for selecting the storage type for write-back cache disks](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#enabling-mcs-storage-optimization-updates) | In the Full Configuration management interface, when creating an MCS catalog, you can now select the storage type for the write-back cache disk. Available storage types include: Premium SSD, Standard SSD, and Standard HDD

## June 2021

| **Feature** | **Detail**
|---|---|
| [Access Azure Shared Image Gallery images](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#access-images-from-azure-shared-image-gallery) | When creating a machine catalog, you can now access images from the Azure Shared Image Gallery on the Master Image screen
| Always use standard SSD for an identity disk to reduce cost in Azure environments | Machine catalogs use the standard SSD storage type for identity disks. Azure standard SSDs are a cost-effective storage option optimized for workloads that need consistent performance at lower IOPS levels.<br><br>You can read more about the benefits of this change [here](https://jkindon.com/2020/10/27/enhancing-citrix-mcs-and-microsoft-azure-part-1-identity-disk-cost-optimization/) and utilise the provided scripts to convert existing deployments

## May 2021

| **Feature** | **Detail**
|---|---|
| [Studio supports selecting Azure Availability Zones](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#provision-machines-into-specified-availability-zones) | Previously, PowerShell was the only choice to provision machines into a specific Availability Zone in Azure environments.<br><br>When using Studio to create a machine catalog, you can now select one or more Availability Zones into which you want to provision machines. If no zones are specified, Machine Creation Services (MCS) lets Azure place the machines within the region. If more than one zone is specified, MCS randomly distributes the machines across them
| [Azure ephemeral disk](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-ephemeral-disk) | Citrix Virtual Apps and Desktops service supports Azure ephemeral disk. An ephemeral disk allows you to repurpose the VM cache to store the OS disk for an Azure-enabled virtual machine.<br><br>Ephemeral OS disks require that your provisioning scheme use managed disks and a Shared Image Gallery.
| [Improved performance for MCS managed VDAs on Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-throttling) | This enhancement changes the default values for Absolute Simultaneous actions for the hosting connection to 500, and Maximum new actions per minute for the hosting connection to 2,000. No manual configuration tasks are required to take advantage of this enhancement

## April 2021

| **Feature** | **Detail**
|---|---|
| [MCS I/O support for Azure VMs without temporary storage](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#machine-creation-service-mcs-storage-optimzation) | MCS I/O now supports machine catalog creation for VMs that do not have temporary disks or attached storage
| Support for Azure Gen2 images | You can now provision a Gen2 VM catalog by using either a Gen2 snapshot or a Gen 2 managed disk to improve boot time performance
| Disabling table storage accounts | Machine Creation Services (MCS) no longer creates table storage accounts for catalogs that use managed disks when provisioning VDAs on Azure
| Eliminating locks in storage accounts | When creating a catalog in Azure using a managed disk, a storage account is no longer created. Storage accounts created for existing catalogs remain unchanged. This change is applicable for managed disks only. For unmanaged disks, there is no change in the existing behavior. Machine Creation Services (MCS) continues creating storage accounts and locks
| Use a customer-managed encryption key to encrypt data on machines | Studio adds a setting called Customer-managed encryption key to the Machine Catalog Setup > Disk Settings page. The setting lets you choose whether to encrypt data on the machines to be provisioned in the catalog

## March 2021

| **Feature** | **Detail**
|---|---|
| [Azure dedicated hosts](https://docs.microsoft.com/en-us/azure/virtual-machines/dedicated-hosts) | Azure dedicated hosts allow you to provision virtual machines on hardware dedicated to a single customer. While using a dedicated host, Azure ensures that your virtual machines would be the only machines running on that host. This provides more control and visibility to customers thereby ensuring they meet their regulatory or internal security requirements. <br><br> A pre-configured Azure host group, in the region of the hosting unit, is required when using the HostGroupId parameter. Also, Azure auto-placement is required. <br><br>When using Azure dedicated hosts, selecting the **Azure Availability Zone** has no effect. The virtual machine is placed by the Azure auto-placement process.
| [Support for Azure server side encryption](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-server-side-encryption) | Citrix Virtual Apps and Desktops service supports customer-managed encryption keys for Azure managed disks. With this support you can manage your organizational and compliance requirements by encrypting the managed disks of your machine catalog using your own encryption key
| [Provision machines into specified availability zones on Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#provision-machines-into-specified-availability-zones) | You can now provision machines into a specific availability zone in Azure environments. With this functionality You can specify one or multiple Availability Zones on Azure. Machines are nominally equally distributed across all provided zones if more than one zone is provided The virtual machine and the corresponding disk are placed in the specified zone (or zones)
| [Azure Shared Image Gallery](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#azure-shared-image-gallery) | Citrix Virtual Apps and Desktops service supports Azure Shared Image Gallery as a published image repository for MCS provisioned machines in Azure. Administrators have the option of storing an image in the gallery to accelerate the creation and hydration of OS disks. This process improves the boot and application launch times for non-persistent VMs

## February 2021

| **Feature** | **Detail**
|---|---|
| [Support for Azure Gen2 images](https://docs.microsoft.com/en-us/azure/virtual-machines/generation-2) | You can now provision managed disks using Gen2 VMs in Azure environments to improve boot time performance
| [Extended support for Citrix Managed Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/#citrix-managed-azure) | Citrix Managed Azure is now available in the following Citrix Virtual Apps and Desktops service editions: Standard for Azure, Advanced, Premium, and Workspace Premium Plus
| [Support for placing master images in Azure Shared Image Gallery](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-master-image) | Studio now provides you an option to place master images in Azure Shared Image Gallery (SIG). SIG is a repository for managing and sharing images. It lets you make your images available throughout your organization. <br><br>Citrix recommend that you store a master image in SIG when creating large non-persistent machine catalogs because doing that enables faster reset of VDA OS disks
| [Retain system disk for MCS machine catalogs in Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#enabling-mcs-storage-optimization-updates) | Studio now lets you control whether to retain system disks for VDAs during power cycles. Ordinarily, the system disk is deleted on shutdown and recreated on startup. This ensures that the disk is always in a clean state but results in longer VM restart times. If system writes are redirected to the cache and written back to the cache disk, the system disk remains unchanged. <br><br>To avoid unnecessary disk recreation, use the Retain system disk during power cycles option, available on the Machine Catalog Setup > Disk Settings page. Enabling the option reduces VM restart times but increases your storage costs. The option can be useful in scenarios where an environment contains workloads with sensitive restart times
| [Studio now supports creating MCS machine catalogs with persistent write-back cache disk](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#enabling-mcs-storage-optimization-updates) | Previously, PowerShell was your only choice to create a catalog with persistent write-back cache disk. You can now use Studio to control whether the write-back cache disk persists for the provisioned VMs in Azure when you are creating a catalog. If disabled, the write-back cache disk is deleted during each power cycle to save storage costs, causing any data redirected to the disk to be lost. <br><br>To retain the data, enable the Use persistent write-back cache disk option, available on the Machine Catalog Setup > Disk Settings page.

## January 2021

| **Feature** | **Detail**
|---|---|
| [Azure Shared Image Gallery](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#configure-shared-image-gallery) | Citrix Virtual Apps and Desktops service supports Azure Shared Image Gallery as a published image repository for MCS provisioned machines in Azure. Administrators have the option of storing an image in the gallery to accelerate the creation and hydration of OS disks from the master image. This process improves the boot and application launch times for non-persistent VMs

## December 2020

| **Feature** | **Detail**
|---|---|
| [Standard SSD disk type support for Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html#create-a-machine-catalog-using-an-azure-resource-manager-master-image) | Studio now adds support for standard SSD disk type. Azure standard SSDs are a cost-effective storage option optimized for workloads that need consistent performance at lower IOPS levels

## October 2020

| **Feature** | **Detail**
|---|---|
| [Use direct upload for Azure managed disks](https://azure.microsoft.com/en-us/blog/introducing-the-preview-of-direct-upload-to-azure-managed-disks/) | Direct upload eliminates the need to attach an empty managed disk to a virtual machine. Directly uploading to an Azure managed disk simplifies the workflow by enabling you to copy an on-premises VHD directly for use as a managed disk. Supported managed disks include Standard HDD, Standard SSD, and Premium SSD 
| [Single Resource Group in Azure](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/resource-location/azure-resource-manager.html) | You can now create and use a single Azure resource group for updating and creating catalogs in Citrix Virtual Apps and Desktops. This enhancement applies to both the full scope and narrow scope service principals. The previous limit of 240 VMs per 800 managed disks per Azure Resource Group has been removed. There is no longer a limit on the number of virtual machines, managed disks, snapshots, and images per Azure Resource Group

## September 2020

| **Feature** | **Detail**
|---|---|
| Support for a new machine type | This release adds support for the NV v4 and the DA v4 series of AMD machines, when configuring Premium Disks for a machine catalog

## August 2020

| **Feature** | **Detail**
|---|---|
| [Improved boot performance for Azure system disks](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#improve-boot-performance) | This release supports improved boot performance for Citrix Cloud implementations using Azure when MCSIO is enabled. With this support, you can retain the system disk. This provides the following advantages: <br>- VMs and applications now boot and launch with performance similar to how the golden image is served <br>- Reduction in API quota consumption, deleting and creating the system disk, and state transition delay caused when you delete a VM

