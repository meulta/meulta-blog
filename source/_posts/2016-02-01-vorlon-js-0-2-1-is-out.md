---
id: 91
title: Vorlon.js 0.2.1 is out !
date: 2016-02-01T14:12:08+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2016/02/01/vorlon-js-0-2-1-is-out/
permalink: /en/2016/02/01/vorlon-js-0-2-1-is-out/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2016/02/01/vorlon-js-0-2-1-is-out.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10667724"
orig_post_name:
  - vorlon js 0 2 1 is out
orig_parent_id:
  - "10667724"
orig_thread_id:
  - "902222"
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
  - "2481"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Vorlon.js 0.2.1 is out !" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2016/02/01/vorlon-js-0-2-1-is-out/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta 3 month ago, we released the 0.1 version of Vorlon.js. We added a lot of great new features such as the Unit Test, the Device Info and the Best Practices plugin. One main improvement for this version..." />
    <meta property="og:image" content="http://ekladata.com/WN5Rhx9M1LOKiQYTgbhSTuVC5gQ.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Vorlon.js 0.2.1 is out !" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2016/02/01/vorlon-js-0-2-1-is-out/" />
    <meta name="twitter:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta 3 month ago, we released the 0.1 version of Vorlon.js. We added a lot of great new features such as the Unit Test, the Device Info and the Best Practices plugin. One main improvement for this version..." />
    <meta name="twitter:image" content="http://ekladata.com/WN5Rhx9M1LOKiQYTgbhSTuVC5gQ.jpg" />
    
image: /wp-content/uploads/2016/02/1500x500.png
categories:
  - Vorlon.js
tags:
  - Accessibility
  - Debug
  - Node.js
  - Vorlon.js
---
> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter: <http://twitter.com/meulta>_ 

