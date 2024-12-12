---
layout: post
title: "Citrix aquires deviceTRUST. Why this is Awesome"
permalink: "/citrix-and-device-trust/"
description: "Some basics about deviceTRUST and why it's awesome"
categories: [Citrix, Windows, deviceTRUST, EUC, DaaS]
image:
  path: /assets/img/citrix-and-device-trust/post_default_image.png
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

The [announcement by Citrix on their latest acquisitions of deviceTRUST and Strong Networks](https://www.citrix.com/blogs/2024/12/10/citrix-acquires-devicetrust-and-strong-network/) is massively cool. Both solutions offer some unreal functionality. In this post, I am going to focus on the more exciting of the two (to me) in deviceTRUST.

## What is deviceTRUST?

For those that haven't come across deviceTRUST before, then welcome to the party baby. This solution is easily one of the single most useful and powerful capabilities to hit the EUC industry. It is a capability that every single customer I have ever met would have had some form of use case for, even if they didn't actively know it.

So, what's the deal with deviceTRUST and why does it make sense for Citrix to pick it up?

Firstly, this is a solution focused on security. Not just boring old security bits and bobs though, DT brings in contextual-based security which is aware of what is now and what changes dynamically (in real-time).

The solution is aimed around the concept of "*if you don't trust the device posture that connects to your virtual workloads, then why would you let it in*" or more aptly, "*what are you going to do about it?*". It also has a stance of "*even though you trusted the device at the start, what happens if something changes to that device – do you still trust it*"?

Secondly, DT is more than just security; it also offers the ability to dynamically control an environment based on dynamically changing conditions. Scenarios such as users roaming around different locations or floors within a business, and dynamically adding or removing printers based on those locations is a great example of immediate contextual-based actions. The network changes, so there is now a better set of printers to use – make it so.

## The Nuts and Bolts

A few basic constructs to paint the picture of how this thing works:

The **Device**. This is the endpoint that you are connecting from. Be it a Windows Notebook, A physical machine, an IGEL endpoint, etc.

The **Context**. A set of attributes or properties associated with the device. This could be antivirus status, Windows Firewall status, peripherals connected, networks, regional locations, software installed, etc. Contexts are dynamic, meaning that they can change.

There are a range of different contexts for different devices.

[![Contexts 1]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_contexts_1.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_contexts_1.png)

[![Contexts 2]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_contexts_2.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_contexts_2.png)

An **Action**. What do you want to do based on a good context, or a changed context? For example, If you mandate that you require the Windows Firewall to be active on the device, what should we do if it is not running? Or more importantly, what should we do if the status **changes** after the initial session is active?

[![Actions]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_actions.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_actions.png)

The **Protected Resource**. This is what you are actioning the protections against. The best example is a VDI session delivered by Citrix. If something changes on the endpoint device, we want to do something to protect the virtual desktop.

There are three touchpoints for the solution to work:

1.  You need to have the deviceTRUST **agent** on your protected infrastructure.
2.  You need to have the **client extension** installed on the endpoints you looking to understand and monitor. This extension is the first context in the mix. If it’s not there, you can simply block access, and provide a range of different notifications, instructions, or actions to get it there.
3.  You need to define **policies** for the solution to operate. This is as simple as nesting the deviceTRUST controls into a Group Policy or driving from the console. You apply the policies to your protected resources.

There is a whole load of different actions that can be taken on any number of different conditions (contexts). A small list below of ones I found historically interesting:

-  Dynamically write Windows Firewall rules in the remote session to block or allow access to certain resources.
-  Dynamically write FSLogix AppMasking rules to prevent access to certain applications or resources within a virtual session.
-  Terminate a process. Combine this with the above to both kill and hide the process from being available until the device is trusted again.
-  Map a drive, remove a drive, map a printer, or remove a printer. Pretty handy when you think about people roaming around different locations or floors.
-  Lock a session with a warning to the user and information on how to remediate.
-  Disconnect a session immediately – terminate access.
-  Write a dynamic AppLocker rule.
-  Execute a custom business-specific process or task – the possibilities are endless.

## Conditional Access vs Contextual Access

A quick note here on Conditional Access vs Contextual Access. Condition Access is part of the solution really – it typically is actioned or assessed at the beginning of a session connection. Contextual Access is about monitoring for any changes to those conditions and executing controls accordingly.

Think of EPA from Citrix or Conditional Access from Microsoft as examples of conditional access (not going into proactive remediation tech here). A request is made for a resource, a check is executed to ensure certain access conditions are met (maybe my firewall is running), and access is granted access. Job done. But what happens when that firewall service stops?

deviceTRUST based *Contextual Access* addresses the real-time assessment of the specific access criteria and makes sure it’s always met. If it’s not (the firewall is turned off), then the access conditions are no longer ok. The firewall context changed, and the device is no longer trusted, so it’s time to action something.

## Example Use Cases and Scenarios

There are a range of things that can be detected, actioned, and controlled, and any combination you think of is likely possible. Some interesting use cases that are easily addressable and likely resonate with those who play in the VDI space:

1.  Healthcare scenarios, where practitioners or staff roam around different areas of a hospital and connect to different networks. You want to restrict specific data or applications in a remote VDI session from being accessible from a cafeteria (patient data anyone?) but you want to still have connectivity into the resource for other tasks such as looking at emails or browsing the web.
2.  A scenario where only approved external devices such as storage media are approved. If someone plugs in a non-approved device, you want to block all access to redirected drives, mapped drives, internal resources, etc. Or maybe you want to lock the session entirely until the device is removed. Maybe both?
3.  The device changes geographical locations and you no longer want certain applications or internal resources to be accessed in any way.
4.  The device has the wrong version of Citrix Workspace App or some other endpoint software that is critical for your environment to function. You can mandate no access to the environment until this is remediated, and you can point the user on how to remediate it.

## Some Control Examples

Straight from the lab....

Here is a nice simple policy that checks the following:

-  Is the device Trust Client available? If not, then block access and tell the user how to remediate.
-  Is an unauthorized USB device plugged in? If it is not, then we are good to go, but if it is, then block access to the session, and tell the user why. When it’s removed, let them in.
-  If they plug it back in after the fact (the context changes), block access to the session again.

[![Example 1]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_1.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_1.png)

Here is a policy that checks If the device connecting from an unapproved network. If so, block the session:

[![Example 2]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_2.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_2.png)

Here is one that unmaps network drives when the device is on Wi-Fi, and then remaps the drive I the device switches back to a LAN network.

[![Example 3]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_3.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_3.png)

Here is a demo example of AppMasking Notepad++ and terminating the process based on an insecure Wi-Fi being detected:

[![Example 4]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_4.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_4.png)

From a user standpoint, if they are on a secure wireless environment, they have a shortcut to Notepad++. If they move to another wireless environment that is not defined as secure, then a dynamic masking rule is written, and Notepad++ is terminated. If they move back to the secure wireless, the rule is removed, and the shortcut is put back in place.

Here is a bit more of a fun example

[![Example 5]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_5.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_5.png)

This one does a few things. If the endpoint is on a secure Wi-Fi environment, then the following exists:

-  A shortcut to a couple of portals
-  A mapped drive to a secure share within the VDI environment

If the device changes to an insecure environment like Maccas Wi-Fi then:

-  The user will be prompted with a message telling them stuff is about to go down – and why.
-  A Windows Firewall rule will be written within the virtual desktop which blocks access to several secure internal sites.
-  The secure drive will be unmapped.
-  A custom process will be executed (in this case, a simple drive removal but you get the drift).
-  A Citrix Policy will be written to prevent any client drive mappings from occurring (this is governed by the rules of Citrix policy application).

And finally, here is another small example of blocking access to a session if a network drive is mapped on the endpoint to something you are not happy with:

[![Example 6]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_6.png)]({{site.baseurl}}/assets/img/citrix-and-device-trust/dt_example_6.png)

## Closing

What is important and exciting about both acquisitions here, is that it is the first time in a long time that Citrix has made targeted investments that focus on what they do, and have always done better than anyone else, which is application and desktop delivery, but also ties in with their focus on security.

One might rightly wonder what the play is here given Citrix has NetScaler EPA, Workspace Environment Management, Device Posture Service and I am sure there are others I have missed. I think (this is my opinion) the answer is simple. This is a complimentary solution that will resonate with all of Citrix’s focus moving forward. It has led the way in contextual awareness and adaptive controls for a long time. It comes from a great pedigree as far as who developed the initial technology set (there are some familiar names there if you go digging) and it aligns perfectly for an enhanced security capability around VDI.

I cannot wait to see the use cases and benefits that customers are going to be able to achieve with these solutions. The capability is immense.
