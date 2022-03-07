---
layout: post
title: The Evolution of Citrix Profile Management
permalink: "/the-evolution-of-citrix-profile-management/"
subtitle: Tracking the progress of Citrix Profile Management capability
cover-img: /assets/img/Sydney1.jpg
thumbnail-img: /assets/img/the-evolution-of-citrix-profile-management/evolution-upm.jpg
share-img: /assets/img/the-evolution-of-citrix-profile-management/evolution-upm.jpg
tags: [Citrix, UPM, Profiles, Windows, CVAD, Cloud]
categories: [Citrix, UPM, Profiles, Windows, CVAD, Cloud]
---

![The Evolution of Citrix Profile Management]({{site.baseurl}}/assets/img/the-evolution-of-citrix-profile-management/evolution-upm.jpg)

Citrix Profile Management is quietly kicking goals and developing quickly. This post aims to track the changes and releases as they occur, and provide a single point of reference. It is a companion post to my initial [Citrix UPM and FSLogix Conainers](https://jkindon.com/citrix-upm-and-fslogix-containers/) post, which outlined some decision points around profile management tool selection.

This list will start at CVAD 1912 LTSR, anything prior to that, refer to the appropriate documentation

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

## - - - - - Version 2112

{: .box-note}

**Feature:** [Support for file-level inclusion and exclusion for the profile container](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container.html#optional-include-and-exclude-folders-and-files)

**Detail:** Previously, only inclusions and exclusions could be configured for the profile container only at the folder level. This can now be configured at the file level. This enhancement gives provides more granular control over profile synchronization

{: .box-note}

**Feature:** [Support for specifying the storage path for VHDX files](https://docs.citrix.com/en-us/profile-management/current-release/configure/specify-network-location-for-vhdx-files.html)

**Detail:** By default, VHDX files are stored in the user store. It is now possible to specify a separate path to store them. Citrix Profile Management provides the following VHDX-based policies:

*  [Search index roaming for Outlook](https://docs.citrix.com/en-us/profile-management/current-release/configure/enable-native-outlook-search-experience.html)
*  [Profile Container](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container.html)
*  [Accelerate folder mirroring](https://docs.citrix.com/en-us/profile-management/current-release/policies/descriptions-and-defaults.html#accelerate-folder-mirroring)

{: .box-note}

**Feature:** [Support for using wildcards in folder names when configuring inclusion and exclusion](https://docs.citrix.com/en-us/profile-management/current-release/configure/include-and-exclude-items/overview.html)

**Detail:** When configuring inclusion and exclusion for the user store and for the profile container, wildcards can now be specified in folder names.

*  [Include and exclude folders and files for the profile container](https://docs.citrix.com/en-us/profile-management/current-release/configure/citrix-profile-management-profile-container.html#optional-include-and-exclude-folders-and-files)
*  [Include and exclude items for the user store](https://docs.citrix.com/en-us/profile-management/current-release/configure/include-and-exclude-items/overview.html)

## - - - - - Version 2109

{: .box-note}

**Feature:** [Windows 11 support](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/2109/whats-new/windows-11.html)

**Detail:** The Citrix components, features, and technologies in this release that support Windows 10 now also support Windows 11, unless otherwise noted

{: .box-note}

**Feature:** [Automatically reattach detached VHDX disks in sessions](https://docs.citrix.com/en-us/profile-management/2109/configure/auto-reattach-detached-vhdx-disks-in-sessions.html)

**Detail:** Citrix Profile Management offers the following VHDX-based policies: [Search index roaming for Outlook](https://docs.citrix.com/en-us/profile-management/2109/configure/enable-native-outlook-search-experience.html), [Profile container](https://docs.citrix.com/en-us/profile-management/2109/configure/citrix-profile-management-profile-container.html), and [Accelerate folder mirroring](https://docs.citrix.com/en-us/profile-management/2109/policies/descriptions-and-defaults.html#accelerate-folder-mirroring). Each policy relies on relevant VHDX virtual disks to function properly. Profile Management attaches those disks during logons and detaches them during logoffs. However, the disks might be accidentally detached during a session preventing the policies from functioning properly. Profile Management can now detect when a VHDX virtual disk is detached in a session and then reattach it automatically. This design ensures the stability of VHDX-based solutions

{: .box-note}

**Feature:** [Profile roaming support for non-domain-joined VDA machines in a customer-managed Azure subscription (preview)](https://docs.citrix.com/en-us/profile-management/2109/configure/roam-user-profiles.html)

**Detail:** Citrix Profile Management now supports user profile roaming on non-domain-joined VDA machines in a customer-managed Azure subscription. A users profile (including the users personal settings, files, and folders) can now roam with the user when the user logs on to a non-domain-joined VDA session.

## - - - - - Version 2106

{: .box-note}

**Feature:** [Windows Server 2022 support](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/2106/whats-new/windows-server-2022.html)

**Detail:** The Citrix components and technologies in this release that support Windows Server platforms now also support Windows Server 2022, unless otherwise noted.

{: .box-note}

**Feature:** [Replicate user stores](https://docs.citrix.com/en-us/profile-management/2106/configure/replicate-user-stores.html)

**Detail:** A new feature to allow replication of a user store to multiple paths upon each logon and logoff in addition to the path that the `Path to user store policy` specifies. The feature is implemented through the Replicate user stores policy. To synchronize to the user stores files and folders modified during a session, enable `active write back`. This feature does not currently support full container solutions. Enabling the policy can increase system I/O and might prolong logoffs.

This is extremely beneficial for multi datacenter deployments and active-active deployments (similar to a cloud cache methodology). In a normal scenario, if both file stores are healthy, UPM will do a differential sync to both locations. Should a file store be out of date, UPM will perform a full sync to bring the data back into line.

{: .box-note}

**Feature:** [Enable credential-based access to user stores](https://docs.citrix.com/en-us/profile-management/2106/configure/enable-credential-based-access-to-user-stores.html)

**Detail:** By default, Citrix Profile Management impersonates the current user to access user stores. Therefore, it requires the current user to have permission to directly access the user stores. Enable this feature if you do not want Profile Management to impersonate the current user when accessing user stores. You can put user stores in storage repositories (for example, Azure Files) that the current user has no permission to access.

To ensure that Profile Management can access user stores, save the profile storage server’s credentials in Workspace Environment Management (WEM) or Windows Credential Manager. Citrix recommend that you use `Workspace Environment Management` to eliminate the need of configuring the same credentials for each machine where Profile Management runs. If you use Windows Credential Manager, use the Local System account to securely save the credentials.

{: .box-note}

**Feature:** [Accelerate folder mirroring](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/policies/reference/profile-management/file-system/synchronization-policy-settings.html#accelerate-folder-mirroring)

**Detail:** With both the `Accelerate folder mirroring` and the `Folders to mirror` policies enabled, Profile Management stores mirrored folders on a VHDX-based virtual disk. It attaches the virtual disk during logons and detaches it during logoffs, thus eliminating the need to copy the folders between the user store and local profiles. Effectively a selective Containerization of data.

## - - - - - Version 2103

{: .box-note}

**Feature:** [Local caching for Citrix Profile Management profile containers](https://docs.citrix.com/en-us/profile-management/2103/configure/citrix-profile-management-profile-container.html)

**Detail:** Local caching support for Citrix Profile Management profile containers through the `Enable local caching for profile containers` policy. With the policy set to `Enabled`, each local profile serves as a local cache of its Citrix Profile Management profile container. If profile streaming is in use, locally cached files are created on demand. Otherwise, they are created during user logons. To use the local caching feature, put an entire user profile in its Citrix Profile Management profile container.

This feature is designed to cater for loss of network connectivity to the container store.

{: .box-note}

**Feature:** [Multi-session write-back support for Citrix Profile Management profile containers](https://docs.citrix.com/en-us/profile-management/2103/configure/enable-multi-session-write-back-for-profile-containers.html)

**Detail:** Previously, changes in sessions were written back only to `FSLogix Profile Container` with the relevant policy enabled. Starting with this release, Citrix renamed the `Enable multi-session write-back for FSLogix Profile Container` policy to `Enable multi-session write-back for profile containers` to accommodate multi-session write-back support for `Citrix Profile Management profile containers`.

Not even FSLogix can do this natively – two sessions writing back to the same profile at the same time...

{: .box-note}

**Feature:** [Profile streaming for folders](https://docs.citrix.com/en-us/profile-management/2103/configure/stream-profiles.html)

**Detail:** With the `Enable profile streaming for folders` policy set to `Enabled`, folders are fetched only when they are being accessed. This approach eliminates the need to traverse all folders during user logons. To use this feature, you must also enable the `Profile streaming` policy.

{: .box-note}

**Feature:** [Improved experience with the Start menu](https://docs.citrix.com/en-us/profile-management/2103/profile-management-best-practices.html#start-menu-roaming)

**Detail:** We have improved the experience with the Start menu on Windows Server 2016 and Windows Server 2019 through automatic configuration of the relevant policies as follows:

*  Citrix added `Appdata\Local\Microsoft\Windows\Caches` to `Folders to Mirror`
*  Citrix are ensuring that `Appdata\Local\Packages` is added to `Exclusion list – directories`
*  Citrix are ensuring that `Appdata\Local\Microsoft\Windows\UsrClass.Dat*` is added to `Exclusion list – files`

To disable automatic configuration, use the [Disable automatic configuration](https://docs.citrix.com/en-us/profile-management/2103/policies/descriptions-and-defaults.html#disable-automatic-configuration) policy