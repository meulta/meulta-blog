---
id: 208
title: Debug your dom history using Vorlon.js
date: 2016-11-15T16:53:05+00:00
author: Etienne Margraff
layout: post
guid: http://meulta.com/?p=208
permalink: /en/2016/11/15/debug-your-dom-history-using-vorlon-js/
enclosure:
  - |
    http://meulta.com/wp-content/uploads/2016/11/Vorlon-Domtimeline.mp4
    1227743
    video/mp4
    
image: /wp-content/uploads/2016/11/Capture-600x212.jpg
categories:
  - Vorlon.js
  - Web
---
Last version of Vorlon.js was focused on debugging JavaScript on the server thanks to the [Node.js and Express.js plugins](https://meulta.com/en/2016/07/05/remote-inspect-node-js-and-express-with-vorlon-js/).

We have been busy since then working tightly with [Francois Remy](https://twitter.com/fremycompany) to help you debug DOM even easier than it already is. And it is now available in [Vorlon.js 0.4](https://www.npmjs.com/package/vorlon) !

**Introducing the DOM Timeline plugin**

Modern web interfaces are more and more complex. JavaScript enables you to do a lot of changes in your DOM. How many times you hide, show or change an HTML element? And how many times you have hard time to debug these changes when something is not going well?

The goal of the DOM Timeline is to let you track the history of DOM events. You can record and then have a look at every change, add or removal that happened while you used the debugged website.

<div style="width: 640px;" class="wp-video">
  <video class="wp-video-shortcode" id="video-208-4" width="640" height="285" preload="metadata" controls="controls"><source type="video/mp4" src="http://meulta.com/wp-content/uploads/2016/11/Vorlon-Domtimeline.mp4?_=4" /><a href="http://meulta.com/wp-content/uploads/2016/11/Vorlon-Domtimeline.mp4">http://meulta.com/wp-content/uploads/2016/11/Vorlon-Domtimeline.mp4</a></video>
</div>

As you can see on the video, you are also able to go back in history and the website is going to be exactly as it was at that specific point in time.

**Next steps**

We are now in the process of getting more stuff done on the server debugging side.

Our next goal is to simplify **bots developpers** life!

  * Vorlon.js **website**: <http://vorlonjs.io>
  * Vorlon.js **github** repo: <http://github.com/microsoftdx/vorlonjs>
  * Vorlonjs **npm** package: <https://www.npmjs.com/package/vorlon>

Thanks to [Camtasia](http://www.techsmith.fr/camtasia.html) for their help on the video!

> If you have any question about Vorlon.js or this article, feel free to contact me on twitter : <http://twitter.com/meulta>