---
layout: post
title: "Citrix MCS Multi Catalog Updates – ProvScheme Mechanics with the Citrix API for Nutanix"
permalink: "/citrix-mcs-catalog-provscheme-mechanics-citrix-api-nutanix/"
categories: [Citrix, MCS, Provisioning, PowerShell, Nutanix, API]
description: Updating Multiple Catalogs with a Single Nutanix Image using the Citrix Rest API
image:
  path: /assets/img/citrix-mcs-catalog-provscheme-mechanics-citrix-api-nutanix/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

I spend a fair bit of time with Citrix MCS, it’s a wonderful provisioning solution that the industry has enjoyed for a long time.

Many environments have multiple MCS *Catalogs*. Each *Catalog*, when deployed using MCS, is tied to an image via the *Provisioning Scheme* construct. This is captured as the `ProvisioningScheme.MasterImage.Name` attribute when consuming the API. That image may be used across multiple different *Catalogs*.

For example, in the Nutanix world, our hosting is currently linked to a Nutanix Cluster via Prism Element, so when we have multiple *Clusters*, we have multiple *Catalogs*, those multiple *Catalogs* may all share the same image which is replicated around the hosting layer to the multiple different Clusters.

In the below image, you can see a rough mockup of how the *ProvScheme* is linked to a *Catalog* and a specific *Hosting Connection*. You can also see the indicative relationship between the image defined on the *ProvScheme* and the associated snapshot on the Nutanix Clusters. These are identified as the coloured objects A, B, and C.

[![platforms]({{site.baseurl}}/assets/img/citrix-mcs-catalog-provscheme-mechanics-citrix-api-nutanix/hosting.png)]({{site.baseurl}}/assets/img/citrix-mcs-catalog-provscheme-mechanics-citrix-api-nutanix/hosting.png)

This update process can be a touch tedious to manage in Studio, it typically means navigating to each *Catalog* and selecting an update job, trawling the *Hosting Connection* for the updated snapshot, and then proceeding with the usual update wizard options.

Lucky for us, there are automation options to help make things nice and fast. Less clicks, more happiness.

## PowerShell Scripting with the Citrix API

I'm sharing a small script that I have written which leverages both the Citrix DaaS and the new Citrix Virtual Apps and Desktops API to handle *Catalog* updates with zero snapins and zero dependencies outside of PowerShell 7, a version of CVAD that supports the API (or DaaS), and appropriate credentials.

The idea of this script is that you can define multiple *Catalogs* within a single *Site* boundary, and a single image name, and have all *Catalogs* updated programmatically. The script uses the *Hosting Connection* defined on *ProvScheme* associated with the *Catalog* (for the nerds, that's the `ProvisioningScheme.ResourcePool.Hypervisor`) to validate that the image you have supplied is reachable. If it is, then it will clap its hands with joy, and proceed to validate the next *Catalog*. For any that can't reach the snapshot, they are ignored.

Once certain that all is well and happy, each *Catalogs* *ProvScheme* is simply updated to reflect the new image, pending the next reboot. Happy times.

What you are responsible for:

-  Ensuring the image/snapshot is replicated to all clusters with an identical name. You can read [more on this here](https://jkindon.com/multi-cluster-image-replication-citrix-mcs-nutanix/).
-  Ensuring you use a CVAD site with the API available. The API was made generally available via CR 2303. It will be in place for the next LTSR drop as well.
-  Providing Credentials. For CVAD, this is via a username and password param (read the notes) and for DaaS, this is preferably via a [SecureClient](https://developer-docs.citrix.com/en-us/citrix-cloud/citrix-cloud-api-overview/get-started-with-citrix-cloud-apis.html#create-an-api-client). Read the notes for options.
-  Rebooting the machines per your usual standards. This script is not touching reboot jobs.

This script is currently scoped for only Nutanix hosting support; however, this is a pretty simple concept to expand on based on your environment and hosting construct. The script currently does a quick validation of the hypervisor against a supported list, then sets the `MasterImagePath` to the appropriate format, and processes an update. You can alter both the supported list and the path manipulation as you see fit. The rest is standard Citrix Rest API work.

## Summary and Download

This is a basic utility, but I have been very much enjoying breaking away from Citrix legacy snapins and being able to process common tasks via the Rest API. This opens the platforms that you can execute your code from. Farewell `asnp Citrix*`

You can [download the script from here](https://github.com/JamesKindon/Citrix/blob/master/QuickCatalogUpdate.ps1). It's also added to the [script index here](https://jkindon.com/ScriptIndex/).