---
id: 71
title: How to create a Vorlon.js plugin
date: 2015-06-01T00:00:00+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/06/01/how-to-create-a-vorlon-js-plugin/
permalink: /en/2015/06/01/how-to-create-a-vorlon-js-plugin/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/05/29/how-to-create-a-vorlon-js-plugin.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10618218"
orig_post_name:
  - how to create a vorlon js plugin
orig_parent_id:
  - "10618218"
orig_thread_id:
  - "892411"
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
  - "2751"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to create a Vorlon.js plugin" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/06/01/how-to-create-a-vorlon-js-plugin/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta A few weeks ago we released Vorlon.js during the keynote of the //BUILD conference. Vorlon.js is a tool which helps you debug your website. You can see it as a remote F12. It is mainly composed of..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7651.clip_image002_thumb_4D4D0447.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to create a Vorlon.js plugin" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/06/01/how-to-create-a-vorlon-js-plugin/" />
    <meta name="twitter:description" content="If you have any question about this article or Vorlon.js, feel free to contact me on twitter: http://twitter.com/meulta A few weeks ago we released Vorlon.js during the keynote of the //BUILD conference. Vorlon.js is a tool which helps you debug your website. You can see it as a remote F12. It is mainly composed of..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7651.clip_image002_thumb_4D4D0447.jpg" />
    
image: /wp-content/uploads/2015/06/tools-1083796_640.jpg
categories:
  - Vorlon.js
tags:
  - HTML5
  - Mobile
  - Vorlon.js
---
> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)

