---
layout: post
title: Mapping Citrix to Omnissa VDI Capabilities
permalink: "/horizon-to-citrix-capability-mapping/"
categories: [Citrix, Omnissa, VDI, DaaS, Nutanix, Prism Central]
description: Mapping Horizon components to Citrix capabilities
image:
  path: /assets/img/horizon-to-citrix-capability-mapping/post_default_image.jpg
sitemap: true
hide_last_modified: true
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro

This page is not a comparison or "vs" page. It is designed to help those familiar with Citrix concepts, map capabilities, components and constructs to an Omnissa equivalent. It is written with a Nutanix lens given the release of Horizon on Nutanix AHV.

This is designed primarily to map Citrix ➟ Horizon, and does not cover a reverse mapping of Horizon ➟ Citrix where those capabilities might exist.

This mapping is focused on the VDI and supporting components of both providers. It does not discuss capabilities addressing the broader EUC technology set. It is focused on components that are relevant to Nutanix AHV only. It does not discuss or outline capabilities as they relate to other hypervisors or platforms.

## Solution Component Mapping

The below break sections outline a logical breakout of common components

### 💡 Solutions Offering & Protocol

➡️ **Citrix Virtual Apps and Desktops** ➟ **Horizon** ✅

Application and Desktop Delivery

➡️ **Citrix Cloud DaaS** ➟ **Horizon Cloud** ✅

Application and Desktop Delivery via Cloud Service

➡️ **Citrix ICA/HDX** ➟ **Horizon Blast** ✅

Two of the most well known protocols out there, Citrix provides HDX, Horizon provides Blast

### 💡 Control, Brokering, Provisioning and Management Constructs

➡️ **Citrix Delivery Controller** ➟ **Horizon Connection Server** ✅

Handles resource publishing, assignments and management tasks, including provisioning against a hypervisor.

A Citrix Delivery Controller talks to a Hypervisor via a Hosting Connection.

A Horizon Connection Server uses the equivalent concept of a Capacity Provider.

➡️ **Citrix Licence Server** ➟ **Horizon Edge Gateway Appliance** ✅

Loosely comparable, both solutions provide licensing capabilities.

The Horizon Edge Gateway Appliance is the broker between Horizon Cloud licences and on-prem Pod Activation.

It is not a hard requirement for licensing in Horizon if using perpetual, but for is required for subscription.

➡️ **Citrix Provisioning Services** ➟ ***No Equivalent*** 🚫

Streams a single vDisk image across the network to target devices. Separate infrastructure required, great for simple image management and scale.

➡️ **Citrix Machine Creation Services** ➟ **Horizon Automated Pools** ✅

Both solutions are integrated into the Controller tiers. A hosting connection (Citrix) is the equivalent of a capacity provider (Horizon). 

Citrix uses a snapshot via PE or a Template via PC. Horizon uses a Template.

Currently Horizon uses a Sysprep based provisioning model, Citrix does not use Sysprep.

### 💡 Machine Provisioning and Resource Presentation Constructs

➡️ **Citrix Catalog** ➟ **Consolidated into a Horizon Desktop Pool** ✅

With Citrix, a Catalog is a group of machines, linked to a provisioning type:

-  Citrix MCS ➟ Horizon Automated Pools
-  Citrix PVS 🚫 `No equivalent`
-  Citrix Power Managed 🚫 `No equivalent`
-  Citrix RemotePC ➟ Manual Pool of Registered Physical Machines
-  Manual ➟ Manual Pool of Registered Non-vSphere Virtual Machines

Citrix Catalogs feed Citrix Delivery Groups.

A Horizon Desktop pool combines a Catalog and Delivery Group concept into a single unit. Abstraction occurs with Global Entitlements via Cloud Pod architecture. 

Horizon supports a Manual, or Automated Pool logic.

➡️ **Citrix Delivery Group** ➟ **Consolidated into a Horizon Desktop Pool** ✅

A Delivery Group is where resources are assigned, presented and controlled for user access. Delivery Groups can be fed by multiple catalogs, delivery groups published app and desktop resources, they also feed application groups.

See **Catalog** detail above for Horizon.

➡️ **Citrix Application Group** ➟ ***No Equivalent*** 🚫

