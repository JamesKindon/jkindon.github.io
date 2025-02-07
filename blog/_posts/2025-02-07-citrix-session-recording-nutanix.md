---
layout: post
title: "Citrix Session Recording on Nutanix"
permalink: "/citrix-session-recording-nutanix/"
description: "Delving into sizing and archiecture for Citrix Session Recordingon Nutanix"
categories: [Citrix, Nutanix, DaaS, Session Recording]
image:
  path: /assets/img/citrix-session-recording-nutanix/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

[Citrix Session Recording](https://docs.citrix.com/en-us/session-recording/current-release.html) is one of the not-so-talked-about hidden gems of the Citrix estate, it’s a solution that allows administrators to capture and record user sessions for monitoring and troubleshooting purposes.

This solution is beneficial in environments where security and compliance are critical, as it provides clear insights into user activities. It is a pretty flexible solution, with all sorts of triggers and policy controls to ensure you capture either everything, nothing, or anything in between.

Session Recording can also help admin and support staff identify and resolve issues quickly by watching exactly what occurred in the user session.

Session Recording adds to the [proper VDI is more than just a connection to a desktop](https://jkindon.com/finding-the-value-in-your-citrix-investment/) story and adds a critical weapon to an organization's arsenal. Best of all, it sits within existing entitlements, ready to go.

The challenge with Session Recording is understanding how to size it properly. Many factors come into play, both technical and organizational, which can impact what and when recordings occur.

Data sets can be substantial (though they are significantly compressed), making server sizing a crucial aspect of the solution. How you store and secure these data sets is an essential part of the architecture.

Here is a [newly released Reference Architecture for deploying Citrix Session Recording on Nutanix solutions](https://portal.nutanix.com/page/documents/solutions/details?targetId=TN-2179-Citrix-Session-Recording-Nutanix:TN-2179-Citrix-Session-Recording-Nutanix). We put SR through its paces and identified all sorts of useful information and considerations, be it for local disk storage, Nutanix Files storage, or just understanding how the data flows and where the considerations are for scale, this document sheds some light and helps you to gain a better understanding of the solution and how to architect it properly.

Whilst a Nutanix focused document, some gems in there will likely pique the interest of anyone in our space.

Enjoy.