3 month ago, we released the [0.1 version of](http://blogs.msdn.com/b/emargraff/archive/2015/10/29/vorlon-js-0-1-0-is-out.aspx) [Vorlon.js](http://vorlonjs.io). We added a lot of great new features such as the Unit Test, the Device Info and the Best Practices plugin. One main improvement for this version was certainly the HTTP proxy which helps you debug a website using Vorlon.js without having to change its source code ([http://vorlonjs.io/documentation/#vorlon-proxy](http://vorlonjs.io/documentation/#vorlon-proxy "http://vorlonjs.io/documentation/#vorlon-proxy")).

<p align="center">
  <strong>Today we are thrilled to tell you that 0.2.1 is out !</strong>
</p>

<p align="center">
  <img src="http://ekladata.com/WN5Rhx9M1LOKiQYTgbhSTuVC5gQ.jpg" alt="Afficher l'image d'origine" width="288" height="267" />
</p>

_Note: if you (still? ;-)) don’t know what Vorlon.js is, you must_ [_read this_](https://blogs.msdn.microsoft.com/eternalcoding/2015/04/29/why-we-made-vorlon-js-and-how-to-use-it-to-debug-your-javascript-remotely/)_, or_ [_watch this_](https://channel9.msdn.com/Shows/codechat/046)_._

<p align="left">
  What makes open source projects so interesting is as much the product itself as the strong community built around it. The 0.1 version has been created by a lot of people around the world and so did the new release we are announcing in this blog post.
</p>

<p align="center">
  <strong>We really want to thank you all</strong>. Sharing and working together is what makes the web so amazing!
</p>

Amoung a lot of improvements, the 4 main new features in 0.2.1 are :

  * **Accessibility rules** added in the Best Practice Analyser (thanks to Deque and their wonderful project : aXe)
  * [Vorlon.js Desktop : a new way to install Vorlon](http://mcnextpost.com/2015/12/01/how-to-use-vorlon-js-desktop/)
  * **Node.js** process debugging !
  * We setup some [DevOps practices](http://blogs.technet.com/b/devops/archive/2016/01/12/vorlonjs-a-journey-to-devops-introducing-the-blog-post-series.aspx) to help us test and deploy our staging environments

I will go through a quick description of all the improvements made to Vorlon.js in this article. Other blog posts will come later this week about these features.

# 

# Node.js debugging: Vorlon.js server side !

We first made Vorlon.js for a specific task: **helping web developers** to debug their JavaScript, HTML and CSS code running on a **mobile**. It was first like an F12 alternative for remote debugging.

We quickly understood that it could be **more than that**. The great work made by the community brought us specialized plugins like **Angular.js inspector** or **QUnit runner**. At this time, Vorlon.js was more and more a relevant tool for web (remote) desktop debugging, bringing additionnal features to classics F12 tools.

As Vorlon.js is built on top of JavaScript, we start wondering if it could be a good idea to use it to also debug **Node.js apps**. Obviously some plugins such as DOM Explorer or Modernizr might not be relevant in this case but what about the Console or the Object Explorer? In a world where Node.js processes are running **everywhere in the cloud and on IOT objects**, remote debugging could really be helpful, right? 🙂

Guess what ? It is now possible!

All you have to do is requiring a new NPM package we created:

**npm install vorlon-node-wrapper**

Requiring it in your project:

**var vorlonWrapper = require(&#8220;vorlon-node-wrapper&#8221;);**

Starting the Vorlon for Node client by giving it your Vorlon.js instance:

**vorlonWrapper.start(serverUrl, dashboardSession, false);**

And voila! Each time you will start your node.js process, you will have remotely access to the Console, the Object Explorer, and the XHRPanel.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3414.image_thumb_62EBE3AB.png" alt="image" width="712" height="401" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4846.image_5178F222.png)

Here is the documentation for this: [http://vorlonjs.io/documentation/#debugging-nodejs-applications](http://vorlonjs.io/documentation/#debugging-nodejs-applications "http://vorlonjs.io/documentation/#debugging-nodejs-applications")

# Vorlon.js Desktop: another way to get our tool

As you can read on our [documentation web site](http://vorlonjs.io/documentation/), Vorlon can be installed in many different ways. You can install it as an **npm** package, clone our GitHub repo or even auto deploy to Microsoft Azure. In the web community these are the common ways to get new tools on your dev box. Some people don’t know or don’t want to learn about these. Some of them don’t want to mess with command lines (yep, it happens ! :)).

We want Vorlon to be accessible to the most people we can. This is why we (and more precisely [Guillaume Leborgne](https://twitter.com/gleborgne) and [Mehdi Lahlou](https://twitter.com/Mehdi_La), kudos to them!) decided to work on a standalone installer. It currently works on Mac and Windows.

Guillaume wrote a great article about this, feel free to take a look at it : [http://mcnextpost.com/2015/12/01/how-to-use-vorlon-js-desktop/](http://mcnextpost.com/2015/12/01/how-to-use-vorlon-js-desktop/ "http://mcnextpost.com/2015/12/01/how-to-use-vorlon-js-desktop/")

<img src="https://mcnextpost.files.wordpress.com/2015/12/screen.png?w=945" alt="screen.PNG" width="677" height="603" />

# Vorlon.js team went DevOps

Well. DevOps means a lot of stuff.

It is about organization, people, tools, practices. As every team on the planet, we always need to improve what we do to release better code, faster and more efficiently. None of us are full time on this project, a lot of the work is done on our free (and passionate!) time. That’s why we love to optimize what we do to be able to achieve more.

This first iteration we did on DevOps covers the basics:

  * We organized better into clear releases using Issues
  * We activated automated checks on commits and pull requests
  * We enabled automated deployment of our internal staging environment
  * We automated the creation of a ready to use Docker Vorlon.js image
  * And more !

A lot of this is using **Visual Studio Team Services** and its integration capabilities with GitHub:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5123.image_thumb_769B5DF0.png" alt="image" width="639" height="125" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7144.image_69A17DDF.png)

DevOps is about **continuous improvement.** This is why it is a work in progress. [Julien Corioland](https://twitter.com/jcorioland) did a great work on that and is sharing all of it with you in a blog posts series. It is a must read!

You can start from here: [http://blogs.technet.com/b/devops/archive/2016/01/12/vorlonjs-a-journey-to-devops-introducing-the-blog-post-series.aspx](http://blogs.technet.com/b/devops/archive/2016/01/12/vorlonjs-a-journey-to-devops-introducing-the-blog-post-series.aspx "http://blogs.technet.com/b/devops/archive/2016/01/12/vorlonjs-a-journey-to-devops-introducing-the-blog-post-series.aspx")

# What else?

We did a lot of other improvements to this release :

  * Added new accessibility rule in the best practices plugin
  * Updated Modernizr to 3.0 and integrated more rules
  * Various bug fixes
  * Added click to URI on a resource in the DOM Explorer (kudos to [Paul Fasola](https://twitter.com/paulfasola))
  * Stability improvements on the dashboard
  * Generating source map to be able to debug using Typescript files (thanks [Rami Sayar](https://twitter.com/ramisayar))
  * Merged the two gulp files to only one (really… I cannot remember why we thought 2 of them was a good idea in the first place… 😉
  * Moved samples to the **client samples** folder. (Containing now a sample for Node.js debugging)

&nbsp;

I also want to notice that [Rami](https://twitter.com/ramisayar) did a huge work porting our Web Standard analyzer to a **Grunt** and **Gulp** extension. You can now check your web code quality during your build workflow:

  * Here is the grunt task: [https://www.npmjs.com/package/grunt-webstandards](https://www.npmjs.com/package/grunt-webstandards "https://www.npmjs.com/package/grunt-webstandards")
  * Here is the gulp task: [https://www.npmjs.com/package/gulp-webstandards](https://www.npmjs.com/package/gulp-webstandards "https://www.npmjs.com/package/gulp-webstandards")
  * Here is a blog article talking about this : [http://www.sitepoint.com/three-plugins-every-gruntfile-gulpfile-needs-make-website-great/](http://www.sitepoint.com/three-plugins-every-gruntfile-gulpfile-needs-make-website-great/ "http://www.sitepoint.com/three-plugins-every-gruntfile-gulpfile-needs-make-website-great/")

&nbsp;

# What’s next ?

We have multiple plans for the next version of Vorlon.js. The main focus now is certainly the Node.js debugging capability. Right now you can connect your node process to Vorlon and debug it but we want to create more specialized plugins. We have 3 of them in mind:

  * **Node.js info** (what you required, which version, and stuff like this)
  * **Express.js** (what view are loaded, automatic logs when a route is called, etc.)
  * **Mocha** (advanced remote test monitor)

&nbsp;

[Sebastien Pertus](https://twitter.com/sebastienpertus) is also working on a plugin to help Office addin developers to debug their JavaScript code inside Vorlon. That should be released soon!

If you have other ideas for the Node.js area or for Vorlon.js in general, do not hesitate to do some [pull requests](https://github.com/MicrosoftDX/Vorlonjs/pulls) or to [add issues to our backlog](https://github.com/MicrosoftDX/Vorlonjs/issues)!

We also now have a **Slack account**. If you want to join and chat about Vorlon, feel free to contact me on twitter 😉

Happy debugging! 🙂