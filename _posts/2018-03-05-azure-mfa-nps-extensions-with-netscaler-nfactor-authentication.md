---
layout: post
title: "Azure MFA NPS Extensions with NetScaler nFactor Authentication"
permalink: "/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/"
subtitle: "Configuring a seamless MFA experience with nFactor and the Azure MFA Extensions"
cover-img: /assets/img/Sydney1.jpg
thumbnail-img: /assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/EndResult1.png
share-img: /assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/EndResult1.png
tags: [Citrix, MFA, NetScaler]
categories: [Citrix, MFA, NetScaler]
redirect_from: 
    - /2018/03/05/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication
    - /2018/03/05/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/
---

![nFactor]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/EndResult1.png)

Azure MFA (Multi Factor Authentication) is fast becoming a topic being discussed with pretty much all my customers, even those that have an existing MFA solution in place, but are realising they may already be entitled to the offering from Microsoft as part of their +Security bundles within the Office 365 space.

The addition of the [Azure NPS extensions](https://docs.microsoft.com/en-us/azure/multi-factor-authentication/multi-factor-authentication-nps-extension) into the product set simplifies the implementation and discussions yet again, as we can now leverage existing servers to provide the RADIUS endpoints for services such as NetScaler to authenticate against.

In this post, I am going to configure NetScaler nFactor Authentication to simplify the on-boarding of Azure MFA Authentication via the NPS Extensions with load balanced RADIUS Servers. My setup for this guide consists of the following components:

*  2 x NPS Servers with the Azure MFA Extensions
*  2 x NetScaler VPX Appliances with Enterprise Licencing
*  1 x AAA vServer
*  1 x RADIUS LB vServer
*  1 x Access Gateway vServer (Unified Gateway)

## Setting up Azure MFA, NPS roles and extensions

Firstly, Christiaan Brinkhoff has a fantastic article [here](https://www.christiaanbrinkhoff.com/2017/02/17/how-to-configure-azure-mfa-for-citrix-netscaler-gateway-radius-by-using-the-new-nps-extension/#Setup-the-NPS-server-role) which I base my initial configurations on. I am not going to reinvent the wheel; his work is always exceptional so that's the starting point for NPS.

I suggest starting with his article as the only point of change here, is once we get to the NetScaler configurations with a few exceptions noted below:

*  My configuration includes multiple NPS Servers for redundancy
*  Because I am load balancing the NPS servers via NetScaler, the NPS Servers need to include the relevant NetScaler SNIP as a RADIUS Client. I include the NSIP of each NetScaler, and the SNIP

This configuration is based on a NetScaler Enterprise Licence, if you do not have Enterprise you will need to configure traditional Authentication Policies.

## Setting up Load Balancing for the NPS Servers

Once you have configured both NPS Servers, it's time to setup RADIUS load balancing on the NetScaler front.

Once again, there is already a documented step by step guide by Carl Stalhood (Surprise!) [here](https://www.carlstalhood.com/radius-load-balancing-netscaler-12/) for RADIUS load balancing. Follow this to get you started and pay attention to the load balancing Method mentioned.

Note that if you are using an earlier version of NetScaler than 12, Carl has guides available as well

## Configuring NetScaler nFactor Authentication

Why nFactor for this type of deployment? Primarily believe it or not, it's due to its simplicity when integrating with multiple client types, the lack of requirement for rewrites on the authentication pages, and the support of whatever theme you want.

As per [Citrix Documentation on nFactor](https://docs.citrix.com/en-us/netscaler-gateway/12/authentication-authorization/nfactor-for-gateway-authentication.html): 

> nFactor authentication enables a whole new set of possibilities with respect to authentication. Administrators using nFactor enjoy authentication, authorization, and auditing (AAA) flexibility when configuring authentication factors for virtual servers
> 
> Traditionally, Citrix clients (including Browsers and Receivers) use the active directory (AD) password as the first password field. The second password is usually reserved for the One-Time-Password (OTP). However, in order to secure AD servers, OTP is required to be validated first. nFactor can do this without requiring client modifications.


### Create Authentication Virtual Server

*Go to Security -> AAA – Application Traffic -> Virtual Servers.* 

**Create** a non-addressable **Authentication vServer**. 

[![Auth vServer 1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer1.png)

    Above: Non-addressable Authentication Virtual Server

**Bind** your Certificate as normal. Skip through the other settings for now 

[![Auth vServer 2]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer2.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer2.png)

    Above: Authentication vServer created and in an Up state

### Add an LDAP and RADIUS Authentication Server Profile

*Go to Security -> AAA – Application Traffic -> Policies -> Authentication -> Basic Policies -> LDAP* 

Select **Servers** and create an **LDAP Server** if you don't have one 

[![LDAP Profile 1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LDAPProfile1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LDAPProfile1.png)

    Above: LDAP(S) Authentication Server

*Go to Security -> AAA – Application Traffic -> Policies -> Authentication -> Basic Policies -> RADIUS*

Select **Servers** and create a **RADIUS Server** if you don't have one (I use the NetScaler VIP created as my RADIUS LB) Ensure that your **RADIUS profile** has the appropriate **timeouts**, **NAS ID** and **password encoding** set 

[![RADIUSServer1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/RADIUSServer1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/RADIUSServer1.png)

    Above: RADIUS Server - Note Time-Out, NAS ID and Password Encoding Type

Once completed, confirm your Server object exists 

[![RADIUSProfile1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/RADIUSProfile1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/RADIUSProfile1.png)

    Above: RADIUS Authentication Server

### **Add LDAP and RADIUS Authentication Policies**

*Go to Security -> AAA – Application Traffic -> Policies -> Authentication -> Advanced Policies -> Authentication Policies.* 

**Add** two policies: one for **LDAP** and one for **RADIUS**. set the **Request Server** to the **Authentication Servers** you created previously, and **set** the expression to ***true***

[![AuthPolicies1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthPolicies1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthPolicies1.png)

    Above: Advanced Authentication Policies - LDAP and RADIUS

### Create an Authentication Login Schema Profile and Policy

*Go to Security -> AAA – Application Traffic -> Login Schema*

Select the **Profiles** tab and Click the **Add** button 

[![LoginSchema1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema1.png)

    Above: New Authentication Login Schema

Select the **pencil** next to the noschema default entry under **Authentication Schema**: Choose the **SingleAuth.xml** entry as your starting template. Select **Edit** on the right hand side 

[![LoginSchema2]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema2.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema2.png)

    Above:  SingleAuth.xml Schema Template

Give the **Schema** **Profile** a name and edit any fields you want to alter 

[![LoginSchema3]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema3.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema3.png)

    Above: Custom Schema Profile Fields

Select **Save** Ensure that you **select** your new template and then select **create**. Do this by pressing **select** on the right hand side

[![LoginSchema4]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema4.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema4.png)

    Above: Ensure you select the new Schema

Confirm the **login Schema Profile** is created 

[![LoginSchema5]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema5.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchema5.png)

    Above: Login Schema Profile created

Select the **Policies** tab and Click the **Add** button Give the **Policy** a name and select the **Profile** you just created. Give the rule a value of **true**. 

[![LoginSchemaPolicy1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchemaPolicy1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchemaPolicy1.png)

    Above: New Login Schema Policy

Select **Create** Confirm the new **policy** is created 

[![LoginSchemaPolicy2]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchemaPolicy2.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/LoginSchemaPolicy2.png)

    Above: Login Schema Policy created

### Create a Policy Label

> A policy label specifies the authentication policies for a particular factor. Each policy label corresponds to a single factor. The policy label must be bound as the next factor of an authentication policy or of another authentication policy label. Typically, a policy label includes authentication policies for a specific authentication mechanism


*Go to Security -> AAA – Application Traffic -> Policies -> Authentication -> Advanced Policies -> Policy Label* 

Select **Add. **Give the **PolicyLabel** a name 

[![AuthenticationPolicyLabel1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthenticationPolicyLabel1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthenticationPolicyLabel1.png)

    Above: New Authentication PolicyLabel for RADIUS Authentication

Select **Continue.** **Select** the **RADIUS** **Authentication Policy** you created above. Note this is a very simple use of nFactor, we are only using a single **Policylabel** with **RADIUS** as our **second factor** 

[![AuthenticationPolicyLabel2]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthenticationPolicyLabel2.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthenticationPolicyLabel2.png)

    Above: Bind the RADIUS Authentication Policy to the PolicyLabel

Select **Bind** 

[![AuthenticationPolicyLabel3]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthenticationPolicyLabel3.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthenticationPolicyLabel3.png)

    Above: Confirm PolicyLabel is created with RADIUS Authentication Policy

### Assign Authentication Policy to the Authentication vServer

*Go to Security -> AAA – Application Traffic -> Virtual Servers*

**Edit** the **Authentication vServer** you created earlier and **select** **"Advanced Authentication Policies"** 

[![AuthvServer3]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer3.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer3.png)

    Above: Advanced Authentication Policies for the Authentication vServer

Select the **LDAP** **Policy** that you created previously and then select your **RADIUS Policy Label** as the **next Factor** 

[![AuthvServer4]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer4.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer4.png)

    Above: LDAPS is our first Factor, RADIUS PolicyLabel as our Second

Select **Bind**

### Assign a Login Schema to the Authentication vServer

*Go to Security -> AAA – Application Traffic -> Virtual Servers* 

**Edit** the **Authentication vServer** you created earlier and select "**Login Schema**" Bind the **Login Schema Policy** you created previously 

[![AuthvServer5]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer5.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthvServer5.png)

    Above: Bind the Login Schema created previously

### Configuring the NetScaler Gateway vServer

At this point, you would **remove existing Authentication Policies** assigned to your Gateway vServer, and bind your new **Authentication Profile.** 

*Go to NetScaler Gateway -> Virtual Servers -> Edit your Gateway -> Select Authentication Profile.*

[![GatewayAuthProf1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/GatewayAuthProf1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/GatewayAuthProf1.png)

    Above: Current Authentication Profile

Select the **+** to Add Give the **Authentication Profile** a **name**, and select the **Authentication vServer** you created earlier 

[![GatewayAuthProf2]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/GatewayAuthProf2.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/GatewayAuthProf2.png)

    Above: Create Authentication Profile

Select **OK** and confirm your **Authentication Profile** is applied 

[![GatewayAuthProf3]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/GatewayAuthProf3.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/GatewayAuthProf3.png)

    Above: Authentication Profile Assigned to Gateway

Note that this creates the profile below, but doesn’t need all the other mandatory fields that creating it manually requires 

*Security -> AAA – Application Traffic -> Authentication Profile* 

[![AuthProfile1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthProfile1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/AuthProfile1.png)

    Above: Authentication Profile Created via Gateway

### End Result

Once everything has been applied, you should experience a simple logon scheme on your Gateway vServer as below: 

[![EndResult1]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/EndResult1.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/EndResult1.png)

    Above: RFWebUI Web Page - First Factor

Once you have entered your first Factor (LDAPS Username and Password), the nFactor configuration will move to RADIUS, the behaviour of the next stage will differ depending on your Authentication Mechanism within MFA. 

If you use the Authenticator App, you will be prompted for confirmation on your mobile device. The NetScaler will wait 30 seconds for this confirmation to take place before timing out. 

If you use Text Message/SMS based authentication, the NetScaler will prompt you for your confirmation PIN as follows: 

[![EndResult2]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/EndResult2.png)]({{site.baseurl}}/assets/img/azure-mfa-nps-extensions-with-netscaler-nfactor-authentication/EndResult2.png)

    Above: RFWebUI Page Page - Second Factor - SMS/Text

This behaviour will follow across Web, Receiver, Mobile Receiver and the SSL VPN Client

## Conclusion

As with everything NetScaler, there are many ways to achieve the same result. This is only a basic use of the nFactor capability on NetScaler and there probably more advanced or different ways of configuring the above, however it seems to fit well together with NPS and Azure MFA across multiple device types.