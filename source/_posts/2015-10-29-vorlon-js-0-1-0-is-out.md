---
id: 131
title: Vorlon.js 0.1.0 is out !
date: 2015-10-29T02:52:06+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/10/29/vorlon-js-0-1-0-is-out/
permalink: /en/2015/10/29/vorlon-js-0-1-0-is-out/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/10/29/vorlon-js-0-1-0-is-out.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10651005"
orig_post_name:
  - vorlon js 0 1 0 is out
orig_parent_id:
  - "10651005"
orig_thread_id:
  - "898789"
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
  - "2674"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Vorlon.js 0.1.0 is out !" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/10/29/vorlon-js-0-1-0-is-out/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta The Vorlon.js core team is split between Paris and Redmond. Last week we decided to ship a new big release and we all took a plane to Redmond and get together for a 2 days intense pair..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4035.vorlon_thumb_11110F35.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Vorlon.js 0.1.0 is out !" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/10/29/vorlon-js-0-1-0-is-out/" />
    <meta name="twitter:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta The Vorlon.js core team is split between Paris and Redmond. Last week we decided to ship a new big release and we all took a plane to Redmond and get together for a 2 days intense pair..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4035.vorlon_thumb_11110F35.png" />
    
image: /wp-content/uploads/2015/10/code-583073_640.jpg
categories:
  - Vorlon.js
tags:
  - HTML5
  - Mobile
  - Responsive
  - Vorlon.js
---
> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter: <http://twitter.com/meulta>_ 

The Vorlon.js core team is split between Paris and Redmond. Last week we decided to ship a new big release and we all took a plane to Redmond and get together for a 2 days intense pair programming session. After multiple hours of bug bashing and last minute features coding we are **happy and proud to announce** that we published the new version of **Vorlon.js : 0.1.0** !

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="vorlon" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4035.vorlon_thumb_11110F35.png" alt="vorlon" width="413" height="265" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8228.vorlon_5629DC6B.png)

