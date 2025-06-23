---
layout: post
title: The Evolution of Citrix Workspace Environment Management Service
permalink: "/the-evolution-of-citrix-wem-service/"
categories: [Citrix, WEM, Windows, CVAD, Cloud, evolution]
description: Tracking the progress of Citrix Workspace Environment Management Service capability
image:
  path: /assets/img/the-evolution-of-citrix-wem-service/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
related_posts:
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-profile-management.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-wem.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-machine-creation-services-with-microsoft-azure.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-workspace.md
---

<!--excerpt-->

-  Table of Contents
{:toc .large-only}

Citrix WEM Service environment is consistently updating and bringing enhanced capability to the table. This post aims to track the changes and releases as they occur, and provide a single point of reference

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

## March 2025

### [UI Enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#ui-enhancements)

The WEM UI enhancements are as follows:

-  **Agent UI Update**: All UI interfaces in the **Agent** section have been updated to adopt the **Windows 11 theme style**.
-  **System Tray Icon Context Menu**: The right-click menu of the Agent UI’s system tray icon has been optimized with a new modern design.
-  **Light and Dark Mode Support**: All Agent UI elements, including the system tray icon’s context menu, now support **Light Mode** and **Dark Mode**. These modes automatically align with the **System theme** settings.
-  **Agent Skin Customization**: Starting from version `2502.1.0.1`, the ability to change skins through the **Console's Workspace Environment Management > Configuration sets > UI agent personalization** feature has been removed for newer agents. Agents from versions before `2502.1.0.1` continue to support skin customization. For more information, see UI Agent Personalization under the web console.

Minimum agent version required: `2502.1.0.1`

### [Summary View for Agent Statistics](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration#summary-view)

This enhancement includes a new summary view with four charts displaying statistical results and a rearranged layout, moving the search bar and filter.

Minimum agent version required: `2502.1.0.1`

### [Enhanced Analysis of Process Activities During User Logon](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#process-activity-and-details)

Citrix introduced an analysis of process activities during user logon in the Windows Logon Analysis to help users identify more logon performance issues

### [Improved Security for Password Storage in Configurations](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#improved-security-for-password-storage-in-configurations)

Citrx have updated the internal workflow to store passwords contained in configurations, such as network drives and printers, more securely. This change is compatible with version `2005.2.0.1` and newer.

Using older versions before `2005.2.0.1` might result in the following issues:

-  WEM agents older than version `2005.2.0.1` are unable to process configurations containing passwords correctly.
-  When importing configuration sets exported with a console older than version `2005.2.0.1`, configurations containing passwords are not imported.
-  When restoring actions or settings backed up with a console older than version `2005.2.0.1`, configurations containing passwords are not restored.
-  When migrating from on-premises older than version `2005.2.0.1` to the cloud service, configurations containing passwords are not migrated.

### [New Functionalities in the Web Console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#create-a-gpo)

New functionalities in the web console:

-  **Save and Assign** button: A new **Save and Assign** button has been added, allowing for continuous action creation.
-  **Manage Assignments** link: A new **Manage Assignments** link has been added to the toast notification.
-  **Registry Operations** column: A **Registry Operations** column has been added to the data table.

### [Enhanced Performance of Assignment Targets and Directory Objects](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment#assignment-targets)

Previously, loading the **Directory objects** and **Assignment target** pages triggerred numerous translation requests leading to slow load times, especially with large datasets.

With this enhancement, the object names are stored in the database, translating them only when necessary, significantly improving the performance. You can manually refresh individual records to see the updated names. Additionally, Refresh options are added to **refresh** all or selected records or only usernames.

## January 2025

### [Expanded Access for Non-Administrator Users](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#expanded-access-for-non-administrator-users)

Non-administrator users can now directly access the WEM Tool Hub with a subset of its features. This subset includes Windows Logon Analysis and third-party applications pinned by users. A switch to the top of the main page is recommended when a non-administrator user must use the restricted functions. This update broadens accessibility, enabling more users to utilize key functionalities efficiently, while maintaining security and control.

### [Process Hierarchy Control](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/security-web-console#process-hierarchy-control)

This release introduces the Process hierarchy control feature in the web console. This feature allows you to control whether specific child processes can be initiated by their parent processes. You create a rule by defining parent processes and then designating an allow list or a block list for their child processes. You then assign the rule on a per user or per user group basis. The following rule types are available:

-  **Path**. Applies the rule to an executable according to the executable file path.
-  **Publisher**. Applies the rule according to publisher information.
-  **Hash**. Applies the rule to identical executables as specified.

Minimum agent version required: `2501.1.0.1`

### [Unique Identification Support in WEM Agent](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration#settings)

Previously, WEM agents used the MAC address as the device identifier. In certain scenarios, the MAC address was not unique that led to the malfunctioning of some WEM features.

With this enhancement, you can use the agent identity concept to replace the MAC address as the device identifier for WEM agents. This feature is applicable to both domain-joined and non-domain-joined agents.

Minimum agent version required: `2501.1.0.1`

### [Enhancement to the WEM Optimizer Template](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#enhancement-to-the-wem-optimizer-template)

You can now use the WEM service to perform template-based system optimizations for Windows 11 2009 and Windows Server 2025 2009 machines. The WEM optimizer template is now updated to support the memory compression and cache disc mount enhancement in the Citrix optimizer.

## December 2024

### [Accurate Search of OUs (Organizational units) with Precise Criteria](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment#add-an-assignment-target)

Previously due to a large number of duplicate-named OUs in the domain controller, WEM was unable to locate the target OU accurately.

This feature now introduces a location configuration option allowing IT administrators to restrict the OU search scope to a specific location node. This helps in finding the desired target OU quickly.

### [Support the New Filter Design to Save Update or Delete Existing Filters](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/reports#columns-to-display-and-filters)

You can now save the filters used as filter sets and directly manage these filter sets. You can conveniently switch between different filter sets when you try to query the required data. This functionality is available for use on the **Reports** page, **Agent statistics** page, and **User statistics** page.

## November 2024

### [Unified Platform experience for navigation](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#unified-platform-experience-for-navigation0)

The primary navigation menu is now expanded to include a secondary navigation menu for the **Monitoring** and **Enrollment** menu items on the WEM web console. Navigation breadcrumbs are now displayed on the top of every page. To provide a unified platform experience, a drop-down menu is now included on the top right-hand corner of the page that lets you switch to either the **Legacy console**, Utilities, or to the **Web console**.

### [User statistics quick search and refresh icon](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration#user-statistics)

This enhancement provides the ability to search in the user statistics table using the user name and other relevant properties, such as, display name and email.

You can now use the refresh icon that appears when you hover your mouse on every record or user display name instead of the SID.

### [Upload scripts for external tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#create-an-external-task)

Previously, to use the external task feature, the path to a script (or executable) on the agent machine (or network storage) had to be specified. This required maintenance of the script files either on network storage locations or locally on a VDA running WEM causing inconvenience.

With this feature, you can now directly upload scripts when configuring external tasks. To create an external task, you now have an option to upload the script file for the task to run. After uploading, you can also view the content of the script.

Minimum agent version required: `2410.1.0.1`

### [Rule Generator updated with expanded app access control features](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#rule-generator-for-app-access-control)

The Rule Generator for App Access Control tool now supports the expanded features of the App access control policy. With this tool, you can now create redirection rules and configure exclusions for rule assignments.

### [Enhancements to Group Policy Migration Tool](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#group-policy-migration-tool)

This feature enables you to auto-configure `script path` and parameters when you migrate the Windows Logon scripts to WEM external tasks using the **Group Policy Migration** Tool

### [New details to diagonize logon duration](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#windows-logon-analysis)

This feature introduces new details to diagonize the logon duration. You can find more details for the sub-metrics, **FSLogix profile loading** and WEM logon services in the table that lists all the metrics, submetrics, and tips in detail.

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#profile-management)

Workspace Environment Management now supports all supported versions of Profile Management through 2411. The following features are now available in the web console.

