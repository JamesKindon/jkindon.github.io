---
layout: post
title: Finding the value in your Citrix investment
permalink: "/finding-the-value-in-your-citrix-investment/"
categories: [Citrix, Cloud, VDI, DaaS]
description: Are you maximizing the value from your Citrix investment?
image:
  path: /assets/img/finding-the-value-in-your-citrix-investment/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

This post is an attempt to help current Citrix customers who are feeling the pinch of changes occurring within both Citrix under Cloud Software Group (CSG) and the EUC industry in general, understand what they have at their fingertips in a Citrix technology stack whilst assessing their next steps.

CSG has made significant changes to the way they sell Citrix, both in the pricing model and at what scale/size they will play, along with how the partner network comes into play. Not all of these are wonderful changes, nor are they the only ones doing this.

Changes in the pricing model, and reducing the customer footprint/focus size, are **not** for a second impacting the core product. The day-to-day technology that Citrix brings to the table has ***never been in a better place***. The roadmap is strong, and the core product set is cranking. The engagement from Citrix within those accounts that are in their current target scope is elevated. This doesn't help those who feel slighted and don't make the list. I get it, but it is an important factor to be thinking about amidst chaos.

Some customers are rightly so, considering their options. Some feel slighted and have already made the call to eject, others are looking at where they could go and what else is out there. The challenge is that the options are limited for those with mature delivery estates. What can muddy the water even more, is that many partners are feeling the pinch, and as such may be pitching alternate solutions and strategies.

There are of course options in the market. Some of those solutions are great and will offer what is needed, but the grass isn't always as green as it may seem on the other side, despite the marketing hype. Customers may well be paying more than they initially planned both in transitional costs, operational costs, management tooling (particularly at scale), and for public cloud-based solutions, the seemingly constant price hikes in that space. Some of course, particularly if angry, may not care (for now).

Whatever the path, I sincerely hope that customers consider delivery solutions that do **not** lock them into one cloud platform or end up in a position where they are told what platform they must run in their data centers. I also hope that the entire picture is assessed inclusive of how those suggesting certain solutions are compensated.

Sometimes it helps to take a step back and assess what you have available to you, what you are consuming, what you maybe are not consuming and could be, and what you stand to lose with a change. Shelfware is an expensive issue.

A delivery solution requires thinking about more than simply brokering a workload. Security, applications, industry, graphics, workload placement, connectivity challenges, and many other factors come into play.

Below is an outline of what I see customers using (or maybe not using when they could be), along with some considerations and info to help find the value in the existing investment. Maybe it helps, maybe it doesn't, but there doesn't seem to be a single place out there that has a nice overview of the portfolio customers may be entitled to.

I have kept my tone relatively neutral, except where I believe false marketing or half information is provided against an existing solution. For that, I am completely unapologetic.

## Citrix DaaS and CVAD are platform-agnostic