A few weeks ago we released [Vorlon.js](http://vorlonjs.io/) during the keynote of the //BUILD conference.



**Vorlon.js** is a tool which helps you debug your website. You can see it as a remote F12. It is mainly composed of a dashboard which displays data coming from your site.

To make it working, you only have to reference a script in you site code.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7651.clip_image002_thumb_4D4D0447.jpg" alt="clip_image002" width="622" height="504" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5287.clip_image002_4CD2F07A.jpg)

We ([Pierre Lagarde](http://twitter.com/pierlag), [David Catuhe](http://twitter.com/deltakosh), [David Rousset](http://twitter.com/davrous) and [myself](http://twitter.com/meulta)) built this primarily to help web developers debugging their websites on **mobile devices**. Of course, proprietary solutions already exist like chrome developer tools to debug chrome mobile, or the equivalent for safari and Visual Studio for Internet Explorer or even Weinre: but none of these is really technology and platform agnostic.

**This is the gap we wanted to fill with Vorlon.js.**

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image004" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7536.clip_image004_thumb_0080540C.png" alt="clip_image004" width="502" height="316" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3162.clip_image004_600FDED6.png)

You can install Vorlon.js either from **npm** or by cloning the **GitHub** repository and using gulp to make it ready to use.

You can find more information about that on our website (<http://vorlonjs.io>) or on the blog article my friend David wrote: <http://blogs.msdn.com/b/eternalcoding/archive/2015/04/30/why-we-made-vorlon-js-and-how-to-use-it-to-debug-your-javascript-remotely.aspx>

To create a plugin for Vorlon, you can use TypeScript or directly JavaScript.

I will give you the JavaScript and TypeScript code so you can read it in your favorite language 🙂

### What we are going to create

In this article I chose to create a plugin which will get device information. This is based on the website http://mydevice.io/ created by [Raphaël Goetter](https://twitter.com/goetter). To keep it simple I will only get the data from the **Sizes** section of the **My Screen** category.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image006" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2330.clip_image006_thumb_339791AE.jpg" alt="clip_image006" width="579" height="456" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2526.clip_image006_38E3E7AE.jpg)

With this plugin activated, the vorlon.js Dashboard will display size information coming from the client.

Before going more into details, have a look at this quick video which show you what we will create.



In this video, I do a demo on a desktop browser but this obviously also works on a mobile phone or tablet.

### First step: writing your code outside of Vorlon.js

A vorlon.js plugin is nothing more than HTML, CSS and JavaScript code. Your plugin is getting data from the client and sending it to the server to display it on the Dashboard.

This means that you can first do it without Vorlon.js, write everything on a simple web project and then include it in the Vorlon.js plugin architecture.

Our plugin will get some information related to the client size and display it on an HTML list. It will also refresh the data when resizing the browser. You can see the full sample running here: <http://meultasamples.azurewebsites.net/vorlonpluginsample/control.html> (it is not pretty, but does the job! ;-)).

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image008" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7823.clip_image008_thumb_406FBAC7.jpg" alt="clip_image008" width="353" height="222" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5621.clip_image008_782274F7.jpg)

The HTML code is pretty light:

<div id="tabset1" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one1">HTML</a>
    </li>
  </ul>
  
  <div id="one1" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      <span style="color: #0000ff;"><</span><span style="color: #800000;">!DOCTYPE</span> <span style="color: #ff0000;">html</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">html</span> <span style="color: #ff0000;">xmlns</span><span style="color: #0000ff;">=&#8221;http://www.w3.org/1999/xhtml&#8221;></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">head</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">title</span><span style="color: #0000ff;">></</span><span style="color: #800000;">title</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">link</span> <span style="color: #ff0000;">href</span><span style="color: #0000ff;">=&#8221;control.css&#8221;</span> <span style="color: #ff0000;">rel</span><span style="color: #0000ff;">=&#8221;stylesheet&#8221;</span> <span style="color: #0000ff;">/></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">script</span> <span style="color: #ff0000;">src</span><span style="color: #0000ff;">=&#8221;vorlon.deviceinfo.js&#8221;></</span><span style="color: #800000;">script</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"></</span><span style="color: #800000;">head</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">body</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">div</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;deviceinfo&#8221;</span> <span style="color: #ff0000;">class</span><span style="color: #0000ff;">=&#8221;deviceinfo-container&#8221;></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">h2</span><span style="color: #0000ff;">></span>My Screen<span style="color: #0000ff;"></</span><span style="color: #800000;">h2</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">ul</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>CSS device-width: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;devicewidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>CSS device-height: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;deviceheight&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS screen.width: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;screenwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS window.innerWidth: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;windowinnerwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS body.clientWidth: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;bodyclientwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS screen.availWidth: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;screenavailwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"></</span><span style="color: #800000;">ul</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"></</span><span style="color: #800000;">div</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"></</span><span style="color: #800000;">body</span><span style="color: #0000ff;">></span><br /> <span style="color: #0000ff;"></</span><span style="color: #800000;">html</span><span style="color: #0000ff;">></span>
    </div>
  </div>
</div>

It is using the following control.css file:

<div id="tabset2" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one2">CSS</a>
    </li>
  </ul>
  
  <div id="one2" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      <p>
        <span style="color: #800000;">.deviceinfo-container</span> {<br /> <span style="color: #ff0000;">font-family</span>: <span style="color: #0000ff;">&#8220;Verdana&#8221;</span>, <span style="color: #0000ff;">&#8220;Comic Sans MS&#8221;</span>;<br /> }
      </p>
      
      <p>
        <span style="color: #800000;">.deviceinfo-container</span> <span style="color: #800000;">h2</span> {<br /> <span style="color: #ff0000;">font-weight</span>: <span style="color: #0000ff;">normal</span>;<br /> }
      </p>
      
      <p>
        <span style="color: #800000;">.deviceinfo-container</span> <span style="color: #800000;">ul</span> <span style="color: #800000;">li</span> {<br /> <span style="color: #ff0000;">font-weight</span>: <span style="color: #0000ff;">bold</span>;<br /> }
      </p>
      
      <p>
        <span style="color: #800000;">.deviceinfo-container</span> <span style="color: #800000;">ul</span> <span style="color: #800000;">span</span> {<br /> <span style="color: #ff0000;">font-weight</span>: <span style="color: #0000ff;">normal</span>;<br /> }
      </p>
    </div>
  </div>
</div>

And the JavaScript code gets the data once the page is loaded and each time the window is resized and updates the list:

<div id="tabset3" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one3">JavaScript</a>
    </li>
  </ul>
  
  <div id="one3" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      <p>
        (<span style="color: #0000ff;">function</span>(){<br /> <span style="color: #0000ff;">var</span> compute = <span style="color: #0000ff;">function</span>() {<br /> document.getElementById(<span style="color: #a31515;">&#8216;devicewidth&#8217;</span>).innerText = document.documentElement.clientWidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;<br /> document.getElementById(<span style="color: #a31515;">&#8216;deviceheight&#8217;</span>).innerText = document.documentElement.clientHeight + <span style="color: #a31515;">&#8216;px&#8217;</span>;<br /> document.getElementById(<span style="color: #a31515;">&#8216;screenwidth&#8217;</span>).innerText =  screen.width + <span style="color: #a31515;">&#8216;px&#8217;</span>;;<br /> document.getElementById(<span style="color: #a31515;">&#8216;windowinnerwidth&#8217;</span>).innerText = window.innerWidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;<br /> document.getElementById(<span style="color: #a31515;">&#8216;bodyclientwidth&#8217;</span>).innerText = document.body.clientWidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;<br /> document.getElementById(<span style="color: #a31515;">&#8216;screenavailwidth&#8217;</span>).innerText = screen.availWidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;<br /> };
      </p>
      
      <p>
        window.onresize = <span style="color: #0000ff;">function</span>(event) {<br /> compute();<br /> };
      </p>
      
      <p>
        document.addEventListener(<span style="color: #a31515;">&#8220;DOMContentLoaded&#8221;</span>, compute);
      </p>
      
      <p>
        })();
      </p>
    </div>
  </div>
</div>

So, until now we are only writing simple classic web code 🙂

Let’s now have a look at how to transform that into a Vorlon.js plugin!

### Create the basic JavaScript/TypeScript code for the plugin

In Vorlon.js, a plugin is composed of 2 JavaScript classes. The minimum code contains a **constructor** and the **getID** function.

The first one is the Client side code which inherits the ClientPlugin class. Its name should end by _.client.js/ts_:

<div id="tabset4" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one4">JavaScript</a>
    </li>
    <li>
      <a href="#two4">TypeScript</a>
    </li>
  </ul>
  
  <div id="one4" class="tabpane activePane">
    <pre style="font-family: consolas; background: white; color: black;"><span style="color: blue;">var</span> __extends = <span style="color: blue;">this</span>.__extends || <span style="color: blue;">function</span> (d, b) 
{     
    <span style="color: blue;">for</span> (<span style="color: blue;">var</span> p <span style="color: blue;">in</span> b) 
        <span style="color: blue;">if</span> (b.hasOwnProperty(p)) d[p] = b[p];
     <span style="color: blue;">function</span> __() { <span style="color: blue;">this</span>.constructor = d; }
     __.prototype = b.prototype;
     d.prototype = <span style="color: blue;">new</span> __();
};

<span style="color: blue;">var</span> VORLON;

(<span style="color: blue;">function</span> (VORLON) {
     <span style="color: blue;">var</span> MyDeviceInfoClient = (<span style="color: blue;">function</span> (_super) {
         __extends(MyDeviceInfoClient, _super);
         <span style="color: blue;">function</span> MyDeviceInfoClient() {
             _super.call(<span style="color: blue;">this</span>, <span style="color: #a31515;">"mydeviceinfo"</span>);
             <span style="color: blue;">this</span>._ready = <span style="color: blue;">true</span>;
         }
         MyDeviceInfoClient.prototype.getID = <span style="color: blue;">function</span> () {
             <span style="color: blue;">return</span> <span style="color: #a31515;">"MYDEVICEINFO"</span>;
         };
         <span style="color: blue;">return</span> MyDeviceInfoClient;
     })(VORLON.ClientPlugin);
     VORLON.MyDeviceInfoClient = MyDeviceInfoClient;
     <span style="color: green;">//Register the plugin with vorlon core</span>
     VORLON.Core.RegisterClientPlugin(<span style="color: blue;">new</span> MyDeviceInfoClient());
})(VORLON || (VORLON = {}));</pre>
  </div>
  
  <div id="two4" class="tabpane">
    <pre style="font-family: consolas; background: white; color: black;"><span style="color: blue;">module</span>
 <span style="color: #2b91af;">VORLON</span> {
    <span style="color: blue;">export</span> <span style="color: blue;">class</span> <span style="color: #2b91af;">MyDeviceInfoClient</span> <span style="color: blue;">extends</span> ClientPlugin {         <span style="color: blue;">constructor</span>() {
             <span style="color: blue;">super</span>(<span style="color: #a31515;">"mydeviceinfo"</span>);
             <span style="color: blue;">this</span>._ready = <span style="color: blue;">true</span>;
         }
         <span style="color: blue;">public</span> getID(): <span style="color: blue;">string</span> {
             <span style="color: blue;">return</span> <span style="color: #a31515;">"MYDEVICEINFO"</span>;
         }
     }
             <span style="color: green;">//Register the plugin with vorlon core</span>
     Core.RegisterClientPlugin(<span style="color: blue;">new</span> <span style="color: #2b91af;">MyDeviceInfoClient</span>());
}</pre>
  </div>
</div>

The second one is the Dashboard side code and inherits from the DashboardPlugin class. Its name should finish by _.dashboard.ts/js_:

<div id="tabset42" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one42">JavaScript</a>
    </li>
    <li>
      <a href="#two42">TypeScript</a>
    </li>
  </ul>
  
  <div id="one42" class="tabpane activePane">
    <pre style="font-family: consolas; background: white; color: black;"><span style="color: blue;">var</span> __extends = <span style="color: blue;">this</span>.__extends || <span style="color: blue;">function</span> (d, b) {
     <span style="color: blue;">for</span> (<span style="color: blue;">var</span> p <span style="color: blue;">in</span> b) <span style="color: blue;">if</span> (b.hasOwnProperty(p)) d[p] = b[p];
     <span style="color: blue;">function</span> __() { <span style="color: blue;">this</span>.constructor = d; }
     __.prototype = b.prototype;
     d.prototype = <span style="color: blue;">new</span> __();
};
<span style="color: blue;">var</span> VORLON;
(<span style="color: blue;">function</span> (VORLON) {
     <span style="color: blue;">var</span> MyDeviceInfoDashboard = (<span style="color: blue;">function</span> (_super) {
         __extends(MyDeviceInfoDashboard, _super);
         <span style="color: blue;">function</span> MyDeviceInfoDashboard() {
             _super.call(<span style="color: blue;">this</span>, <span style="color: #a31515;">"mydeviceinfo"</span>, <span style="color: #a31515;">"control.html"</span>, <span style="color: #a31515;">"control.css"</span>);
             <span style="color: blue;">this</span>._ready = <span style="color: blue;">true</span>;
         }
         MyDeviceInfoDashboard.prototype.getID = <span style="color: blue;">function</span> () {
             <span style="color: blue;">return</span> <span style="color: #a31515;">"MYDEVICEINFO"</span>;
         };
         <span style="color: blue;">return</span> MyDeviceInfoDashboard;
     })(VORLON.DashboardPlugin);
     VORLON.MyDeviceInfoDashboard = MyDeviceInfoDashboard;
     <span style="color: green;">//Register the plugin with vorlon core</span>
     VORLON.Core.RegisterDashboardPlugin(<span style="color: blue;">new</span> MyDeviceInfoDashboard());
})(VORLON || (VORLON = {}));</pre>
  </div>
  
  <div id="two42" class="tabpane">
    <pre style="font-family: consolas; background: white; color: black;"><span style="color: blue;">module</span> <span style="color: #2b91af;">VORLON</span> {
     <span style="color: blue;">export</span> <span style="color: blue;">class</span> <span style="color: #2b91af;">MyDeviceInfoDashboard</span> <span style="color: blue;">extends</span> DashboardPlugin {
         <span style="color: blue;">constructor</span>() {
             <span style="color: blue;">super</span>(<span style="color: #a31515;">"mydeviceinfo"</span>, <span style="color: #a31515;">"control.html"</span>, <span style="color: #a31515;">"control.css"</span>);
             <span style="color: blue;">this</span>._ready = <span style="color: blue;">true</span>;
         }         <span style="color: blue;">public</span> getID(): <span style="color: blue;">string</span> {
             <span style="color: blue;">return</span> <span style="color: #a31515;">"MYDEVICEINFO"</span>;
         }
     }
     <span style="color: green;">//Register the plugin with vorlon core</span>
     Core.RegisterDashboardPlugin(<span style="color: blue;">new</span> <span style="color: #2b91af;">MyDeviceInfoDashboard</span>());
}</pre>
  </div>
</div>

The ID is simply a string which you can choose. You will need it when you will add your plugin to the dashboard.

The constructor calls the **super** function and gives it its name. In the Dashboard side class, you also have the control.html and control.css files. This is a prerequisite for it to know these files and load them when necessary.

The last line of code is registering the plugin to the list managed by the Core (either for the Dasbhoard or the Client side of the plugin). The Core role is to handle all the communication and data exchange between the client and the dashboard.

### Rendering on the dashboard

Each time it is loading a plugin, the dashboard creates a new tab in its right pane. This is a space for your plugin to render.

The layout part for a Vorlon.js plugin is contained in an HTML file. In the sample we are going to create, it is called control.html which is a convention in Vorlon.js plugins. It is not displayed by default, you have to manage it in you plugin code. This is done using **_insertHtmlContentAsync** and generally in the **startDashboardSide** function.

**startDashboardSide** is called when the dashboard is instantiating your plugin on the server side. It only has one parameter which is the HTML div where you can render your control. Basically, it is the div that is displayed on your plugin tab.

**_insertHtmlContentAsync** is a helper that loads asynchronously all the files you gave during the plugin construction. The first argument is the render div and the second is a callback function giving you the loaded div once everything is done.

On the Dashboard side plugin class, add the following code:

<div id="tabset5" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one5">JavaScript</a>
    </li>
    <li>
      <a href="#two5">TypeScript</a>
    </li>
  </ul>
  
  <div id="one5" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      MyDeviceInfoDashboard.prototype.startDashboardSide = <span style="color: #0000ff;">function</span> (div) {
    </div>
  </div>
</div>

<span style="color: #0000ff;">if</span> (div === <span style="color: #0000ff;">void</span> 0) { div = <span style="color: #0000ff;">null</span>; }

<span style="color: #0000ff;">this</span>._insertHtmlContentAsync(div, <span style="color: #0000ff;">function</span> (filledDiv) {

<span style="color: #008000;">//load data</span>

});

};

<div id="two5" class="tabpane">
  <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
    <span style="color: #0000ff;">public</span> startDashboardSide(div: HTMLDivElement = <span style="color: #0000ff;">null</span>): <span style="color: #0000ff;">void</span> {
  </div>
</div>

<span style="color: #0000ff;">this</span>._insertHtmlContentAsync(div, (filledDiv) => {

<span style="color: #008000;">//load data</span>

})

}

On the control.html part, you only have to remove the JavaScript reference which results in the following code:

<div id="tabset6" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one6">HTML</a>
    </li>
  </ul>
  
  <div id="one6" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      <span style="color: #0000ff;"><</span><span style="color: #800000;">!DOCTYPE</span> <span style="color: #ff0000;">html</span><span style="color: #0000ff;">></span>
    </div>
  </div>
</div>

<span style="color: #0000ff;"><</span><span style="color: #800000;">html</span> <span style="color: #ff0000;">xmlns</span><span style="color: #0000ff;">=&#8221;http://www.w3.org/1999/xhtml&#8221;></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">head</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">title</span><span style="color: #0000ff;">></</span><span style="color: #800000;">title</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">link</span> <span style="color: #ff0000;">href</span><span style="color: #0000ff;">=&#8221;control.css&#8221;</span> <span style="color: #ff0000;">rel</span><span style="color: #0000ff;">=&#8221;stylesheet&#8221;</span> <span style="color: #0000ff;">/></span>

<span style="color: #0000ff;"></</span><span style="color: #800000;">head</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">body</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">div</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;mydeviceinfocontainer&#8221;</span> <span style="color: #ff0000;">class</span><span style="color: #0000ff;">=&#8221;deviceinfo-container&#8221;></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">h2</span><span style="color: #0000ff;">></span>My Screen<span style="color: #0000ff;"></</span><span style="color: #800000;">h2</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">ul</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>CSS device-width: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;devicewidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>CSS device-height: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;deviceheight&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS screen.width: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;screenwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS window.innerWidth: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;windowinnerwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS body.clientWidth: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;bodyclientwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"><</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>JS screen.availWidth: <span style="color: #0000ff;"><</span><span style="color: #800000;">span</span> <span style="color: #ff0000;">id</span><span style="color: #0000ff;">=&#8221;screenavailwidth&#8221;></</span><span style="color: #800000;">span</span><span style="color: #0000ff;">></</span><span style="color: #800000;">li</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"></</span><span style="color: #800000;">ul</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"></</span><span style="color: #800000;">div</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"></</span><span style="color: #800000;">body</span><span style="color: #0000ff;">></span>

<span style="color: #0000ff;"></</span><span style="color: #800000;">html</span><span style="color: #0000ff;">></span>

### Sending Data from the client to the plugin

So, now that you are rendering your control template in the dashboard you need to send it the data from the client. On the initial code it was done on the same page. Now you need to package everything and send it.

All the communication process is handle for you. You only have to create an object with data in it and call the correct function. It is a helper available in **Core.Messenger** named **sendRealTimeMessage**.

In the Client side plugin class we add a custom function named sendClientData. It will get all the current size information and send it.

<div id="tabset61" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one61">JavaScript</a>
    </li>
    <li>
      <a href="#two61">TypeScript</a>
    </li>
  </ul>
  
  <div id="one61" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      MyDeviceInfoClient.prototype.sendClientData = <span style="color: #0000ff;">function</span> () {
    </div>
  </div>
</div>

<span style="color: #0000ff;">var</span> data = {

<span style="color: #a31515;">&#8220;devicewidth&#8221;</span>: document.documentElement.clientWidth,

<span style="color: #a31515;">&#8220;deviceheight&#8221;</span>: document.documentElement.clientHeight,

<span style="color: #a31515;">&#8220;screenwidth&#8221;</span>: screen.width,

<span style="color: #a31515;">&#8220;windowinnerwidth&#8221;</span>: window.innerWidth,

<span style="color: #a31515;">&#8220;bodyclientwidth&#8221;</span>: document.body.clientWidth,

<span style="color: #a31515;">&#8220;screenavailwidth&#8221;</span>: screen.availWidth

};

VORLON.Core.Messenger.sendRealtimeMessage(<span style="color: #0000ff;">this</span>.getID(), data, 0 <span style="color: #008000;">/* Client */</span>);

};

<div id="two61" class="tabpane">
  <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
    <span style="color: #0000ff;">public</span> sendClientData(): <span style="color: #0000ff;">void</span> {
  </div>
</div>

<span style="color: #0000ff;">var</span> data = {

<span style="color: #a31515;">&#8220;devicewidth&#8221;</span> : document.documentElement.clientWidth,

<span style="color: #a31515;">&#8220;deviceheight&#8221;</span> : document.documentElement.clientHeight,

<span style="color: #a31515;">&#8220;screenwidth&#8221;</span> :  screen.width,

<span style="color: #a31515;">&#8220;windowinnerwidth&#8221;</span> : window.innerWidth,

<span style="color: #a31515;">&#8220;bodyclientwidth&#8221;</span> : document.body.clientWidth,

<span style="color: #a31515;">&#8220;screenavailwidth&#8221;</span> : screen.availWidth

};
  
Core.Messenger.sendRealtimeMessage(<span style="color: #0000ff;">this</span>.getID(), data, RuntimeSide.Client);

}

sendRealtimeMessage have 3 mandatory parameters :

  * The plugin ID (which is the string you return on the getID function)
  * The object you want to send (here containing the sizes information)
  * The tenant were the request comes from. (Client or Dashboard)

This function needs to be called each time the dashboard asks for it (when the user switch to this client for instance) and each time the browser size changes.

Still in the Client side plugin class, we add the **startClientSide** function which will be called at client initialization to register to the window.onresize event:

<div id="tabset7" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one7">JavaScript</a>
    </li>
    <li>
      <a href="#two7">TypeScript</a>
    </li>
  </ul>
  
  <div id="one7" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      MyDeviceInfoClient.prototype.startClientSide = <span style="color: #0000ff;">function</span> () {
    </div>
  </div>
</div>

<span style="color: #0000ff;">var</span> that = <span style="color: #0000ff;">this</span>;

window.onresize = <span style="color: #0000ff;">function</span> (event) {

that.sendClientData();

};

};

<div id="two7" class="tabpane">
  <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
    <span style="color: #0000ff;">public</span> startClientSide(): <span style="color: #0000ff;">void</span> {
  </div>
</div>

<span style="color: #0000ff;">var</span> that = <span style="color: #0000ff;">this</span>;

window.onresize = (event) => {

that.sendClientData();

};

}

Each time the user changes the size of the browser, this code will send the new information to the dashboard.

And finally we need to add the **refresh** function. It will be called each time the dashboard need the current information from the client.

<div id="tabset8" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one8">JavaScript</a>
    </li>
    <li>
      <a href="#two8">TypeScript</a>
    </li>
  </ul>
  
  <div id="one8" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      MyDeviceInfoClient.prototype.refresh = <span style="color: #0000ff;">function</span> () {
    </div>
  </div>
</div>

<span style="color: #0000ff;">this</span>.sendClientData();

};

<div id="two8" class="tabpane">
  <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
    <span style="color: #0000ff;">public</span> refresh(): <span style="color: #0000ff;">void</span> {
  </div>
</div>

<span style="color: #0000ff;">this</span>.sendClientData();

}

And that is all ! 🙂

### Displaying data on the dashboard

Now that the data are sent from the client to the dashboard, you still need to handle them on the other side.

To do this, you can use the **onRealtimeMessageReceivedFromClientSide** function. It is called each time the client send a message through the Core.Messenger. It only have 1 parameter in which you get the object that you sent.

In this sample, we only have to use each value and set the correct DOM element to update the list with the new values.

The following code obviously goes on the Dashboard plugin side classe.

<div id="tabset9" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one9">JavaScript</a>
    </li>
    <li>
      <a href="#two9">TypeScript</a>
    </li>
  </ul>
  
  <div id="one9" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      MyDeviceInfoDashboard.prototype.onRealtimeMessageReceivedFromClientSide = <span style="color: #0000ff;">function</span> (receivedObject) {
    </div>
  </div>
</div>

document.getElementById(<span style="color: #a31515;">&#8216;devicewidth&#8217;</span>).innerText = receivedObject.devicewidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;deviceheight&#8217;</span>).innerText = receivedObject.deviceheight + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;screenwidth&#8217;</span>).innerText = receivedObject.screenwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

;

document.getElementById(<span style="color: #a31515;">&#8216;windowinnerwidth&#8217;</span>).innerText = receivedObject.windowinnerwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;bodyclientwidth&#8217;</span>).innerText = receivedObject.bodyclientwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;screenavailwidth&#8217;</span>).innerText = receivedObject.screenavailwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

};

<div id="two9" class="tabpane">
  <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
    <span style="color: #0000ff;">public</span> onRealtimeMessageReceivedFromClientSide(receivedObject: <span style="color: #0000ff;">any</span>): <span style="color: #0000ff;">void</span> {
  </div>
</div>

document.getElementById(<span style="color: #a31515;">&#8216;devicewidth&#8217;</span>).innerText = receivedObject.devicewidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;deviceheight&#8217;</span>).innerText = receivedObject.deviceheight + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;screenwidth&#8217;</span>).innerText =  receivedObject.screenwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;;

document.getElementById(<span style="color: #a31515;">&#8216;windowinnerwidth&#8217;</span>).innerText = receivedObject.windowinnerwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;bodyclientwidth&#8217;</span>).innerText = receivedObject.bodyclientwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

document.getElementById(<span style="color: #a31515;">&#8216;screenavailwidth&#8217;</span>).innerText = receivedObject.screenavailwidth + <span style="color: #a31515;">&#8216;px&#8217;</span>;

}

### Let’s test this!

To be able to test this plugin, you need to go through some simples steps.

**Compile and minify**

If you chose TypeScript you will need to use a tool such as the TypeScript compiler available on **npm** or integrate yourself in the gulp process by modifying the gulpfile.js available in the /Plugins folder.

After the compilation from TypeScript to JavaScript is done you need to minify your JS file. It is important that you use this convention:

  * vorlon.yourPluginName.client.js (for the maximized version)
  * vorlon.yourPluginName.client.min.js (for the minified version)
  * vorlon.yourPluginName.dashboard.js (for the maximize²d version)
  * vorlon.yourPluginName.dashboard.min.js (for the minified version)

**Copy everthing in the server**

The second step is to copy all your files in the /Server/public/vorlon/plugins folder. There you have to create a folder using your plugin name and put everything under it. This include your html, css and js files.

Here is how it is done for the plugin we are creating in this article:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image010" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7506.clip_image010_thumb_27BCDD80.jpg" alt="clip_image010" width="347" height="202" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6560.clip_image010_51311EC0.jpg)

**Add your plugin to the catalog.json file**

The next step is to register your plugin in the server. To do this, add a line in the Server/config.json file:

<div id="tabset10" class="tabset">
  <ul class="tabnavs">
    <li>
      <a class="activeTab" href="#one10">JSON</a>
    </li>
  </ul>
  
  <div id="one10" class="tabpane activePane">
    <div style="overflow: auto; white-space: nowrap; color: #000000; background-color: #ffffff; padding: 2px 5px 2px 5px;">
      <p>
        {
      </p>
      
      <p>
        <span style="color: #2e75b6;">&#8220;IncludeSocketIO&#8221;</span>: <span style="color: #0000ff;">true</span>,
      </p>
    </div>
  </div>
</div>

<span style="color: #2e75b6;">&#8220;plugins&#8221;</span>: [

{ <span style="color: #2e75b6;">&#8220;id&#8221;</span>: <span style="color: #a31515;">&#8220;CONSOLE&#8221;</span>, <span style="color: #2e75b6;">&#8220;name&#8221;</span>: <span style="color: #a31515;">&#8220;Interactive Console&#8221;</span>, <span style="color: #2e75b6;">&#8220;panel&#8221;</span>: <span style="color: #a31515;">&#8220;bottom&#8221;</span>, <span style="color: #2e75b6;">&#8220;foldername&#8221;</span> : <span style="color: #a31515;">&#8220;interactiveConsole&#8221;}</span>,

{ <span style="color: #2e75b6;">&#8220;id&#8221;</span>: <span style="color: #a31515;">&#8220;DOM&#8221;</span>, <span style="color: #2e75b6;">&#8220;name&#8221;</span>: <span style="color: #a31515;">&#8220;Dom Explorer&#8221;</span>, <span style="color: #2e75b6;">&#8220;panel&#8221;</span>: <span style="color: #a31515;">&#8220;top&#8221;</span>, <span style="color: #2e75b6;">&#8220;foldername&#8221;</span> : <span style="color: #a31515;">&#8220;domExplorer&#8221;</span> },

{ <span style="color: #2e75b6;">&#8220;id&#8221;</span>: <span style="color: #a31515;">&#8220;MODERNIZR&#8221;</span>, <span style="color: #2e75b6;">&#8220;name&#8221;</span>: <span style="color: #a31515;">&#8220;Modernizr&#8221;</span>,<span style="color: #2e75b6;">&#8220;panel&#8221;</span>: <span style="color: #a31515;">&#8220;bottom&#8221;</span>, <span style="color: #2e75b6;">&#8220;foldername&#8221;</span> : <span style="color: #a31515;">&#8220;modernizrReport&#8221;</span> },

{ <span style="color: #2e75b6;">&#8220;id&#8221;</span> : <span style="color: #a31515;">&#8220;OBJEXPLORER&#8221;</span>, <span style="color: #2e75b6;">&#8220;name&#8221;</span> : <span style="color: #a31515;">&#8220;Obj. Explorer&#8221;</span>,<span style="color: #2e75b6;">&#8220;panel&#8221;</span>: <span style="color: #a31515;">&#8220;top&#8221;</span>, <span style="color: #2e75b6;">&#8220;foldername&#8221;</span> : <span style="color: #a31515;">&#8220;objectExplorer&#8221;</span> },

{ <span style="color: #2e75b6;">&#8220;id&#8221;</span> : <span style="color: #a31515;">&#8220;MYDEVICEINFO&#8221;</span>, <span style="color: #2e75b6;">&#8220;name&#8221;</span> : <span style="color: #a31515;">&#8220;My Device Info&#8221;</span>,<span style="color: #2e75b6;">&#8220;panel&#8221;</span>: <span style="color: #a31515;">&#8220;top&#8221;</span>, <span style="color: #2e75b6;">&#8220;foldername&#8221;</span> : <span style="color: #a31515;">&#8220;mydeviceinfo&#8221;</span> }

]

}

You can find more information about this here: <http://vorlonjs.io/documentation/#vorlonjs-server-advanced-topics>

**Start the server**

Open a command line on the /Server folder and run the following command:

<pre class="code">node server.js</pre>

**Launch a client**

Finally, launch a client referencing your vorlon.js local instance. You can use the sample provided in the /Plugins/samples folder.

Browse the dashboard using <http://localhost:1337/dashboard/default>

And… rock’n’roll ! 🙂

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image012" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6840.clip_image012_thumb_7A606911.jpg" alt="clip_image012" width="557" height="392" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7331.clip_image012_3B6C57C5.jpg)

You can try to change the size of the browser in which you display your client code, you will see it change live on the dashboard.

Easy, isn’t it? 🙂

### What to do now?

I hope I illustrated here how easy we want the plugin creation to be. You really have to see it like writing classic web code and just split it in two parts:

  * The one collecting data on the client
  * The one displaying it on the dashboard

Vorlon.js is not only our project, it is yours also. I am pretty sure that you will have plenty of plugin ideas and we will be happy to integrate them in the project.

Do not hesitate to fork <https://github.com/MicrosoftDX/Vorlonjs> and send us pull request with your creations!

You can find the full sample here : <https://github.com/meulta/meultasamples/tree/master/vorlonpluginsample>

> _If you have any question about this article or Vorlon.js, feel free to contact me on twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)

**_Etienne Margraff &#8211; HTML5 Evangelist_**