An Application Group is an abstraction of a group of applications from the underlying Delivery Group. Apps are assigned to an Application Group, Users are assigned to an Application Group. The Application Group is assigned to one more many Delivery Groups.

Horizon does not have a direct equivalent to an Application Group construct.

➡️ **Citrix Assignment** ➟ **Horizon Entitlement** ✅

A mapping of a resource to a user. Horizon supports Global and local Entitlements.

➡️ **Citrix Tag** ➟ ***No equivalent*** 🚫

A Citrix Tag can be used to control launch, assignments, policy application and autoscale scenarios.

Horizon has no direct equivalent.

➡️ **Citrix AutoScale** ➟ **Horizon Automated Pools** ✅

Citrix Provides a dedicated autoscale engine associated at the Delivery Group Level, AutoScale works in conjunction with power management capabilities.

Horizon relies  on an autoscale  logic tied to the Automated Pool. For an Automated Pool guest shutdown and guest reboot commands are available, however power OFF and power ON commands are not available, nor is a power state status provided (a view of how the hypervisor knows the VM power state).

One should be careful when altering power states outside of the pool scaling logic, this can have varied results.

➡️ **RBAC - Citrix Scoped Roles** ➟ **RBAC - Horizon Access Groups** ✅

A collection of resources grouped for a common administrative delegation point.

➡️ **Citrix Configuration Logging** ➟ **Event Configuration** ✅

Both solutions offer a database backed logging infrastructure. Citrix uses Microsoft SQL with a dedicated database table set, Horizon offers support for SQL, PostgresSQL and Oracle.

### 💡 Access & Identity Components and Scale Constructs

➡️ **Citrix StoreFront** ➟ **Consolidated with the Horizon Connection Server Role** ✅

Citrix StoreFront is the resource presentation tier for Citrix. It's a web based solution providing a landing point for either HTML5, or Citrix Workspace App based connections. It enumerates published resources from Citrix Delivery Controllers, in a Cloud architecture, Controllers are Citrix hosted and proxied via Cloud Connectors.

Citrix StoreFront is available as a direct landing point, or can be accessed via a Citrix NetScaler Gateway.

Horizon consolidates the resource publishing component with the Connection Server as an all inclusive unit.

➡️ **Multi-Site aggregation** ➟ **Cloud Pod Architecture** ✅

Citrix uses a site based construct. A site is a collection of Controllers tied to a SQL Databases. Resource with a site are resilient across controllers. Configuration is not sync’d across multiple sites.

Horizon uses a Pod based architecture. A pod contains multiple Connection Servers. Configuration is shared via an ADAM database, replicated across each Connection Server in the Pod. The only SQL dependency is for event monitoring.

To provide access to multiple sites, and aggregate/enumerate resources for user consumption, Citrix StoreFront utilises Site Aggregation. Site aggregation allows for HA, site failover, active-active or active-passive configurations, presenting multiple sets of resources from numerous sites as a single set of resources.

Horizon uses Cloud Pod Architecture, effectively layering entitlements and aggregation across multiple Horizon Pods. This configuration occurs via the concept of a federation, which a pod joins. Federation configuration and detail is stored in a second ADAM database, which is replicated across all Connection Servers in all pods.

➡️ **Optimal Gateway Routing** ➟ **Cloud Pod Architecture URLS** ✅

In a multi-site Citrix architecture, NetScaler Gateways can be placed near the workloads to ensure an optimal connection path. StoreFront is responsible for providing the correct gateway for the resource.

Horizon provides similar functionality in CPA via the site URL defined on the Site object (a site is a collection of pods). Resources launched from Site 1, will tunnel via the URL defined on the site, keeping tunnel traffic local to the resources.

➡️ **Citrix Federated Authentication Services** ➟ **Horizon Enrollment Server** ✅

Citrix FAS maps SAML assertion information to user certificates, allowing authentication to occur at an external iDP (EntraID, OKTA, Google etc.), and authentication to a published resource to occur via a smart card certificate.

Horizon uses the Horizon Enrollment Server to request a short-lived certificate on behalf of the authenticated user. This is used to logon to the published resource.

