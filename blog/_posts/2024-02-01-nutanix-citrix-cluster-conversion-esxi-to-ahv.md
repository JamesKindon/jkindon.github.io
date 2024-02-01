---
layout: post
title: Switching your Citrix Workloads on Nutanix Clusters from ESXi to AHV
permalink: "/nutanix-citrix-cluster-conversion-esxi-to-ahv/"
categories: [Citrix, Nutanix, VDI, ESXi, AHV]
description: Switch your Nutanix clusters running Citrix workloads from ESXi to AHV
image:
  path: /assets/img/nutanix-citrix-cluster-conversion-esxi-to-ahv/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

Customers across the globe have enjoyed Citrix workloads running on VMWare ESXi with Nutanix Cloud Infrastructure for many years.

In some scenarios, the choice to use ESXi was made because it was known and was a logical decision. For others, AHV may not have had the relevant feature set required at the time.

[Nutanix AHV](https://www.nutanix.com/au/products/ahv) is an enterprise-grade, proven hypervisor that supports Citrix deployments all over the world at a significant scale. All Nutanix customers are entitled to it.

Regardless of the original reason for choosing ESXi, given the current state of the industry, it's likely time to visit whether you need to pay for an additional hypervisor for your Citrix workloads.

Additionally, moving to AHV unlocks the simplicity and power of Nutanix Cloud Clusters (NC2) allowing a single hypervisor to be deployed across multiple data centers, and private or public cloud providers such as Azure and AWS. This is a [compelling story for Citrix workloads](https://portal.nutanix.com/page/documents/solutions/details?targetId=RA-2191-Citrix-DaaS-NC2Z-MCS-Windows-10:RA-2191-Citrix-DaaS-NC2Z-MCS-Windows-10).

Switching your Citrix environment from ESXi to AHV may seem like a significant task, however, the recent guide published by the solutions engineering team [has you covered](https://portal.nutanix.com/page/documents/solutions/details?targetId=BP-2157-Migrate-Citrix-to-Nutanix-AHV-from-ESXi:BP-2157-Migrate-Citrix-to-Nutanix-AHV-from-ESXi).

We provide guidance on migrating:

-  Citrix Provisioning (PVS) based deployments.
-  Citrix Machine Creation Services (MCS) based deployments.
-  Standard workloads without any provisioning.

We also provide best practices collateral for deploying your Citrix solutions on Nutanix with a focus on AHV:

-  [Citrix Virtual Apps and Desktops on Nutanix](https://portal.nutanix.com/page/documents/solutions/details?targetId=BP-2079-Citrix-Virtual-Apps-and-Desktops:BP-2079-Citrix-Virtual-Apps-and-Desktops)
-  [Citrix DaaS on Nutanix](https://portal.nutanix.com/page/documents/solutions/details?targetId=BP-2062-Citrix-Virtual-Apps-and-Desktops-Service:BP-2062-Citrix-Virtual-Apps-and-Desktops-Service)
