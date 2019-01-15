---
id: 141
title: How to deploy an online Vorlon.js server with authentication
date: 2015-09-17T12:35:13+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication/
permalink: /en/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10642318"
orig_post_name:
  - how to deploy an online vorlon js server with authentication
orig_parent_id:
  - "10642318"
orig_thread_id:
  - "896978"
orig_application_key:
  - emargraff
orig_post_author_id:
  - "285541"
orig_post_author_username:
  - Etienne Margraff
orig_post_author_email:
  - etienne.margraff@live.fr
orig_post_author_created:
  - 2010-06-09 04:06:12.000
orig_is_approved:
  - "1"
orig_attachment_count:
  - "0"
total_views:
  - "1674"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deploy an online Vorlon.js server with authentication" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta When we started Vorlon.js with Pierre, David and David we wanted to keep it as simple as possible. It is our main concern, our mojo. That is why you only have to run npm install –g vorlon..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7245.image_thumb_673CC676.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deploy an online Vorlon.js server with authentication" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication/" />
    <meta name="twitter:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta When we started Vorlon.js with Pierre, David and David we wanted to keep it as simple as possible. It is our main concern, our mojo. That is why you only have to run npm install –g vorlon..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7245.image_thumb_673CC676.png" />
    
image: /wp-content/uploads/2015/09/deployazure.png
categories:
  - Vorlon.js
tags:
  - Vorlon.js
---
> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)

When we started <a href="http://vorlon.io" target="_blank">Vorlon.js</a> with <a href="http://twitter.com/pierlag" target="_blank">Pierre</a>, <a href="https://twitter.com/deltakosh" target="_blank">David</a> and <a href="https://twitter.com/davrous" target="_blank">David</a> we wanted to keep it as simple as possible. It is our main concern, our mojo. That is why you only have to run **npm install –g vorlon** to get a Vorlon server and that you only have to add **ONE** line of code in your client to connect it to the Vorlon dashboard. This is why in the early version we did not implement any kind of **authentication**.

In this article I will explain to you why we added this and how to activate it.

If you never used Vorlon.js, read this first : [http://blogs.msdn.com/b/eternalcoding/archive/2015/04/30/why-we-made-vorlon-js-and-how-to-use-it-to-debug-your-javascript-remotely.aspx](http://blogs.msdn.com/b/eternalcoding/archive/2015/04/30/why-we-made-vorlon-js-and-how-to-use-it-to-debug-your-javascript-remotely.aspx "http://blogs.msdn.com/b/eternalcoding/archive/2015/04/30/why-we-made-vorlon-js-and-how-to-use-it-to-debug-your-javascript-remotely.aspx")

# Why we implemented authentication

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7245.image_thumb_673CC676.png" alt="image" width="341" height="179" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4274.image_6E59723D.png)

When we did our first demos in public we published our own Vorlon server instance in a Microsoft Azure website. At this time we didn’t have a way to specify a login and password for the dashboard.

**This once led to a huge fail 🙂**

Someone in the public copied the url displayed on my screen and accessed the dashboard from his computer. This messed up with the one displayed on my computer and totally screwed our demo. **YEY ! o/**

From this fail we made the decision to implement a simple authentication. This is obviously helping us for our demos but also you in the case you want to publish a publicly accessible version of the dashboard.

# How to deploy Vorlon.js online easily ?

Vorlon is really easy to install. All you need to to is having Node.js Package Manager (npm) on you box and run the correct command line. Everything is get to you from the npm platform and you can start you instance typing **vorlon** in your command line.

From there you need to make your server accessible through the internet and open the correct tcp port etc. etc. This can be a bit complicated and if you do not want to manage that yourself you can use a feature we added for you in our github repository : [https://github.com/microsoftdx/vorlonjs](https://github.com/microsoftdx/vorlonjs "https://github.com/microsoftdx/vorlonjs").

If you go on the bottom of the repo, in the readme section,  you get access to a **Deploy to Azure** button.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8080.image_thumb_713B45E0.png" alt="image" width="552" height="251" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6470.image_72111B19.png)

By clicking on this, we automatically get you through a 3 steps process which will:

  * Create an Azure website on your Azure subscription (*)
  * Deploy the latest version of Vorlon on it

&nbsp;

**_(*) if you do not have an azure subscription and want to get one you can know more in the last section of this article (with FREE options in it ;-))_**

All of this is **automated**. You can see a quick video of this here :



# How to activate authentication

_**PLEASE NOTE:** For now the authentication is only available in the **development-0.0.16** branch on the GitHub repo. To get it, you need to deploy the code from this branch (manually somewhere you want or using Azure deploy). It will be available on the npm package in the 0.0.16 version we should release by the end of september._

We implemented authentication using <a href="http://passportjs.org/" target="_blank">passport.js</a>. We chose to activated a simple mode which you specify a login and password. For now you can only specify one account and we may implemented a more sophisticated version of this later (including **Twitter** and **Facebook** auth and multiple accounts management).

You can activate a basic authentication on the Vorlon.js dashboard by adding 3 values to the config.json file:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6675.image_thumb_37BAC69A.png" alt="image" width="692" height="116" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6254.image_47C704A0.png)

This file is located in the **/server** folder on your Vorlon.js deployment folder (or in the _node_modules_ folder if you deployed using **npm**).

Restart your Vorlon instance and **BAM** you are now prompted and asked to give your username and password.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="vorlonauth" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3858.vorlonauth_thumb_201D57AB.png" alt="vorlonauth" width="662" height="486" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6237.vorlonauth_333BF3A6.png)

Easy right? 🙂

# How to change the config.json file when deployed on Azure

If you chose to deploy Vorlon on an Azure subscription you can access the files hosted on the Azure Web App using Visual Studio Online Monaco. This is a free tool actionable from the **Configure** section of your web app in the Azure Dashboard.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1033.image_thumb_413B3723.png" alt="image" width="491" height="94" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4382.image_3F6AE15C.png)

You can then get access to the **Edit in Visual Studio Online** button on your web app dashboard page.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0676.image_thumb_6E52B4A2.png" alt="image" width="298" height="46" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4375.image_37E202A0.png)

Navigate to the config.json file and edit it to activate authentication (or add / remove plugins also !):

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3681.image_thumb_1C35247D.png" alt="image" width="719" height="560" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2262.image_521788E6.png)

_**Note : do not forget to restart the service for this to be taken into account**_.

## 

# I want to use an Azure Web App but do not have an account yet, what are my options ?

You can create an account on the <http://azure.microsoft.com> website. This will get you the ability to create free azure web apps. 🙂

Another way to test it is to get a trial by going here : [https://azure.microsoft.com/en-us/pricing/free-trial/](https://azure.microsoft.com/en-us/pricing/free-trial/ "https://azure.microsoft.com/en-us/pricing/free-trial/"). You will have a credit card-free account to try azure for one month.

Finally, if you are a Startup or anything else which matches with the requirements you can create a Bizspark account: [https://www.microsoft.com/bizspark](https://www.microsoft.com/bizspark "https://www.microsoft.com/bizspark") this will enable you pretty much the same thing as the trial but going on for 3 years.

And if you **really** want to host Vorlon elsewhere there are no problems, it will work the same way 🙂

> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)