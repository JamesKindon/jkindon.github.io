---
layout: post
title: "Extending VM Persistent Disks on Nutanix with PowerShell"
permalink: "/nutanix-extend-persistent-disk-powershell/"
categories: [Citrix, PowerShell, Nutanix, API]
description: Programatically extending the size of a Nutanix Disk with PowerShell and the v2 API
image:
  path: /assets/img/nutanix-extend-persistent-disk-powershell/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

Often what you provision, isn't sufficient for what you need a few months down the track.

Let's say for example, you have deployed a Citrix Machine Creation Services (MCS) persistent Catalog with an 80 GiB fixed OS disk. Or maybe you deployed a nonpersistent Catalog and you decided to add an additional data disk. Maybe you even used [Mr Kees Baggermans script](https://blog.myvirtualvision.com/2019/11/19/nutanix-ahv-and-citrix-mcs-adding-a-persistent-disk-via-powershell-v2/) to do so.

If you need to extend the disk capacity on these drives in a programmatic fashion, my preferred meethod on Nutanix infrastructure is via the API.

Here is a [small PowerShell script](https://github.com/JamesKindon/Nutanix/blob/main/ResizeVMDiskAPI.ps1), to help you expand existing disks for one or many machines, using the Prism Element V2 API. Simply specify a list of machines as known to Prism Element, a device bus (typically SCSI so it's the default), a Device Index of the disk (0, 1, 2 for example) and the capacity you want to add in GB. Run it in whatif mode for planning output.

Job done.

The script is also linked in the usual [Script Index](https://github.com/JamesKindon/Nutanix/blob/main/ResizeVMDiskAPI.ps1) portion of this site.
