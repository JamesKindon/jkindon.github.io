---
layout: post
title: The Evolution of Citrix Workspace
permalink: "/the-evolution-of-citrix-workspace/"
categories: [Citrix, Cloud, evolution, Workspace, DaaS]
description: Tracking the progress of Citrix Workspace
image:
  path: /assets/img/the-evolution-of-citrix-workspace/post_default_image.jpg
sitemap: true
hide_last_modified: false
comments: true
related_posts:
  - evolution/_posts/2024-04-01-the-evolution-of-citrix-profile-management.md
  - evolution/_posts/2024-04-01-the-evolution-of-citrix-machine-creation-services-with-microsoft-azure.md
  - evolution/_posts/2024-04-01-the-evolution-of-citrix-wem-service.md
  - evolution/_posts/2024-04-01-the-evolution-of-citrix-wem.md
---

<!--excerpt-->

-  Table of Contents
{:toc .large-only}

Citrix Workspace is consistently updating and bringing enhanced capability to the table. This post aims to track the changes and releases as they occur, and provide a single point of reference.

Workspace releases are broken into two categories:

-  Platform. These are platform functionalities and cover features and capabilities relevant for administrators.
-  User Interface. This the interface consumed by the users, features released here tend to be directly visibile to the end-user.

Citrix DaaS also has features which impact the Workspace Service, as such, any relevant DaaS feature is captured in this blog under the Platform section in the same month. You should keep an eyes on the DaaS releases [here](https://docs.citrix.com/en-us/citrix-daas/whats-new.html).

I will do my best to maintain this list as and when features come out, as well as some commentary around their value where I can.

# Citrix Workspace Platform

You can find the official release documentation for Workspace Platform releases [here](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-platform)

## Feb 2024

### [Suspend VMs from the Workspace interface](https://docs.citrix.com/en-us/citrix-daas/whats-new.html#new-and-enhanced-features-2)

Suspend VMs from the Workspace interface. You can now suspend persistent VMs with active sessions from the Workspace user interface. This enhancement offers the following benefits:

-  Resume the system from where you left off.
-  Faster launch time compared to a stopped deallocated machine.
-  Cost-effective and energy efficient.
-  Efficient resource allocation using the Autoscale feature.

### [Create multiple Workspace URLs - General Availability (GA)](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-multiple-workspace-url)

he multiple Workspace URL feature is now generally available for all users. You can now create multiple Workspace URLs (subdomains of cloud.com) and use these URLs as policy inputs. For example, you can configure different URLs for different subsidiaries or divisions within your organization. Each of these URLs can have different branding, authentication methods, or desktops and apps.

## Dec 2023

### [Create multiple Workspace URLs (Technical Preview)](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-multiple-workspace-url)

You can now create multiple Workspace URLs (subdomains of cloud.com) and use these URLs as policy inputs. For example, you can configure different URLs for different subsidiaries or divisions within your organization. Each of these URLs can have different branding, authentication methods, or desktops and apps.

Each store is accessible by a unique URL can differ in the following aspects:

-  [Branding of the UI (post login)](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-multiple-workspace-url#configure-themes-and-logos-based-on-workspace-urls)
-  [Apps and desktops](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-multiple-workspace-url#filter-resources-based-on-workspace-urls)
-  [Authentication configuration (such as different identity providers)](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-multiple-workspace-url#configure-nfactor-authentication-flows-based-on-workspace-urls)

### [Redesigned Access Policy UI for more flexible resource access control](https://docs.citrix.com/en-us/citrix-daas/install-configure/delivery-groups-manage#restrict-access-to-resources-in-a-delivery-group)

Citrix redesigned the **Edit Delivery group -> Access Policy UI** to give you more flexibility in managing resource access for delivery groups. The following are the key features available with the new design:

-  **Support for adding policies**. You can now add access policies to restrict resource access based on attributes of user connections. A policy can consist of two types of criteria:
    -  **Inclusion criteria**. Let you specify user connections that are allowed to access the delivery group.
    -  **Exclusion criteria**. Let you specify user connections that are prohibited from accessing the delivery group.
-  **Expanded filter support**. You can now define inclusion and exclusion criteria using a range of SmartAccess filters. Those filters include Workspace filters such as `Citrix.Workspace.UsingDomain` and `Citrix-Via-Workspace`, as well as filters for network location-based adaptive access.
-  **Match All logic support for included criteria**. The new logic enables you to achieve a high level of precision and control when specifying allowed user connections for delivery groups.

## Nov 2023

### [Configure a custom domain - General Availability](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-custom-domain)

The Custom Domain feature is now generally available. You can configure a custom domain for your workspace, which allows you to use a domain of your choice to access your Citrix Workspace store. You can then use this domain in place of your assigned cloud.com domain for access from both a web browser and Citrix Workspace applications.

## Aug 2023

### [Add your own TLS certificate for custom domain (Preview)](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-custom-domain#adding-a-custom-domain)

You can now upload your own TLS certificate for authentication while configuring a custom Workspace URL.

## May 2023

### [Configure a custom domain (Preview)](https://docs.citrix.com/en-us/citrix-workspace/configure/configure-custom-domain)

You can configure a custom domain for your workspace, which allows you to use a domain of your choice to access your Citrix Workspace store. You can then use this domain in place of your assigned cloud.com domain for access from both a web browser and Citrix Workspace applications.

## March 2023

### [Additional inactivity timeout settings](https://docs.citrix.com/en-us/citrix-workspace/experience/policies#set-inactivity-timeout-for-web)

You can now enable extra inactivity timeout settings for both desktop and mobile users of Workspace app

## December 2022

### [Additional send custom announcement configuration option](https://docs.citrix.com/en-us/citrix-workspace/experience/policies#send-custom-announcements)

You can now set the page placement when configuring Send custom announcement to either top or bottom.

### [Support for Traditional Chinese language](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-platform#december-2022)

Citrix Workspace is now available in the Traditional Chinese language.

## October 2022

### [Support for Korean language](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-platform#october-2022)

Citrix Workspace is now available in the Korean language.

### [Support to customize Citrix Workspace app settings](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-platform#october-2022)

Administrators can now configure the settings for Citrix Workspace app for iOS, Android, HTML5, Mac, and Windows platforms using the Global App Configuration service.

## August 2022

### [Improvements to Workspace launch experience](https://docs.citrix.com/en-us/citrix-workspace/get-started)

When a user launches their workspace over web or browser, a notification is triggered showing the launch status. If the user attempts to close the browser when a launch is in progress, the user is prompted for confirmation and informed that a session launch is in progress.

## June 2022

### [Support for service continuity with Safari](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity#service-continuity-in-browser)

Citrix Workspace Web extensions make service continuity available to users who access their apps and desktops through a browser.

## May 2022

### [New configuration option for federated identity provider](https://docs.citrix.com/en-us/citrix-workspace/experience/interaction#workspace-sessions)

[Remember this one](https://jkindon.com/azure-ad-and-citrix-workspace-sso/)? Enable or disable your federated identity provider to allow your subscribers to be prompted to authenticate when logging in to Workspace.

### [Reauthentication period for Workspace app general availability](https://docs.citrix.com/en-us/citrix-workspace/experience/policies#set-a-reauthentication-period-for-citrix-workspace-app)

Reauthentication periods allow subscribers to stay signed in to Workspace without being prompted to sign in every time they access their workspace. When signing in through Workspace app, subscribers consent to stay signed in. Subscribers remain signed in during the reauthentication period as long as they're using their apps and desktops.

### [Support for service continuity on iOS](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity)

Service continuity is now supported for Citrix Workspace app for iOS in general availability.

### [New error codes for service continuity](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity#monitoring-and-troubleshooting)

New error codes are now available to aid in troubleshooting failed service continuity connections.

## March 2022

### [Support for service continuity on Android and iOS](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity)

Service continuity is now supported for Citrix Workspace app for Android in general availability and Citrix Workspace app for iOS in technical preview.

## February 2022

### [Support for service continuity with Citrix Workspace app for Android (general availability) and Citrix Workspace app for iOS (technical preview)](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity)

Service continuity allows users to connect to their virtual apps and desktops even during outages. It is now supported for Citrix Workspace app for Android in general availability and Citrix Workspace app for iOS in technical preview.

### [Send custom announcement and custom sign-in policy](https://docs.citrix.com/en-us/citrix-workspace/experience/policies)

Two new features are now available for all customers. These features allow Workspace administrators to display their own post-login persistent banner and pre-login custom message or license agreement in Citrix Workspace app.

## December 2021

### [Remove the default, split sign-in screen for employee and client users of Citrix Content Collaboration](https://docs.citrix.com/en-us/citrix-workspace/experience/policies#create-a-unified-user-sign-in-flow)

Citrix Workspace now allows you to enable a single sign-in flow for both client and employee users.

### [Support for service continuity in browser with Citrix Workspace app for Mac](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity)

Citrix Workspace Web extensions make service continuity available to users who access their apps and desktops through a browser. This feature now is supported on devices running Citrix Workspace app for Mac.

## November 2021

### [Policy-driven theming](https://docs.citrix.com/en-us/citrix-workspace/appearance.html)

You can create and prioritize Workspace themes, and add each theme to different user groups in **Workspace Configuration**.

## October 2021

### [Electronic signature language support](https://support.citrix.com/article/CTX312371)

Electronic signature now offers support for Italian and Brazilian Portuguese in addition to the following languages: German, French, Spanish, Japanese, Dutch, and Simplified Chinese.

### [FAS support for multiple resource locations general availability](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/workspace-federated-authentication)

Citrix Workspace now supports providing single sign-on to virtual apps and desktops across multiple resource locations. Also, FAS servers in one resource location can be designated as primary or secondary to provide failover for FAS servers in other resource locations.

## September 2021

### [Citrix Workspace app for HTML5 introduced to Citrix Workspace](https://docs.citrix.com/en-us/citrix-workspace-app-for-html5/about.html)

Citrix Workspace app for HTML5 delivers the Citrix Workspace experience in browsers without any installation on the device.

### [Support for service continuity in browser general availability](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity#service-continuity-in-browser)

Citrix Workspace Web extensions make service continuity available to users who access their apps and desktops through a browser. This feature is for Google Chrome and Microsoft Edge on Windows devices.

## July 2021

### [Custom subscriber license agreement policy](https://docs.citrix.com/en-us/citrix-workspace/experience/policies#configure-a-sign-in-policy)

You can present subscribers with a custom usage agreement policy to read and accept before they sign into their Workspace. For more information about this feature

### [Reauthentication period for Workspace app preview](https://docs.citrix.com/en-us/citrix-workspace/experience/policies#set-a-reauthentication-period-for-citrix-workspace-app)

Reauthentication periods allow subscribers to stay signed in to Workspace without being prompted to sign in every time they access their workspace. When signing in through Workspace app, subscribers consent to stay signed in. Subscribers remain signed in during the reauthentication period as long as they're using their apps and desktops.

### [Network location configuration through Citrix Cloud](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/workspace-network-location)

You can now configure network locations through the Citrix Cloud management console in addition to using the Citrix-provided PowerShell script.

## June 2021

### [FAS support for multiple resource locations preview:](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/workspace-federated-authentication)

Citrix Workspace now supports providing single sign-on to virtual apps and desktops across multiple resource locations. FAS servers in one resource location can be designated as primary or secondary to provide failover for FAS servers in other resource locations.

### [Support for service continuity in browser technical preview](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity#service-continuity-in-browser)

Citrix Workspace Web extensions make service continuity available to users who access their apps and desktops through a browser. This technical preview is for Google Chrome and Microsoft Edge on Windows devices.

### [Service continuity general availability](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity)

Service continuity allows users to connect to their virtual apps and desktops even during outages in Citrix Cloud components or in public and private clouds.

### [Citrix RightSignature app available](https://docs.citrix.com/en-us/citrix-gateway-service/saas-apps-templates/citrix-gateway-right-signature-saas.html)

Take advantage of Citrix app, an electronic signature solution that comes with Workspace Premium and Premium Plus to request e-signatures on documents on any device through Citrix Workspace.

## May 2021

### [Custom themes technical preview](https://docs.citrix.com/en-us/citrix-workspace/experience/appearance)

Customizing the appearance of Workspace for subscribers now supports custom themes that you can assign to different user groups. Create, customize, and prioritize themes so subscribers in those user groups see their appropriate workspace theme when they sign in.

### [Electronic signature language support](https://support.citrix.com/article/CTX312371)

Electronic signature capability now offers support for the following languages: German, French, Spanish, Japanese, Dutch, and Simplified Chinese.

## February 2021

### [Account password changes](https://docs.citrix.com/en-us/citrix-workspace/experience/policies#allow-subscribers-to-change-their-account-password)

Subscribers can change their domain password from within Citrix Workspace. Administrators can also provide password guidance to subscribers for creating valid complex passwords in accordance with their organization's password policy.

## December 2020

### [Service continuity technical preview](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/service-continuity)

Service continuity allows users to connect to their Citrix DaaS even during outages in Citrix Cloud components or in public and private clouds.

## October 2020

### [FedRAMP Ready](https://docs.citrix.com/en-us/citrix-cloud-government#fedramp-ready)

Citrix Workspace is FedRAMP Ready when deployed in Citrix Cloud Government. FedRAMP is a program that promotes security standards for cloud services used by US government organizations. US government organizations that require FedRAMP Ready cloud services can now use Citrix Workspace and Citrix DaaS services to deliver DaaS

## May 2020

### [Get Started with Citrix Workspace guide](https://docs.citrix.com/en-us/citrix-workspace/get-started)

Citrix Workspace now includes a step-by-step walkthrough to help you deliver workspaces quickly to your end-users. The walkthrough guides you through the Citrix Cloud console so you can configure an identity provider, add administrators, and enable workspace authentication and services

## December 2019

### [Network Location Service](https://docs.citrix.com/en-us/citrix-workspace/optimize-cvad/workspace-network-location)

You can now ensure that users who launch apps and desktops in Workspace from within the corporate network are routed directly to their VDAs. This bypasses the gateway and results in faster DaaS sessions.

### [Improvements for Recent and Favorite apps](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-platform#december-2019)

Recents and Favorites are loaded first in Workspace, so users can launch their commonly used apps and desktops right away.

# Citrix Workspace UI

You can find the official release documentation for Workspace UI releases [here](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience)

## 24.12

### [Manage installation prompt for Workspace Web extension (Preview)](https://docs.citrix.com/en-us/citrix-workspace/experience/interaction#launching-apps-and-desktops)

You can now manage the display of the installation prompt for the Workspace Web extension. Enabling the prompt allows Workspace to detect whether the extension is installed on the user's device when they open Citrix Workspace from a browser. If the extension isn't installed, users are prompted to download and install it. Once users install the extension, it helps to open the apps and desktops in the native Citrix Workspace app automatically without the intervention of Workspace detection screen. As per your preference, you can set the prompt as either mandatory or optional. This prompt feature is compatible with Google Chrome and Microsoft Edge browsers.

When users click the Install button, it redirects the users to the respective browser's web extension store, where they can download the Workspace Web extension. The prompt won't appear next time once the user downloads and installs the extension.

## 24.11

### [Activity Manager has manual refresh option](https://docs.citrix.com/en-us/citrix-workspace/get-started/activity-manager#enable-activity-manager)

With this release, end users can now manually refresh the list of items within the **Activity Manager** for the cloud store, accessible on both desktops and mobile devices. They are no longer required to restart the **Activity Manager** to see the updated list. Two options are available to refresh the list: a refresh button and a refresh icon. End users can use the **Refresh** button when the **Activity Manager** screen is empty, and they can use the refresh icon refresh icon to update the existing list. This new feature enhances the end user experience by allowing them to manage the sessions within the **Activity Manager** more efficiently and conveniently.

## 24.9

### [Disable Simple View of Workspace UI](https://docs.citrix.com/en-us/citrix-workspace/get-started/user-experience#workspace-visual-and-layout-improvements)

Currently, when users launch Citrix Workspace app with fewer than 20 resources, they see the screen with Simple View where users don't see navigation tabs, like Home, Apps, and Desktops. All the apps and desktops are consolidated on one page and administrators don't have the control to disable this view. With this release, you can disable the Simple View and customize the new Workspace UI as per your preference.

Even if the number of resources are less than 20, you can still use the navigation tabs if you prefer a consistent view for your users.

## 23.48

### [View user's display name and profile picture on Workspace UI](https://docs.citrix.com/en-us/citrix-workspace/get-started/user-experience#manage-users-display-name-and-profile-picture)

Users can now view their display name and profile picture on the Workspace UI. The user's display name is shown along with the greetings. The profile picture, initials, or a generic image appears on the user menu at the upper-right corner. Admins must note that Workspace UI displays this information only if the Active Directory fetches valid data.

## 23.40

### [Streamlined discovery of new apps](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#streamlined-discovery-of-new-apps)

End users can now easily spot newly added apps, making it easier to explore and utilize the latest apps. When an admin delivers a new app to an end user, it is highlighted on the end user's workspace and a green dot is displayed on the app tile for the first time.

## 23.37

### [New Workspace UI - General Availability](https://docs.citrix.com/en-us/citrix-workspace/get-started/user-experience)

The new Workspace user interface is now generally available. It introduces new UI capabilities with a modern look and feel for a cleaner view. The UI enhancements are applicable for web, desktops, and mobile. Admins can enable it for their end users from **Workspace Configuration -> Customize -> Features**.

### [Activity Manager - General Availability](https://docs.citrix.com/en-us/citrix-workspace/get-started/activity-manager#enable-activity-manager)

The Activity Manager feature is now generally available on the new UI for cloud. Activity Manager is a simple yet powerful feature that empowers users to effectively manage their resources.It enhances productivity by facilitating quick actions on active and disconnected apps and desktops from any device. Admins can enable this feature for their end users from **Workspace Configuration -> Customize -> Features -> Activity Manager**.

Once enabled, apps and desktops that are either active or in a disconnected state are displayed on the Activity Manager panel. End users can click the ellipses (…) icon to take quick actions.

Following actions can be performed for active apps and desktops.

-  **Disconnect**: Disconnects the remote session but the apps and desktops are active in the background.
-  **Log out**: Logs out from the current session. All the apps in the sessions are closed, and any unsaved files are lost.
-  **Shut Down**: Closes your disconnected desktops.
-  **Force Qui**t: Forcefully powers off your desktop in case of a technical issue.
-  **Restart**: Shuts down your desktop and start it again.

Activity Manager also enables end users to interact with their disconnected apps and desktops.

## 23.36

### [View sub-categories for applications on mobile platforms](https://docs.citrix.com/en-us/citrix-workspace/get-started/user-experience#add-folder-path)

End users can now view their apps organized into categories and sub-categories on android and iOS devices, providing easy access and a pleasant app browsing experience. To view categories, navigate to the Apps tab and click the Categories dropdown.

Select the relevant category, a list of available sub-categories and applications is displayed based on the configuration made by the admin. Sub-categories are displayed as folders that might contain further sub-folders or applications as per the admin configuration.

### [Manage disconnected sessions on Activity Manager from any device](https://docs.citrix.com/en-us/citrix-workspace/get-started/activity-manager#disconnected-apps-and-desktops)

Activity Manager now enables end users to view and take actions on apps and desktops that are running in disconnected mode, locally or remotely. Sessions can be managed from mobile or desktop devices, enabling end users to take action on the go. Taking action on disconnected sessions such as log out or shut down promotes optimized use of resources and reduces energy consumption.

## 23.33

### [Enhanced user experience with app categorization](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#enhanced-user-experience-with-app-categorization)

End users can view their applications organized into categories and sub-categories on the Workspace user interface. If the categorization involves more than two levels, end users will see their applications arranged within a folder structure. The navigation breadcrumbs are visible to the users. When the number of primary categories created by the admins exceeds the available space on the user's screen, the user interface adjusts based on the screen size, and dynamically moves categories under the **More** dropdown.

## 23.32

### [App categorization for easy access](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#app-categorization-for-easy-access)

Admins can deliver apps organized into categories and subcategories, providing a pleasant app browsing experience for their end users. From the second level of categorization, end users will see a folder structure. The organized multi-level structure makes for a clutter-free, optimized experience that helps enhance the overall user satisfaction.

## 23.30

### [Manage Activity Manager](https://docs.citrix.com/en-us/citrix-workspace/get-started/activity-manager)

As an admin, you can now enable or disable the Activity Manager feature for your end users. As per your organization policies, you can enable the feature for everyone or selected users and user groups. When enabled, the Activity Manager panel lets your end users view and interact with their active apps and desktops

## 23.28

### [Deprecation announcement for Internet Explorer](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#deprecation-announcement-for-internet-explorer)

UI version 23.26 is available on Internet Explorer till the last week of 2023. Citrix does not support new features, bug fixes, or security patches post the 23.26 release. Additionally, administrators receive a notification to upgrade to the supported browsers and supported LTSR (LTSR2203 or later).

## 23.25

### [View description of apps and desktops](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#view-description-of-apps-and-desktops)

End users can now view the description provided by admins for apps and desktops. These descriptions aid in comprehending the intended functionality of an app or desktop. They are especially useful in case multiple apps exist with the same name but differ in their configuration, location, environment, etc. To view the description of an app or desktop, click ellipses on the respective tile and then click **View Details**.

## 23.22

### [Introducing Activity Manager](https://docs.citrix.com/en-us/citrix-workspace/get-started/activity-manager)

You can now manage and take quick actions on the apps and desktops that are active across any device from a single window pane within the Workspace UI. All the active apps and desktops are grouped in the session that you're currently using.

## 23.15

### [New Workspace user interface](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#new-workspace-user-interface)

Introduces new UI capabilities with a modern look and feel for a cleaner view. The UI enhancements are applicable for web, desktops, and mobile.

### [Enhanced first-time user experience](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#enhanced-first-time-user-experience)

When you launch the downloaded or Citrix from a browser for the first time, you're prompted with a screen that lists the relevant apps. These apps are decided by the admin, and you can add these apps as favorites with a single click.

### [Enhanced search experience](https://docs.citrix.com/en-us/citrix-workspace/whats-new/whats-new-workspace-user-experience#enhanced-search-experience)

The enhanced **Search** feature gives you faster results from the search engines. The **Search** option allows you to do a quick and intuitive search from within the Workspace app.