---
id: 183
title: One year of Vorlon.js
date: 2016-06-04T17:40:26+00:00
author: Etienne Margraff
layout: post
guid: http://meulta.com/?p=183
permalink: /en/2016/06/04/one-year-of-vorlon-js/
image: /wp-content/uploads/2016/06/hourglassvorlon-600x196.png
categories:
  - Vorlon.js
  - Web
---
It has already been one year that we started Vorlon.js. One year full of feedbacks, new features, a lot of talks in meetups and conferences. It is really a pleasure to talk with devs and Vorlon.js users to understand what they like about it or what they would like to have there! 🙂

<img class="wp-image-184 aligncenter" src="http://meulta.com/wp-content/uploads/2016/06/vorlon.gif" alt="vorlon ultra quick demo" width="450" height="316" />

As David explained [here](https://www.eternalcoding.com/?p=1894) we ended up creating Vorlon.js to help web front devs in their remote debug scenarios, particularly on **phones and tablets**. When we released the first version, it only contained 4 plugins.

Today, we have more than 10 of them. They debug various things like **Angular.js, Office Addins**, and more. What is really interesting is that we have different features than classic F12 tools more specialized to some languages or rendering frameworks. Vorlon.js is easy to extend and a lot of people are doing it and contributing!

In only a few month, we managed to create a good F12 like experience. **I am proud of that, and I am proud of the team **🙂

At the beginning of this year, we thought that front web debugging was not enough. Server development with Node.js obviously uses JavaScript. And we were already able to inspect and debug JavaScript. This is why we decided to add support for [node.js debugging](http://vorlonjs.com/documentation/#debugging-nodejs-applications). Now, you can use a node module inside your server apps and get the Interactive Console, the **XHR Panel** and the **Object Explorer** to inspect and debug your running code.

<img class="wp-image-189 aligncenter" src="http://meulta.com/wp-content/uploads/2016/06/4846.image_5178F222.png" alt="4846.image_5178F222" width="539" height="303" srcset="http://meulta.com/wp-content/uploads/2016/06/4846.image_5178F222.png 1024w, http://meulta.com/wp-content/uploads/2016/06/4846.image_5178F222-300x169.png 300w, http://meulta.com/wp-content/uploads/2016/06/4846.image_5178F222-768x432.png 768w, http://meulta.com/wp-content/uploads/2016/06/4846.image_5178F222-945x532.png 945w, http://meulta.com/wp-content/uploads/2016/06/4846.image_5178F222-600x338.png 600w" sizes="(max-width: 539px) 100vw, 539px" />

**Where are we going ?**

In the next few months we are going to improve the support for **Node.js debugging**. A lot is coming in this area. We are working on Node.js and Express.js dedicated plugins. We still need to improve the stability of node.js debugging: this is pretty new and some things are not identical to front debugging and inspection.

We want to get an **hosted Vorlon.js platform**. Right now you have to locally install the server to use it (or install it somewhere in the cloud). It is not a hard task but us developers are lazy folks: the more is done for us the better ;). You can simply picture this as a webpage where you can click on a &#8220;I want an online Vorlon.js server&#8221; button and get it instantly, ready to use. I really hope we will be ready to release this soon!

We are going to do a lot of refactoring on the server side. We barely changed this since the first version to focus on the plugins and user experience part. We want to clean it to make it easier to change in the future.

We also have some awesome projects we will be able to talk about soon! 🙂

**What is new in the last version?**

A couple of weeks ago, we released the 0.2.2 version. It contains some great features and mainly 2 new plugins.

  * **The Universal Windows Platform plugin**

It is possible to create a first class Windows application using HTML and JavaScript. You have direct access to the WinRT API and your app gets native performances by design. It is not running as a webview, but really by Windows core. This Vorlon.js plugin helps you understand better your code behavior. You have access to the CPU and Memory usage and more usefull infos.

<img class="size-full wp-image-186 aligncenter" src="http://meulta.com/wp-content/uploads/2016/06/sans-titre.png" alt="sans-titre" width="630" height="332" srcset="http://meulta.com/wp-content/uploads/2016/06/sans-titre.png 630w, http://meulta.com/wp-content/uploads/2016/06/sans-titre-300x158.png 300w, http://meulta.com/wp-content/uploads/2016/06/sans-titre-600x316.png 600w" sizes="(max-width: 630px) 100vw, 630px" />

  * **Office Addins plugin**

**Office is everywhere**. You can get it on your **iPhone**, your **Android**, your **iPad**, your **Mac**, your **PC**, your [_put whatever you want here_]. And you are not alone. A lot of us have office on our devices. Office 365 is a plateform behind the Office apps and softwares. It is a mail, file, contact, calendar, app server for enterprises.

And it matters. A **lot**.

A recent study showed that Office 365 is the Software as a Service app the most used in the world. If you never consider creating apps for it, you should. By creating app I mean an addin: it can be a pane inside the email composition interface or a tool inside Excel, or something inside Word. To create it you use web front tools that you already know. The addin is hosted somewhere and displayed inside every version of office you want (on ipad, android, etc.).

So, why am I talking to you about this? Because when it comes to debugging Office addins on tablets or phone, there are no great options. Or at least, there WAS! 😉

You can use all the features from Vorlon.js to debug the DOM, understand an issue using the console or the object explorer, improve performances thanks to the Network monitor, etc. You can also use the new Office Addin plugin. It helps you get access to the whole office addin API (which is JavaScript of course) and call some of them, get configuration values and more!

<img class="size-full wp-image-187 aligncenter" src="http://meulta.com/wp-content/uploads/2016/06/2313.image_099DC3E5.png" alt="2313.image_099DC3E5" width="800" height="493" srcset="http://meulta.com/wp-content/uploads/2016/06/2313.image_099DC3E5.png 800w, http://meulta.com/wp-content/uploads/2016/06/2313.image_099DC3E5-300x185.png 300w, http://meulta.com/wp-content/uploads/2016/06/2313.image_099DC3E5-768x473.png 768w, http://meulta.com/wp-content/uploads/2016/06/2313.image_099DC3E5-600x370.png 600w" sizes="(max-width: 800px) 100vw, 800px" />

You can read more about this and how to use it here: https://blogs.msdn.microsoft.com/mim/2016/02/18/vorlonjs-plugin-for-debugging-office-addin

  * **User interface for Config editing !**

All the Vorlon.js configuration is done through the config.json file. It is not always handy to change it when you installed Vorlon from the **npm** package or if you deployed it on a remote server. We now have a user interface to be able to edit the plugins list. You can **activate / deactivate a plugin**, change its **name** or choose on which **pane** it will be displayed. You can also see an icon indicating you if you can use it in Node.js debug scenarios.

<img class="wp-image-188 aligncenter" src="http://meulta.com/wp-content/uploads/2016/06/CiFYYPHW0AAGl9X.jpg" alt="CiFYYPHW0AAGl9X" width="799" height="379" srcset="http://meulta.com/wp-content/uploads/2016/06/CiFYYPHW0AAGl9X.jpg 1024w, http://meulta.com/wp-content/uploads/2016/06/CiFYYPHW0AAGl9X-300x142.jpg 300w, http://meulta.com/wp-content/uploads/2016/06/CiFYYPHW0AAGl9X-768x365.jpg 768w, http://meulta.com/wp-content/uploads/2016/06/CiFYYPHW0AAGl9X-945x449.jpg 945w, http://meulta.com/wp-content/uploads/2016/06/CiFYYPHW0AAGl9X-600x285.jpg 600w" sizes="(max-width: 799px) 100vw, 799px" />

You can read more about this in the readme file here : https://github.com/MicrosoftDX/Vorlonjs/blob/master/whatsnew.md

**You want to help ?**

The more people we are the better! If you have an idea of plugin, or if you want to chat with us about Vorlon, feel free to join us on slack.



> <span style="text-align: center;">If you have any question about this article, feel free to contact me on http://twitter.com/meulta 🙂</span>