---
layout: post
title: "Sync Citrix Tags and Nutanix Categories"
permalink: "/citrix-tags-nutanix-categories-sync/"
description: "Using Citrix and Nutanix APIs to sync Tags and Categories"
categories: [Citrix, Nutanix, PC, Prism, DaaS, PowerShell, Playbooks, Tags, Categories]
image:
  path: /assets/img/citrix-tags-nutanix-categories-sync/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

New year new toys, (well that would be kind of a lie given we released it last year, but hey, it sounds neat), welcome to 2025.

For anyone managing Nutanix environments, you will have noticed we are quite fond of our Categories and use them heavily to control many aspects of the environment. A Prism Central construct, Categories drive our Disaster Recovery, Automation, Storage and Network Security policies.

Today, if you manage a Citrix solution running on Nutanix, you will likely have some use case for Categories. Most folks do in one way or another.

There is a good chance also that you are using Citrix Tags somewhere in your estate, Tags perform somewhat of a similar function in the Citrix world, really kind of being used as a "marker" for other things to use – Autoscale, resource launch, policy filtering etc.

Unfortunately, today, the two constructs whilst similar, are also completely independent of each other. Prism Central has zero idea about Citrix Tags, and Citrix has absolutely no idea about a Prism Central Category, so to manage either, you drive the bus from the home solution: PC for Categories and Studio for Tags.

Be kind of neat if you could Tag a resource in Citrix and have its corresponding Nutanix VM assigned a Category in Prism, and also be neat if you could assign a Category in Prism and have it assign a Tag in studio. Hello automation.

Both Citrix and Nutanix provide API access to their respective platforms, so with a bit of logic and some PowerShell, we can automate the synchronization between the two platforms.

You can [read up on the root logic here](https://www.nutanix.dev/2023/07/26/managing-categories-for-euc-workloads-in-prism-central/), basically a sync capability allowing you to sync Tags and Categories in a two-way fashion – this gives you the ability to handle full provisioning etc. at the Citrix level and then ensure that by assigning the appropriate Tag in Studio. the corresponding Nutanix VMs get a Category assigned. And vice versa, if you make a change in Prism Central, and want that change to be reflected in Citrix Tags, you can do that too. Cool right? I thought so.

There are loads of ways to execute this sort of thing in a scheduled fashion, however, Nutanix being Nutanix, there is a nice little automation option built right into our platform in the form of playbooks. So here is a [follow up post](https://www.nutanix.dev/2024/12/18/synchronizing-nutanix-prism-central-categories-and-citrix-tags-using-prism-central-playbooks/) walking you through how to configure playbooks to automatically execute the above code on a schedule, or anything else that you can trigger a playbook on – the possibilities are pretty much endless.

There is a whole load of controls and safety built into the framework, and you are welcome to extend and expand as you see fit.

Happy syncing. A [direct link to GitHub](https://github.com/nutanixdev/euc-samples/tree/main/citrix/categories/sync_pc_categories_to_citrix_tags ) is provided for your enjoyment.
