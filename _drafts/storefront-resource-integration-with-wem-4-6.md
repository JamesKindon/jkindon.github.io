---
layout: post
title: "Storefront Resource Integration with WEM 4.6"
permalink: "/storefront-resource-integration-with-wem-4-6/"
subtitle: "Delivering Citrix Published Applications via Citrix WEM"
cover-img: /assets/img/Sydney1.jpg
thumbnail-img: /assets/img/storefront-resource-integration-with-wem-4-6/Feature.png
share-img: /assets/img/storefront-resource-integration-with-wem-4-6/Feature.png
tags: [Citrix, Start Menu, WEM, Windows, XenApp]
categories: [Citrix, Start Menu, WEM, Windows, XenApp]
redirect_from: 
    - /2018/03/28/storefront-resource-integration-with-wem-4-6
    - /2018/03/28/storefront-resource-integration-with-wem-4-6/
#Interactive Image (For Body): [![name-me]({{site.baseurl}}/assets/img/storefront-resource-integration-with-wem-4-6/iometer_Eph_Response.png)]({{site.baseurl}}/assets/img/storefront-resource-integration-with-wem-4-6/image-name.png)
---

![Feature]({{site.baseurl}}/assets/img/storefront-resource-integration-with-wem-4-6/Feature.png)

One of the cool new features of WEM 4.6 is the ability to directly call Storefront resources as WEM applications and push into relevant Start Menu's or desktops the same as you would any other WEM driven application. We have been able to achieve the same result previously by utilising the receiver *selfservice.exe* with a *launch* switch, but this integrates a little nicer.

There are a few things to note as pre-requisites and a few things to consider before you run off conquering giants and all that.

*  The Server hosting the WEM console you are adding StoreFront applications from must have Citrix Receiver installed
*  WEM will publish the application shortcut regardless of the user having access to the Published Application. It may make sense to align your WEM assignments to your application publishing groups
*  You will want to think about how you display the WEM Agent for published applications, else you can end up with duplicates which whilst makes sense to us, may confuse users as below - hiding the Agent for published applications may make a little more sense than usual

[caption id="attachment_804" align="aligncenter" width="453"]![Image1_DoubleUp](https://jkindon.files.wordpress.com/2018/03/image1_doubleup.png) Duplicate Agents[/caption] 

There are a few new items in the WEM console to support this new functionality **Advanced Settings -> Storefront** Here you can add, edit and remove StoreFront Stores 

[caption id="attachment_805" align="aligncenter" width="940"]![Image2_Storefront](https://jkindon.files.wordpress.com/2018/03/image2_storefront.png) New StoreFront Configuration Tab[/caption] 

The WEM Application dialog box has also been redesigned 

[caption id="attachment_806" align="aligncenter" width="487"]![Image3_AppActionLayout](https://jkindon.files.wordpress.com/2018/03/image3_appactionlayout.png) Redesigned Application Action Screen[/caption]

## Configuring the Integration

The flow to enable this new functionality is as follows

1.  Enable your storefront stores within the WEM Console Itself
2.  Create WEM Applications based on these stores

**Advanced Settings -> Storefront -> Select Add** Enter your StoreFront Store (you will need a URL per Store) 

[caption id="attachment_807" align="aligncenter" width="940"]![Image4_StoreAddition](https://jkindon.files.wordpress.com/2018/03/image4_storeaddition.png) Adding a Store[/caption] 

Select **Add** and **Apply** your Config. Navigate back to **Actions -> Applications** and **add** a new Application Select the Application Type as "**Storefront Store**" 

[caption id="attachment_806" align="aligncenter" width="476"]![Image3_AppActionLayout](https://jkindon.files.wordpress.com/2018/03/image3_appactionlayout.png) Adding a new Application Action[/caption] 

Select the Store you defined previously and select **Browse** 

[caption id="attachment_808" align="aligncenter" width="608"]![Image5_AppAdd1](https://jkindon.files.wordpress.com/2018/03/image5_appadd1.png) Choosing the Store[/caption] 

Note at this point receiver will kick in an enumerate resources from the store you have defined. This is actioned via Citrix Receiver 

[caption id="attachment_809" align="aligncenter" width="648"]![Image6_AppAdd2](https://jkindon.files.wordpress.com/2018/03/image6_appadd2.png) Enumerating Apps via Receiver[/caption] 

From here you can select any of your published applications and create a WEM application action from them 

[caption id="attachment_810" align="aligncenter" width="513"]![Image7_AppAddStoreEnum](https://jkindon.files.wordpress.com/2018/03/image7_appaddstoreenum.png) Receiver Apps ready to be created as WEM Actions[/caption] 

Give it the normal details and enable self-healing if you need [caption id="attachment_811" align="aligncenter" width="495"]![Image8_AppAddDetails](https://jkindon.files.wordpress.com/2018/03/image8_appadddetails.png) Application Details[/caption] 

I build out start menu's, and you can add the Application the same as any other 

[caption id="attachment_812" align="aligncenter" width="500"]![Image9_StartLayout](https://jkindon.files.wordpress.com/2018/03/image9_startlayout.png) Start Menu Layout[/caption] 

Carry out your assignments (Take note of the first point discussed above - align this to a group that has access to the application via Citrix) 

[caption id="attachment_813" align="aligncenter" width="643"]![Image10_Assignment](https://jkindon.files.wordpress.com/2018/03/image10_assignment.png) Assignment Actions[/caption] 

Refresh the WEM agent on your published desktop 

[caption id="attachment_814" align="aligncenter" width="940"]![Image11_Desktop1](https://jkindon.files.wordpress.com/2018/03/image11_desktop1.png) First Pass at Desktop with Ugly Icons[/caption] 

Note that the icon is a bit narky - this is pulled from the cache in receiver on the server with the WEM console, so is worth changing to something nicer manually under the application properties in WEM 

[caption id="attachment_815" align="aligncenter" width="596"]![Image12_Icon1](https://jkindon.files.wordpress.com/2018/03/image12_icon1.png) Initial Icon from Cache[/caption] 

[caption id="attachment_816" align="aligncenter" width="586"]![Image13_Icon2](https://jkindon.files.wordpress.com/2018/03/image13_icon2.png) Nicer Icon from proper path[/caption] 

Refresh your agent again....Much nicer 

[caption id="attachment_817" align="aligncenter" width="923"]![Image14_Desktop2](https://jkindon.files.wordpress.com/2018/03/image14_desktop2.png) Second Pass Desktop with nice Icon[/caption] 

Launch the application 

[caption id="attachment_818" align="aligncenter" width="577"]![Image15_LaunchApp](https://jkindon.files.wordpress.com/2018/03/image15_launchapp.png) Typical Citrix Launch Screen[/caption] 

As expected - a nicely launched published app 

[caption id="attachment_819" align="alignnone" width="940"]![Image16_Proof](https://jkindon.files.wordpress.com/2018/03/image16_proof.png) Success - Published App Provisioned by WEM[/caption]

## Conclusion

This is probably the first true bit of integration with existing Citrix components we have seen. Admittedly its simply utilising receiver but it’s a start. Hopefully it’s a start of many more convergences with the existing product set

(Dear Citrix, please integrate more stuff)