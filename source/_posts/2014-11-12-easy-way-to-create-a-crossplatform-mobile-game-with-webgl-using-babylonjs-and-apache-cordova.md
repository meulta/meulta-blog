---
id: 33
title: Easy way to create a crossplatform mobile game with WebGL using BabylonJS and Apache Cordova
date: 2014-11-12T14:29:00+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2014/11/12/easy-way-to-create-a-crossplatform-mobile-game-with-webgl-using-babylonjs-and-apache-cordova/
permalink: /en/2014/11/12/easy-way-to-create-a-crossplatform-mobile-game-with-webgl-using-babylonjs-and-apache-cordova/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2014/11/12/easy-way-to-create-a-crossplatform-mobile-game-with-webgl-using-babylonjs-and-apache-cordova.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10571988"
orig_parent_id:
  - "10571988"
orig_thread_id:
  - "882160"
orig_application_key:
  - emargraff
orig_post_author_id:
  - "285541"
orig_post_author_username:
  - Etienne Margraff
orig_post_author_created:
  - 'Jun  9 2010 04:06:12:000AM'
orig_is_approved:
  - "1"
orig_attachment_count:
  - "0"
orig_url_title:
  - http://blogs.msdn.com/b/emargraff/archive/2014/11/12/easy-way-to-create-a-crossplatform-mobile-game-with-webgl-using-babylonjs-and-apache-cordova.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Easy way to create a crossplatform mobile game with WebGL using BabylonJS and Apache Cordova" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2014/11/12/easy-way-to-create-a-crossplatform-mobile-game-with-webgl-using-babylonjs-and-apache-cordova/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="As David Rousset says in his blog (http://blogs.msdn.com/b/davrous/archive/2014/06/20/the-web-the-next-game-frontier.aspx), the web is the next game frontier. I totally agree with him. The web is everywhere. When you create a responsive website, you eventually get to all the connected devices in the world, with just a URL. That is why there is so much effort and work..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8765.image_thumb_565D959F.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Easy way to create a crossplatform mobile game with WebGL using BabylonJS and Apache Cordova" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2014/11/12/easy-way-to-create-a-crossplatform-mobile-game-with-webgl-using-babylonjs-and-apache-cordova/" />
    <meta name="twitter:description" content="As David Rousset says in his blog (http://blogs.msdn.com/b/davrous/archive/2014/06/20/the-web-the-next-game-frontier.aspx), the web is the next game frontier. I totally agree with him. The web is everywhere. When you create a responsive website, you eventually get to all the connected devices in the world, with just a URL. That is why there is so much effort and work..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8765.image_thumb_565D959F.png" />
    
image: /wp-content/uploads/2014/11/video-game-1332694_640.png
categories:
  - Uncategorized
tags:
  - BabylonJS
  - Cordova
  - Game
  - HTML5
  - Mobile