-  [Alert user when profile size exceeds quota](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#other-options). This feature helps prevent data loss by notifying users when their profile size exceeds a quota. You can customize the quota limit and the notification content based on the default settings. The feature is available under each configuration set in **Profiles** -> **Profile Management Settings** -> **Advanced settings**.
-  [Enable UWP app load acceleration](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#applications). This feature accelerates the loading of UWP apps and improves their consistency in non-persistent environments. By default, Windows stores UWP App registration information locally on each machine, which can be lost upon restart in non-persistent environments. With this policy enabled, Profile Management creates a VHDX container for each machine to store the UWP app registration data, speeding up user logon and preventing data loss on restarts. The feature is available under each configuration set in **Profiles** -> **Profile Management Settings** -> **Advanced settings**.
-  [App access control policy expanded](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#app-access-control). With the policy, you can now implement machine-level redirections for files, folders, registry keys, and registry values. In addition, you can now exclude specific users, machines, and processes from rule enforcement for more precise control. The feature is available under each configuration set in **Profiles** -> **Profile Management Settings** -> **App access control**.
-  [Folder redirection policy enhanced for more secure access control](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#folder-redirection). With a new option, Grant access to specific users and groups, you can now grant specific users or groups Read and Execute permissions on the redirection target folders.

Minimum agent version required: `2411.1.0.1`

## October 2024

### [Group policy migration to WEM](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#group-policy-migration-tool)

You can now migrate Group policy preferences that cause slow sign-ons into WEM actions to improve your sign-on experience. In the WEM Tool Hub, you can begin the migration workflow either within a logon duration report, while viewing GPO processing times, or from the **Group Policy Migration Tool**. This tool allows you to scan for currently applied GPOs.

You can select from the listed items supported for migration. Selected items are exported as a ZIP file to the local machine, which is later imported as WEM actions. This feature is enhanced to guide you through the process of creating an assignment group with the exported settings, and also assign the group to the respective user.

### [Introducing new insights to monitor and diagonize logon duration](https://docs.citrix.com/en-us/workspace-environment-management/service/how-to/analyze-logon-duration)

This enhancement introduces profile container and GPP processing insights to monitor and diagonize logon duration. This feature enables you to identify the possible issues, which may cause slow logon and to also provide recommendations to resolve issues.

### [Centralized configuration set level agent cache synchronization](https://docs.citrix.com/en-us/workspace-environment-management/service/get-started/install-and-configure#agent-cache-utility-options)

This feature is introduced to enhance the existing agent cache synchronization mechanism. Based on the new mechanism, you can avoid performance issues for large WEM deployments and the database cost on the Cloud is also reduced.

Minimum agent version required: `2409.1.0.1`

## September 2024

### [Support data export to Splunk](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/reports#manually---export-to-third-party-platform)

Previously, you were restricted only to Grafana when exporting agent reports to third-party platforms. With this feature, you can now effortlessly export the data to Splunk as well.

### [Privilege elevation](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/security-web-console#privilege-elevation)

This enhancement enables you to configure privilege elevation rules and assign them to users using the web console. You can now use the existing File Info Viewer in WEM Tool Hub to get the file information needed for rule configuration, such as, path, publisher, and hash values.

Minimum agent version required: `2408.1.0.1`

### [WEM agent support for persistent cache on non-persistent machines](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#wem-agent-support-for-persistent-cache-on-non-persistent-machines)

This enhancement enables the WEM agent to automatically detect non-persistent machines provisioned by MCS or PVS and use the persistent data location provided by the underlying Provisioning Service to persist agent cache and other crucial information. This improves the WEM performance and resiliency on non-persistent machines. Also, the WEM agent enrollment now supports non-persistent machines. You can now enroll the master image and the provisioned non-persistent machines are automatically enrolled.

Minimum agent version required: `2408.1.0.1`

### [Configuring registry and GPO settings with a new registry value type](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#import-group-policy-settings)

`REG_NONE` registry value type is introduced for more customized configurations by providing a way to specify settings or parameters that do not fit into other predefined data categories, such as, strings, integers, or binary data. You can use this flexibility to handle unique or specialized configurations.

`REG_NONE` registry value type supports the following functions:

-  In creating/updating registry entry action
-  In creating/updating registry entry-based GPO action
-  When importing a registry entry-based GPO
-  On the agent side
-  For legacy console
-  For backup and restore from the web console and the legacy console

Minimum agent version required: `2408.1.0.1`

### [Selective WEM reset feature](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#selective-wem-reset-feature)

WEM is enhanced to selectively reset WEM actions tracking cache. When you enable **Allow Users to reset Cached Actions**, the **Reset Cached Actions** is turned on. On clicking it, a new wizard gets displayed and then you can choose the cached actions that need a reset. This enhancement enables you to reset the process history for JSON files or the user group policy objects. After the reset, the actions get processed during the subsequent user logons.

Minimum agent version required: `2408.1.0.1`

## August 2024

### [Enhancements to the selection of Microsoft Entra ID (Azure AD) groups or users](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#enhancements-to-the-selection-of-microsoft-entra-id-azure-ad-groups-or-users)

Policies, including actions and security rules, assigned to Microsoft Entra ID (Azure AD) groups or users now automatically take effect on the agent side without requiring manual user-device associations. To ensure the proper functioning of this feature, adhere to the following requirements:

-  In Citrix WEM User Logon Service Properties dialog, set the Startup type as Automatic.
-  Log out of your local machine and login again.

Minimum agent version required: `2407.2.0.1`

### [Add new built-in scripted tasks to reduce operation efforts](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks)

Added more built-in script tasks that help admins use built-in scripted tasks directly and reduce operation efforts. This feature resolves unregistered VDA issues and sets CDF trace configurations.

### [VHD disk compaction report](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings#monitoring-preferences)

Administrators can now view the VHD disk compaction reports in the web console by enabling VHD disk compaction report collection.

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#profile-management-1)

Workspace Environment Management now supports all supported versions of Profile Management through 2407. The following features are now available in the web console.

-  [Enable in-session profile container failover among user stores](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#advanced-settings) Specifies whether to enable in-session profile container failover among user stores. This feature enhances profile redundancy in the contain-based solution by expanding the container failover scope from occurring ***only at user logons*** to ***throughout the entire session***. The feature is available under each configuration set in **Profiles** -> **Profile Management Settings** -> **Advanced settings** -> **Replicate user stores**.
-  [Folder redirection](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#folder-redirection) enhanced with two new options:
    -  **Redirect to the local user profile**, allowing you to redirect a folder to the local user profile.
    -  **Move contents to new location**, allowing you to decide whether to move contents from the previous folder to the new one when setting or modifying redirection target folders.

Minimum agent version required: `2407.1.0.1`

## June 2024

### [Support for testing the app access control rules](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#rule-generator-for-app-access-control)

You can now validate app access control rules on the local machine before deploying in the testing or production environment.

### [View a GPO](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#group-policy-settings)

You can now view the WEM Group Policy settings. GPO summaries in read-only mode without editing the GPO. This implementation eliminates the risk of misconfiguration while reviewing the existing settings.

### [Support data export to third-party platforms for flexible management](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/reports)

Previously, you were restricted to exporting reports solely to cloud storage or local machines, hindering your ability to effectively analyze and monitor task outcomes.

With this feature, you can now effortlessly configure and export report data to third-party platforms such as Grafana. This enhancement helps to seamlessly integrate and utilize external analytics tools for comprehensive performance monitoring and analysis, whether automatically scheduled or manually initiated.

## May 2024

### [Windows event-based triggers for external tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#considerations)

Windows event-based triggers for external tasks now allow you to associate external tasks (session-level tasks) with them. When the Windows events meet the defined criteria, the trigger is activated. This trigger begins to perform the associated external tasks that help in automatically managing the session-level tasks, based on Windows events.

Minimum agent version required: `2404.1.0.1`

### [WEM agent basic deployment mode](https://docs.citrix.com/en-us/workspace-environment-management/service/manage-basic-deployment-agents)

A basic deployment mode for the WEM agent is introduced to provide basic agent functions, such as system optimization and logon duration analysis without the need to connect to the infrastructure service. You can use this deployment method for utilizing WEM basic functionalities.

Minimum agent version required: `2404.1.0.1`

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#folder-redirection)

**Folder redirection settings**: This feature lets you configure rule sets for redirecting the paths of local folders to new locations. Each rule set specifies where you want to redirect the folders based on the users accessing them.

To configure folder redirection for a configuration set, locate the set, go to **Profiles** -> **Profile Management Settings** -> **Folder redirection**, and then add rule sets.

A much nicer way of handling group based folder redirection that the [previous method I played](https://jkindon.com/multi-site-and-onedrive-folder-redirection-with-wem/).

## March 2024

### [Enhanced automatic backup limit for configuration sets](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets#manage-automatic-backup)

WEM provides automatic backup of configuration sets. The automatic backup limit is now enhanced to support storage of up to 25 backup files for each configuration set before overwriting the oldest existing file. This enhancement reduces the operation effort, especially for large and complex environments.

### [Customizing the Start menu layout for Windows 11](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#customize-the-start-menu-layout-for-windows-11)

To support user level assignments, you can now apply the WEM action **JSON files** for the Windows 11 Start menu configuration. Using the new tool **Start Menu Configurator for Windows 11** in the WEM Tool Hub, you can now select applications that you prefer to add to the **Pinned** section of the **Start** menu and arrange the layout as needed. After customizing the layout, copy the configuration data and paste the data in the web console, when you add a new JSON object in the **JSON Files** page.

Minimum agent version required: `2403.1.0.1`

### [User Store Creation Tool](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#user-store-creation-tool)

This tool is introduced in the WEM Tool Hub to help you create user stores. The user store is the central network location for storing Citrix user profiles. This tool helps you to set up user stores by creating file shares and setting appropriate permissions to them according to your specifications. This tool simplifies the configuration process and reduces errors. You can choose to create the user store on the current machine (running the tool) or on a different machine.

## February 2024

### [Assignment Groups (Preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment#assignment-groups)

This feature lets you group individual actions and manage their assignments in one place. Assignments are created per action rather than at the group level. You can now add actions to a group and select assignment targets, create, edit, and delete assignment groups. Assignment details like filters and options are maintained at the individual item level.

### [Health check enhancements in the web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration#statistics)

You can now gain a clearer and more detailed insight into the status of Profile Management through Workspace Environment Management:

-  **Invalid**: Indicates that Profile Management is either not found or not enabled.
-  **Error**: Indicates configuration issues in Profile Management.
-  **Warning**: Identifies a suboptimal state of Profile Management.
-  **Notice**: Identities an acceptable state of Profile Management.
-  **Good**: Identities Profile Management is in a healthy state.

### [Enhanced analysis capability for Windows Logon](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#windows-logon-analysis)

This enhancement provides a more detailed data analysis for **User profile** and **Citrix Profile Management**. **Group policy objects** sub-metric is now introduced with **HDX connection** sub-metric being enabled.

Minimum agent version required: `2401.1.0.1`

### [WEM health check tool](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-health-check-tool)

You can now open the WEM standalone tool to check the status of the WEM components and troubleshoot. This tool can run on WEM agents or the infrastructure server providing results for different selected (check) items respectively. After completing a check, a report is saved to their machine. You can turn on the debug mode and retrieve the log files to the specified location. You can also fix some configuration issues automatically.

## January 2024

### [Additional Actions in the Web Console](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#january-2024)

The following actions have been made available in the web console:

-  [User Data source name](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#user-dsns). Using the web console, you can now add user data source names (DSNs) and assign them to users.
-  [Ports](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#ports). Using the web console, you can now add port mappings and assign them to users
-  [INI files](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#ini-files). Using the web console, you can now add INI file operations and assign them to users.

### [Agent on-demand task history](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration#agents)

This enhancement allows you to check the progress and results of tasks initiated in the last 24 hours. You can see the task status for each of the target agents after you trigger a task. You can also view the history of recent tasks and their statuses. For tasks with reports, you can access those reports directly from the **Reports** tab

### [Enhanced filter condition capability for report management](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#enhanced-filter-condition-capability-for-report-management)

This enhancement lets you filter and add multiple values by separating each value with a semicolon when you choose the **Result summary** condition, providing a flexible method for report management that enables you to monitor and optimize the system.

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#profile-management)

Workspace Environment Management now supports all supported versions of Profile Management through 2311. The following features are now available in the web console.

-  [User store selection method](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#advanced-settings) Specifies the user store selection method when multiple user stores are available. Options include:
    -  **Configuration order**. Lets Profile Management select the earliest configured store.
    -  **Access performance**. Lets Profile Management select the store with the best access performance. 
    -  The features are available under each configuration set in **Profiles -> Profile Management Settings -> Advanced settings -> Replicate user stores**.
-  [Deduplicate files this size or larger (MB](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#file-deduplication) Specifies the minimum size of files to deduplicate from profile containers. The default size is **256** MB. The feature is available under each configuration set in **Profiles -> Profile Management Settings -> File deduplication -> Enable file deduplication**.
-  [Log off users when profile container is not available during logon](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#profile-container) Specifies whether to force log-off users when the profile container is unavailable during user logon. The feature is available under each configuration set in **Profiles -> Profile Management Settings -> Profile container -> Enable profile container.**
-  [Set users and groups to access profile container](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#profile-container) Specifies which AD domain users and groups have Read & Execute permission on profile containers. By default, a profile container is accessible only to its owner. The feature is available under each configuration set in **Profiles -> Profile Management Settings -> Profile container**.

Minimum agent version required: `2311.1.0.1`

## November 2023

### [Automatic agent upgrade](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/app-package-delivery)

The following enhancements have been made to the automatic agent upgrade feature:

-  You can select the desired agent package from the centralized SMB share package storage location, and schedule automatic upgrades for all agent machines in a configuration set.
-  You can now specify the time period and schedule the day(s) of the week on which you want WEM to automatically roll out the upgrade to all agent machines in a configuration set.
-  You can now specify the device name and IP of agent machines in a configuration set for which you want WEM to automatically roll out the upgrades.

Minimum agent version required: `2310.1.0.1`

### [Extended limit for the Memory Usage Limit functionality](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new#extended-limit-for-the-memory-usage-limit-functionality)

This feature is enhanced to extend the limitation set for the maximum value of the Memory Usage Limit functionality from 4 GB to 32 GB in 64-bit OS. This enhancement provides more flexibility based on real situations in the customer system environment.

Minimum agent version required: `2310.1.0.1`

### [Windows Logon analysis](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#windows-logon-analysis)

This tool collects the logon duration data and generates reports about the recent logon duration data. Each logon report is categorized further allowing you to identify potential issues and bottlenecks.

This is a really cool amount of information similar to the gathered by Diretor/Monitor, ControlUp or multiple 3rd party PowerShell scripts.

### [Application security log reports](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings#monitoring-preferences)

Administrators can now review the Application security logs in the web console by enabling application security log collection per configuration set and get the corresponding reports. The administrator can view the logs by subtype within the details of each report.

Minimum agent version required: `2310.1.0.1`

## October 2023

### [Registry Entries](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#registry-entries)

Using the web console, you can now add registry entries as assignable actions, which let you create, set, or delete registry values in the user environment. The feature has been enhanced to provide a better user experience.

Additionally, you are now able to add tags to registry entries and assign multiple registry entries at the same time. This is yet another example of "ask and ye shall receive". Awesome!

### [Enhancements to extended data in reports](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/reports#export-reports)

Two new export options are introduced for agent reports, **CSV (formatted)** and **JSON (formatted)**. These options enhance the readability of extended data within the reports

### [Categorize Profile Management settings in the web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management)

This feature lets you reorganize your view of Profile Management settings. The three built-in tags, **File-based**, **Container-based**, and **App access control** act like filters, helping filter on the settings available to the selected tag. The latest selected tags are retained as your preference.

### [Enhancements to optimization and usage insights](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/insights#excluded-applications)

This feature lets you configure the list of excluded applications by providing the application names. You can add, edit, and delete the excluded applications using the settings under **Preferences**.

### [Support for File Type Association (FTAs) settings on web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#file-type-associations)

This feature lets the administrators create, manage FTAs, and assign them to the users. Administrators can also use the **File Type Association Assistant** tool in the **WEM Tool Hub** to easily get the information they need for configuring FTAs in the web console.

### [Enhanced Agent Settings](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings#agent-settings)

A new setting **Enable agent to use cached domain search results** is added to the agent settings. When enabled, the agent uses the cache for domain query results to improve performance and resiliency. You can also update WEM group policies when the agent cannot contact the domain.

Minimum agent version required: `2309.2.0.1`

### [Enhancements to the health check report functionality in web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/reports)

This feature improves the user experience of configuring Profile Management through WEM. When you follow the link on the Agent health check result page to **Profile Management** settings, you can see the errors/warnings in the results with its corresponding setting highlighted in the **Profile Management** configuration page on the web console. You can then modify the settings according to the results displayed in the footer.

### [New version of WEM Tool Hub](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub)

A new version of WEM Tool Hub is now available: `2309.2.0.1`. This version includes performance enhancements, support for AAD/NDJ object selector support, and bug fixes.

## September 2023

### [Support for the Windows 11 and Windows Server 2022 in Citrix Optimizer](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/system-optimization/citrix-optimizer)

Citrix added support for the Windows 11 version 21H2 (build 2009) and Windows Server 2022 21H2 (build 2009) in Citrix Optimizer. You can now use the WEM service to perform template-based system optimizations for Windows 11 2009 and Windows Server 2022 2009 machines.

In addition, Citrix have updated all existing templates to reflect changes introduced in the latest standalone Citrix optimizer.

Minimum agent version required: `2309.1.0.1`

### [Enhancements to the manual backup limit](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets#back-up-a-configuration-set)

Citrix have enhanced the maximum manual export limit from 10 to 25 per account.

### [Enhancements to the optimization and usage insight application limit](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/insights)

Citrix have enhanced the maximum manual export limit from 10 to 25 per account

### [Registry Entries](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#registry-entries)

This is another enhancement request after years of painful single-object-management or registry entries. Now it's much nicer.

Using the web console, you can now add registry entries as assignable actions, which let you create, set, or delete registry values in the user environment. The feature has been enhanced to provide a better user experience.

Additionally, you are now able to add tags to registry entries and assign multiple registry entries at the same time.

### [AAD/NDJ object selector tool](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub#assigning-app-access-rules-to-aad-usersgroups-and-ndj-machines)

You can now assign app access rules to AAD users/groups and NDJ machines in addition to AD users/groups and domain-joined machines that are currently supported. A tool, **AAD/NDJ object selector** is now available on the web console, where you can get the object data and paste them into the Rule Generator.

Minimum agent version required: `2309.1.0.1`

### [File System Operations in web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions#file-system-operations)

Administrators can create and manage file system operations and assign them to the users now using the web console.

### [User-level Profile Management settings](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#user-level-profile-management-settings)

This feature lets you configure Profile Management settings at the user level for customization and precise control. Use this feature to apply specific Profile Management settings to individual users or user groups, tailoring the profile experience as needed.

See also [The Evolution Of Citrix Profile Management](https://jkindon.com/theevolutionseries/)

### [Support reporting Privilege elevation and process hierarchy control logs through agent reports](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings#monitoring-preferences)

Administrators can now review the privilege elevation logs in the web console by enabling security log collection per configuration set and get the corresponding reports. The administrator can view the logs by sub-type within the details of each report.

Minimum agent version required: `2309.1.0.1`

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#profile-management)

Workspace Environment Management now supports all supported versions of Profile Management through 2308. The following features are now available in the web console:

-  [Enable VHD auto-expansion for profile container](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#profile-container). If enabled, when the profile container reaches 90% utilization, it automatically expands by 10 GB, with a maximum capacity of 80 GB. Depending on your needs, you can adjust the default auto-expansion settings using the following options: Auto-expansion trigger threshold (%), Auto-expansion increment (GB), Auto-expansion limit (GB).
-  [Default capacity of VHD containers](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#advanced-settings). Specifies the default storage capacity (in GB) of each VHD container.
-  [Enable exclusive access to profile container](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#advanced-settings). If enabled, the profile container allows only one access at a time.
-  [Enable exclusive access to OneDrive container](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#advanced-settings). If enabled, the OneDrive container allows only one access at a time.
-  [Enable UWP app roaming](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management#advanced-settings). If enabled, UWP (Universal Windows Platform) apps roam with users. As a result, users can access the same UWP apps from different computers.

All features are available under each configuration set in **Profiles -> Profile Management Settings -> Profile Container**.

Minimum agent version required: `2307.1.0.1`

See also [The Evolution Of Citrix Profile Management](https://jkindon.com/theevolutionseries/)

### [Configure task settings](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks#configure-task-settings-option)

A new option, **Configure task settings** is introduced in the **Scripted Tasks** page that directs you to the specifically chosen filtered task wizard in the **Scripted Task Settings** page.

### [New version of WEM Tool Hub](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub)

A new version of WEM Tool Hub is now available: 2309.1.0.1. This version includes performance enhancements, support for AAD/NDJ object selector support, and bug fixes.

## July 2023

### [User-level Profile Management settings (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html#user-level-profile-management-settings)

This feature lets you configure Profile Management settings at the user level for customization and precise control. Use this feature to apply specific Profile Management settings to individual users or user groups, tailoring the profile experience as needed.

To enable this feature, go to **Home**, click the **preview features** icon in the upper-right corner, and enable **User-level Profile Management settings**.

### [Enhanced WEM agent event logging](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/agent-event-logs.html)

Citrix have made enhancements to WEM agent event logging, aiming at improving troubleshooting capabilities. The enhancements include:

-  Comprehensive event logs: Citrix have provided comprehensive event logs, giving you a complete picture of agent activities.
-  Unique event IDs: Each event log now has a distinct ID, making it easier for you to filter and identify specific events.

Minimum agent version required: `2307.1.0.1`

### [Microsoft Edge browser support for WEM Transformer](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#microsoft-edge-browser-support-for-wem-transformer)

The WEM Transformer now supports the latest version of the Microsoft Edge browser.

Minimum agent version required: `2307.1.0.1`

### [JSON object assignment](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#json-files)

I love this feature because it's yet another example of the WEM team taking on ideas and feedback. I put this in front of them months ago as a suggestion on how to managed Microsoft Teams - we now have a full engine.

You can now add JSON objects and assign them to create or modify JSON files. Using this feature, you can apply personalized settings to applications with a JSON configuration file (for example, Microsoft Teams).

Minimum agent version required: `2306.1.0.1`

### [Add local applications for quick access](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub.html#add-local-applications-for-quick-access)

This feature lets you add local applications to the WEM Tool Hub for quick access. The added applications are considered your personal data and are retained when you switch machines within the Profile Management environment. You can add and remove multiple applications at a time.

Minimum agent version required: `2307.1.0.1`

### [New version of WEM Tool Hub](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub.html)

A new version of WEM Tool Hub is now available: `2307.1.0.1`. The version includes performance enhancements and bug fixes.

## June 2023

### [Enhancements to CPU spike protection](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/system-optimization.html#cpu-spike-protection)

This release introduces enhancements to the CPU spike protection feature, giving you more granular control. The enhancements include the following changes:

-  Citrix have reorganized CPU spike protection options with intuitive logic for easier configuration.
-  When customizing CPU spike protection, you can now configure the CPU usage limit using non-integer values.
-  A new option, **Set limit relative to single CPU core**, is now available, letting you set a limit on CPU usage based on a single CPU core as a reference.

Minimum agent version required: `2306.1.0.1`

### [Additional Actions in the Web Console](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#june-2023)

The following actions have been made available in the web console:

-  [Environment variables](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#environment-variables). Using the web console, you can now add environment variables as assignable actions. When assigned, those environment variables are created or set in the user environment.

Minimum agent version required: `2306.1.0.1`

### [Group Policy setting processing results](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/dynamic-tokens.html#dynamic-token-support-for-group-policy-settings)

You can now use dynamic tokens in Group Policy settings. This feature allows for more adaptable policy configuration in different environments, reduces manual configuration, and simplifies policy management

### [JSON object assignment (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#json-files)

You can now add JSON objects and assign them to create or modify JSON files. Using this feature, you can apply personalized settings to applications with a JSON configuration file (for example, Microsoft Teams). This feature is available only in the web console.

To enable this feature, go to Home, click the preview features icon in the upper-right corner, and enable JSON object assignment.

Minimum agent version required: `2306.1.0.1`

## May 2023

### [Profile Management backup and quick setup (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html#quick-setup)

You can now [back up and restore](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets.html#back-up-and-restore) your Profile Management settings. You can now also setup Citrix Profile configurations using a restored backup, or a fresh template.

This template methodology is something we have been requesting for a little while now, so this is nice to see the first stages of this coming into the release. We hope to see this sort of logic make its way to Citrix Policy and ADMX as well.

Minimum agent version required: `2304.2.0.1`

### [Additional Actions in the Web Console](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#may-2023)

The following actions have been made available in the web console:

-  [Network Drives](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#network-drives). Using the web console, you can now add network drives as assignable actions. When assigned, those network drives are available for use within the user’s desktop. The feature has been enhanced to provide a better user experience.
-  [Virtual drives](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#virtual-drives). Using the web console, you can now add virtual drives as assignable actions. When assigned, those virtual drives are available for use within the user’s desktop. The feature has been enhanced to provide a better user experience.

Minimum agent version required: `2304.2.0.1`

### [Improved advanced settings now available in the web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings.html)

Advanced settings have been migrated to the web console and are available in **Advanced Settings** under each configuration set. Citrix have reorganized the settings to provide a better user experience.

### [Set your start page](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#set-your-start-page)

You can now set one of the following pages as your start page so that you land on it every time you sign in to the web console:

-  Agents
-  Reports
-  User Statistics
-  Usage Insights
-  Optimization Insights
-  Profile Container Insights

If no start page is set, you land on the Home page instead. After setting your start page, you can access it quickly by clicking the lightning icon on the left navigation of the console.

### [New version of WEM Tool Hub](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub.html)

A new version of WEM Tool Hub is now available: `2304.2.0.1`. The version includes performance enhancements and bug fixes.

## April 2023

### [App access control](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html#app-access-control)

This is the AppMasking equivalent feature discussed in the Profile Management tracking post. Using the web console, you can now add rules to control user access to items such as files, folders, and registries. A typical use case is to apply rules to control user access to apps installed on machines — whether to make apps invisible to relevant users. This feature can simplify application and image management. For example, using the feature, you can deliver identical machines to different departments while meeting their different application needs, thus reducing the number of images

Minimum agent version required: `2304.1.0.1`

### [Printers](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#printers)

Using the web console, you can now add printers to assign to your users. When assigned, those printers are available for use within the user’s desktop. The feature has been enhanced to provide a better user experience

Minimum agent version required: `2304.1.0.1`

### [WEM Tool Hub (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub.html)

The following two tools are now available in WEM Tool Hub:

-  **Printer assistant**. Use it to get a list of printers from your print server so that you can add them as assignable actions in the management console.
-  **Rule generator for app access control**. The equivalent of the FSLogix App Rule Editor. Use it to create rules to control user access to items such as files, folders, and registries. The rules are implemented through Citrix Profile Management. A typical use case is to apply rules to control user access to apps installed on machines — whether to make apps invisible to relevant users.

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#profile-management)

Workspace Environment Management now supports all supported versions of Profile Management through 2303. The following features are now available in both the legacy console and the web console.

-  **Enable active write back on session lock and disconnection**. If enabled, profile files and folders are written back only when a session is locked or disconnected. With both this option and the Enable active write back registry option enabled, registry entries are written back only when a session is locked or disconnected. If enabled, profile files and folders are written back only when a session is locked or disconnected. With both this option and the **Enable active write back registry** option enabled, registry entries are written back only when a session is locked or disconnected.
    -  In the [web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html#basic-settings), the feature is available under each configuration set in **Profiles > Profile Management Settings -> Basic settings**.
    -  In the [legacy console](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html#main-citrix-profile-management-settings), the feature is available in **Policies and Profiles > Citrix Profile Management Settings -> Main Citrix Profile Management Settings**.
-  **Enable app access control**. If enabled, Profile Management controls user access to items (such as files, folders, and registries) based on the rules you provide.
    -  In the [web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html#app-access-control), the feature is available under each configuration set in **Profiles -> Profile Management Settings > App access control**
    -  In the [legacy console](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html#app-access-control), the feature is available in **Policies and Profiles -> Citrix Profile Management Settings > App Access Control**.
-  **Enable VHD disk compaction**. If enabled, VHD disks are automatically compacted on user logoff when certain conditions are met. This option enables you to save the storage space consumed by profile container, OneDrive container, and mirror folder container.
    -  In the [web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html#profile-container), the feature is available under each configuration set in **Profiles -> Profile Management Settings -> Profile container**.
    -  In the [legacy console](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html#profile-container-settings), the feature is available in **Policies and Profiles -> Citrix Profile Management Settings -> Profile Container Settings**.
-  **Set free space ratio to trigger VHD disk compaction**, **Set number of logoffs to trigger VHD disk compaction**, and **Disable defragmentation for VHD disk compaction**. If E**nable VHD disk compaction** is enabled, use these three policies to adjust the default VHD compaction settings and behavior.
    -  In the [web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html#advanced-settings), the feature is available under each configuration set in **Profiles -> Profile Management Settings -> Advanced settings**.
    -  In the [legacy console](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html#advanced-settings), the feature is available in **Policies and Profiles -> Citrix Profile Management Settings -> Advanced Settings**.

Minimum agent version required: `2304.1.0.1`

## February 2023

### [Applications (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#applications-preview)

The new web console is slick. Here is another new addition for applications.

Using the web console, you can now add applications to assign to your users. When assigned, those applications have their shortcuts created on the desktop, Start menu, or taskbar, depending on your configuration. The feature has been enhanced to provide a better user experience. For more information, see Actions.

To enable this feature, go to **Home**, click the preview features icon in the upper-right corner, and enable **Applications**.

Minimum agent version required: `2302.1.0.1`

### [WEM Tool Hub (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/reference/wem-tool-hub.html)

A tool set, **WEM Tool Hub**, is now available for WEM administrators. It includes a collection of tools that aims to simplify the configuration experience for administrators. To download it, go to **Citrix Cloud > WEM service > Utilities**.

Expect growth in this toolset, currently it is the missing link between pulling resources from internal storefront environments (and workspace resources) into WEM, and assisting with the creation of icons without the madness of import/export/upload/etc.

### [New settings added to external tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#new-settings-added-to-external-tasks)

When using external tasks in the web console, you can now directly configure when the agent processes external tasks without going to **Legacy Console > Advanced Settings** for related settings. The newly added settings are:

-  Process external tasks on logon and refresh
-  Process external tasks on reconnection

This enhancement also provides detailed information on how to ensure that the agent processes external tasks.

## January 2023

### [Enhancements to automatic agent upgrade](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings.html#agent-settings)

The automatic agent upgrade feature has been migrated to the web console and is available in **Advanced Settings > Agent Settings** under each configuration set. The feature now provides a better user experience and offers extra capabilities. In addition to scheduling automatic upgrades for the agents, you now have the flexibility to control whether to apply agent upgrades to persistent or non-persistent machines.

Another good example of the WEM team listening to feedback - nice to see things come to life.

Minimum agent version required: `2301.1.0.1`

### [Automatically bind non-domain-joined agents to desired configuration sets](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/directory-objects.html#advanced-settings)

You can now set up binding rules for unbound non-domain-joined agents. Those rules dictate which configuration set to bind the matching agents to. This feature simplifies the process of adding non-domain-joined agents for WEM to manage.

Minimum agent version required: `2301.1.0.1`

### [Support for assigning GPOs to organizational units](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment.html#add-an-assignment-target)

Using the web console, you can now assign GPOs to organizational units. This eliminates the need to change your Active Directory structure for use with WEM.

Minimum agent version required: `2301.1.0.1`

## November 2022

### [External task (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html)

Using the web console, you can now create external tasks to assign to users. External tasks can be scripts or applications. Specify when to run external tasks to manage user environments precisely and effectively. The web console provides an extra capability for external tasks — letting you associate the scheduled trigger with external tasks to schedule when to run

To enable this feature, go to **Home**, click the preview features icon in the upper-right corner, and enable **External task**

Minimum agent version required: `2211.1.0.1`

### [Agents to download configuration data only when needed](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#november-2022)

Previously, WEM agents periodically connected to the WEM service to download configuration data whether or not there was a configuration change. Agents now periodically check with the service to see if any configuration changes were made:

-  If yes, agents download the configuration data.
-  If no, the configuration data is not downloaded.

This enhancement significantly reduces network usage, especially if you have a large deployment with many agents.

Minimum agent version required: `2211.1.0.1`

### [Filter enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment.html#add-a-filter)

This is a **huge** feature addition to the WEM Service and has been long awaited. This feature lets you use the **AND** and **OR** operators to build filters. You can use the operators to combine two or more conditions into a compound condition. This feature gives you more flexibility to build filters for use with assignments and scripted tasks.

Minimum agent version required: `2210.2.0.1`

## October 2022

### [Additional trigger types available](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/triggers.html)

The following built-in trigger types are now available when you create triggers:

-  **Machine shutdown**. Activates the trigger when machines shut down
-  **Machine startup**. Activates the trigger when machines start up

You can create triggers of these types and associate tasks with them. When activated, the triggers start those tasks in the user environment. The two additional trigger types give you more flexibility to control when to run your scripted tasks

Minimum agent version required: `2210.1.0.1`

### [Support for using task results as triggers (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/triggers.html#create-a-trigger)

The following trigger types are now available when you create triggers

-  **Cloud Health Check result**. Activates the trigger when Cloud Health Check returns specified health statuses
-  **Profile Management health check result**. Activates the trigger when Profile Management health check returns specified health statuses
-  **Custom scripted task result**. Activates the trigger when scripted tasks return specified results

You can create triggers of these types and associate tasks with them. When activated, the triggers start those tasks in the user environment. These trigger types let you automatically manage your user environments based on task execution results.

To enable this feature, go to Home, click the preview features icon in the upper-right corner, and enable **Use task results as triggers**.

Minimum agent version required: `2210.1.0.1`

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html#file-deduplication)

Workspace Environment Management now supports all supported versions of Profile Management through 2209. The following feature is now available in both the legacy console and the web console.

-  **File deduplication**. If enabled, Profile Management removes duplicate files from the user store and stores one copy of them in a central location. Doing so reduces the load on the user store by avoiding file duplication, thus reducing your storage cost.
    -  In the web console, the feature is available under each configuration set in **Profiles > Profile Management Settings > File deduplication**
    -  In the legacy console, the feature is available in **Policies and Profiles > Citrix Profile Management Settings > File Deduplication**

Minimum agent version required: `2210.1.0.1`

### [View the registration status of agents](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration.html#registrations)

In the web console, a tab, **Registrations**, is now available in **Monitoring > Administration > Agents**. The tab lets you view the registration status of agents in your WEM deployment. With the information, you can troubleshoot agent registration issues.

### [Support for cloning assignment targets](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment.html#clone-an-assignment-target)

You can now clone assignment targets (users and groups) from one configuration set to another, without the need to add them from scratch

## September 2022

### [Install and upgrade: Workspace Environment Management agent](https://docs.citrix.com/en-us/workspace-environment-management/service/get-started/install-and-configure.html#step-1-download-the-agent)

The Workspace Environment Management agent is no longer included as an additional component in the VDA installation.

## August 2022

### [Use Windows events as triggers](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/triggers.html)

A new trigger type, **Windows event**, is now available when you create triggers. It lets you create a Windows event based trigger. You can then associate tasks with it. When the Windows events meet the defined criteria, the trigger is activated and starts the associated tasks. This trigger type lets you automatically manage your user environments based on Windows events

Minimum agent version required: `2208.1.0.1`

### [Use file shares for file downloads on the agent side](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings.html)

Previously, file downloads on the agent side always occurred through Citrix Cloud. You can now let file downloads on the agent side occur through file shares. Doing so reduces network resources needed for other critical operations. This feature reduces traffic on networks and reduces the time to download files to agent machines.

Minimum agent version required: `2208.1.0.1`

### [Set timeouts for scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/scripted-task-settings.html#configure-a-scripted-task)

An option, **Set a timeout value**, is now available when you configure a scripted task. The option lets you specify the time (in minutes) after which the task is forced to end. If you do not specify a timeout, the task might keep running, thus preventing other tasks from running

Minimum agent version required: `2207.2.0.1`

### [Invite users to enroll agents](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/enrollment.html)

A new node, Enrollment, is now available in the web console. The node contains two pages:

-  **Enrolled Agents**. Lists all enrolled agents. You can manage them as needed.
-  **Invitation**. Lets you send enrollment invitations to users. Each invitation includes an invitation code and the steps needed to complete the enrollment.

Minimum agent version required: `2207.2.0.1`

### [Contextualize scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/scripted-task-settings.html#configure-a-scripted-task)

An option, Filter, is now available in General when you configure a scripted task. The option lets you use a filter to contextualize the task. As a result, the WEM agent runs the task only when all conditions in the selected filter are met

Minimum agent version required: `2207.2.0.1`

## July 2022

### [Support for performing administrative tasks for non-domain-joined and enrolled agents](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/administration.html#agents)

You can now perform administrative tasks (such as refreshing the cache, resetting settings, and retrieving agent information) for non-domain-joined and enrolled agents through the administration console, just like you do for other agents. Technically, this feature is a different implementation. The target agents are not immediately notified of performing those tasks. The notifications are sent when the target agents or other agents on the same subnet connect to Citrix Cloud to refresh settings. So, there might be a delay until the tasks run on the agent side. The more agents you have on the same subnet, the shorter the delay.

This feature is available in both the legacy console and the web console.

-  In the web console, go to **Monitoring > Administration > Agents**
-  In the legacy console, go to **Administration > Agents**

Minimum agent version required: `2207.1.0.1`

### [Configure Windows GPOs by using Group Policy Administrative Templates](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#group-policy-settings)

In the web console, a tab, **Template-based**, is now available in **Actions > Group Policy Settings** under each configuration set. The tab lets you configure Windows GPOs by using Group Policy Administrative Templates. You can configure GPOs at a machine and user level. After that, you deploy them by assigning them to your users, just like you do for registry-based GPOs.

Minimum agent version required: `2207.1.0.1`

### [New features available in scripted task settings](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/scripted-task-settings.html#configure-a-scripted-task)

The following new features are now available when you configure a scripted task:

-  **File path**. A parameter type that lets you pass a file path as a parameter to the `System.IO.FileInfo` class.
-  **Collect output even if runtime errors occur**. An option that controls whether to collect output file content and console output even if errors occur while running the task

Minimum agent version required: `2207.1.0.1`

### [Deploy GPOs through the web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/actions.html#group-policy-settings)

In the web console, you can now manage Group Policy settings. The management takes the form of configuring Windows Group Policy Objects (GPOs). After you add or import your settings, you deploy them by assigning them to your users

Minimum agent version required: `2206.2.0.1`

### [Profile Management](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html#advanced-settings)

Workspace Environment Management now supports all versions of Profile Management through 2206. The following new options are now available in both the legacy console and the web console.

-  **Enable profile streaming for pending area**. If enabled, files in the pending area are fetched to the local profile only when they are requested. This ensures optimum logon experience in concurrent session scenarios.
    -  In the web console, the option is available under each configuration set in **Profiles > Profile Management Settings > Streamed user profiles**
    -  In the legacy console, the option is available in **Policies and Profiles > Citrix Profile Management Settings > Streamed user profiles**
-  **Enable concurrent session support**. Provides native Outlook search experience in concurrent sessions. If enabled, each concurrent session uses a separate Outlook OST file. You can specify the maximum number of VHDX disks for storing Outlook OST files.
-  **Enable asynchronous processing for user Group Policy on logon**. If enabled, Profile Management roams with users a registry value that Windows uses to determine the processing mode for the next user logon — synchronous or asynchronous processing mode. This ensures that the actual processing mode is applied each time users log on.
-  **Enable OneDrive container**. If enabled, Profile Management roams OneDrive folders with users by storing the folders on a VHDX disk. The disk is attached during logons and detached during logoffs.
    -  In the web console, the three options are available under each configuration set in **Profiles > Profile Management Settings > Advanced settings**
    -  In the legacy console, the three options are available in **Policies and Profiles > Citrix Profile Management Settings > Advanced settings**

Minimum agent version required: `2206.2.0.1`

### [Application launcher](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/applications.html#application-launcher)

An application launcher tool, AppLauncherUtil.exe, is now available in the agent installation folder. The tool aggregates all applications you assigned to your users through the administration console. Using the tool, users can launch all assigned applications in one place

Minimum agent version required: `2206.2.0.1`

## May 2022

### [Enroll agents without configuring Citrix Cloud Connectors](https://docs.citrix.com/en-us/workspace-environment-management/service/get-started/enroll-agent.html)

Previously, you had to configure Cloud Connectors for WEM agents to manage them. You can configure Cloud Connectors in two ways:

-  [Configure Cloud Connectors while installing the agent](https://docs.citrix.com/en-us/workspace-environment-management/service/get-started/install-and-configure.html#step-3-install-the-agent)
-  [Configure the Discover Citrix Cloud Connector from CVAD service policy](https://docs.citrix.com/en-us/workspace-environment-management/service/get-started/install-and-configure.html#step-2-configure-group-policies-optional). The agent discovers Cloud Connector information from the relevant Citrix DaaS (formerly Citrix Virtual Apps and Desktops service) deployment and then connects to the corresponding Cloud Connector machines

Starting with this release, you can enroll WEM agents without configuring Citrix Cloud Connectors. The enrollment applies to both domain-joined and non-domain-joined machines.

Minimum agent version required: `2205.1.0.1`

### [Scripted task updates](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks.html#add-a-scripted-task)

The following features are now available with scripted tasks:

-  [Support for bundling multiple files into a single zip file to upload](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks.html#add-a-scripted-task). When adding a scripted task, you can now bundle multiple files into a single zip file to upload. This feature is useful when you want to run a scripted task that comprises multiple script files. After uploading the zip file, you specify an entry point, indicating which file to run at the beginning of the task
-  [Include only regular expression matches in scripted task reports](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/scripted-task-settings.html#configure-a-scripted-task). A new option, **Include only regular expression matches in reports**, is now available in **Output** when you configure a scripted task. The option controls whether to include the entire output content in reports or only content that matches the regular expression. Enabling the option reduces the amount of data transmitted to Citrix Cloud
-  [Ability to use tags to identify scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks.html#add-a-scripted-task). You can now use tags to identify your scripted tasks. Also, the tags act as filters, letting you rearrange your view of tasks depending on criteria that are important to you
-  [More scheduling options available with scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/scripted-task-settings.html#configure-a-scripted-task). You now have additional options to control when scripted tasks run. In addition to the hourly recurring pattern, you can now set daily, weekly, and monthly recurrence patterns. You can also specify the date and time at which you want scripted tasks to run, giving you more precise control. For agents earlier than 2205.1.0.1, be aware of the considerations when using the feature

Minimum agent version required: `2205.1.0.1`

### [Enhancements to Profile Management health check](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings.html#monitoring-preferences)

Enhancements to the Profile Management health check feature:

-  In the **More** menu of **Monitoring > Administration > Agents**:
    -  Renamed **Refresh Profile Management configuration check** to **Run Profile Management health check** to make it easy to understand
    -  Added an option, **View Profile Management health check report**. The option provides quick access to Profile Management health reports related to the target agent machines.
-  In **Advanced Settings > Monitoring Preference**s under a configuration set
    -  Added a section, **Profile Management health check**. The section lets you specify which aspects to cover in Profile Management health check reports

Minimum agent version required: `2205.1.0.1`

### [Ability to import Group Policy settings from registry files](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/group-policy-settings.html)

An option, **Import Group Policy settings from Registry Files**, is now available in **Legacy Console > Actions > Group Policy Settings**. With the option, you can convert registry values that you export using the Windows Registry Editor into GPOs for management and assignment. If you are familiar with the **Import registry files** option available with Registry Entries, this feature:

-  Lets you import registry values under both `HKEY_LOCAL_MACHINE` and `HKEY_CURRENT_USER`
-  Lets you import registry values of the `REG_BINARY` and `REG_MULTI_SZ` types
-  Supports converting deletion operations associated with registry keys and values that you define in .reg files

### [Filters now available in the web console](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment.html#filters)

In the web console, a new page, **Filters**, is now available within **Assignments** under each configuration set. Using that page, you can add filters for controlling when to assign actions to your users.

## April 2022

### [Updates to the **More** menu in **Monitoring > Administration**](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration.html#wem-agents)

This release organizes existing options in the **More** menu in **Web Console > Monitoring > Administration** into the following groups: **Agent, Profile**, and **Power management**. The workflows for using the options remain the same.

Additional updates to the **More** menu include:

-  Renaming **Wake up agents** to **Wake** and moving it to the **Power management** group
-  Adding the following four power management options:
    -  **Shut down**. Lets you shut down agents
    -  **Restart**. Lets you restart agents
    -  **Sleep**. Lets you put agents into sleep mode
    -  **Hibernate**. Lets you put agents into hibernate mode

Minimum agent version required: `2204.1.0.1`

### [Support for cloning scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks.html#clone-a-scripted-task)

You can now clone an existing scripted task to use as a template for a new one, without the need to create a similar task from scratch

### [Manage Azure Virtual Desktop using Citrix Optimization Pack](https://docs.citrix.com/en-us/workspace-environment-management/service/citrix-optimization-pack/azure-virtual-desktop.html)

The Citrix Optimization Pack for Azure Virtual Desktop is a new Citrix offering for optimizing Azure Virtual Desktop workloads

## March 2022

### [Profile Management now available in the web console (preview)](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/citrix-profile-management.html)

In the web console, you can now use Citrix Profile Management to manage user profiles across sessions and desktops (You need to turn this feature on to use it)

### [Ability to pass parameters to scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/scripted-task-settings.html#configure-a-scripted-task)

Using the web console, you can now provide inputs as parameter variables in a scripted task at runtime. Doing that lets you control how the scripted task behaves without changing the underlying code.

WEM provides you flexibility in what parameters you want to use — parameters that accept only objects of a specific type (such as, string, integer, switch) and named parameters (using the name of the parameter)

Minimum agent version required: `2203.2.0.1`

### [Option to upgrade agents on demand](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/monitoring/administration.html#wem-agents)

You can now upgrade your WEM agents from the console on demand. The option is available in both the legacy console and the web console. To use the feature:

-  In the legacy console, go to **Administration > Agents**, right-click an agent, and then select **Upgrade agent to latest version**
-  In the web console, go to **Monitoring > Administration > Agents**, select one or more agents, click **More**, and then select **Upgrade agent to latest version**

Minimum agent version required: `2203.2.0.1`

### [Updates for the web console](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#march-2022)

This release introduces the following pages to the web console:

-  [**Home**](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/home.html): Provides an overview of your WEM deployment along with information necessary for you to get to know and get started with WEM quickly. The interface comprises the following four parts:
    -  **Overview**: Provides an overview of the WEM deployments
    -  **Quick access**: Provides quick access to a subset of the key features that WEM offers
    -  **Highlights**: Shows the key features that WEM offers
    -  **Preview features**: Shows features that are currently in preview. You can enable or disable preview features yourself
-  [**Directory Objects** *Preview!*](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/directory-objects.html) Lets you add machines, groups, OUs, and more, that you want WEM to manage. You can now do the following:
    -  Add machines, groups, Organizational Units (OUs), and more, that you want WEM to manage
    -  Apply settings to agents that are not bound to any configuration set. You can control how unbound agents behave
-  [**Assignment Target** *Preview!*](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/assignment.html) Lets you add users and groups (targets) so that you can assign actions and security rules to them

### [Support for migrating your service instance yourself](https://docs.citrix.com/en-us/workspace-environment-management/service.html)

If your WEM service instance does not reside in your current region, you can now migrate the instance to the current region yourself. Sign in to Citrix Cloud, go to `Workspace Environment Management > Utilities` and select `Start migration`.

It can take up to two days to receive the notification. Citrix encourages migration to the current region to improve performance. This is signficant for those that did not have a local WEM region initially (APJ for example)

## January 2022

### [Web console now available as a preview](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#january-2022)

A new, web-based Workspace Environment Management (WEM) console is now available. Citrix are in the process of migrating the full set of functionalities from the legacy console to the web console. The web console generally responds faster than the legacy console. You can switch between the web console and the legacy console from within the Manage tab to perform your configuration or deployment management tasks. Click the down arrow next to Manage and select an option:

-  **Legacy Console** takes you to the legacy console
-  **Web Console** takes you to the new, web-based console

The following features are available only in the web console:

-  [Run scripted tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/scripted-tasks.html) Scripted tasks can be added to WEM and automatically executed
-  [Save a backup of a configuration set automatically](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets.html#manage-automatic-backup) Automatic backup for configuration sets
-  [Scan large files in profile containers](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/advanced-settings.html) The WEM agent to run a scan of large files on profile containers when container usage exceeds the specified threshold value
-  [Prevent child processes from inheriting CPU priority](https://docs.citrix.com/en-us/workspace-environment-management/service/manage/configuration-sets/system-optimization.html#cpu-spike-protection) Allows for specifying a processes whose child processes should not inherit the CPU priority
-  Language localization support for the web console. The web console supports non-English characters and keyboard input even when the console itself is not localized in the preferred language of an administrator. The supported languages are as follows: French, German, Spanish, and Japanese

### [Apply settings to unbound agents](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/active-directory-objects.html#advanced)

You can now apply settings to agents that are not bound to any configuration set. The feature lets you control how unbound agents behave.

Minimum agent version required: `2201.2.0.1`

### [Support for managing non-domain-joined machines in Citrix Virtual Apps and Desktops Standard for Azure deployments](https://docs.citrix.com/en-us/workspace-environment-management/service/manage-non-domain-joined-machines.html)

You can now use WEM service to manage non-domain-joined machines in Citrix Virtual Apps and Desktops Standard for Azure deployments. This support enables you to assign policies and settings to non-domain-joined machines as you do with domain-joined machines.

Minimum agent version required: `2201.2.0.1`

### [Support for enumerating Azure AD users and groups](https://docs.citrix.com/en-us/citrix-cloud/citrix-cloud-management/identity-access-management/connect-azure-ad.html)

WEM service now supports enumerating Azure Active Directory (AD) users and groups. After connecting your Citrix Cloud account to your Azure AD, you can add Azure AD users and groups that you want WEM to manage

### [External task enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/external-tasks.html)

This release includes enhancements to the external task feature. The feature now provides you with three additional options to control when to run external tasks:

-  **Disconnect** controls whether to run the external task when a user `disconnects` from a machine where the agent is running
-  **Lock** controls whether to run the external task when a user `locks` a machine where the agent is running
-  **Unlock** controls whether to run the external task when a user `unlocks` a machine where the agent is running

Minimum agent version required: `2201.1.0.1`

### [Profile Management enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html)

Workspace Environment Management now supports all versions of Profile Management through 2112. The following new options are now available in the `Administration Console > Policies and Profiles > Citrix Profile Management Settings` interface:

-  **Enable File Exclusions for Profile Container**. Available on the `Profile Container Settings` tab, the option controls whether to exclude the listed files from the profile container
-  **Enable File Inclusions for Profile Container**. Available on the `Profile Container Settings` tab, the option controls whether to keep the listed files in the profile container when their parent folders are excluded
-  **Customize storage path for VHDX files**. Available on the `Advanced Setting`s tab, the option controls whether to store VHDX files of different policies in different folders under the specified storage path

Minimum agent version required: `2110.2.0.1`

### [Administrative access to WEM service based on Azure Active Directory group membership](https://docs.citrix.com/en-us/citrix-cloud/citrix-cloud-management/identity-access-management/connect-azure-ad.html)

You can now manage administrative access to WEM service based on Azure AD group membership. Users (administrators) within the Azure AD group can directly onboard to Citrix Cloud and access WEM service – you do not need to manually add them in Citrix Cloud. A general workflow to use the feature is as follows:

Connect your Citrix Cloud account to your Azure AD -> Add the applicable group to Citrix Cloud from Azure AD -> Users can sign in to Citrix Cloud by using their Azure AD credentials

## November 2021

### Message about instance migration

If you use a service in another region, a message now appears when you sign in to the administration console. The message reminds you to migrate your service instance to your current region

### [Export Statistics for Migration](https://docs.citrix.com/en-us/workspace-environment-management/service/migrate.html#step-2-export-the-database-data-to-an-sql-file)

Citrix added an option `Export statistics` to the migration tool. Use the option to control whether to export agent and user statistics when performing migrations

## October 2021

### [Allow users to self-elevate certain applications](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#self-elevation)

This release introduces `self-elevation` for the `privilege elevation` feature. With s`elf-elevation`, you can automate privilege elevation for certain users without the need to provide the exact executables beforehand. Those users can request self-elevation for any applicable file simply by right-clicking the file and then selecting `Run with administrator privileges` in the context menu. After that, a prompt appears, requesting that they provide a reason for the elevation. This reason is for captured for auditing purposes. If the criteria is met, the elevation is applied, and the files run successfully with administrator privileges.

In addition, self-elevation provides flexibility to create allow lists for the files you permit users to self-elevate or block lists for files you want to prevent users from self-elevating.

Minimum agent version required: 2109.2.0.1

### [Bind a Citrix Virtual Apps and Desktops service catalog to a configuration set](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/machine-catalogs-create.html#workspace-environment-management-optional)

You can now use the CVAD Service console to bind a catalog to a WEM configuration set. This is a quick option to automatically add a catalog to WEM configuration sets

{: .box-warning}

Whilst a great feature, I have seen instances of inconsistencies in configuration set bindings - tried and proven AD objects in WEM fixed the issue

### [Workspace Environment Management now available in Citrix Cloud Japan](https://docs.citrix.com/en-us/citrix-cloud-japan)

Workspace Environment Management service is now available in Citrix Cloud Japan, a cloud that is isolated and separate from Citrix Cloud. Japanese customers can use the service in a dedicated Citrix-managed environment.

The service requires Citrix Cloud Connector version `6.29.0.58841`

### [Support for Windows 11](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#october-2021)

Minimum agent version required: 2109.2.0.1

## September 2021

### [More granular control over applying privilege elevation to child processes](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

Previously, when you used the Apply to Child Processes setting in a rule, you applied the rule to all child processes that the executable started. This release provides you with three additional options, giving you more granular control over applying privilege elevation to child processes

-  Apply only to executables in the same folder
-  Apply only to signed executables
-  Apply only to executables of the same publisher

Minimum agent version required: 2109.2.0.1

### [Support for Windows Server 2022](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#september-2021)

Minimum agent version required: 2109.2.0.1

## August 2021

### [Enablement of Asia Pacific South based instances](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#august-2021)

Citrix now offers Asia Pacific South based instances

## July 2021

### [Notifications about new agent versions](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#july-2021)

You can now opt in to Agent Version Upgrade notifications

## June 2021

### [Parameter matching for privilege elevation](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

This release introduces parameter matching for the privilege elevation feature. Parameter matching gives you more granular control by letting you restrict privilege elevation to executables that match the specified parameter. A parameter works as a match criterion. To further expand the criterion, you can use regular expressions.

Minimum agent version required: 2106.2.0.1

### [Privilege elevation support for Windows installer files](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

Starting with this release, you can apply privilege elevation to `.msi` and `.msp` Windows installer files. Using the feature, you elevate the privileges of non-administrative users to an administrator level necessary for some Windows installer files. As a result, those users can run those files as if they are members of the administrators group

Minimum agent version required: 2105.1.0.1

### [Profile Management Enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html)

Workspace Environment Management now supports all versions of Profile Management through 2106. The Administration Console > Policies and Profiles > Citrix Profile Management Settings user interface has changed, adding:

-  Replicate user stores
-  Accelerate folder mirroring
-  User Store Credentials

Minimum agent version required: 2106.2.0.1

## May 2021

### [Configure user processes as triggers for external tasks](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/external-tasks.html)

This release includes enhancements to the external task feature. The feature now provides you with two additional options to control when to run external tasks:

-  **Run when processes start** controls whether to run the external task when specified processes start
-  **Run when processes end** controls whether to run the external task when specified processes end

Using the two options, you can define external tasks to supply resources only when certain processes are running and to revoke those resources when the processes end. Using processes as triggers for external tasks lets you manage your user environments more precisely compared with processing external tasks on logon or logoff

Minimum agent version required: 2104.1.0.1

### [Enhancements to process hierarchy control](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#process-hierarchy-control)

This release introduces enhancements to the process hierarchy control feature that improve overall performance and stability. The enhancements include the following changes:

-  The AppInfoViewer tool has been updated to include the following two options: `Enable Process Hierarchy Control` and `Disable Process Hierarchy Control`. For the process hierarchy control feature to work, you must first use the tool on each agent machine to enable the feature. Every time you use the tool to enable or disable the feature, a machine restart is required
-  In certain scenarios, you must restart your agent machine after upgrading or uninstalling the agent

Minimum agent version required: 2105.1.0.1

## April 2021

### [Process hierarchy control](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#process-hierarchy-control)

This release introduces the process hierarchy control feature. The feature lets you control whether certain child processes can be started through their parent processes. You create a rule by defining parent processes and then designating an allow list or a block list for their child processes. You then assign the rule on a per user or per user group basis. The following rule types are available:

-  **Path** applies the rule to an executable according to the executable file path
-  **Publisher** applies the rule according to publisher information
-  **Hash** applies the rule to identical executables as specified

Minimum agent version required: 2103.2.0.1

### [Overwrite or merge application security rules](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#application-security)

This release adds two settings, **Overwrite** and **Merge**, to the **Administration Console > Security > Application Security tab**. The settings let you determine how the agent processes application security rules.

-  Select Overwrite if you want to overwrite existing rules. When selected, the rules that are processed last overwrite rules that were processed earlier. We recommend that you apply this setting only to single-session machines
-  Select Merge if you want to merge rules with existing rules. When conflicts occur, the rules that are processed last overwrite rules that were processed earlier

## March  2021

### [Discover Citrix Cloud Connectors from the CVAD service](https://docs.citrix.com/en-us/workspace-environment-management/service/get-started/install-and-configure.html#step-2-configure-group-policies-optional)

This release introduces a policy setting titled Discover Citrix Cloud Connector from CVAD service. If you have not yet configured Cloud Connectors for the agent, use the setting to control whether the agent discovers Cloud Connector information from the relevant Citrix Virtual Apps and Desktops (CVAD) service deployment. The agent then connects to the corresponding Cloud Connector machines automatically

### [Support for the Windows 10 2009 template](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/system-optimization/citrix-optimizer.html)

Citrix added support for the Windows 10 2009 (also known as 20H2) template introduced in Citrix optimizer. You can now use WEM service to perform template-based system optimizations for Windows 10 2009 machines. In addition, Citrix have updated all existing templates to reflect changes introduced in the latest standalone Citrix optimizer

### [Brand-new home page](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#march-2021)

This release replaces the home page of the WEM administration console with a quick-start page that provides information necessary for you to get started with the WEM service

### [Profile Management Enhancements](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/policies-and-profiles/citrix-upm-settings.html)

Workspace Environment Management service now supports all versions of Profile Management through 2103. The following new options are now available in the Administration Console > Policies and Profiles > Citrix Profile Management Settings interface:

-  Enable Local Cache for Profile Container
-  Enable multi-session write-back for profile containers
-  Enable Profile Streaming for Folders

## January  2021

### [Microsoft Sync Framework 2.1 deprecation](https://docs.citrix.com/en-us/workspace-environment-management/service/whats-new.html#january-2021)

Microsoft Sync Framework 2.1 reached End of Life on January 12, 2021. WEM has removed the legacy sync service based on that framework and instead uses a new sync framework, Dotmim.Sync, an open-source sync framework

### [WEM agent integration with the Citrix Virtual Apps and Desktops product software](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops-service/install-configure/install-vdas.html#step-5-workspace-environment-management)

The WEM agent is integrated with the Citrix Virtual Apps and Desktops product software, letting you include the WEM agent when installing a Virtual Delivery Agent (VDA). This integration is reflected in the Citrix Virtual Apps and Desktops 2012 product software and later

### [Support for condition-based assignment of Group Policy settings](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/actions/group-policy-settings.html#contextualize-group-policy-settings)

Starting with this release, you can make Group Policy settings conditional by using a filter to contextualize their assignments. A filter comprises a rule and multiple conditions. The WEM agent applies the assigned Group Policy settings only when all conditions in the rule are met in the user environment at runtime. Otherwise, the agent skips those settings when enforcing filters.

### [Privilege elevation](https://docs.citrix.com/en-us/workspace-environment-management/service/using-environment-management/security.html#privilege-elevation)

This release introduces the privilege elevation feature. The feature lets you elevate the privileges of non-administrative users to an administrator level necessary for some executables. As a result, those users can start those executables as if they are members of the administrators group.

You can configure how a rule behaves according to the type of the operating system. You can also configure whether a rule takes effect at a particular time or within a particular time range. You assign a rule on a per user or per user group basis.

Minimum agent version required: 2010.2.0.1