The concepts are similar, implementation is different, but outcome is the same - a single sign on to a windows resource with an initial Authentication provided by a federated iDP.

### 💡 External Access, Gateway and Load Balancing Constructs

➡️ **Citrix NetScaler Gateway** ➟ **Unified Access Gateway** ✅

NetScaler Gateway is the ingress point to a Citrix environment, proxies StoreFront services, the landing point for external (and often internal) users, Integrates with external iDPs, manages endpoint analysis and typically sits within a DMZ.

Omnissa offers a Unified Gateway appliance which performs the equivalent Gateway Role, it provides Secure Gateway Services and integrates with 3rd party iDPs as required. Typically maps 1:1 with a Horizon Connection Server. Can be load balanced via 3rd party load balancing solution or using native HA capability

➡️ **Citrix NetScaler Load Balancer** ➟ ***No equivalent*** 🚫

NetScaler load balancer load balances StoreFront, WEM, Session Recording, and other components. It ensures no 1:1 mapping between any component in a CVAD architecture flow and has health monitoring for all components.

NetScaler can be used to load balance Horizon components..

➡️ **Global Server Load Balancing (GSLB)** ➟ ***No equivalent*** 🚫

GSLB is natively available within a NetScaler deployment and includes integration with Citrix services to understand health status and optimal flows.

Horizon does not offer a GSLB solution, however 3rd party options exist (including NetScaler) to provide the equivalent in conjunction with Cloud Pod Architecture.

➡️ **NetScaler Advanced Endpoint Analysis (EPA)** ➟ **UAG Endpoint Compliance Check** ✅

With EPA, an endpoint device is scanned for security information, such as operating system, antivirus, web browser versions etc. before an administrator can grant access to NetScaler Gateway

Horizon offers Endpoint Compliance Check via the UAG.

Both solutions use an OPSWAT framework, though they use them differently (native vs integration).

➡️ **Citrix Adaptive Access** ➟ **Workspace One Access** ✅

Citrix Cloud provides services such as

-  Device Posture Service
-  Adaptive Access (including network location)

Horizon Cloud integrates with Workspace One Access Policies.

### 💡 Profile Management and User Environment Management

➡️ **Citrix Profile Management** ➟ **App Volumes Writeable Volumes and DEM** ✅

Citrix Profile management offers file and container based roaming profile solutions. CPM allows full, partial and highly customisable configurations.

For profiles in a container, you can use Writeable Volumes with the Profile option.

➡️ **Citrix User/Personalization Layer** ➟ **App Volumes Writeable Volumes** ✅

Horizon offers writeable volumes via App Volumes specifically to allow the capture of a application settings and user profile data.

There is close comparison between Citrix App Layering User Layers and App Volumes Writeable Volumes.
For user installed applications you can use Writeable Volumes with the UIA or UIA + Profile models.

➡️ **Citrix Workspace Environment Management** ➟ **Dynamic Environment Manager** ✅

Builds out the user environment, primarily items focused on the user context (drive maps, printers, files, app settings , logon tasks etc.)

Citrix has WEM, Agent based connection to set of Servers or Cloud Service.

Horizon uses DEM. DEM stores it's configuration on a file share. Agents talk to the file share, as does the management console. DEM offers User Environment Management as well as Application setting roaming. It layers configuration on top of a local profile.

### 💡 Endpoint Client and Device Components (VDI focused)

➡️ **Citrix Workspace App** ➟ **Horizon Client** ✅

Provides the endpoint client which talks to the publishing component.

Citrix Workspace App talks to either StoreFront, or NetScaler Gateway.

The Horizon Client talks to either the Connection Server, or the UAG

➡️ **Citrix Workspace app for HTML5** ➟ **Horizon Web Client** ✅

Provides access to published apps or desktops through a webbrowser.

### 💡 Database Requirements

➡️ **Citrix** ➟ **Horizon** ✅

Citrix Virtual Apps and Desktops requires Microsoft SQL databases for the following:

-  Citrix Site, Config and Event Database
-  Citrix Session Recording
-  Citrix Workspace Environment Manager
-  Citrix Provisioning

Horizon requires external databases for the following components:

-  Horizon Event Monitoring
-  Horizon Session Recording 
-  App Volumes manager

