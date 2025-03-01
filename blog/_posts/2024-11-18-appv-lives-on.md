---
layout: post
title: "A win for common sense – Microsoft App-V lives another day"
permalink: "/appv-lives-on/"
description: "Microsoft flips the coin on App-V EOL"
categories: [Citrix, Windows, AppV, AppVentix, Microsoft]
image:
  path: /assets/img/appv-lives-on/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## A breath of life for App-V

In a rare win for common sense, Microsoft has altered its stance on the impending App-V end of life, logically (and finally) revoking its stance that arguably the most proven app-virt solution globally will be killed off from a support perspective. The impending April 2026 EOL for App-V Client and Sequencer is no more. Huzzah.

App-V has been one of the most consistent and respected options for app virtualization for a long time, and whilst I am not any form of application expert, my time in consulting and continued engagement with customers globally shone, and continues to shine, a clear light that the EOL of App-V was a frightening prospect, leaving organisations confused and not always happy with the options available.

I've heard of some customers so disenfranchised with the options (or costs associated with them) that it's been more appealing to go back to local installs for applications that have been happily packaged in App-V for years. This speaks volumes in my book.

A common point of confusion has been that if the technology works, is stable, and proven, then why the need to kill it off? The simplest answer is simply because Microsoft has a new plaything in the form of MSIX. Everyone loves MSIX right? Everyone...

The latest announcement, or more accurately, changes to existing announcements are not a clear turnaround on everything App-V but make a lot of sense and align to EUC strategies and methodologies that we have discussed with customers for years, predominantly that package delivery has superior options to the App-V server components:

-  The App-V client technology will [remain supported](https://learn.microsoft.com/en-us/microsoft-desktop-optimization-pack/app-v/appv-support-policy#is-there-a-new-end-of-support-date-for-the-app-v-client-and-sequencer). You can run your App-V packages. No more EOL for now. "*The App-V client and sequencer have moved to fixed extended support and is no longer deprecated.*"
-  The App-V sequencer will remain supported. You can continue to create and alter packages. No more EOL for now.
-  The App-V server components [remain EOL](https://learn.microsoft.com/en-us/microsoft-desktop-optimization-pack/app-v/appv-support-policy#are-the-app-v-server-components-still-deprecated) which is just more ammunition and reason to be looking at [AppVentix](https://appventix.com/) (anyone deploying App-V at scale should be looking at this solution). There is no huge loss here. "*The App-V server components are still deprecated and support will end in April 2026*".

This a small plug for a great tool, anyone supporting VDI or DaaS solutions with an App-V presence in the mix, it's more than past time to be looking at how [AppVentix fits in](https://appventix.com/features/). This is one of the best tools to land in the EUC landscape and dramatically simplifies the support, management, deployment, and even conversion of packages at scale. For those hanging onto the App-V Server components, the end is coming, and with a breath of life thrown back to the App-V world, it's surely time to be kicking the old bits out the door.

Interestingly the whole AppAttach world is now open to include App-V packages as well, so for those interested in that approach, MSIX is no longer the only option there.

Tim Mangan has a [good write-up here](https://www.tmurgent.com/TmBlog/?p=3925) around his take on it all, as one of the App-Virt megaminds, it's worth taking note for future and current planning.

I can think of a few organizations that will be happy with this result. A good win I say.
