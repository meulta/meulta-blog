---
id: 111
title: How Vorlon.js helps you improve your web code
date: 2015-11-27T08:36:11+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/11/27/how-vorlon-js-helps-you-improve-your-web-code/
permalink: /en/2015/11/27/how-vorlon-js-helps-you-improve-your-web-code/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/11/27/how-vorlon-js-helps-you-improve-your-web-code.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10656991"
orig_post_name:
  - how vorlon js helps you improve your web code
orig_parent_id:
  - "10656991"
orig_thread_id:
  - "899958"
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
  - "4214"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How Vorlon.js helps you improve your web code" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/11/27/how-vorlon-js-helps-you-improve-your-web-code/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta When it comes to writing good code in web development it is easy to get lost in the quantity of resources you find online. There are some basics that everyone knows or should know and there are..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0027.image_thumb_5A9D8B9A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How Vorlon.js helps you improve your web code" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/11/27/how-vorlon-js-helps-you-improve-your-web-code/" />
    <meta name="twitter:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta When it comes to writing good code in web development it is easy to get lost in the quantity of resources you find online. There are some basics that everyone knows or should know and there are..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0027.image_thumb_5A9D8B9A.png" />
    
image: /wp-content/uploads/2015/11/programming-1009134_640.jpg
categories:
  - Vorlon.js
  - Web
tags:
  - Accessibility
  - HTML5
  - Mobile
  - Responsive
  - Vorlon.js
---
> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter: <http://twitter.com/meulta>_ 

When it comes to writing good code in web development it is easy to get lost in the quantity of resources you find online. There are some basics that everyone knows or should know and there are some more specific ones.

Are you able to tell me right now that you sure you follow these practices ? Probably not. You probably have the intuition that you do and you are certainly writing your code with them in mind but you cannot be sure you always respect them.

As I said, there are a <a href="http://thenextweb.com/dd/2015/10/19/10-rules-of-best-practice-for-responsive-design/" target="_blank">lot</a> <a href="http://thenextweb.com/dd/2015/10/19/10-rules-of-best-practice-for-responsive-design/" target="_blank">of</a> <a href="http://www.webaxe.org/" target="_blank">different</a> <a href="http://webuilddesign.com/10-css-best-practices-for-2015/" target="_blank">resources</a> <a href="http://jstherightway.org/" target="_blank">on the web</a>. It is not easy to know all of them. It is not easy to follow all of them. And it is **sure** not easy to be sure you did it correctly.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0027.image_thumb_5A9D8B9A.png" alt="image" width="673" height="154" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1513.image_316750DD.png)

This is why we decided to create the **<a href="http://vorlonjs.com/documentation/#best-practices" target="_blank">Best Practices</a>** plugin in Vorlon.js. It is a way for you to automatically get hints and recommandations about how you could improve your code. The current list of practices and scans have been created from our own experience. It is extensible and you can add your own rules to contribute to this plugin and make it more accurate and comprehensive. 🙂

> _A **great thanks** to_ <a href="https://twitter.com/gleborgne" target="_blank"><em>Guillaume Leborgne</em></a> _and_ <a href="https://twitter.com/Mehdi_La" target="_blank"><em>Mehdi Lahlou</em></a> _for their strong work on this!_

## How to use the best practices plugin