With both [Citrix DaaS](https://docs.citrix.com/en-us/citrix-daas/overview.html) and [Citrix VAD](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/technical-overview.html), customers can choose wherever they want to deploy workloads. This can be Microsoft Azure, Amazon Web services, Google Cloud Platform, IBM, Alibaba, vSphere, Nutanix [including NC2](https://www.citrix.com/blogs/2023/05/09/accelerate-your-hybrid-strategy-with-citrix-nutanix-cloud-clusters-on-azure/), Hyper-V, XenServer and pretty much anything you can power on including physical desktops and servers.

[![platforms]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/platforms.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/platforms.jpg)

Citrix is Platform Agnostic
{:.figcaption}

To delve into this a touch more, alternate solutions that might seem appealing, could well be locking you into not just their cloud platform, but also dictating what you can run in your datacentres. Additionally, if you decide to make the leap and deploy supported on-premises infrastructure solutions, you are going to incur charges for the service, which is expected, but should be considered.

[Citrix Image Portability Service (IPS)](https://docs.citrix.com/en-us/tech-zone/learn/tech-briefs/image-portability-service.html) provides Citrix administrators with a simple workflow to manage workloads between on-premises and public cloud platforms. Amongst other scenarios, its goal is to support:

-  Migration from on-premises to public cloud (cross-platform).
-  Business Continuity by image distribution to alternate platforms.
-  Simplified image maintenance with a build once and deployment to many platforms methodology.

Citrix DaaS and CVAD are **Platform agnostic** allowing you to run whatever workload you like, on whatever platform you like (within appropriate licensing constraints). You have the freedom to move as and when it makes sense. Citrix **Image Portability Service** is the mechanism to support a **single image operating in multiple different cloud environments**. This is one of the most important factors. Customers should be allowed to consume what makes sense and when, not be locked in because of their brokering provider choice.
{:.tldr}

## Citrix Operating System Support including Remote PC Access

Citrix supports Windows Client, Windows 10/11 Client Multi-Session, and Windows Server Operating systems, alongside a long list of Linux distributions. If you are a Linux customer needing to deliver virtual desktops, then your range of alternatives slims down a little.

Customers often invest heavily in extremely powerful desktop workstations to address developer or designer workload demands. These can present a challenge when a user removes themselves from the physical location hosting the desktop.

With **Citrix Remote PC Access** for [DaaS](https://docs.citrix.com/en-us/citrix-daas/install-configure/remote-pc-access.html) or [CVAD](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/install-configure/remote-pc-access.html), customers can deploy the Citrix Virtual Delivery Agent onto these endpoints and have them report to their existing delivery solution. Consumers can then access those workloads over the HDX protocol, with all the security and management features expected for virtual workloads.

This is often missed in customer deployments but is technology available out of the box. It is one of the most under-utilized components of a Citrix solution.

Citrix supports **Windows and Linux** workloads. Citrix **Remote PC Access** provides **secure connectivity to physical endpoints** integrated with the full management stack of Citrix.
{:.tldr}

## Citrix Provisioning and Lifecycle Management

[MCS and PVS](https://docs.citrix.com/en-us/tech-zone/design/reference-architectures/image-management.html) are two extraordinarily powerful technologies that any CVAD or DaaS environment at scale will have taken as a given.

The whole idea of VDI and DaaS is to achieve simplicity, security, and consistency. For non-persistent scenarios, MCS and PVS are the two baseline technologies that provide this globally for organizations.

Moving back to solutions that offer only persistent VMs natively brings back all the challenges of managing RDS farms. Sure, there are tools like Intune, etc. to manage them, but it's not at all similar to what can be delivered with modern approaches, and very much falls back to a legacy methodology.

Maybe this doesn't matter to smaller deployments, but it sure will for those that are focused on security, management, scale updates, consistent images, and rapid change response scenarios.

Want to see just how powerful and advanced MCS is in Azure? You can [track the progress here](https://jkindon.com/the-evolution-of-citrix-machine-creation-services-with-microsoft-azure/).

Citrix **MCS** and **PVS** are the crown jewels of provisioning, **addressing scale challenges, security, and image management**. Some of the commonly suggested alternatives take you back to the days of RDS unless you bring in 3rd party tooling to try and make things more like Citrix. You should consider how alternate solutions handle this process, and if third-party tooling is required, which will impact your TCO of the solution.
{:.tldr}

## Citrix Access Capabilities + Citrix Authentication Flexibility

[Citrix Workspace](https://docs.citrix.com/en-us/citrix-workspace/overview.html) in Citrix DaaS is the single landing page for all users, regardless of where they are coming from and where their workload lives. It is a customizable workspace that can be branded and provides notifications, disclaimers (sign-in policies), and associated user experience controls. For CVAD deployments, this is provided by [StoreFront](https://www.citrix.com/products/citrix-daas/citrix-storefront.html). The gap between these two solutions is changing under the new Citrix mantra of hybrid. This means that both solutions, either Workspace or StoreFront, should ultimately offer the same technical capability moving forward.

Users can choose to access resources (or administrators can control it) via either an HTML 5 site or a native client.

Citrix Workspace can also be integrated with [on-premises CVAD sites](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/add-on-premises-site.html) to provide a central aggregation point and additional security services such as Remote Browser Isolation and Secure Private Access.

[![Workspace]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/workspace1.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/workspace1.jpg)

Citrix Workspace Unified Interface
{:.figcaption}

Service Continuity is a feature of the workspace that allows access during offline or cloud outage conditions to DaaS service resources through Workspace app.

From an access standpoint (how users get into the environment), Citrix leverages two Gateway functionalities depending on the deployment and requirement:

-  The Gateway Service is cloud-hosted across multiple providers and uses a geo-awareness capability to route the user to the closest Gateway Point of Presence.
-  NetScaler Gateways can be placed in strategic locations to provide a more optimal path closer to the users and the workloads. An example of this would be regional universities that have users and compute on campus, deploying a NetScaler locally allows HDX connectivity via a local Gateway rather than traversing the internet to find a Cloud Gateway which may be a sub-optimal path.

Citrix has intelligent services and capabilities to ensure that workloads are connected in the most optimal fashion. Solutions like [Rendezvous Protocol](https://docs.citrix.com/en-us/citrix-daas/hdx-transport/rendezvous-protocol.html) ensure the most optimal path to the virtual desktop or application for users that operate externally, whereas features like [Direct Workload Connection](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/workspace-network-location.html) or [HDX Direct](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/hdx-transport/hdx-direct.html) allow endpoints with a direct line of sight to connect directly to that workload, bypassing a Gateway altogether.

**Access** doesn't just mean ***how*** to get to a workload, it means addressing security considerations before allowing access to occur. This is often handled at the authentication layer but also expands out to endpoint awareness and device posture.

Citrix has several solutions. For DaaS customers, there is the new [Device Posture Service](https://docs.citrix.com/en-us/citrix-secure-private-access/device-posture.html) which is like the [Advanced Endpoint Analysis](https://docs.netscaler.com/en-us/citrix-gateway/current-release/vpn-user-config/advanced-endpoint-analysis-policies.html) feature delivered by a traditional NetScaler which still serves both DaaS and CVAD customers depending on their architecture. Additionally, Adaptive Access from Citrix offers a range of controls and advanced capabilities including [network location-based resource enumeration](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/adaptive-access/adaptive-access-based-on-users-network-location.html).

[![device_posture]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/device_posture.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/device_posture.jpg)

Citrix DaaS Device Posture Service
{:.figcaption}

Conversely, if you want to get really down and dirty with contextual security and access across both Citrix and other technologies, then [DeviceTRUST](https://devicetrust.com/) is out-of-control awesome in this space, allowing far more flexibility than any provider has natively. This is pure gold in a security-conscious deployment.

Citrix solutions offer many [different authentication capabilities](https://docs.citrix.com/en-us/tech-zone/learn/tech-briefs/workspace-identity.html) and approaches. From standard everyday SAML integration with the likes of Okta, Azure Active Directory, Google, etc., out to [Adaptive Authentication](https://www.citrix.com/solutions/secure-access/what-is-adaptive-authentication.html) for selective authentication requirements with DaaS. Choose your identity model and requirement, and there is a good chance Citrix supports it. [Federated Authentication Service (FAS)](https://docs.citrix.com/en-us/federated-authentication-service/current-release) is used to issue certificates based on SAML requests. This allows for SSO to resources.

[![identity]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/identity.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/identity.jpg)

Citrix DaaS Identity Options (This also extends to NetScaler Auth for CVAD)
{:.figcaption}

Citrix solutions provide **multiple access methods and connectivity options**. Additionally, Citrix provides **adaptive and flexible authentication options** for advanced use cases. NetScaler capability can be a massive differentiator in some environments where control and visibility are non-negotiable.
{:.tldr}

## Citrix HDX Protocol

ICA and [HDX](https://www.citrix.com/solutions/vdi-and-daas/hdx/what-is-hdx.html). Two acronyms that the industry has always associated with End User Computing. HDX/ICA is easily the benchmark of protocols and always has been. This protocol is the core of resource delivery for Citrix resources and provides a dynamic, adaptive, secure, and performant protocol with exceptional user experience.

This focal point might not be all that important for some, but many verticals rely on HDX heavily to provide responsive and rich experiences across a broad range of challenging environments.

The protocol is always enhanced, offering huge strides in performance capability. Some examples of recent enhancements:

-  [Maximizing User Experience with Advanced Video Codec Support in Citrix HDX](https://www.citrix.com/blogs/2023/06/12/maximizing-user-experience-with-advanced-video-codec-support-in-citrix-hdx/)
-  [Reduce your HDX bandwidth usage by up to 15%](https://www.citrix.com/blogs/2023/04/06/reduce-your-hdx-bandwidth-usage/)
-  [Your guide to Citrix graphics workload deployments with Citrix HDX 3D Pro](https://www.citrix.com/blogs/2022/08/09/your-guide-to-citrix-graphics-workload-deployments-with-citrix-hdx-3d-pro/)
-  [Next Gen HDX Multimedia Audio Redirection: A difference you can hear](https://www.citrix.com/blogs/2022/03/23/next-gen-hdx-multimedia-audio-redirection-a-difference-you-can-hear/)

[![hdx]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/hdx.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/hdx.jpg)

Citrix HDX Protocol
{:.figcaption}

The Citrix **HDX protocol** is the meat and beans of Citrix Delivery. It is the **industry benchmark for protocol performance and security**. Several of the alternative solutions use RDP. Does the job, and has some enhancements over the years, but it is no HDX. Does this matter? You be the judge.
{:.tldr}

## Citrix Monitoring, Helpdesk, and Analytics

Customers using Citrix Delivery technology will rely on [Director](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/director.html), [Monitor](https://docs.citrix.com/en-us/citrix-daas/monitor.html), and [Analytics](https://docs.citrix.com/en-us/performance-analytics.html) to support the environment. These tools not only provide visibility into the environment but also provide a delegated control plane for managing sessions and user issues.

This is typically the first, and last touchpoint for administrators and support staff that provides an absolute wealth of capability and control.

[![Monitor]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/director1.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/director1.jpg)

Citrix Monitor/Director Troubleshooting
{:.figcaption}

[![director_logon]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/director_logon.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/director_logon.jpg)

Citrix Monitor Logon Times
{:.figcaption}

[![director_logon]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/director_machine.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/director_machine.jpg)

Citrix Monitor Machine Performance
{:.figcaption}

Analytics is an additional product assisting with trending, visibility, and analysis into the full connection stack including infrastructure monitoring.

When looking at an alternative solution, it's important to be thinking about the operational changes. Does your next solution have anything close to these tools? Some do have capabilities for sure, but not all are built equally. Some are even going to land you extra costs, so it's worth investigating and factoring that in.

[Desktop and Application Probing](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/director/troubleshoot-deployments/applications/desktop-probing.html) is an inbuilt functionality within Citrix solutions to proactively test access to published resources, and alert on failure. The data is rolled up and presented with Director/Monitor for historical reporting and trending. The idea here is that administrators are aware of problems before users are.

[![Probing]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/desktop_probe.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/desktop_probe.jpg)

Citrix Desktop Probing
{:.figcaption}

Citrix **Monitor/Director** is the first touchpoint for managing a Citrix Delivery environment, providing a wealth of **visibility and control** that other solutions don't come close to. Citrix **Desktop and Application probing** is designed to **proactively** test an environment with the goal of alerting administrators before users experience a service outage. Do the alternatives come even close to this? Does it matter? A factor to consider either way.
{:.tldr}

## Citrix Enhanced Cloud Cost Savings + Citrix Autoscale

Citrix DaaS in particular has some great wins for Cloud environments when looking with a cost-reduction lens. With a focus on Azure, DaaS offers:

-  Ephemeral Disk capability (no OS disk costs).
-  Change of Storage Tier when VMs shut down (when machines shut down their disk type changes).
-  On-demand provisioning (when the machine is off, there are no costs other than a dirt-cheap 1GiB identity disk).
-  Citrix Autoscale is discussed below.
-  Citrix [VDI reclamation service](https://www.citrix.com/blogs/2023/05/23/reduce-your-cloud-costs-with-citrix-vdi-reclamation-service/).
-  [Azure hibernation support](https://docs.citrix.com/en-us/citrix-daas/install-configure/power-management/power-manage-azure-vms.html#create-hibernation-capable-vms-preview) (Preview)

[Citrix Autoscale](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/autoscale.html) aims to balance costs and user experience by proactively power-managing machines. The capability includes:

-  Schedule-based and load-based settings.
-  Dynamic session timeouts.
-  Autoscale tagged machines (cloud burst).
-  Dynamic machine provisioning.
-  User logoff notifications.
-  [Predictive Scaling](https://docs.citrix.com/en-us/citrix-daas/manage-deployment/autoscale/predictive-scaling).

Autoscale from Citrix is one of the most efficient ways of managing costs. Combined with Machine Creation Services' cost-saving capabilities, the reduction in cloud computing costs can be significant.

[![autoscale_results]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/autoscale_savings.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/autoscale_savings.jpg)

Citrix Autoscale Reporting
{:.figcaption}

[![predictive_scale]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/autoscale_predictive.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/autoscale_predictive.jpg)

Citrix Predictive Autoscale
{:.figcaption}

Alternative solutions with workloads running purely on the public cloud will talk to reserved instances (longer commit) and/or reduced rates depending on how aggressive the pitch is, but they typically have minimal technology within the service to help. More often than not, customers are paying for 3rd party tooling to help manage costs. Some solutions that offer hybrid deployment options have some good capabilities.

Citrix **Autoscale** is an extremely powerful solution to assist with **cost management and user experience**. Citrix **MCS** also aims to significantly decrease run costs.
{:.tldr}

## Citrix Workspace Environment Management + Citrix Policy Engine

[Citrix Workspace Environment Management](https://docs.citrix.com/en-us/workspace-environment-management/service.html) is a powerful user environment management tool. Its job is to optimize and enhance the user experience, as well as provide a fine-grained control system to build out the user environment based on any number of filters and conditions. It also has a [huge security focus](https://docs.citrix.com/en-us/workspace-environment-management/current-release/user-interface-description/security.html) with privilege elevation engines along with AppLocker integration etc.

WEM is not just a static point-in-time solution either, it is actively developed with features and enhancements released quarterly. You can track the progress of the [Citrix Workspace Environment Management Solution here](https://jkindon.com/the-evolution-of-citrix-wem/) and the [Service Offering here](https://jkindon.com/the-evolution-of-citrix-wem-service/)

[![WEM Service]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/citrix_wem_services.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/citrix_wem_services.jpg)

Citrix WEM Service
{:.figcaption}

The equivalent when you leave? Mostly Group Policy Preferences, some Intune capability (limited), and the good old days of whatever customers did on physical desktops before modern capability was introduced. Some providers offer some UEM controls, but it could be a significant shift.

[Citrix policies](https://docs.citrix.com/en-us/citrix-daas/policies.html) control user access and session behaviour. Citrix policies are an efficient method of controlling connection, security, and bandwidth settings. You can create policies for specific groups of users, devices, or connection types.

[![Citrix Policy]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/citrix_policy.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/citrix_policy.jpg)

Citrix Policy Engine
{:.figcaption}

Citrix Policies are not the same as Microsoft Group Policies. They work in conjunction to secure and control an environment, however, Citrix Policies control almost every aspect of the connection and session. These policies directly control the behaviour of HDX etc.

**Citrix Workspace Environment Management** is an out-of-the-box technology set designed to **enhance, control, and secure user environment management**. Citrix **Policy engine** allows fine-grained tuning.
{:.tldr}

## Citrix Profile Management and User Personalisation Layers

Citrix provides its profile management solution in the form of the [Citrix Profile Management](https://docs.citrix.com/en-us/profile-management/current-release.html) product. CPM has been the benchmark of profile solution technologies for a long time and has never stopped innovation and development. It offers both file and container-based solutions.

For customers with advanced user-driven application installations, Citrix offers [User Personalisation Layers](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/install-configure/user-personalization-layer.html) which operate alongside CPM.

Citrix Profile Management even includes an equivalent engine to FSLogix AppMasking capability in the form of [App Access Control](https://www.citrix.com/blogs/2023/04/26/simplify-app-image-management-with-citrix-profile-managements-app-access-control/) allowing for even more control of the user environment.

Sadly, for the EUC world, Microsoft has let FSLogix deteriorate over time, in both stability and feature development. It is still a solid technology but has fallen out of favour with the lack of features, constant string of bugs, and horrific support. I wrote previously about some considerations of both [CPM and FSLogix](https://jkindon.com/citrix-upm-and-fslogix-containers/) and then updated with some [newer thoughts here](https://jkindon.com/citrix-upm-and-fslogix-containers-2023/).

You can track the progress of the [Citrix Profile Management Solution here](https://jkindon.com/the-evolution-of-citrix-profile-management/)

**Citrix Profile Management** offers flexibility and enhanced profile-based capability, both file and container depending on the scenario requirements. It is rare that any other provider has their own profile tooling (some do) and most fall back on FSLogix. Does this make sense for you?
{:.tldr}

## Citrix Enhanced Security Features + Citrix Session Recording

For regulated and sensitive environments, [Citrix Session Recording](https://docs.citrix.com/en-us/session-recording/current-release.html) offers an integrated solution to record, monitor, and review user sessions. Session Recording captures and archives screen updates, including mouse activity and visible output of keystrokes to provide a record of activity for specific users, applications, and servers.

[![Session Recording]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/session-recording-service-diagram.jpg)]({{site.baseurl}}/assets/img/finding-the-value-in-your-citrix-investment/session-recording-service-diagram.jpg)

Additional capabilities exist for enhanced security, both solutions have an offering so whilst this isn't a differentiator, it's still important to note.

-  Text-based session [Watermarks](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/graphics/session-watermark.html) help to deter and enable tracking data theft.
-  [App Protection](https://docs.citrix.com/en-us/citrix-workspace-app/app-protection.html) provides enhanced security when using published resources. Two policies provide anti-keylogging and anti-screen-capturing capabilities.

Some alternate solutions offer similar capabilities in one form or another.

Citrix Session Recording is a **highly advanced security and auditing toolset** that is heavily used in regulated and sensitive environments. Citrix provides **anti-screen capture and watermarking** and an option for **anti-keylogging**. Are you using these now? Should you be using these now?
{:.tldr}

## Citrix Enhanced Disaster Recovery

With both CVAD and DaaS, desktop and application delivery can be easily [architected for efficient disaster recovery](https://docs.citrix.com/en-us/tech-zone/design/design-decisions/cvad-disaster-recovery.html). DaaS supports all the platforms listed above and provides tooling to ensure seamless failover to different environments based on different conditions.

CVAD is catching up to DaaS with the new direction of Citrix, and whilst there are more components to think about with CVAD, DR is still a simple achievable goal across multiple platforms.

Citrix supports a robust **disaster recovery** solution that can span multiple clouds and platforms. Are you taking advantage of these features today? What do the alternatives offer, does it suit your organisation?
{:.tldr}

## Citrix Application Delivery

Citrix has a solution called [App Layering](https://docs.citrix.com/en-us/citrix-app-layering/4.html). Love it or hate it, App Layering is a technology set that allows applications to be installed into a "*layer*". Layers are combined to create an image (which can be deployed by either PVS or MCS) allowing customers to update and manage application sets outside of the underlying Operating System.

Citrix solutions also support a range of application delivery capabilities, including some that are in lockstep with Microsoft, such as App-V and MSIX including App-Attach.

Whilst Microsoft has made it clear that MSIX is the future of their packaging and app virtualization capability, the success rate is not amazing with customers still utilizing App-V heavily.

Citrix out-of-the-box integrates and drives the delivery of those packages. For customers who are happy with MSIX including App-Attach, Citrix supports the [integration and delivery of these packages](https://www.citrix.com/blogs/2023/04/12/simplify-your-app-deployment-with-citrix-daas-and-microsoft-msix/) also.

Again, conversely, for either platform handling either of these package types, it would be completely remiss of me to not include a reference to the sensational work Bram Wolfs has done in building out the [AppVentix](https://appventix.com/) solution which trumps both Microsoft and Citrix delivery methods.

Citrix has **App Layering** and management of both **MSIX & App-V solutions**. How are you going to deliver the same packages if you are looking at something else? How much fun have you had with MSIX to date?
{:.tldr}

## Citrix Universal Print Server

Printing in any remoting solution is a pain and always has been. Citrix offers the [Universal Print Server](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/printing/printing-provision-printers.html) solution to take away some of the driver challenges at scale.

Let's be fair, regardless of the tech you choose, at scale, most customers use a third-party management solution to take away the headache of printer management.

Citrix provides the **Universal Print Server**. Printing sucks without 3rd party tooling.
{:.tldr}

## Citrix ITSM Adapter

[IT Service Management (ITSM) Adapter](https://docs.citrix.com/en-us/citrix-itsm-adapter-service.html) is a Citrix Cloud service that lets customers extend ServiceNow capabilities into Citrix DaaS environments. With the service, IT teams and end users can deliver and manage Citrix virtual apps and desktops using ITSM workflows in ServiceNow.

Citrix provides integration into ServiceNow via ITSM
{:.tldr}

## Feature Comparison Matrix - Citrix and ???

Based on what we have discussed above, let's summarize in a table. Instead of doing a direct comparison with any one solution, I am going to leave this table as a placeholder for you to think about:

| **Feature** | **Citrix** | **Alternative** |
|---|---|:---:|
| **Platform** | Nutanix, Azure, AWS, GCP, IBM, Alibaba, vSphere, Hyper-V, XenServer, Private Cloud (provider supplied) |❓|
| **Authentication** | Any IDP supporting SAML. Citrix FAS for SSO |❓|
| **Access** | Citrix Gateway Service (DaaS) NetScaler Gateway (DaaS and CVAD) Direct Workload Connection (DaaS) Rendezvous (DaaS) |❓|
| **Provisioning** | Machine Creation Services & Provisioning Services |❓|
| **Remote PC** | Remote PC Access |❓|
| **User Environment Management** | Citrix Workspace Environment Management & GPO |❓|
| **Profile Management** | Citrix Profile Management (Containers and File based) on any SMB solution |❓|
| **Application Delivery** | Citrix App Layering, MSIX Delivery including App-Attach integration & App-V Delivery |❓|
| **Session Recording** | Citrix Session Recording |❓|
| **Monitoring, Helpdesk and Analytics** | Citrix Monitor (DaaS), Citrix Director (CVAD), Citrix Analytics is additional 💰 |❓|
| **Autoscale** | Full-fledged solution within CVAD and DaaS |❓|
| **Proactive Session Testing** | Citrix App and Desktop probing |❓|
| **Protocol** | ICA/HDX |❓|
| **Policy Control for protocol and session handling** | Citrix Policy to control the connection. Security, Network, Client, offload capability etc |❓|
| **OS Support** | Windows Server, Windows Client, Windows Client Multi-Session, Linux |❓|
| **User Resource Access** | Citrix Workspace or Citrix StoreFront, HTML 5 or Client based, highly customisable with inbuilt continuity |❓|
| **Printing** | Citrix Universal Print Server |❓|
| **Images** | Image Portability Service |❓|
| **Cloud Cost Management** | Autoscale (including Predictive Scaling), On-Demand Provisioning, Disk Tiering changes, Ephemeral Disks, VDI reclamation service |❓|
| **Disaster Recovery** | With DaaS, any platform, any provider, cloud-managed. With CVAD, multi-site architectures provide DR |❓|
| **Enhanced Security Features** | Watermarking, anti-screen capture, anti-key Logging |❓|
{:.smaller}

## What Customers Pay for in an AVD Deployment

Here is the one product I am going to touch on with specifics. This isn't a negative shot, it's an awareness piece and tells a story of how things are often a touch more than they seem on the surface.

AVD is often *considered* free. If customers have an entitlement to use the Service, then the brokering and Gateway capability is not charged whilst you are in Azure **natively** (different story for Azure Stack HCI). The following costs exist when using the native AVD solution:

-  💵 Compute for the workloads (the Session Hosts).
-  💵 Storage for the workloads (the disk(s) on the Session Hosts).
-  💵 Storage for user profiles and data (Azure Files or Azure NetApp Files or Windows Servers).
-  💵 Log Analytics for monitoring.
-  💵 Network Egress for cross-region deployments and standard egress traffic flows.
-  💵 Universal Print costs.
-  💵 Azure Site Recovery for instance protection.
-  💵 Azure Backup for backup capability (VMs and Storage).
-  💵 Azure Stack HCI is what Microsoft is positioning for on-premises deployments using the AVD. This will incur additional charges for the AVD Service, a hybrid service fee alongside the ASHCI pricing. Worth making sure that is covered when you cost it all up.

It is unlikely that customers can manage AVD appropriately at any form of scale natively, so additional tooling starts to be required, for example:

-  💲 Nerdio Manager for Enterprise.
-  💲 Parallels Remote Application Server.
-  💲 Project Hydra or its free equivalent in WVDAdmin

The following soft costs are harder to quantify, but are also often not considered:

-  💰 Administration overhead. Without the toolset that Citrix offers, management of the environment is considerable if customers wish to maintain the same level of security, control, and performance as Citrix can deliver.
-  💰 Technical debt is a reality when customers choose to automate the environment to address shortcomings. Whilst automation is king, the reality is that many administrators responsible for EUC environments are not automation specialists, and automation can introduce complexity. When customers lose the owners of those automation flows, they can become black holes. Most prefer a supported 3rd party solution to mitigate the risk.
-  💰 Disaster Recovery for AVD is locked into Azure. Customers must consider multi-region failover scenarios to cater to DR, and there is no option to execute on another platform outside of ASHCI. This may be fine, but with something like Citrix DaaS, multi-cloud, multi-platform, multi-everything is a breeze (within licensing constraints set by our friends at Microsoft).

Are you thinking about these components when looking at a cost comparison between solutions? Are there more? This is just my list. What else is there?
{:.tldr}

## Summary

My goal in this post is just to bring some focus onto what customers may or may not have in place currently and get them thinking about whether or not there are options to find additional value in their current investments.

Let me leave you with some personal thoughts for what it's worth.

-  I find it ever amusing that those building solutions to replace Citrix, are at the forefront of downplaying Citrix's relevance, at the same time as they build solutions trying to model what Citrix can do natively today. That tells us that Citrix has set the benchmark. My point here? Don't believe the marketing hype around Citrix being a "legacy provider". That is utterly ridiculous. Mature and proven? Absolutely. Legacy? I don't think so.
-  Cloud-only DaaS offerings are a method to drive Public Cloud consumption. It's amazing how many EUC specialists turned up once it became a matter of deploying VMs and registering with a cloud brokering Service.
-  Many mid-tier customers can find that Citrix is too complex a beast for their requirements, and this is completely fair. The complexity is there because there is more to the story than simply brokering workloads, however, that story doesn't exist for everyone.
-  Many integrators do not invest in relevant training for Citrix consultants, so many deployments and implementations are sub-par, and do not reflect the modern capabilities and architectures for a high-performing and resilient delivery model. The appeal of simplicity can be very real for customers burned by poor implementations.
-  It is amazing how good an alternative solution can look when you are comparing 10-year-old non-maintained solutions against a brand new shiny blank system. If you don't have good practices and management techniques for VDI or DaaS environments today, what looks nice and shiny will quickly fall into disarray if you don't change your practices. This has always been the case and always will be.
-  The current state of licensing capability and lockdowns in our industry is absurd. The lockdowns in place that ultimately restrict the choice of what customers can consume and where they can consume it are mind-bending. What's even worse is the little exceptions here and there which only benefit the other big players.

Many environments are well suited to some of the solutions that aren't Citrix. But try and see through the marketing hype that seeks to understate the capability and value that Citrix can (and does) deliver to an organization.

Am I going to change minds, and does it even matter? That's not the point of this post. CSG has a clear path for Citrix, and many customers are not in a position to even afford the technology anymore. That is a shame, and it is frustrating for some, but it doesn't change the fact that Citrix is the pinnacle of innovation and capability when it comes to modern application and desktop delivery.

You want to be sure you are not losing out if you are deciding to egress. The costs are likely still floating around, they are just sneaking up on you in different places.