---
As [David Rousset](http://www.twitter.com/davrous) says in his blog (<http://blogs.msdn.com/b/davrous/archive/2014/06/20/the-web-the-next-game-frontier.aspx>), the web is [the next game frontier](http://blogs.msdn.com/b/davrous/archive/2014/03/20/next-game-frontier-2014-videos-amp-content.aspx). I totally agree with him.

<p align="center">
  <i><strong><span style="font-size: large;">The web is everywhere.</span></strong> </i>
</p>

When you create a responsive website, you eventually get to all the connected devices in the world, with just a URL. That is why there is so much effort and work going on around WebGL and all the frameworks available to help developers creating new gaming experiences on the web.

Just by giving a look at the [BabylonJS](http://babylonjs.com/) website, you can see how incredible “3D in web” can be.

[<img style="float: none; margin-left: auto; display: block; margin-right: auto; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8765.image_thumb_565D959F.png" alt="image" width="679" height="492" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3362.image_08308AD5.png)

When talking about distribution though the web may not be always the best channel. Do people have to search for your game url or run into it by chance? How can you tell the world that your game is really great on mobile and they need to test it?

Mobile has long time been a great opportunity for game developers. In this world, one did not wait for WebGL to appear to create and distribute applications and games. The application stores of each of the 3 main platforms (iOS, Android, Windows) are a really great way to do this. People go there to search and find games. You want to be there.

[<img style="float: none; margin-left: auto; display: block; margin-right: auto; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6786.image_thumb_08A11D85.png" alt="image" width="703" height="381" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0045.image_1AC538F2.png)

And that is only one of many reasons that having your game available as an application is a good strategy. When you are hosted in an application, many features are available easily: phone contacts to find friends to play with, mobile orientation, storage, push notifications, etc. Moreover, you do not need internet to be playable.

That being said, what if it could be easy to create a game playable in a full browser experience from a web URL and also as an application with enhanced features? Your game will really be available **every**where, wouldn’t it?

Well… the good news is that since a few month (and the support of WebGL on every mobile browsers), this dream finally come true!

Here is a quick video showing you the exact same code running inside an application on iOS, Android and Windows Phone.



> You can download the full sample here : [https://meulta.blob.core.windows.net/samples/BabylonJsSample.zip](https://meulta.blob.core.windows.net/samples/BabylonJsSample.zip "https://meulta.blob.core.windows.net/samples/BabylonJsSample.zip")

In this article, I will explain you how to do this in a really simple way using **Apache Cordova**, **CocoonJS** and the incredibly powerful and simple to use WebGL framework: **BabylonJS**. 🙂

> _Feel free to get in touch with me on twitter to talk about this:_ [_http://twitter.com/emargraff_](http://twitter.com/emargraff)__

> _This article is not going into detail about how to use BabylonJS to create great 3D scenes. To learn more about this, you can follow the MVA course done by [David Catuhe](http://channel9.msdn.com/Series/Introduction-to-WebGL-3D-with-HTML5-and-Babylonjs) and David Rousset_ **:** <http://channel9.msdn.com/Series/Introduction-to-WebGL-3D-with-HTML5-and-Babylonjs>****

**To be able to do this, you need to follow some easy steps. Let’s go!**

# 1. Install Cordova

The easiest way to install Cordova is to use NodeJS Package Manager (npm) that you can get from the [www.nodejs.com](http://www.nodejs.com) website. Once installed, you just have to run the following command line:

<pre class="code"><b><i>  npm install –g cordova</i></b></pre>

_Note: on iOS, you need to prefix all your commands (npm and later Cordova) with **sudo** to run it as an administrator._

# 2. Install frameworks

Cordova works in a really simple way: you put all your HTML/Javascript code inside a **www** folder and Cordova manage for you the creation of a project for each platform containing your code. On iOS and Android, this code is running inside a WebView even if the HTML code is stored inside the app and not get from an online server. On Windows (Phone and Tablet) this is a bit different as this platform is able to run HTML/Javascript as a first class language to create native apps. That is why there is no WebView on the Windows platform project generated by Cordova and why any Cordova app will be faster on Windows.

Anyway, you need to install and configure the build tools and frameworks Cordova will be using to compile for each platform:

  * [Tools for Windows](http://cordova.apache.org/docs/en/4.0.0/guide_platforms_win8_index.md.html#Windows%20Platform%20Guide)
  * [Tools for Android](http://cordova.apache.org/docs/en/4.0.0/guide_platforms_android_config.md.html#Android%20Configuration)
  * [Tools for iOS](http://cordova.apache.org/docs/en/4.0.0/guide_platforms_ios_config.md.html#iOS%20Configuration)

# 3. Create the cordova project

This is a really simple step as you only need to run the following command line:

<pre class="code"><b><i>  cordova create myproject</i></b></pre>

Where **myproject** have to be replaced with your project name.

> _We usually use a reverse domain name notation to name cordova project such as **com.mycompany.myproject.** This is not mandatory._

This command line initialize a directory containing some folders such as **www** which will contain your code and **plugins** where Cordova store the code for each plugin you add.

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7587.image_thumb_61FA434A.png" alt="image" width="437" height="349" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1854.image_395BD743.png)

> _A plugin is a Cordova extension generally used to access a specific feature on the phone. There is one for the camera, another one for accelerometer, etc._

# 4. Add the BabylonJS 3D scene

For this example, we are going to create a really simple scene containing a cube.

Open the index.html file in an HTML editor such as Visual Studio and delete all its content. From there, you can add any BabylonJS code you want. You can find great samples on the [www.babylonjs.com](http://www.babylonjs.com) website.

To create a simple 3D scene, copy the following code in you index.html file:

<p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
  <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">html</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">xmlns</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;http://www.w3.org/1999/xhtml&#8221;></span>
</p>

<p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
  <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span class="GramE"><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">head</span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
</p>

<p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span class="GramE"><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">meta</span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">http-equiv</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;Content-Type&#8221;</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">content</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;text/html; charset=utf-8&#8243;</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">/></span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span class="GramE"><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">title</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">Babylon &#8211; Basic scene</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">title</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span><!--?xml namespace=namespace prefix="o" ?-->
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span class="GramE"><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">style</span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span class="GramE"><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">html</span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">,<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">body</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>{</span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span class="GramE"><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">overflow</span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">hidden</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">width</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">100%</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">height</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">100%</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">margin</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">padding</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span>}</span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">#renderCanvas</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>{</span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">width</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">100%</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">height</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">100%</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">touch-action</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">:<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">none</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">;</span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span>}</span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">style</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">src</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;babylon.js&#8221;></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">src</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;hand.js&#8221;></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">src</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;cordova.max.js&#8221;></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">head</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">body</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">canvas</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">id</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;renderCanvas&#8221;></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">canvas</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"><</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: red;">type</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">=&#8221;text/javascript&#8221;></span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Get the canvas element from our HTML below</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>canvas = document.getElementById(</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: #a31515;">&#8220;renderCanvas&#8221;</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">);</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"> </span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Load the BABYLON 3D engine</span>
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>engine =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.Engine(canvas,<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">true</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">);</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"> </span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>cube;</span>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-</span>
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Here begins a function that we will &#8216;call&#8217; just after it&#8217;s built</span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>createScene =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">function</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>() {</span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Now create a basic Babylon Scene object</span>
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>scene =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.Scene(engine);</span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"> </span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// This creates and positions a free camera</span>
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span class="GramE"><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>camera =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.TouchCamera(</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: #a31515;">&#8220;camerarotate&#8221;</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">, <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.Vector3(0, 0, 10), scene);</span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>camera.rotation =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.Vector3(0, Math.PI, 0);</span>
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"> </span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// This attaches the camera to the canvas</span>
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>camera.attachControl(canvas,<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">false</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">);</span>
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"> </span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// This creates a light, aiming 0,1,0 &#8211; to the sky.</span>
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>light =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.HemisphericLight(</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: #a31515;">&#8220;light1&#8221;</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">,<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.Vector3(0, 1, 0), scene);</span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Dim the light a small amount</span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>light.intensity = .5;</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>cube =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.Mesh.CreateBox(</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: #a31515;">&#8220;box&#8221;</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">, 2, scene);</span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>cube.material =<span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">new</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>BABYLON.StandardMaterial(</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: #a31515;">&#8220;Mat&#8221;</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">, scene);</span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">cube.rotation.z = 100;</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>cube.rotation.y = 100;</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Register a render loop to repeatedly render the scene</span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>engine.runRenderLoop(</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">function</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>() {</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">               <span class="Apple-converted-space"> </span>scene.render();</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span>});</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Leave this function</span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">           <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">return</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>scene;</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span>}; <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// End of createScene function</span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-</span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: green;">// Now, call the createScene function that you just finished creating</span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">       <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">var</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"><span class="Apple-converted-space"> </span>scene = createScene();</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"> </span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;">   <span class="Apple-converted-space"> </span></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">script</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: black;"> </span>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">body</span><span lang="EN-US" style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
      </p>
      
      <p class="MsoNormal" style="white-space: normal; word-spacing: 0px; text-transform: none; color: #000000; font: 11pt calibri, sans-serif; margin: 0cm 0cm 0pt; letter-spacing: normal; text-indent: 0px; -webkit-text-stroke-width: 0px;">
        <span style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;"></</span><span class="GramE"><span style="font-size: 9.5pt; font-family: consolas; background: white; color: maroon;">html</span></span><span style="font-size: 9.5pt; font-family: consolas; background: white; color: blue;">></span>
      </p>
      
      <p>
        You also need to download the Babylon.js and hand.js files that are available here: <a href="https://github.com/BabylonJS/Babylon.js">https://github.com/BabylonJS/Babylon.js</a> and here: <a href="http://handjs.codeplex.com/">http://handjs.codeplex.com/</a>.
      </p>
      
      <p>
        You can test the result in a web browser, here is how this simple cube looks in IE.
      </p>
      
      <p>
        <a href="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2335.image_73D967C8.png"><img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5482.image_thumb_1C77D3D0.png" alt="image" width="568" height="395" border="0" /></a>
      </p>
      
      <h1>
        5. Add the Windows platform
      </h1>
      
      <p>
        Now that all our web code is ready and available in the<b> www</b> folder, all we have to do is add the project to deploy on each platform. This is done using Cordova command line tool.
      </p>
      
      <pre class="code"><b><i>  cordova platform add Windows</i></b></pre>
      
      <p>
        This command “simply” create a Visual Studio solution and some projects in it which are hosting the files from the <b>www</b> folder. As I said earlier in this article, the Windows project generated by Cordova take advantage of the Windows platform and generate a native html/javascript app. That is why you will not find a WebView in the Visual Studio projects.
      </p>
      
      <p>
        You can use the Microsoft tooling to build, deploy and debug the files generated by cordova but this is only mandatory for the debug part. Building and deploying can be done directly from the command line.
      </p>
      
      <p>
        For instance, building is done through this line:
      </p>
      
      <pre class="code"><b><i>  cordova build windows</i></b></pre>
      
      <p>
        The build instruction is a shortcut for 2 successive commands which are: <b>prepare</b> and <b>compile</b>. You can use them independently to respectively: update the platform generated project with any change done in the cordova project files and compile the platform.
      </p>
      
      <p>
        You can run your app on a specific platform using the <b>run</b> command. It is possible to run it in a local emulator or a physical device connecting through USB.
      </p>
      
      <p>
        This will run on the phone emulator
      </p>
      
      <pre class="code"><b><i>  cordova run windows --emulator -- --phone </i></b></pre>
      
      <p>
        This will run on a physical phone:
      </p>
      
      <pre class="code"><b><i>  cordova run windows --device -- --phone</i></b></pre>
      
      <blockquote>
        <p>
          <i>Please note the double dashes ‘&#8211;‘ which are not a typing mistake I made here but a required command in the line.</i>
        </p>
      </blockquote>
      
      <p>
        And here is the result on the Windows Phone emulator:
      </p>
      
      <p>
        <a href="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8078.image_2C1A6F92.png"><img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0160.image_thumb_22C13B0F.png" alt="image" width="275" height="504" border="0" /></a>
      </p>
      
      <h1>
        6. Going crossplatform
      </h1>
      
      <p>
        The good part is that all of these steps are working exactly the same on iOS. All you need is having a mac somewhere, copy your folder on it and run the following command:
      </p>
      
      <pre class="code"><b><i>  cordova platform add ios</i></b></pre>
      
      <p>
        Then running the <b><i>run</i></b> command for ios will deploy and run it on the emulator or the device connected.
      </p>
      
      <p>
        However, for this to work you need to configure your environment according to this documentation: <a href="http://cordova.apache.org/docs/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide">http://cordova.apache.org/docs/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide</a> and you need to be on iOS 8 or higher because the iOS webview only support WebGL since this specific version.
      </p>
      
      <p>
        On Android, this is pretty much the same story. There is a problem though : the Android webview only support WebGL from the 36.0.0.0 version which is going to be shipped with Android L and not available at the moment I am writing this article.
      </p>
      
      <p>
        So: what can you do to get a crossplatform game using WebGL? There is a really simple solution provided by <a href="https://www.ludei.com/cocoonjs/">CocoonJS.</a>
      </p>
      
      <p>
        CocoonJS is a solution to create multiplatform applications. It provides an extension to the cordova command line and give you a cordova plugin call <i>WebView+</i>. This plugin is based on Chromium and enables WebGL even if you are on a version of Android where the webview does not support it by default. In other words, CocoonJS replaces the default WebView used by Cordova by this WebView+.
      </p>
      
      <p>
        To do it, you need to install CocoonJS using the following command line:
      </p>
      
      <pre class="code"><b><i>  npm install -g cocoonjs</i></b></pre>
      
      <p>
        This install a new command line tool which is working exactly the same cordova does. To add the android platform, run this:
      </p>
      
      <pre class="code"><b><i>  Cocoonjs platform add android</i></b></pre>
      
      <p>
        Then, to force cordova to use the WebView+ instead of the classic one:
      </p>
      
      <pre class="code"><b><i>  Cocoonjs plugin add com.ludei.webview.plus</i></b></pre>
      
      <p>
        &nbsp;
      </p>
      
      <p>
        <a href="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6886.image_04768419.png"><img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5265.image_thumb_0FA29F14.png" alt="image" width="636" height="111" border="0" /></a>
      </p>
      
      <p>
        Build it, run it, and there you go: it just works! 🙂
      </p>
      
      <blockquote>
        <p>
          <i>Be aware that when you do this, the <strong>WebView+</strong> is using chrome, which cannot be used in emulators. When you add it to your project you are stuck with real device debugging. </i>
        </p>
      </blockquote>
      
      <h1>
        7. Getting the most of each platform
      </h1>
      
      <p>
        We now have a multiplatform HTML5 game that is distributed as an application and can be discovered from each application store. That is great but we can do more.
      </p>
      
      <p>
        As I told you, the second Cordova goal is to make us capable of easily using the phone features from Javascript in a uniform way across platforms. This is done through plugins. You can find the whole plugin list on the Apache Cordova website: <a href="http://cordova.apache.org/docs/en/3.6.0/cordova_plugins_pluginapis.md.html#Plugin%20APIs">http://cordova.apache.org/docs/en/3.6.0/cordova_plugins_pluginapis.md.html#Plugin%20APIs</a>
      </p>
      
      <p>
        I am pretty sure you will find a lot of great ideas on what plugins to use and be creative about it 🙂
      </p>
      
      <h1>
        8. Working with great tools : Visual Studio 2015
      </h1>
      
      <p>
        This is not new that <strong>Microsoft</strong> is deeply involved in the Open Source community and working a lot with open source projets. With Visual Studio 2015, a new step is being taken mainly because this important things:
      </p>
      
      <ul>
        <li>
          Visual Studio 2015 is going to be FREE for students and open source developers (yes <b>FREE</b>).
        </li>
        <li>
          Visual Studio 2015 comes by default with Cordova tooling for create, improving and debugging cordova projects.
        </li>
        <li>
          Visual Studio 2015 comes with a really really really fast android emulator you can use to debug your android apps (created using Xamarin, C++ or Cordova technologies)
        </li>
        <li>
          Cordova tooling will help you get plug and play iOS debugging through network
        </li>
      </ul>
      
      <p>
        &nbsp;
      </p>
      
      <p>
        A real advantage is also that it is going to install all the tools you need to compile on Android as you can see on this screenshot from the installer.
      </p>
      
      <p>
        <a href="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0714.Capture_593862AB.png"><img style="display: inline; border-width: 0px;" title="Capture" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7838.Capture_thumb_68715C29.png" alt="Capture" width="412" height="578" border="0" /></a>
      </p>
      
      <p>
        Why am I talking about this here? Obviously because this can be a great tool for you to create crossplatform WebGL games. Run it, attach Visual Studio 2015 to it and let the debug begin 🙂
      </p>
      
      <p>
        You can learn more about this here:
      </p>
      
      <ul>
        <li>
          Visual Studio tools for Apache Cordova : <a href="http://www.visualstudio.com/en-us/explore/cordova-vs.aspx">http://www.visualstudio.com/en-us/explore/cordova-vs.aspx</a>
        </li>
        <li>
          Android emulator : <a href="http://channel9.msdn.com/events/Visual-Studio/Connect-event-2014/516">http://channel9.msdn.com/events/Visual-Studio/Connect-event-2014/516</a>
        </li>
        <li>
          More information about Visual Studio 2015 and the open source world : <a href="http://www.hanselman.com/blog/AnnouncingNET2015NETasOpenSourceNETonMacandLinuxandVisualStudioCommunity.aspx">http://www.hanselman.com/blog/AnnouncingNET2015NETasOpenSourceNETonMacandLinuxandVisualStudioCommunity.aspx</a>
        </li>
      </ul>
      
      <h1>
        Conclusion
      </h1>
      
      <p>
        You just get through really simple steps to create you app using web languages. In a near future I really hope that every platform is going to understand HTML and Javascript as first class languages to create apps. Windows does it in Windows RT apps since a lot a time and Windows Phone is there since the last version (8.1). That could be a great advance for the future of mobile apps and games.
      </p>
      
      <blockquote>
        <p>
          <i>Do not hesitate to share your thoughts and tests on the comments or on twitter! (<a href="http://twitter.com/emargraff">@emargraff</a>)</i>
        </p>
      </blockquote>