First of all, you need to setup a Vorlon.js environment. You can follow the documentation we provide here : [http://vorlonjs.com/documentation/#vorlonjs-server](http://vorlonjs.com/documentation/#vorlonjs-server "http://vorlonjs.com/documentation/#vorlonjs-server")

Once you have an up and running vorlon.js server and your website is connected to it, hit the “play” button on the Best Practice tab. It will run dynamic and static tests on the page you are currently debugging and the resources linked to it (JavaScript files, CSS files, etc.)



<span style="color: #333333;">The above video shows you the kind of result you get when using this plugin. All the recommendations are organized into 4 categories, <strong>Web Standards</strong>, <strong>Accessibility</strong>, <strong>Performances</strong>, <strong>Mobile Web</strong>.</span>

<span style="color: #333333;">Let’s have a look at some of the rules you get in each of these categories.</span>

## 1. Web Standards

There are a lot of common mistakes we can do in this area. Sometimes, it is not even a mistakes. Take the JavaScript libraries you use for instance: how frequently do you go and check if the version you are referencing is obsolete or not ? Or consider the CSS prefixes problematic: are you sure you always add all the vendor prefixes? That could be a good idea to make sure your site works correctly on the widest range of computers. Do you have code which does browser detection ? You should change it to feature detection. Etc. etc.

This section gives your insights about what you can improve in this area:

  * **Avoid browser detection**: tells you if you have code calling _navigator.userAgent_
  * **Avoid browser specific content**: is checking whether your website is sending a different content for some browsers
  * **Avoid conditionnal comment**: Conditional comments are not the best way to adapt your website to target browser, and support is dropped for IE > 9.
  * **Incorrect use of css fallback**: validates that all the css rules present in the CSS file are really there in the computed styles. This is a dynamic check and the result might be _true_ or _false_ depending on the browser you use.
  * **Incorrect use of prefixes**: this one is performing a static scan on your CSS files to ensure you are always using all the vendor prefixes
  * **Object and embed**: the modern web is only about web languages not plugins, activeX and other embeded objects. This validates that your website does not include one
  * **Update JavaScript libraries**: checks if all the JS files you are using are considered by their creators as not obsolete
  * **Use modern doctype**: Modern doctype like <!DOCTYPE html> are better for browser compatibility and enable using HTML5 features.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6012.image_thumb_6A42B80D.png" alt="image" width="678" height="325" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7635.image_3F67C34A.png)

## 2. Accessibility

Following web standards does not guarantee you that your web page is easily accessible. **Accessibility** is something the Vorlon.js team is really concerned about.

A lot of work is done currently for sometimes now about this by great people. One exemple is the <a href="http://www.deque.com/products/aXe/" target="_blank">aXe</a> product created by <a href="http://www.deque.com" target="_blank">deque</a>. It is an open source tool which gives you a gigantic list of advices about your website. They go deep in the analysis and can for instance tell you that a specific element has insufficient color contrast for someone visually impaired to see properly. This is really awesome work and we worked with the team at deque to integrate this into this plugin.

_Note : this integration is not available in the npm version of Vorlon.js yet but you can get it form the <a href="https://github.com/Microsoftdx/vorlonjs/tree/dev" target="_blank">dev branch</a> in the github repository._

There are too much rules in there for me to be able to list them all but here are the fixed one:

  * **Form elements must have labels**: for them to be understandable by automated web readers
  * **Images must have alternate text**: this one is listing you all the <img /> tag which does not contain the alt attribute.
  * **Use aria attributes**

All the **aXe** rules are displayed only if they are in a failed state :

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2273.image_thumb_3BEBC311.png" alt="image" width="697" height="299" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0830.image_0C2E1A92.png)

## 3. Performances

You can follow some simple rules to get better performances for your website.

  * **Encore static content**: tries to determine if you are using gzip or deflate encoding to reduce de network bandwith
  * **Minify static files**: checks if you used a minification process to reduce the size of your CSS and JavaScript files
  * **Try bundling your files**: simple algorithm that checks if you created a single file for all your scripts to reduce HTTP requests

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4034.image_thumb_119F1BE7.png" alt="image" width="684" height="239" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6087.image_5DD72595.png)

## 4. Mobile Web

When it comes to mobiles, a lot of web devs forget to add the correct elements and information to take it correctly into account.

  * **define platform icons**: This is really not mandatory but it gives the user a better experience when they are pinning your websites
  * **use meta viewport**: Use meta viewport tag to choose how your website will get scaled on smaller devices like phones. Define at least <meta name=&#8221;viewport&#8221; content=&#8221;width=device-width, initial-scale=1&#8243;>
  * **use responsive approaches**: Even if your website target only certain devices, you may have users with unexpected devices or screen ratio.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6283.image_thumb_0A163D2B.png" alt="image" width="655" height="304" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1731.image_2860F421.png)

## Your turn !

The plugin provides for now somes basic rules. We really hope this will be completed by new rules that anyone in the community can create. Do not hesitate to add yours and create a pull request in the <a href="https://github.com/Microsoftdx/vorlonjs" target="_blank">Vorlon.js repo</a>.

> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter: <http://twitter.com/meulta>_