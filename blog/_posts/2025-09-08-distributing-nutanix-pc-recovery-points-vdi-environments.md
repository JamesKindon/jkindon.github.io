---
layout: post
title: Distributing Prism Central Recovery Points for VDI Environments
permalink: "/distributing-nutanix-pc-recovery-points-vdi-environments/"
categories: [Citrix, MCS, Omnissa, Horizon, PowerShell, Nutanix, HCI, Prism]
description: Automating The Replication of EUC Images on Nutanix
image:
  path: /assets/img/distributing-nutanix-pc-recovery-points-vdi-environments/post_default_image.jpg
sitemap: true
hide_last_modified: true
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

In many Nutanix deployments, VDI environments often represent many VMs, clusters, and distributed Prism Centrals. Any well-architected VDI solution, at scale, will align to a block and pod architecture, ensuring that pods can self-sustain and scale as required.

With these architectures, a common scenario arises: How do you keep gold images in sync between clusters, to ensure a consistent deployment across one or many pods (clusters)?

There are many ways to address this challenge, and there are previously provided script examples for replicating images with Nutanix Protection Domains and replicating images with Nutanix Prism Central Protection Policies in a [previous post](https://jkindon.com/multi-cluster-image-replication-citrix-mcs-nutanix/).

This option is focused on the Prism Central Recovery Point object itself, rather than automating the disaster recovery solutions that use these Recovery Points. This script example outlines a method of scaling replication outside the limits of disaster recovery constructs such as Protection Domains and Protection Policies.

It operates in a mesh logic, attempting to self learn and replication outbound to learned entities from a single source of truth. The script should server as an example of how to perform many Nutanix based tasks using the API and PowerShell.

## Summary and Technical Bits

The solution provided here utilises the Prism Central V4 API for all PC operations, and the Prism Element V2 API for any cluster level operations such as Snapshot creation. It runs in PowerShell 7 only, and if utilised in conjunction with the Citrix auto Catalog update option, will use the CVAD or DaaS API to update one or many Catalogs aligned to the pods.

You can read up on more detail over at [nutanix.dev](https://www.nutanix.dev/2025/08/06/distributing-prism-central-recovery-points-for-vdi-environments/), and the script is [available here on GitHub](https://github.com/nutanixdev/euc-samples/tree/main/DistributePCRecoveryPoints)
