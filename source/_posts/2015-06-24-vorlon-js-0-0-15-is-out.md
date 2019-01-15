---
id: 81
title: Vorlon.js 0.0.15 is out !
date: 2015-06-24T08:06:48+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/06/24/vorlon-js-0-0-15-is-out/
permalink: /en/2015/06/24/vorlon-js-0-0-15-is-out/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/06/24/vorlon-js-0-0-15-is-out.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10623662"
orig_post_name:
  - vorlon js 0 0 15 is out
orig_parent_id:
  - "10623662"
orig_thread_id:
  - "893494"
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
  - "3522"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Vorlon.js 0.0.15 is out !" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/06/24/vorlon-js-0-0-15-is-out/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta 2 months. We release Vorlon.js 2 months ago and we cannot tell you how thrilled we are about the response from all of you: the web community. When we launched the project during the //BUILD conference keynote,..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6102.1_thumb_5ABE6A1A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Vorlon.js 0.0.15 is out !" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/06/24/vorlon-js-0-0-15-is-out/" />
    <meta name="twitter:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta 2 months. We release Vorlon.js 2 months ago and we cannot tell you how thrilled we are about the response from all of you: the web community. When we launched the project during the //BUILD conference keynote,..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6102.1_thumb_5ABE6A1A.png" />
    
image: /wp-content/uploads/2016/02/1500x500.png
categories:
  - Vorlon.js
tags:
  - HTML5
  - Mobile
  - Vorlon.js
