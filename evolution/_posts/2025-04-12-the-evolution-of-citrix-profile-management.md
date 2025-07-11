---
layout: post
title: The Evolution of Citrix Profile Management
permalink: "/the-evolution-of-citrix-profile-management/"
categories: [Citrix, UPM, Profiles, Windows, CVAD, Cloud, evolution]
description: Tracking the progress of Citrix Profile Management capability
image:
  path: /assets/img/the-evolution-of-citrix-profile-management/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
related_posts:
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-wem-service.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-wem.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-machine-creation-services-with-microsoft-azure.md
  - evolution/_posts/2025-04-12-the-evolution-of-citrix-workspace.md
---

<!--excerpt-->

-  Table of Contents
{:toc .large-only}

Citrix Profile Management is quietly kicking goals and developing quickly. This post aims to track the changes and releases as they occur, and provide a single point of reference. It is a companion post to my initial [Citrix UPM and FSLogix Conainers](https://jkindon.com/citrix-upm-and-fslogix-containers/) post, which outlined some decision points around profile management tool selection.

This list will start at CVAD 1912 LTSR, anything prior to that, refer to the appropriate documentation

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

## Version 2411

### [Support for machine-level redirections](https://docs.citrix.com/en-us/profile-management/current-release/configure/rule-based-redirections)

With the **App access control** policy, you can now implement machine-level redirections for files, folders, registry keys, and registry values using rules. The use cases for this feature include:

-  Implement data roaming. Redirect non-user-profile data to a file share, ensuring users can access the same data regardless of which machines they sign into.
-  Enhance data protection. Redirect critical data to alternative locations or values, protecting it from unauthorized access.
-  Customize the user experience. Tailor app experience based on specific requirements.

### [App access control policy enhanced with assignment exclusions](https://docs.citrix.com/en-us/profile-management/current-release/configure/app-access-control)

You can now specify excluded users, machines, and processes when configuring rule assignments for the **App access control** policy. Previously, you could only assign rules to groups of users, machines, and processes. This enhancement lets you define exclusions within those groups, offering more precise control over rule enforcement.

### [New policy for access control for redirected folders](https://docs.citrix.com/en-us/profile-management/current-release/configure/configure-folder-redirection#grant-users-access-to-redirected-folders)

By default, when you enable folder redirection policies for a user, the redirection target folders are accessible only to the user and the SYSTEM user. Previously, to grant other users access, you had to enable the **Grant administrator permission** policy. This policy grants members in the Local Administrators group access to the redirection target folders.

With a new policy, **Users and groups to access redirection target paths**, you can now grant specific domain users or groups **Read & Execute** permissions on the redirection target folders, eliminating the need to add them to the Local Administrators group. This policy enhances security by limiting permissions only to what is necessary.

### [New policy for accelerating UWP app loading](https://docs.citrix.com/en-us/profile-management/current-release/configure/uwp-app-loading-accelerate)

With a new policy, **Enable AppX package load acceleration**, you can now accelerate the loading of UWP apps and improve their consistency in non-persistent environments.
By default, Windows stores UWP App registration information locally on each machine, which can be lost upon restart in non-persistent environments. With this policy enabled, Profile Management creates a VHDX container for each machine to store the UWP app registration data, speeding up user logon and preventing data loss on restarts. 

### [New policies for notifying users when their profile size exceeds a quota](https://docs.citrix.com/en-us/profile-management/current-release/configure/alert-users-for-oversized-profile)

Citrix Profile Management now introduces two new policies to monitor the user profile size and notify users when it exceeds a quota:

-  **Notify user when profile size exceeds quota**: Lets you set a quota for the user profile and notify users when their profile size exceeds it.
-  **Notification message when profile size exceeds quota**: Lets you set the notification message users receive.

This feature helps prevent data loss by notifying users to manage their profile data before logging off. It applies only to the file-based profile solution.

### [In-session failover support for profile streaming](https://docs.citrix.com/en-us/profile-management/current-release/whats-new.html#in-session-failover-support-for-profile-streaming)

Profile streaming now includes improved failover capabilities. When the **Replicate user stores** policy is enabled, if the active user store becomes unavailable, Profile Management automatically switches to an available store for subsequent streaming requests. This enhancement lets files and folders be streamed continuously after the failover, minimizing data disruptions.

This update applies to profile streaming for files, folders, and the pending area.

## Version 2407

### [In-session profile container failover among user stores](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container#optional-enable-in-session-profile-container-failover-among-user-stores)

By default, when multiple user stores are deployed, profile container failover occurs only ***at user logon***. A new policy, **Enable in-session policy container failover among user stores**, now expands the failover scope to the entire session, ensuring profile redundancy throughout the session. With this policy enabled, if Profile Management loses connection to the active profile container during a session, it automatically switches to another available one.

### [Support for OneNote cache synchronization](https://docs.citrix.com/en-us/profile-management/current-release/whats-new#support-for-onenote-cache-synchronization)

OneNote cache folders can now roam with users. Therefore, a user can access the same OneNote cache data from different devices.

### [Registry exclusion and inclusion support extended to container-based profile solution](https://docs.citrix.com/en-us/profile-management/current-release/configure/include-and-exclude-items)

The existing registry exclusion and inclusion policies now apply to the container-based profile solution. With those policies, you can specify registry keys in the HKCU hive that Profile Management excludes from syncing to profile containers during user logoff.

### [Enhancements to Folder Redirection policies](https://docs.citrix.com/en-us/profile-management/current-release/configure/configure-folder-redirection)

Improved Folder Redirection policies with two enhancements for greater configuration flexibility:

-  **Redirect to the local user profile location**. A new option that enables you to redirect folders to the local user profile location. Previously, to disable a folder redirection, you had to set the corresponding **Folder Redirection** policy to either **Not Configured** or **Disabled**. With this new option, you can now achieve the same goal of disabling folder redirection while keeping the policy **Enabled**.
-  **Disable moving contents to new location**. By default, when you modify redirection paths, Profile Management automatically moves contents from the previous path to the new one. With this new option, you can now disable content moving.

### [Windows event for calculating logon duration](https://docs.citrix.com/en-us/profile-management/current-release/troubleshoot/events#list-of-events)

Profile Management introduces a new Window event (event ID: 5009) for calculating logon duration. With this event, you can now receive a clear indication when the desktop window becomes visible, a crucial endpoint for logon completion.

### [User store sync enhancement](https://docs.citrix.com/en-us/profile-management/current-release/whats-new#user-store-sync-enhancement)

Previously, during fault recovery for a replicated user store, Profile Management copied user profiles from a functioning user store to the failed one ***during user logon***. This behavior often strained file servers and storage during peak hours, leading to potential delays in user logon times. With this enhancement, synchronization is now delayed ***until after user logon***, ensuring a more efficient and streamlined process.

### [Enhanced profile reset for the container-based solution](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/director/troubleshoot-deployments/user-issues/reset-user-profile.html)

When resetting container-based profiles, Profile Management now not only restores policy settings to defaults but also preserves user data. With this enhancement, you can reset container-based profiles without the risk of losing user data.

### [Health check enhancements](https://docs.citrix.com/en-us/profile-management/current-release/whats-new#health-check-enhancements)

To describe Profile Management status, Citrix introduced new result types for the Profile Management health check tool:

-  **Invalid**: Indicates Profile Management is either not found or not enabled.
-  **Error**: Indicates configuration issues in Profile Management.
-  **Warning**: Identifies a suboptimal state of Profile Management.
-  **Notice**: Identities an acceptable state of Profile Management.
-  **Good**: Identities Profile Management is in a healthy state.

You can now gain a clearer and more detailed insight into the status of Profile Management through Workspace Environment Management.

### [Ability to collect insights on VHD compaction actions](https://docs.citrix.com/en-us/profile-management/current-release/whats-new#ability-to-collect-insights-on-vhd-compaction-actions)

Profile Management can now collect statistical data on VHD compaction actions and provide it to Workspace Environment Management (WEM) for reporting.

### [Enhanced user profile monitoring](https://docs.citrix.com/en-us/profile-management/current-release/whats-new#enhanced-user-profile-monitoring)

The Profile Management plug-in can now gather performance metrics from Profile Management and FSLogix. This enhancement enables Citrix Director to deliver comprehensive profile usage and performance data in user session reports.

## Version 2402 (CU1)

LTSR 2402 CU1 introduced two changes for CPM:

-  Profile streaming for folders feature is enabled by automatic configuration in the file-based profile solution
-  Citrix profile management supports new Microsoft Teams registration in user roaming scenario

## Version 2311

### [Improved user store selection](https://docs.citrix.com/en-us/profile-management/current-release/configure/replicate-user-stores#change-the-user-store-selection-method)

By default, when multiple user stores are available, CPM selects the store with the *latest* profile data. If more than one store has the latest profile, Profile Management selects the one configured earliest.

With a new policy, **User store selection method**, you can now enable Profile Management to select the store with the best access performance.

CPM performs a check to see which store has the better performance (how fast it can be accessed) and then uses that path as the primary store.

### [Files deduplication support extended to profile containers](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-file-deduplication)

File deduplication has been extended to profile containers, allowing you to efficiently reduce storage costs for profile containers. By default, Profile Management deduplicates files from profile containers only when those files are larger than 256 MB. If necessary, you can increase this threshold size using a new policy, **Minimum size of files to deduplicate from profile containers**.

### [Support for force logging off users when the profile container is unavailable during logon](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container#optional-specify-whether-to-log-off-users-when-the-profile-container-is-not-available-during-logon)

By default, when the profile container is unavailable during user logon, a user logs on using the temporary profile instead. However, this behavior leads to data loss for any changes made during the session.

There is a new policy, **Log off users when profile container is not available during logon**. With this policy, you can now force log-off users off instead.

### [Support for enabling read access to profile containers](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container#optional-grant-ad-users-read-access-to-profile-containers)

By default, a profile container is accessible only to its owner. With a new policy, **Users and groups to access profile container**, you can now enable other users to have Read access to the profile container.

This policy empowers you to exercise more precise and secure control over profile container access.

### [Support for enabling both multi-session write-back and local caching for profile containers](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container)

In container-based profile solutions, you can now enable both the **Enable multi-session write-back for profile containers** and **Enable local caching for profile containers** policies. This enhancement improves user experience by combining the benefits of both policies, which include:

-  Data consistency across concurrent sessions (through multi-session write-back)
-  Faster logon and logoff times and reduced network load (through local caching)

### [Multi-session runtime sync support for OneDrive files](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-the-onedrive-container)

With the OneDrive container enabled, any changes a user makes to OneDrive files in a session are now instantly visible in its concurrent sessions. This improvement reduces synchronization conflicts and ensures data integrity.

### [Single Sign-On (SSO) sync support for OneDrive Container](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-the-onedrive-container)

With this enhancement, users now don’t have to reenter credentials for OneDrive during subsequent logons, improving user convenience.

### [Support for the new Microsoft Teams](https://docs.citrix.com/en-us/profile-management/current-release/whats-new.html#support-for-the-new-microsoft-teams)

With the UWP app roaming policy enabled, the new Microsoft Teams app can now roam with users. Therefore, users can access the same Microsoft Teams app with their personalized settings and data from different devices.

### [Health check enhancements](https://docs.citrix.com/en-us/profile-management/current-release/whats-new.html#health-check-enhancements)

Citrix enhanced the Profile Management health check tool to provide more comprehensive health checks. Besides the existing status checks, the tool can now provide more checks such as an assessment of logon times, letting you quickly identify and resolve issues that might impact the user experience.

### [Enhanced Profile Management logs](https://docs.citrix.com/en-us/profile-management/current-release/troubleshoot/log-file-checklist)

Citrix enhanced the Profile Management logs to provide more details for user logon and logoff processes. This improvement enables you to quickly pinpoint the underlying reasons for slow logons or logoffs.

### [New Windows events for monitoring size changes and sync process durations for pending areas](https://docs.citrix.com/en-us/profile-management/current-release/troubleshoot/events)

Citrix added more Windows events for monitoring tools to track both size changes and sync process durations for the pending area. This enhancement provides you with valuable data to more efficiently identify and resolve relevant issues.

## Version 2308

### [Extended app access control (AppMasking)](https://docs.citrix.com/en-us/profile-management/current-release/configure/app-access-control)

The *app access control* feature (AppMasking equivalent) now applies to users and machines outside the traditional domain environment. You can implement app access control for non-domain-joined machines and control app access based on Active Directory and Azure Active Directory user accounts.

The built-in PowerShell rule generator has also been enhanced. You can now set up app access rules not only for AD users and machines but also for Azure Active Directory users and non-domain-joined machines.

### [Profile migration tool for Citrix container-based profile solution](https://docs.citrix.com/en-us/profile-management/current-release/upgrade-and-migrate/migrate)

Looking to ditch FSLogix Profiles for something that is actually focused on?

Citrix Profile Management now offers a profile migration tool to facilitate the migration process to the Citrix container-based profile solution. With this tool, you can migrate user profiles from the following profile solutions to the Citrix container-based profile solution:

-  Windows local profiles
-  FSLogix Profile Container
-  Citrix file-based profile solution

### [Auto-expansion policies for profile containers](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container#optional-enable-and-configure-vhd-auto-expansion)

Citrix Profile Management now offers a set of storage auto-expansion policies for profile containers:

-  Enable VHD auto-expansion for profile container
-  Profile container auto-expansion threshold
-  Profile container auto-expansion increment
-  Profile container auto-expansion limit

With these policies, profile containers can automatically expand as user profiles grow, eliminating the need for manual expansion and delivering improved user experience.

This is the equivalent of the FSLogix `SizeInMBs` expansion capability.

### [Support for enabling exclusive access to VHD containers](https://docs.citrix.com/en-us/profile-management/current-release/configure/vhd-disk-compaction#enable-exclusive-access-to-vhd-containers)

This one is important (and a feature request answered). In the FSLogix world, the default container access is mode 0 (Direct-Access). In CPM Profile Containers, the default and only model was the equivalent of a Mode 3 (Try for Read Write, Fall back to Read-Only) logic. This has now been fixed to allow you to do an appropriate Direct-Access approach. Citrix calls this `Exclusive Access`
{:.attention}

By default, VHD containers allow concurrent access. With a new policy, **Enable exclusive access to VHD containers**, you can disable concurrent access for profile containers and OneDrive containers, letting them allow only direct access to the Container.

### [UWP app roaming (preview)](https://docs.citrix.com/en-us/profile-management/current-release/configure/uwp-app-roaming)

With the new policy, **UWP app roaming**, UWP (Universal Windows Platform) apps can now roam with users. As a result, users can access the same UWP apps from different devices.

For those wondering, UWP = Modern Apps. Those things.

## Version 2305

### [Support for user-level policy settings](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-configure-user-level-settings.html)

By default, most Profile Management policies work only at the machine level. With the user-level policy settings feature enabled, those policies can work at the user level, and user-level settings override machine-level settings.

This feature is useful for organizations where different users or user groups require different Profile Management settings.

### [Enhancements to Outlook container](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-native-outlook-search-experience.html)

These enhancements simplify the process of fully enabling Outlook containers while offering a high level of availability for Outlook service:

-  Automatic enabling of Cached Exchange mode. Previously, to have OST files downloaded to Outlook containers, you had to manually enable the **Use Cached Exchange Mode to download email to an Outlook data file** setting for each user’s Exchange account. Profile Management now automatically enables this setting for users when all conditions for Outlook containers to work are met.
-  Automatic switching between Cached Exchange mode and Online mode. This enhancement offers a high level of availability for the Outlook service.
    -  When the container is detached, Outlook automatically switches to Online mode.
    -  When the container is reattached, Outlook automatically switches back to Cached Exchange mode.

### [Always On Tracing logs](https://docs.citrix.com/en-us/profile-management/current-release/troubleshoot/collect-diagnostics.html#collect-the-always-on-tracing-log-file)

The Always on Tracing feature is now available for Profile Management. This feature provides detailed logs that can help identify critical problems with Profile Management, thereforce reducing the need to reproduce problems.

### [Support for Google Drive in Mirroring Files for Sync mode](https://docs.citrix.com/en-us/profile-management/current-release/whats-new.html#support-for-google-drive-in-mirroring-files-for-sync-mode)

Profile Management containers now support Google Drive both in **Mirroring Files for Sync mode** and **Streaming Files for Sync mode**, giving you more flexibility in choosing cloud storage.

## Version 2303

### [App access control](https://docs.citrix.com/en-us/profile-management/current-release/configure/app-access-control.html)

Hello AppMasking. The long awaited missing feature that had us all deploying FSLogix regardless of using it for Profiles or not, this is Citrix first steps into the AppMasking space. This will warrant it's own post in time.

Profile Management can now hide applications from users, machines, and processes based on the rules you provide. With a new policy, **App access control**, you can enable this feature and provide control rules.

A PowerShell tool, **Rule Generator**, is delivered with the Profile Management installation package, letting you create, manage, and generate rules for app access control.

Note that this toolset is actually a combination of tools still being released. There is a PowerShell tool to assist with basic rule creation for simple CPM only deployments, and there is a releasing feature as part of the WEM Service which will provide a nice GUI to create the rules and provide the raw data for import into WEM, Citrix Policy or GPO.

This is part one, it's effectively a preview release for now, don't expect the world just yet.

### [Active write-back on session lock and disconnection](https://docs.citrix.com/en-us/profile-management/current-release/configure/active-write-back.html)

Active write back is a silent killer in many environments, it can very quickly knock file servers off their perch and into a pitt of doom. Sometimes there is a valid use case for it though, so this is a welcome change to try and reduce the impacts of AWB.

A new policy, **Active write back on session lock and disconnection**, is now available to extend the Active write back and Active write back registry policies:

-  With both this new policy and the **Active write back policy** enabled, profile files and folders are written back only when a session is locked or disconnected.
-  With this new policy and both the **Active write back** and **Active write back registry** policies enabled, registry entries are written back only when a session is locked or disconnected.

### [VHD disk compaction](https://docs.citrix.com/en-us/profile-management/current-release/configure/vhd-disk-compaction.html)

Hello FSLogix feature parity...and more

With a new policy, **Enable VHD disk compaction**, VHD files are now automatically compacted on user logoff when certain conditions are met. This policy enables you to save the storage space consumed by profile container, OneDrive container, and folder mirroring container.

Depending on your needs and the resources available, you can adjust the default VHD compaction settings and behavior using the following policies:

-  Free space ratio to trigger VHD disk compaction
-  Number of logoffs to trigger VHD disk compaction
-  Disable defragmentation for VHD disk compaction

## Version 2212

### [Ability to access file-based user stores using credentials](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-credential-based-access-to-user-stores.html)

Previously, impersonating the current user was the only solution to access file-based user stores. With the **Enable credential-based access to user stores policy**, you can now enable Profile Management to access file-based user stores using the stores’ own credentials. This feature gives you more flexibility in deploying and accessing file-based user stores

## Version 2209

### [File deduplication policies to reduce storage cost for the user store](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-file-deduplication.html)

Identical files can exist among various user profiles in the user store. With the new policies enabled, Profile Management removes duplicate files from the user store and stores one copy of them in a central location. Doing so avoids file duplications in the user store, thus saving your storage cost

### [Ability to replicate the profile container for profile redundancy](https://docs.citrix.com/en-us/profile-management/current-release/configure/replicate-user-stores.html)

With the profile container enabled for the full user profile, you can now replicate the container to multiple paths using the **Replicate user stores** policy. Doing so provides profile redundancy for user logons. This is a similar concept to FSLogix Cloud Cache

### [OneDrive container policy generally available](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-the-onedrive-container.html)

Previously available as a preview, the **Enable OneDrive container** policy is now generally available.

## Version 2206

This is a significant release as it relates to the evolution of Citrix Profile Management Containers vs FSLogix capability. There are a couple of very key features to note below:

-  OneDrive support (preview)
-  Async policy processing control
-  concurrent session support for Outlook search data roaming

Combine this capability with the wealth of other options and controls including combining the best of file and container capability, UPM should now start becoming a much more attractive solution for all use cases. The best thing is that the solution is actively and aggressively developed. "Ask and you shall receive" so to speak...

### [Enhancement to profile streaming in concurrent session scenarios](https://docs.citrix.com/en-us/profile-management/current-release/configure/stream-profiles.html)

A new policy, `Enable profile streaming for pending area`, is now available as an enhancement to the profile streaming feature. This enhancement ensures optimal logon experience in concurrent session scenarios

### [Concurrent session support for Outlook search data roaming](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-native-outlook-search-experience.html)

A new policy, `Enable Concurrent session support for Outlook search data roaming`, is now available as an enhancement to the `Search index roaming for Outlook` policy. With the two policies enabled, Citrix Profile Management can provide a native Outlook search experience in concurrent sessions

***Important Note:*** To let the search index roaming feature work on Microsoft Windows 10 1809 and later, and on Windows Server 2019 and later, add a `DWORD` value `EnablePerUserCatalog` = `0` under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Search`. Restart the VDA to make your registry setting take effect. This indicates that whilst Microsoft have now removed per user search index roaming from FSLogix in favor of OS level capability, Citrix can, and does, still support roaming this index using the traditional mode

### [Enable asynchronous processing for user Group Policy on logon](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-async-for-user-gpo.html)

In the fallout of this [little discovery around Synchronous Processing](https://jkindon.com/fslogix-synchronous-processing/) we spoke with the Citrix Profile Management team. Ask the right people, get a good answer

Windows provides both synchronous and asynchronous processing modes for user Group Policy. Windows uses a registry value to determine the processing mode for the next user logon. If the registry value doesn't exist, synchronous mode is applied.

With a new policy, `Enable asynchronous processing for user Group Policy on logon`, the registry value can now roam with users. As a result, the actual processing mode is applied each time users log on

### [Support for roaming OneDrive folders (preview)](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-the-onedrive-container.html)

The last major gap between FSLogix and UPM Container capability. OneDrive support.

With a new policy, `Enable OneDrive container`, OneDrive folders can now roam with users. A user's OneDrive folders are stored in a VHDX file (called OneDrive container). The VHDX file is attached on user logon and detached on user logoff.

Starting with this release, the profile container for the entire profile now supports roaming OneDrive folders `by default`

## Version 2203

### [Policy to automatically reattach VHDX disks in sessions](https://docs.citrix.com/en-us/profile-management/current-release/configure/auto-reattach-detached-vhdx-disks-in-sessions.html)

Previously, to have Profile Management automatically reattach VHDX disks in sessions, you had to configure the registry manually. You can now enable the feature by using a policy. With the Automatically reattach VHDX disks in sessions feature, Profile Management ensures a high level of stability of VHDX-based policies.

Profile Management monitors VHDX disks that are in use. If any of the disks are detached, Profile Management reattaches the disk automatically. This is a container resiliency solution.

## Version 2112

### [Support for file-level inclusion and exclusion for the profile container](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container.html#optional-include-and-exclude-folders-and-files)

Previously, only inclusions and exclusions could be configured for the profile container only at the folder level. This can now be configured at the file level. This enhancement gives provides more granular control over profile synchronization

### [Support for specifying the storage path for VHDX files](https://docs.citrix.com/en-us/profile-management/current-release/configure/specify-network-location-for-vhdx-files.html)

By default, VHDX files are stored in the user store. It is now possible to specify a separate path to store them. Citrix Profile Management provides the following VHDX-based policies:

-  [Search index roaming for Outlook](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-native-outlook-search-experience.html)
-  [Profile Container](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container.html)
-  [Accelerate folder mirroring](https://docs.citrix.com/en-us/profile-management/current-release/policies/descriptions-and-defaults.html#accelerate-folder-mirroring)

### [Support for using wildcards in folder names when configuring inclusion and exclusion](https://docs.citrix.com/en-us/profile-management/current-release/configure/include-and-exclude-items/overview.html)

When configuring inclusion and exclusion for the user store and for the profile container, wildcards can now be specified in folder names.

-  [Include and exclude folders and files for the profile container](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container.html#optional-include-and-exclude-folders-and-files)
-  [Include and exclude items for the user store](https://docs.citrix.com/en-us/profile-management/current-release/configure/include-and-exclude-items/overview.html)

## Version 2109

### [Windows 11 support](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/2109/whats-new/windows-11.html)

The Citrix components, features, and technologies in this release that support Windows 10 now also support Windows 11, unless otherwise noted

### [Automatically reattach detached VHDX disks in sessions](https://docs.citrix.com/en-us/profile-management/2109/configure/auto-reattach-detached-vhdx-disks-in-sessions.html)

Citrix Profile Management offers the following VHDX-based policies: [Search index roaming for Outlook](https://docs.citrix.com/en-us/profile-management/2109/configure/enable-native-outlook-search-experience.html), [Profile container](https://docs.citrix.com/en-us/profile-management/2109/configure/citrix-profile-management-profile-container.html), and [Accelerate folder mirroring](https://docs.citrix.com/en-us/profile-management/2109/policies/descriptions-and-defaults.html#accelerate-folder-mirroring). Each policy relies on relevant VHDX virtual disks to function properly. Profile Management attaches those disks during logons and detaches them during logoffs. However, the disks might be accidentally detached during a session preventing the policies from functioning properly. Profile Management can now detect when a VHDX virtual disk is detached in a session and then reattach it automatically. This design ensures the stability of VHDX-based solutions

### [Profile roaming support for non-domain-joined VDA machines in a customer-managed Azure subscription (preview)](https://docs.citrix.com/en-us/profile-management/2109/configure/roam-user-profiles.html)

Citrix Profile Management now supports user profile roaming on non-domain-joined VDA machines in a customer-managed Azure subscription. A users profile (including the users personal settings, files, and folders) can now roam with the user when the user logs on to a non-domain-joined VDA session.

## Version 2106

### [Windows Server 2022 support](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/2106/whats-new/windows-server-2022.html)

The Citrix components and technologies in this release that support Windows Server platforms now also support Windows Server 2022, unless otherwise noted.

### [Replicate user stores](https://docs.citrix.com/en-us/profile-management/2106/configure/replicate-user-stores.html)

A new feature to allow replication of a user store to multiple paths upon each logon and logoff in addition to the path that the `Path to user store policy` specifies. The feature is implemented through the Replicate user stores policy. To synchronize to the user stores files and folders modified during a session, enable `active write back`. This feature does not currently support full container solutions. Enabling the policy can increase system I/O and might prolong logoffs.

This is extremely beneficial for multi datacenter deployments and active-active deployments (similar to a cloud cache methodology). In a normal scenario, if both file stores are healthy, UPM will do a differential sync to both locations. Should a file store be out of date, UPM will perform a full sync to bring the data back into line.

### [Enable credential-based access to user stores](https://docs.citrix.com/en-us/profile-management/2106/configure/enable-credential-based-access-to-user-stores.html)

By default, Citrix Profile Management impersonates the current user to access user stores. Therefore, it requires the current user to have permission to directly access the user stores. Enable this feature if you do not want Profile Management to impersonate the current user when accessing user stores. You can put user stores in storage repositories (for example, Azure Files) that the current user has no permission to access.

To ensure that Profile Management can access user stores, save the profile storage server’s credentials in Workspace Environment Management (WEM) or Windows Credential Manager. Citrix recommend that you use `Workspace Environment Management` to eliminate the need of configuring the same credentials for each machine where Profile Management runs. If you use Windows Credential Manager, use the Local System account to securely save the credentials.

### [Accelerate folder mirroring](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/policies/reference/profile-management/file-system/synchronization-policy-settings.html#accelerate-folder-mirroring)

With both the `Accelerate folder mirroring` and the `Folders to mirror` policies enabled, Profile Management stores mirrored folders on a VHDX-based virtual disk. It attaches the virtual disk during logons and detaches it during logoffs, thus eliminating the need to copy the folders between the user store and local profiles. Effectively a selective Containerization of data.

## Version 2103

### [Local caching for Citrix Profile Management profile containers](https://docs.citrix.com/en-us/profile-management/2103/configure/citrix-profile-management-profile-container.html)

Local caching support for Citrix Profile Management profile containers through the `Enable local caching for profile containers` policy. With the policy set to `Enabled`, each local profile serves as a local cache of its Citrix Profile Management profile container. If profile streaming is in use, locally cached files are created on demand. Otherwise, they are created during user logons. To use the local caching feature, put an entire user profile in its Citrix Profile Management profile container.

This feature is designed to cater for loss of network connectivity to the container store.

### [Multi-session write-back support for Citrix Profile Management profile containers](https://docs.citrix.com/en-us/profile-management/2103/configure/enable-multi-session-write-back-for-profile-containers.html)

Previously, changes in sessions were written back only to `FSLogix Profile Container` with the relevant policy enabled. Starting with this release, Citrix renamed the `Enable multi-session write-back for FSLogix Profile Container` policy to `Enable multi-session write-back for profile containers` to accommodate multi-session write-back support for `Citrix Profile Management profile containers`.

Not even FSLogix can do this natively – two sessions writing back to the same profile at the same time...

### [Profile streaming for folders](https://docs.citrix.com/en-us/profile-management/2103/configure/stream-profiles.html)

With the `Enable profile streaming for folders` policy set to `Enabled`, folders are fetched only when they are being accessed. This approach eliminates the need to traverse all folders during user logons. To use this feature, you must also enable the `Profile streaming` policy.

### [Improved experience with the Start menu](https://docs.citrix.com/en-us/profile-management/2103/profile-management-best-practices.html#start-menu-roaming)

We have improved the experience with the Start menu on Windows Server 2016 and Windows Server 2019 through automatic configuration of the relevant policies as follows:

-  Citrix added `Appdata\Local\Microsoft\Windows\Caches` to `Folders to Mirror`
-  Citrix are ensuring that `Appdata\Local\Packages` is added to `Exclusion list – directories`
-  Citrix are ensuring that `Appdata\Local\Microsoft\Windows\UsrClass.Dat*` is added to `Exclusion list – files`

To disable automatic configuration, use the [Disable automatic configuration](https://docs.citrix.com/en-us/profile-management/2103/policies/descriptions-and-defaults.html#disable-automatic-configuration) policy

## Version 2009

### [Profile container enhancements](https://docs.citrix.com/en-us/profile-management/2009/configure/profile-container.html)

Starting with this release, multiple concurrent sessions can access a profile container and you can put an entire user profile in its profile container. In addition, Profile Management now accesses the VHDX files in a user context and does not grant Domain Computers full control of the folder where the VHDX files are stored

## Version 2003

### [Enable multi-session write-back for FSLogix Profile Container](https://docs.citrix.com/en-us/profile-management/2003/configure/enable-multi-session-write-back-for-fslogix-profile-container.html)

Profile Management now provides a solution to save changes in multi-session scenarios for FSLogix Profile Container. If the same user launches multiple sessions on different machines, changes made in each session are synchronized and saved to FSLogix Profile Container.