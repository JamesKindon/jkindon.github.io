---
layout: post
title: The Evolution of Citrix Workspace Environment Management Service
permalink: "/the-evolution-of-citrix-wem-service/"
subtitle: Tracking the progress of Citrix Workspace Environment Management Service capability
cover-img: /assets/img/Sydney1.jpg
thumbnail-img: /assets/img/the-evolution-of-citrix-wem-service/evolution-wem.jpg
share-img: /assets/img/the-evolution-of-citrix-wem-service/evolution-wem.jpg
tags: [Citrix, WEM, Windows, CVAD, Cloud]
categories: [Citrix, WEM, Windows, CVAD, Cloud]
---

![The Evolution of Citrix Workspace Environment Management Service]({{site.baseurl}}/assets/img/the-evolution-of-citrix-wem-service/evolution-wem.jpg)

Citrix WEM Service environment is consistently updating and bringing enhanced capability to the table. This post aims to track the changes and releases as they occur, and provide a single point of reference

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

## - - - - - March 2022

{: .box-note}

**Feature:** [Updates for the web console](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#march-2022)

**Detail:** This release introduces the following pages to the web console:

*  [**Home**](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/home.html): Provides an overview of your WEM deployment along with information necessary for you to get to know and get started with WEM quickly. The interface comprises the following four parts:
    *  **Overview**: Provides an overview of the WEM deployments
    *  **Quick access**: Provides quick access to a subset of the key features that WEM offers
    *  **Highlights**: Shows the key features that WEM offers
    *  **Preview features**: Shows features that are currently in preview. You can enable or disable preview features yourself
*  [**Directory Objects** *Preview!*](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/directory-objects.html) Lets you add machines, groups, OUs, and more, that you want WEM to manage. You can now do the following:
    *  Add machines, groups, Organizational Units (OUs), and more, that you want WEM to manage
    *  Apply settings to agents that are not bound to any configuration set. You can control how unbound agents behave
*  [**Assignment Target** *Preview!*](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment.html) Lets you add users and groups (targets) so that you can assign actions and security rules to them

{: .box-note}

**Feature:** [Support for migrating your service instance yourself](https://docs.citrix.com/en-us/workspace-environment-management/service.html)

**Detail:** If your WEM service instance does not reside in your current region, you can now migrate the instance to the current region yourself. Sign in to Citrix Cloud, go to `Workspace Environment Management > Utilities` and select `Start migration`.

It can take up to two days to receive the notification. Citrix encourages migration to the current region to improve performance. This is signficant for those that did not have a local WEM region initially (APJ for example)

## - - - - - January 2022

{: .box-note}

**Feature:** [Web console now available as a preview](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#january-2022)

**Detail:** A new, web-based Workspace Environment Management (WEM) console is now available. Citrix are in the process of migrating the full set of functionalities from the legacy console to the web console. The web console generally responds faster than the legacy console. You can switch between the web console and the legacy console from within the Manage tab to perform your configuration or deployment management tasks. Click the down arrow next to Manage and select an option:

*  **Legacy Console** takes you to the legacy console
*  **Web Console** takes you to the new, web-based console

The following features are available only in the web console:

*  [Run scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks.html) Scripted tasks can be added to WEM and automatically executed
*  [Save a backup of a configuration set automatically](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets.html#manage-automatic-backup) Automatic backup for configuration sets
*  [Scan large files in profile containers](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings.html) The WEM agent to run a scan of large files on profile containers when container usage exceeds the specified threshold value
*  [Prevent child processes from inheriting CPU priority](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/system-optimization.html#cpu-spike-protection) Allows for specifying a processes whose child processes should not inherit the CPU priority
*  Language localization support for the web console. The web console supports non-English characters and keyboard input even when the console itself is not localized in the preferred language of an administrator. The supported languages are as follows: French, German, Spanish, and Japanese

{: .box-note}

**Feature:** [Apply settings to unbound agents](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/active-directory-objects.html#advanced)

**Detail:** You can now apply settings to agents that are not bound to any configuration set. The feature lets you control how unbound agents behave.

Minimum agent version required: `2201.2.0.1`

{: .box-note}

**Feature:** [Support for managing non-domain-joined machines in Citrix Virtual Apps and Desktops Standard for Azure deployments](https://docs.citrix.com/en-us/workspace-environment-management/service/manage-non-domain-joined-machines.html)

**Detail:** You can now use WEM service to manage non-domain-joined machines in Citrix Virtual Apps and Desktops Standard for Azure deployments. This support enables you to assign policies and settings to non-domain-joined machines as you do with domain-joined machines.

Minimum agent version required: `2201.2.0.1`

{: .box-note}

**Feature:** [Support for enumerating Azure AD users and groups](https://docs.citrix.com/en-us/citrix-cloud/citrix-cloud-management/identity-access-management/connect-azure-ad.html)

**Detail:** WEM service now supports enumerating Azure Active Directory (AD) users and groups. After connecting your Citrix Cloud account to your Azure AD, you can add Azure AD users and groups that you want WEM to manage

{: .box-note}

**Feature:** [External task enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/external-tasks.html)

**Detail:** This release includes enhancements to the external task feature. The feature now provides you with three additional options to control when to run external tasks:

*  **Disconnect** controls whether to run the external task when a user `disconnects` from a machine where the agent is running
*  **Lock** controls whether to run the external task when a user `locks` a machine where the agent is running
*  **Unlock** controls whether to run the external task when a user `unlocks` a machine where the agent is running

Minimum agent version required: `2201.1.0.1`

{: .box-note}

**Feature:** [Profile Management enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html)

**Detail:** Workspace Environment Management now supports all versions of Profile Management through 2112. The following new options are now available in the `Administration Console > Policies and Profiles > Citrix Profile Management Settings` interface:

*  **Enable File Exclusions for Profile Container**. Available on the `Profile Container Settings` tab, the option controls whether to exclude the listed files from the profile container
*  **Enable File Inclusions for Profile Container**. Available on the `Profile Container Settings` tab, the option controls whether to keep the listed files in the profile container when their parent folders are excluded
*  **Customize storage path for VHDX files**. Available on the `Advanced Setting`s tab, the option controls whether to store VHDX files of different policies in different folders under the specified storage path

Minimum agent version required: `2110.2.0.1`

{: .box-note}

**Feature:** [Administrative access to WEM service based on Azure Active Directory group membership](https://docs.citrix.com/en-us/citrix-cloud/citrix-cloud-management/identity-access-management/connect-azure-ad.html)

**Detail:** You can now manage administrative access to WEM service based on Azure AD group membership. Users (administrators) within the Azure AD group can directly onboard to Citrix Cloud and access WEM service – you do not need to manually add them in Citrix Cloud. A general workflow to use the feature is as follows:

Connect your Citrix Cloud account to your Azure AD -> Add the applicable group to Citrix Cloud from Azure AD -> Users can sign in to Citrix Cloud by using their Azure AD credentials

## - - - - - November 2021

{: .box-note}

**Feature:** Message about instance migration

**Detail:** If you use a service in another region, a message now appears when you sign in to the administration console. The message reminds you to migrate your service instance to your current region

{: .box-note}

**Feature:** [Export Statistics for Migration](https://docs.citrix.com/en-us/workspace-environment-management/service/migrate.html#step-2-export-the-database-data-to-an-sql-file)

**Detail:** Citrix added an option `Export statistics` to the migration tool. Use the option to control whether to export agent and user statistics when performing migrations

## - - - - - October 2021

{: .box-note}

**Feature:** [Allow users to self-elevate certain applications](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#self-elevation)

**Detail:** This release introduces `self-elevation` for the `privilege elevation` feature. With s`elf-elevation`, you can automate privilege elevation for certain users without the need to provide the exact executables beforehand. Those users can request self-elevation for any applicable file simply by right-clicking the file and then selecting `Run with administrator privileges` in the context menu. After that, a prompt appears, requesting that they provide a reason for the elevation. This reason is for captured for auditing purposes. If the criteria is met, the elevation is applied, and the files run successfully with administrator privileges.

In addition, self-elevation provides flexibility to create allow lists for the files you permit users to self-elevate or block lists for files you want to prevent users from self-elevating.

Minimum agent version required: 2109.2.0.1

{: .box-note}

**Feature:** [Bind a Citrix Virtual Apps and Desktops service catalog to a configuration set](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#workspace-environment-management-optional)

**Detail:** You can now use the CVAD Service console to bind a catalog to a WEM configuration set. This is a quick option to automatically add a catalog to WEM configuration sets

{: .box-warning}

Whilst a great feature, I have seen instances of inconsistencies in configuration set bindings - tried and proven AD objects in WEM fixed the issue

{: .box-note}

**Feature:** [Workspace Environment Management now available in Citrix Cloud Japan](https://docs.citrix.com/en-us/citrix-cloud-japan)

**Detail:** Workspace Environment Management service is now available in Citrix Cloud Japan, a cloud that is isolated and separate from Citrix Cloud. Japanese customers can use the service in a dedicated Citrix-managed environment.

The service requires Citrix Cloud Connector version `6.29.0.58841`

{: .box-note}

**Feature:** [Support for Windows 11](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#october-2021)

**Detail:**

Minimum agent version required: 2109.2.0.1

## - - - - - September 2021

{: .box-note}

**Feature:** [More granular control over applying privilege elevation to child processes]()

**Detail:**

{: .box-note}

**Feature:** [Support for Windows Server 2022]()

**Detail:**

## - - - - - August 2021

{: .box-note}

**Feature:** [Enablement of Asia Pacific South based instances]()

**Detail:**

## - - - - - July 2021

{: .box-note}

**Feature:** [Notifications about new agent versions]()

**Detail:**

## - - - - - June 2021

{: .box-note}

**Feature:** [Parameter matching for privilege elevation]()

**Detail:**

{: .box-note}

**Feature:** [Privilege elevation support for Windows installer files]()

**Detail:**

{: .box-note}

**Feature:** [Profile Management Enhancements]()

**Detail:**

## - - - - - May 2021

{: .box-note}

**Feature:** [Configure user processes as triggers for external tasks]()

**Detail:**

{: .box-note}

**Feature:** [Enhancements to process hierarchy control]()

**Detail:**

## - - - - - April 2021

{: .box-note}

**Feature:** [Process hierarchy control]()

**Detail:**

{: .box-note}

**Feature:** [Overwrite or merge application security rules]()

**Detail:**

## - - - - - March  2021

{: .box-note}

**Feature:** [Discover Citrix Cloud Connectors from the CVAD service]()

**Detail:**

{: .box-note}

**Feature:** [Support for the Windows 10 2009 template]()

**Detail:**

{: .box-note}

**Feature:** [Brand-new home page]()

**Detail:**

{: .box-note}

**Feature:** [Profile Management Enhancements]()

**Detail:**

## - - - - - January  2021

{: .box-note}

**Feature:** [Microsoft Sync Framework 2.1 deprecation]()

**Detail:**

{: .box-note}

**Feature:** [WEM agent integration with the Citrix Virtual Apps and Desktops product software]()

**Detail:**

{: .box-note}

**Feature:** [Support for condition-based assignment of Group Policy settings]()

**Detail:**

{: .box-note}

**Feature:** [Privilege elevation]()

**Detail:**

