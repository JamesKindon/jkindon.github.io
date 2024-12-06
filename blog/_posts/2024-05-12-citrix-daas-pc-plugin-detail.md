---
layout: post
title: "Citrix DaaS Native Integration with Nutanix Prism Central"
permalink: "/citrix-daas-pc-plugin-detail/"
description: "Some more indepth detail about the PC integration from Citrix"
categories: [Citrix, Windows, Nutanix, PC, Prism, DaaS]
image:
  path: /assets/img/citrix-daas-pc-plugin-detail/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

Customers running the Citrix workloads on Nutanix AHV have been used to integrating Citrix Machine Creation Services (MCS) and Citrix Provisioning (PVS) at the cluster level via Prism Element, using a co-developed plugin. This meant that each cluster would have its own Hosting Connection and was both a management and workload boundary.

Nutanix Prism Central offers a whole suite of advanced functionality and capability within the Nutanix stack. Multi-cluster management, advanced networking, security, disaster recovery, VM provisioning, automation tooling, and all sorts of other juicy features.

As customers grow, and more clusters are added to the mix, centralised management becomes an important part of the puzzle. Additionally, as more features are introduced, and organizations use more and more of what Prism Central has to offer, the demand/need for Citrix integration to support Prism Central has become more apparent, and in some scenarios, mandatory.

Nutanix released a plugin for our Azure NC2 customers, which allowed, for this specific scenario, MCS to integrate with Prism Central and the associated network constructs. This is primarily due to some Azure defined requirements for our NC2 stack where the usual plugins were no longer able to be consumed. This laid the groundwork for where we are today.

History aside, as per the [recent Citrix announcement](https://www.citrix.com/blogs/2024/10/21/now-in-tech-preview-introducing-citrix-integration-with-nutanix-prism-central-on-ahv/), there is now available, for Citrix DaaS, a technical preview of a Citrix managed Nutanix Prism Central Plugin for customers to consume, bringing the Nutanix PC integration native. It has been aptly named: **Citrix integration with Nutanix Prism Central (PC) on AHV**.

## What's The Big Deal?

Why is this exciting and how does it impact our customers? Below is a brief outline:

-  The Nutanix PC integration is 100% developed and supported by Citrix.
-  There are no more plugins to be installed on Delivery Controllers or Cloud Connectors.
-  Integration with Prism Central allows for advanced networking (VPC Overlay networks) to be consumed as part of the provisioning process. This is great news for customers using VPCs.
-  Prism Central Templates allow for the deployment of virtual machines across multiple clusters using a single image (Template) which is available across all clusters under the same PC.
-  The new plugin capability can be enabled and tested side by side with Nutanix Prism Element integration. They are not mutually exclusive.

Citrix has even provided a migration path for our customers running in Azure NC2 today, consuming the Nutanix PC plugin. The ability to switch seamlessly to the Citrix native integration is a nice win for those customers.

This is a tech preview release as of today. Once, enabled, you get a nice new Hosting Connection type show up in your list.

[![PC Hosting]({{site.baseurl}}/assets/img/citrix-daas-pc-plugin-detail/pc_hosting.png)]({{site.baseurl}}/assets/img/citrix-daas-pc-plugin-detail/pc_hosting.png)

## Common Questions and Current State of Play

This is not an official Nutanix release post, this is just some general guidance at a technical level. The answers to a few common questions and the current state of play are below:

-  The new release is currently for Citrix DaaS customers only. This will come to CVAD customers, but as of today, it's Citrix DaaS.
-  Citrix PC integration uses AHV Templates for MCS Catalog provisioning. A Template is a PC construct. Our current plugins with PE use VM Snapshots. A Snapshot is a PE construct. To use the same image you have today, you will need to create a Template in PC. You can use the same VM that you use to create a Snapshot, as the VM to create a Template.
-  For customers familiar with Prism Central Templates and their versioning capability, it's important to note that today, only the **Active** Version of the Template in Prism Central is used for provisioning. You cannot select a different version of the Template when looking at it from a PC Template construct logic. If you create a new version of the Template, you must make that version Active, and then update the Citrix Catalog by selecting the Template again. All operations, be it create, update or rollback honor only the active Template version. Alternatively, you can create a new Template from the source VM. Either approach is fine.
-  For customers using Prism Element integration today who want to move to Prism Central, the following logic applies:
    -  For MCS nonpersistent Catalogs, simply deploy a new Catalog using a PC Template and replace your existing Catalog.
    -  For MCS persistent deployments, switch the existing machines to a manual power managed Catalog, then switch their hosting connections. You can do this in a one-step (migrate to PC power managed) or two-step (migrate to PE power-managed first, then PC power managed next) approach. This is currently handled with [PowerShell logic](https://github.com/JamesKindon/Citrix/tree/master/Migration%20Scripts/MigrateMCSToManual).
-  If you have machines that are manually provisioned and power managed via Prism Element today, you can re-map those machines to the Prism Central hosting connections and retain power management. An unofficial [example script can be found here](https://github.com/JamesKindon/Citrix/blob/master/Migration%20Scripts/MigrateDedicatedMachines/Nutanix/MigrateDaaSHostedMachineFromPEtoPC.ps1)
-  The new release supports MCS and manual machine deployments. For Citrix Provisioning to use the Virtual Apps and Setup Wizard, you need to stay with the PE plugin today. Reach out to us for a discussion if you have requirements/questions about this. We can chat through the logic and options. [Nutanix Solutions on Bluesky](https://bsky.app/profile/nutanixsolutions.bsky.social) or our usual contact details.
-  You will still deploy a Catalog per Cluster, however, you have the benefit of a single hosting connection to manage those clusters, and you can use a single template image across those multiple clusters.
-  If you use multiple PC deployments with an Availability Zone architecture, then you will need a hosting connection to each PC deployment. That hosting connection will unlock the clusters managed beneath. You will need to replicate the image between PC instances. A known construct when comparing against other solution integrations.
-  You will still need a full admin account for integration. There is no RBAC support today.
-  Your new hosting connection from Citrix will come with low action concurrency (10) per minute. You can up these to a more suitable value in your environment, you should test and validate the appropriate setting.
-  From a multi-cluster networking standpoint, if you are going to continue to use VLAN backed networks (the new plugin supports Overlay networks too), then you are going to have a more enjoyable experience today if each of your networks has different names in each cluster (for example, **Network1_Cluster1** and **Network1_Cluster2** rather than **Network1** on each cluster)

## Wrapping Up

The biggest benefit to customers today will likely be the ability to deploy a single image across multiple clusters without needing to think about replicating the images around (this isn't hard today, you can read [here for more detail](https://jkindon.com/multi-cluster-image-replication-citrix-mcs-nutanix/)). Additionally, being able to utilize overlay networking is extremely powerful. What is exciting beyond this, is the sheer opportunity for integration between Citrix and Nutanix solutions moving forward. By moving the initial provisioning tasks to Prism Central, we have unlocked the ability to start now really thinking about innovation between the two solutions. The road ahead is exciting.