You can get it by running the **npm install –g vorlon** command, clone the GitHub repo: [https://github.com/Microsoftdx/vorlonjs](https://github.com/Microsoftdx/vorlonjs "https://github.com/Microsoftdx/vorlonjs") or install it using the new **deploy to Azure** button we added between the last version and the new one (<a href="http://blogs.msdn.com/b/emargraff/archive/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication.aspx" target="_blank">read more about this</a>).

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0777.image_thumb_5241A93D.png" alt="image" width="482" height="225" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2251.image_70F89328.png)

4 month between the 0.0.15 and the 0.1.0 version and we are now up to almost **1000** commits, **100** pull requests and we closed and fixed **120** issues. Vorlon.js is heading the right direction and this is mainly thanks to the web community: **thanks to you guys** ! 🙂

# What is new in this release

## Unit testing plugin

We now have a unit testing plugin based on qUnit. You can upload you Qunit file or directly type your test on the Vorlon.js dashboard : it will run it on the client side and get you the result summary.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7848.image_thumb_2F0EBA78.png" alt="image" width="705" height="412" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3441.image_3F872B73.png)

This has been done by <a href="https://github.com/cubitouch" target="_blank">Cubitouch</a>.

## 

## Device plugin

This is inspired from the <http://mydevice.io> website created by <a href="https://twitter.com/goetter" target="_blank">Raphael Goetter</a>. It is giving you information about the device you are running your website on like the pixel ratio, the pixel per points, the meta viewport or even the User Agent.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7382.image_thumb_059A7938.png" alt="image" width="715" height="369" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3806.image_314B4334.png)

## Best practices plugin

Creating a web site can be challenging sometimes because you have to follow a lot of rules and best practices to provide the best experience possible. We decided to help you improving your code with Vorlon.js through the Best Practices analyzer. It is performing static and dynamic analytics on your code to tell you what could be better. It is organized into 4 categories:

  * **Accessibility:** Warn you if you have forgotten thing like **alt** on images or aria attributes
  * **Mobile Web:** Are you using responsive practices ? do you use the meta viewport tag?
  * **Performances:** Are your files minified? Did you bundle them do reduce http request count ?
  * **Web standards:** Are you doing browser detection? Are you correctly using CSS prefixes?

&nbsp;

This is only a subset of all the rules we have here, and the two guys who did it (<a href="https://github.com/gleborgne" target="_blank">Guillaume Leborgne</a> and <a href="https://github.com/lahloumehdi" target="_blank">Mehdi Lahlou</a>) made it extensible. You can create your own rules and easily add them to this analyzer.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5102.image_thumb_3794AA73.png" alt="image" width="787" height="377" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5808.image_40EDDEF6.png)

## Improvements and other plugins :

Vorlon.js got its first third party plugin : <a href="https://github.com/MicrosoftDX/Vorlonjs/tree/master/plugins%20library" target="_blank">Wappalyzer</a> which is available in the GitHub repo folder **plugins library**.

The DOM Explorer has been highly improved with :

  * All of the nodes displayed (not only body, but head too)
  * CSS updates
  * A better search UI
  * Select a DOM on the client

&nbsp;

Object explorer is better integrated in the dashboard and we did some bug fixes.

## Dashboard

We did a lot of refactoring, performance and stability improvements on the dashboard. You can also refresh the client side from there by clicking on the **reload client** button.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6886.image_thumb_38FB5DF6.png" alt="image" width="281" height="357" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7282.image_3BA188F6.png)

## HTTP Proxy : use Vorlon.js without changing your client code

We created a new awesome feature we were able to ship on this version : the **HTTP proxy**. This allows you to inject the **Vorlon.js client code automatically** while browsing your website.

The way it works is really simple: all the **http requests** you do for your client site are redirected through an http proxy hosted on node.js side by side with the Vorlon.js server. Each time an HTML page goes there we inject the **script** tag you would have had to add yourself.

To use it: only browse this url : <http://localhost:1337/httpproxy> (or any domain name you are using instead of localhost).

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3542.image_thumb_43BB45FC.png" alt="image" width="610" height="620" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4431.image_6205FCF2.png)

Enter your url and click on  :

  * **Open website only** : to open a proxified url for your website
  * **Open dashboard only**: to open the dashboard plugged to a session according to the proxified version of your website
  * **Inspect with Vorlon.js**: to open both in one click

&nbsp;

You can notice than the URL is different from your original one :

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4645.image_thumb_47D13562.png" alt="image" width="563" height="223" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8400.image_06795F54.png)

It is composed of multiple parts:

<http://localhost:5050/vorlonproxy/root.html?vorlonproxytarget=[YOURWEBSITEURL]&vorlonsessionid=[DASHBOARDSESSION>]

You just have to browse your Vorlon.js instance using the correct session :

<http://localhost:1337/dashboard/[DASHBOARDSESSION]>

And everything works the same way you already know ! 🙂 Isn’t that awesome ?

A huge thanks to Guillaume Leborgne who did a really strong work on this one.

## More improvements

We added support for authentication  :

[<img title="vorlonauth" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3858.vorlonauth_thumb_201D57AB.png" alt="vorlonauth" width="665" height="488" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6237.vorlonauth_333BF3A6.png)

And automated deployment from GitHub to you Microsoft Azure account:

[<img title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8080.image_thumb_713B45E0.png" alt="image" width="644" height="293" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6470.image_72111B19.png)

You can read more about this here : [http://blogs.msdn.com/b/emargraff/archive/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication.aspx](http://blogs.msdn.com/b/emargraff/archive/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication.aspx "http://blogs.msdn.com/b/emargraff/archive/2015/09/17/how-to-deploy-an-online-vorlon-js-server-with-authentication.aspx")

Do not hesitate to share about this with us on twitter or to create an issue on GitHub: [https://github.com/MicrosoftDX/Vorlonjs](https://github.com/MicrosoftDX/Vorlonjs "https://github.com/MicrosoftDX/Vorlonjs")

And if you want to participate, jump in and create new plugins ! Here is something to get you started : [http://blogs.msdn.com/b/emargraff/archive/2015/06/01/how-to-create-a-vorlon-js-plugin.aspx](http://blogs.msdn.com/b/emargraff/archive/2015/06/01/how-to-create-a-vorlon-js-plugin.aspx "http://blogs.msdn.com/b/emargraff/archive/2015/06/01/how-to-create-a-vorlon-js-plugin.aspx")

Have fun 🙂

> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter: <http://twitter.com/meulta>_