---
> If you have any question about this article or Vorlon.js, feel free to contact me on twitter: [_http://twitter.com/meulta_](http://twitter.com/meulta)__

**2 months.** We release Vorlon.js 2 months ago and we cannot tell you how thrilled we are about the response from all of you: the web community.

When we launched the project during the //BUILD conference keynote, we only had 3 plugins: the DOM Explorer, the Interactive Console and Modernizr. We knew at this time that the key to the success for a project such as Vorlon is the quantity and quality of plugins. When you want to debug your website, you do not want to do much complicated things. You just want to pick the correct plugin and get the correct information.

This is why we made this project open source. We know you have a lot of ideas to provide great debug experiences to web developers.

**So… 2 months, 66 pull requests, 78 issues and 547 commits later: we are proud to announce that we (YOU and the team) just released Vorlon.js version 0.0.15!**

You can get it by either cloning our GitHub repository (<https://github.com/MicrosoftDX/Vorlonjs>) or installing it using **npm** command tool (npm install –g vorlon).

_**Note**: if you are still wondering what Vorlon.js is, please read this article from David Catuhe first:_ [_http://blogs.msdn.com/b/eternalcoding/archive/2015/04/30/why-we-made-vorlon-js-and-how-to-use-it-to-debug-your-javascript-remotely.aspx_](http://blogs.msdn.com/b/eternalcoding/archive/2015/04/30/why-we-made-vorlon-js-and-how-to-use-it-to-debug-your-javascript-remotely.aspx)_)._

Let’s have a look at what is new in this version.

## New plugins

**XHR Panel** is here to help you get the list of requests done through XMLHttpRequest. You can choose to enable or disable the recording using the **play** button.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="1" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6102.1_thumb_5ABE6A1A.png" alt="1" width="707" height="256" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8712.1_1E06E18A.png)

**Network Monitor** is bringing the ability for you in Vorlon to see all the network exchanges that are done between the browser and the web server. It provides the resource name, the server domain, the type of request, the duration in milliseconds and a nice visual timeline!

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="2" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3276.2_thumb_50FB9353.png" alt="2" width="723" height="262" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4807.2_0D24CE4B.png)

**Resource Explorer** gives you information about what is stored locally on the client browser instance. There is data about **Sessions**, **Cookies**, and **Local Storage**. This can be really useful when you want to debug local cache or login / persistent user data issues.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="3" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2021.3_thumb_1FFE7357.png" alt="3" width="733" height="467" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6874.3_004D08DE.png)

**NG Inspector** is a $scope debugger for Angular.js. You have an easy access to all the values stored in each scope. This first version gives you information, a future one will give you the ability to edit your scopes.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="4" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2818.4_thumb_7A2ADDA4.png" alt="4" width="738" height="277" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3058.4_16390BDF.png)

## Plugin improvements

**DOM Explorer** has been improved a **LOT**.

Previously, this plugin was sending all the DOM data from the client to the dashboard each time it changed. This had a huge impact on performances. This is now fixed and you can refresh the DOM from the client either by asking it manually hitting the **refresh** button, or activating the auto-refresh on the **Settings** pane. The autofresh is smarter and uses MutationObserver if available on the client browser.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="5" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8105.5_thumb_2FC5BA6E.png" alt="5" width="745" height="307" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0638.5_7784B2A4.png)

Bonus feature: when the DOM changes on the client side, the round indicator in the refresh button changes to red! 😉

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="6" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1682.6_thumb_4F0AF1F2.png" alt="6" width="124" height="53" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6567.6_6F9231A4.png)

As you can see, the DOM Exploring pane is more beautiful and easier to read.

You can now edit HTML content and attributes by clicking on it. When hitting ENTER, the changes will be applied on the client side.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="7" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7024.7_thumb_680952E8.png" alt="7" width="602" height="38" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7802.7_384BAA69.png)

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="8" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0820.8_thumb_3E28DEB3.png" alt="8" width="609" height="33" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1565.8_2A0FC22A.png)

The DOM highlighting feature is easier to access. It happens when your mouse goes over the DOM element on the DOM explorer in the Vorlon dashboard.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="9" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6138.9_thumb_5F3E6BFE.png" alt="9" width="715" height="232" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6758.9_7910117C.png)

You can also right click on an element to remove or edit things. This is the best ergonomic way to enable deletion on attributes.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="10" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1200.10_thumb_79A0EFC6.png" alt="10" width="384" height="267" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6562.10_7EEFD677.png)

In the right pane, you have more information that just only the real CSS code now.

The **layout** tab gives you information that you are used to get in classic F12 tools: the margin, padding, border and size information.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="11" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0020.11_thumb_78CB1A8D.png" alt="11" width="416" height="388" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5852.11_3011A1C9.png)

Same thing for the **computed styles** which contains all the CSS styles applied explicitly and implicitly inherited.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="12" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5857.12_thumb_14060440.png" alt="12" width="418" height="388" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3386.12_4F56D94D.png)

The **HTML** tab is a better tool to edit text in the DOM. You can do breaklines and apply the change by hitting the save button.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="13" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3175.13_thumb_6C6218C6.png" alt="13" width="409" height="382" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1588.13_1C89638A.png)

Finally, the **settings** section is where is you can activate the auto refresh for the DOM.

**Interactive Console** have some new features too.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="14" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6710.14_thumb_6DC8CC49.png" alt="14" width="707" height="218" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5287.14_54CA6B53.png)

We have the **windows.onerror**, **console.dir** and complex **object** log support. You can navigate in object properties using a visual tree. Filters are available to only show a subset of logs and you can filter using a search-like text area.

## Other changes and improvements

We did a lot of other changes in the code organization and structures that are not directly visible in plugins and features.

For instance, we renamed and moved the catalog.json file which contains the list of plugins and some parameters to the Server folder. It is now called config.json because some parameters are not related to plugins. To avoid copy paste and to simplify debug and usage, we also added an **enabled** boolean parameter in the plugins configuration in config.json. If false for a specific plugin it will not be loaded in the dashboard and not sent to the client in the generated **vorlon.js** file.

We also split the plugins in 2 separated files. Originally a plugin was composed of only one JavaScript file containing the code for the dashboard and the client side. It was easier when we started the project. Now that more complex plugins are created and for optimization reasons we split this into 2 different files: **yourplugin.client.js** and **yourplugin.dashboard.js**.

You can read more about the changes we made in the **whatsnew.md** file available on our GitHub repo: <https://github.com/MicrosoftDX/Vorlonjs/blob/master/whatsnew.md>

## What’s next?

We are now working on the next version which will contain new plugins and core improvements. Authentication, webgl, webaudio are part of the list!

As I said, we want this project to be the web developer’s project. If you have an idea, you can either:

  * Submit an issue on GitHub: <https://github.com/MicrosoftDX/Vorlonjs/issues>
  * Create is yourself and submit a pull request (we review this every day!)

_Note: to help you learn how to create plugins, I have written this: http://bit.ly/vorlonplugin_

**Let’s work together on Vorlon.js to make debug experiences easier and better.**

Do not forget to follow our team twitter account <http://twitter.com/vorlonjs> !

_Written by Etienne Margraff on behalf of all the Vorlon.js core team: David Catuhe, David Rousset, Pierre Lagarde and Justin Garrett._

> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)