### 💡 Help Desk, Analytics, Visibility and Monitoring

➡️ **Citrix Director / Monitor** ➟ **Horizon Helpdesk Tool** ✅

Director is a monitoring and troubleshooting console for Citrix Virtual Apps and Desktops. It is a dedicated role with the Citrix VAD architecture and provided as Citrix Monitor in a DaaS deployment.

Horizon Help Desk Tool is a Web application used to get the status of Horizon 8 user sessions and to perform troubleshooting and maintenance operations

➡️ **Citrix Desktop and Application Probing** ➟ **Horizon Availability Monitoring** ✅

Citrix Application and desktop probing automates the process of checking the health of the apps and desktops that are published in a site by test launching them using StoreFront. The results of probing are available in Director.

Horizon Availability Monitoring offers a client that you can install and use to test the health of Horizon Edge resources.

➡️ **Citrix Session Recording** ➟ **Horizon Session Recording** ✅

Similar technology with different level of maturity and features. Citrix Session Recording offers a significant amount of control and policy driven recording capability. Horizon Session Recording offers an all or nothing approach to session recording. Both have a database dependency.

➡️ **Citrix UberAgent** ➟ **Workspace ONE Experience Management** ✅

UberAgent was acquired by Citrix and provides deep in guest performance and security monitoring. It is a leader in DEX and security analytics.

An argument could be made that Omnissa Workspace ONE Experience Management is the closest thing that compares to some of what UberAgent can deliver.

➡️ **Citrix Analytics** ➟ **Omnissa Intelligence** / **Workspace ONE Experience Management** / **Omnissa DEX** ✅

Citrix Analytics is a Cloud-based service that works across Citrix portfolio products and third-party products. The Analytics service receives data from these products (or data sources) and uses built-in Machine Learning (ML) algorithms to detect anomalous behavior of a user or any other entity. It then monitors and troubleshoots user sessions and share links across an organization that uses Citrix products.

Omnissa Cloud services offer a combination of Omnissa Workspace ONE Experience Management and Omnissa Intelligence to achieve a similar set of information, alongside their DEX offering

### 💡 Dedicated Security Tools and Features

➡️ **Citrix deviceTRUST** ➟ ***No equivalent*** 🚫

deviceTRUST was acquired by Citrix and provides a dynamic contextual access based security engine actioning controls in the published resource, based on the state of the endpoint device connecting in. These context are constantly monitored and immediately actioned based on rule sets.

Horizon offers no equivalent solution, though they have some device based controls built into the product which is closer to EPA than deviceTRUST.

Conversely, deviceTRUST has full support for Horizon and the associated virtual channels, though it is unlikely to be available for new customers given the current ownership.

➡️ **Citrix Secure Developer Spaces** ➟ ***No equivalent*** 🚫

Citrix acquired Strong Network and have renamed the offering to Citrix Secure Developer Spaces.

Strong Network offers a secure platform for Cloud Development Environments (CDEs) using isolated, lightweight, container-based Linux coding environments accessible online.

➡️ **Unicon eLux and Scout** ➟ ***No equivalent*** 🚫

Citrix acquired Unicon and their eLux/Scout solution which is a thinClient OS and management suite.

Omnissa has no direct equivalent. eLux supported/supports Horizon, however given the current ownership, access to the solution might be harder to attain.

### 💡 Automation and Management Constructs

➡️ **Citrix PowerShell Modules and Snapins** ➟ **Horizon PowerCLI** ✅

Citrix offers PowerShell Modules and Plugins, versions and capabilities depend on the offering (DaaS vs CVAD etc).

Horizon (for AHV) offers both API and PowerShell capabilities.

➡️ **Citrix API** ➟ **Horizon API** ✅

Citrix offers an API for both CVAD and DaaS management.

Horizon offers the same constructs.

### 💡 Licensing Options

Licensing is never an enjoyable topic, but good to know there are options.

-  Citrix Platform License
-  Citrix Universal Hybrid Multi Cloud

Citrix offer only subscription licenses.

-  Horizon Universal Subscription (named and concurrent)
-  Horizon Term edition licenses

Omnissa offers both subscription and term based options.
