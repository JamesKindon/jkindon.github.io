---
layout: post
title: "Microsoft Azure Zone Architecture with Citrix Cloud Virtual Apps and Desktops Service"
permalink: "/microsoft-azure-zone-architecture-with-citrix-cvads/"
subtitle: "Designing, Implementing and Operating CVADS with using an Azure Zone Architecture"
cover-img: /assets/img/Sydney1.jpg
thumbnail-img: /assets/img/microsoft-azure-zone-architecture-with-citrix-cvads/availability-zones.png
share-img: /assets/img/microsoft-azure-zone-architecture-with-citrix-cvads/availability-zones.png
tags: [Citrix, CVAD, Cloud, Azure]
categories: [Citrix, CVAD, Cloud, Azure]
#Interactive Image (For Body): [![name-me]({{site.baseurl}}/assets/img/microsoft-azure-zone-architecture-with-citrix-cvads/iometer_Eph_Response.png)]({{site.baseurl}}/assets/img/microsoft-azure-zone-architecture-with-citrix-cvads/image-name.png)
---

![AZ]({{site.baseurl}}/assets/img/microsoft-azure-zone-architecture-with-citrix-cvads/availability-zones.png)

Microsoft offers two native forms of high-availability and resiliency within Azure, [Availability Sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets) and [Availability Zones](https://azure.microsoft.com/en-au/global-infrastructure/availability-zones/#overview). A nice quick overview of the two is referenced [here](https://techcommunity.microsoft.com/t5/itops-talk-blog/understanding-availability-sets-and-availability-zones/ba-p/1992518).
 
Availability Zones are the more commonly preferred deployment model that I am seeing across my engagements globally now, with the majority of new builds opting for AZ architecture vs that of AS.
