---
id: 197
title: Remote inspect Node.js and Express with Vorlon.js
date: 2016-07-05T22:44:39+00:00
author: Etienne Margraff
layout: post
guid: http://meulta.com/?p=197
permalink: /en/2016/07/05/remote-inspect-node-js-and-express-with-vorlon-js/
enclosure:
  - |
    http://meulta.com/wp-content/uploads/2016/07/settings.mp4
    697265
    video/mp4
    
  - |
    http://meulta.com/wp-content/uploads/2016/07/nodejsdebugging.mp4
    337855
    video/mp4
    
  - |
    http://meulta.com/wp-content/uploads/2016/07/expressjsdebug.mp4
    700851
    video/mp4
    
image: /wp-content/uploads/2016/07/nodejs_logo_green-600x257.jpg
categories:
  - Express.js
  - Node.js
  - Vorlon.js
---
Here we are !

A few weeks after the last release we are excited to ship Vorlon.js 0.3 to the world. 🙂

In this version we focused to make node.js inspection better with Vorlon.js. Special thanks to [Sofiene Djebali](https://twitter.com/totose_) who is doing an awesome contribution to Vorlon.js!

We already added a preview of this capability in the 0.2 version, you can read more about it here : <http://meulta.com/en/2016/02/01/vorlon-js-0-2-1-is-out/>

&nbsp;

**Why would I want to use Vorlon.js to inspect my node.js app ?**

The idea behind this is to make you capable of getting all the information you need to debug a node.js app remotely.

We all know Tools to debug locally and we also know some of them that work remotely. What we are aiming is to create an easy-to-use set of Tools specialized on various node.js modules:

  1. In version 0.2 we added the possibilty to inspect a node.js app with Vorlon.js. To do this you only have to **npm install** and **require** the vorlonjs-node-wrapper npm module. Then you can start the client part of Vorlon.js Inside your node app as documented here : http://vorlonjs.io/documentation/#debugging-nodejs-applications. Thanks to this, you can use Vorlon.js plugins
  2. Still in version 0.2 we made the standard **Interactive Console**, **Object Explorer** and **XHR** plugins working in node.js inspection scenarios
  3. In version 0.3 we are bringing you 2 new plugins specifically crafted for node.js debugging 
      1. Node.js
      2. Express.js

We plan to add more of these specialized plugin to help you going through your worst debugging cases! 🙂

To activate these, you just have to go in the settings from the Vorlon.js Dashboard page.

<div style="width: 640px;" class="wp-video">
  <!--[if lt IE 9]><![endif]--><video class="wp-video-shortcode" id="video-197-1" width="640" height="384" loop="1" autoplay="1" preload="metadata" controls="controls"><source type="video/mp4" src="http://meulta.com/wp-content/uploads/2016/07/settings.mp4?_=1" />
  
  <a href="http://meulta.com/wp-content/uploads/2016/07/settings.mp4">http://meulta.com/wp-content/uploads/2016/07/settings.mp4</a></video>
</div>

&nbsp;

**The Node.js plugin**

This one is the main that you want to use in a remote node debug scenario. As the Console, XHR and Object Explorer one it can be use for any node.js apps.

It is composed of 3 panes:

  * One displaying the hierarchy of modules you required inside your app
  * One showing a graph of your app memory usage
  * One giving you information about the node process

<div style="width: 640px;" class="wp-video">
  <video class="wp-video-shortcode" id="video-197-2" width="640" height="384" loop="1" autoplay="1" preload="metadata" controls="controls"><source type="video/mp4" src="http://meulta.com/wp-content/uploads/2016/07/nodejsdebugging.mp4?_=2" /><a href="http://meulta.com/wp-content/uploads/2016/07/nodejsdebugging.mp4">http://meulta.com/wp-content/uploads/2016/07/nodejsdebugging.mp4</a></video>
</div>

&nbsp;

**The Express.js plugin**

To be able to use this plugin, you obviously have to use Express.js in your node app. You also have to declare a variable so that Vorlon.js is able to access the Express informations:

_EXPRESS_VORLONJS = app;_

Once this is done, you will have access to :

  * The list of routes configured in your express app
  * The requests that has been made and that hit your routes
  * Your session variables
  * And the express local configuration

<div style="width: 640px;" class="wp-video">
  <video class="wp-video-shortcode" id="video-197-3" width="640" height="384" loop="1" autoplay="1" preload="metadata" controls="controls"><source type="video/mp4" src="http://meulta.com/wp-content/uploads/2016/07/expressjsdebug.mp4?_=3" /><a href="http://meulta.com/wp-content/uploads/2016/07/expressjsdebug.mp4">http://meulta.com/wp-content/uploads/2016/07/expressjsdebug.mp4</a></video>
</div>

&nbsp;

**Next steps**

We are now going to start a huge refactoring process to be sure that the server part catches up with our plugin ambitions. We have a lot of great stuff in our roadmap. We will share this soon, stay tuned ! 🙂

If you have any idea of improvements or ideas of plugins that might be useful in Node.js remote inspection scenario, reach out with the team via twitter or slack 🙂

To get this version you can:

  * Clone our [github repo](https://github.com/MicrosoftDX/Vorlonjs)
  * run: npm install vorlon (<https://www.npmjs.com/package/vorlon>)
  * Clic on the [Deploy on azure button](https://github.com/MicrosoftDX/Vorlonjs#deploy-on-azure) on the Github repo readme page
  * Use the [Docker image](https://hub.docker.com/r/vorlonjs/dashboard/) brought to you by [Julien Corioland](http://twitter.com/jcorioland)

> If you have any question about Vorlon.js or this article, feel free to contact me on twitter : <http://twitter.com/meulta>