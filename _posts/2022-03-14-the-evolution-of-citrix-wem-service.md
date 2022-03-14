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

**Detail:** Minimum agent version required: 2109.2.0.1

## - - - - - September 2021

{: .box-note}

**Feature:** [More granular control over applying privilege elevation to child processes](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

**Detail:** Previously, when you used the Apply to Child Processes setting in a rule, you applied the rule to all child processes that the executable started. This release provides you with three additional options, giving you more granular control over applying privilege elevation to child processes

*  Apply only to executables in the same folder
*  Apply only to signed executables
*  Apply only to executables of the same publisher

Minimum agent version required: 2109.2.0.1

{: .box-note}

**Feature:** [Support for Windows Server 2022](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#september-2021)

**Detail:** Minimum agent version required: 2109.2.0.1

## - - - - - August 2021

{: .box-note}

**Feature:** [Enablement of Asia Pacific South based instances](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#august-2021)

**Detail:** Citrix now offers Asia Pacific South based instances

## - - - - - July 2021

{: .box-note}

**Feature:** [Notifications about new agent versions](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#july-2021)

**Detail:** You can now opt in to Agent Version Upgrade notifications

## - - - - - June 2021

{: .box-note}

**Feature:** [Parameter matching for privilege elevation](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

**Detail:** This release introduces parameter matching for the privilege elevation feature. Parameter matching gives you more granular control by letting you restrict privilege elevation to executables that match the specified parameter. A parameter works as a match criterion. To further expand the criterion, you can use regular expressions.

Minimum agent version required: 2106.2.0.1

{: .box-note}

**Feature:** [Privilege elevation support for Windows installer files](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

**Detail:** Starting with this release, you can apply privilege elevation to `.msi` and `.msp` Windows installer files. Using the feature, you elevate the privileges of non-administrative users to an administrator level necessary for some Windows installer files. As a result, those users can run those files as if they are members of the administrators group

Minimum agent version required: 2105.1.0.1

{: .box-note}

**Feature:** [Profile Management Enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html)

**Detail:** Workspace Environment Management now supports all versions of Profile Management through 2106. The Administration Console > Policies and Profiles > Citrix Profile Management Settings user interface has changed, adding:

*  Replicate user stores
*  Accelerate folder mirroring
*  User Store Credentials

Minimum agent version required: 2106.2.0.1

## - - - - - May 2021

{: .box-note}

**Feature:** [Configure user processes as triggers for external tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/external-tasks.html)

**Detail:** This release includes enhancements to the external task feature. The feature now provides you with two additional options to control when to run external tasks:

*  **Run when processes start** controls whether to run the external task when specified processes start
*  **Run when processes end** controls whether to run the external task when specified processes end

Using the two options, you can define external tasks to supply resources only when certain processes are running and to revoke those resources when the processes end. Using processes as triggers for external tasks lets you manage your user environments more precisely compared with processing external tasks on logon or logoff

Minimum agent version required: 2104.1.0.1

{: .box-note}

**Feature:** [Enhancements to process hierarchy control](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#process-hierarchy-control)

**Detail:** This release introduces enhancements to the process hierarchy control feature that improve overall performance and stability. The enhancements include the following changes:

*  The AppInfoViewer tool has been updated to include the following two options: `Enable Process Hierarchy Control` and `Disable Process Hierarchy Control`. For the process hierarchy control feature to work, you must first use the tool on each agent machine to enable the feature. Every time you use the tool to enable or disable the feature, a machine restart is required
*  In certain scenarios, you must restart your agent machine after upgrading or uninstalling the agent

Minimum agent version required: 2105.1.0.1

## - - - - - April 2021

{: .box-note}

**Feature:** [Process hierarchy control](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#process-hierarchy-control)

**Detail:** This release introduces the process hierarchy control feature. The feature lets you control whether certain child processes can be started through their parent processes. You create a rule by defining parent processes and then designating an allow list or a block list for their child processes. You then assign the rule on a per user or per user group basis. The following rule types are available:

*  **Path** applies the rule to an executable according to the executable file path
*  **Publisher** applies the rule according to publisher information
*  **Hash** applies the rule to identical executables as specified

Minimum agent version required: 2103.2.0.1

{: .box-note}

**Feature:** [Overwrite or merge application security rules](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#application-security)

**Detail:** This release adds two settings, **Overwrite** and **Merge**, to the **Administration Console > Security > Application Security tab**. The settings let you determine how the agent processes application security rules.

*  Select Overwrite if you want to overwrite existing rules. When selected, the rules that are processed last overwrite rules that were processed earlier. We recommend that you apply this setting only to single-session machines
*  Select Merge if you want to merge rules with existing rules. When conflicts occur, the rules that are processed last overwrite rules that were processed earlier

## - - - - - March  2021

{: .box-note}

**Feature:** [Discover Citrix Cloud Connectors from the CVAD service](https://docs.citrix.com/en-us/workspace-environment-management/service/get-started/install-and-configure.html#step-2-configure-group-policies-optional)

**Detail:** This release introduces a policy setting titled Discover Citrix Cloud Connector from CVAD service. If you have not yet configured Cloud Connectors for the agent, use the setting to control whether the agent discovers Cloud Connector information from the relevant Citrix Virtual Apps and Desktops (CVAD) service deployment. The agent then connects to the corresponding Cloud Connector machines automatically

{: .box-note}

**Feature:** [Support for the Windows 10 2009 template](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/system-optimization/citrix-optimizer.html)

**Detail:** Citrix added support for the Windows 10 2009 (also known as 20H2) template introduced in Citrix optimizer. You can now use WEM service to perform template-based system optimizations for Windows 10 2009 machines. In addition, Citrix have updated all existing templates to reflect changes introduced in the latest standalone Citrix optimizer

{: .box-note}

**Feature:** [Brand-new home page](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#march-2021)

**Detail:** This release replaces the home page of the WEM administration console with a quick-start page that provides information necessary for you to get started with the WEM service

{: .box-note}

**Feature:** [Profile Management Enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html)

**Detail:** Workspace Environment Management service now supports all versions of Profile Management through 2103. The following new options are now available in the Administration Console > Policies and Profiles > Citrix Profile Management Settings interface:

*  Enable Local Cache for Profile Container
*  Enable multi-session write-back for profile containers
*  Enable Profile Streaming for Folders

## - - - - - January  2021

{: .box-note}

**Feature:** [Microsoft Sync Framework 2.1 deprecation](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#january-2021)

**Detail:** Microsoft Sync Framework 2.1 reached End of Life on January 12, 2021. WEM has removed the legacy sync service based on that framework and instead uses a new sync framework, Dotmim.Sync, an open-source sync framework

{: .box-note}

**Feature:** [WEM agent integration with the Citrix Virtual Apps and Desktops product software](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/install-vdas.html#step-5-workspace-environment-management)

**Detail:** The WEM agent is integrated with the Citrix Virtual Apps and Desktops product software, letting you include the WEM agent when installing a Virtual Delivery Agent (VDA). This integration is reflected in the Citrix Virtual Apps and Desktops 2012 product software and later

{: .box-note}

**Feature:** [Support for condition-based assignment of Group Policy settings](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/group-policy-settings.html#contextualize-group-policy-settings)

**Detail:** Starting with this release, you can make Group Policy settings conditional by using a filter to contextualize their assignments. A filter comprises a rule and multiple conditions. The WEM agent applies the assigned Group Policy settings only when all conditions in the rule are met in the user environment at runtime. Otherwise, the agent skips those settings when enforcing filters.

{: .box-note}

**Feature:** [Privilege elevation](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

**Detail:** This release introduces the privilege elevation feature. The feature lets you elevate the privileges of non-administrative users to an administrator level necessary for some executables. As a result, those users can start those executables as if they are members of the administrators group.

You can configure how a rule behaves according to the type of the operating system. You can also configure whether a rule takes effect at a particular time or within a particular time range. You assign a rule on a per user or per user group basis.

Minimum agent version required: 2010.2.0.1
