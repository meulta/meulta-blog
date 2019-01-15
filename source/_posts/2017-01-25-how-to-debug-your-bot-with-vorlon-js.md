---
id: 220
title: How to debug your bot with Vorlon.js
date: 2017-01-25T19:15:39+00:00
author: Etienne Margraff
layout: post
guid: http://meulta.com/?p=220
permalink: /en/2017/01/25/how-to-debug-your-bot-with-vorlon-js/
enclosure:
  - |
    http://meulta.com/wp-content/uploads/2017/01/BotInspector-1.mp4
    8429775
    video/mp4
    
image: /wp-content/uploads/2017/01/Untitled-Project-600x268.gif
categories:
  - Bots
  - Node.js
  - Vorlon.js
tags:
  - Bots
---
# **Bots.** 

They are everywhere. Everyone talks about it and everyone wants to have one.
  
And **you**, developer, always dreamt of creating your own. An artificial intelligence that you could shape and which could rule the web and, later, even the world.

Well not so fast. It is not that easy. It is getting easiER but still requires work and knowledge in various areas.

A bot (or Conversational Agent) is basically a **web API**. This web API is plugged to a conversation channel such as Skype, Facebook or Kik and do 2 things:

  * Receiving messages from the user
  * Doing stuff and sending a message to the user

Receiving and sending messages is not really the complex part. The hard piece of code is the one that is going to make your **bot look intelligent**. And there are a lot of challenges here, from **understanding** what the user wants, to managing the data and the **conversation flow** and history.

At Microsoft, we are working on solutions to help you on all those aspects:

  * The [bot framework](https://dev.botframework.com/) helps you 
      * Create and maintain a conversation state with the Bot Builder sdk
      * Expose your bot to multiple conversation channel with no or little configuration
  * [LUIS.ai](http://luis.ai) is here to help understanding the structure of a sentence. It is using NLP ([Natural Language Processing](https://en.wikipedia.org/wiki/Natural_language_processing)) to give you a hint about what the human user intent is. This way, you can try and answer something appropriate and go to one or another path of your conversation.
  * [Microsoft Azure](https://azure.microsoft.com/en-us) contains a huge list of services that are helpful here. Obviously you can think of [web apps](https://docs.microsoft.com/en-us/azure/app-service-web/) or [functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview) to host your bot API but there also is [Cognitive Services](https://www.microsoft.com/cognitive-services/en-us/apis) for image analysis, emotion analysis, face recognition and so on. [Azure Search](https://docs.microsoft.com/en-us/azure/search/) is a component that has proven to be a great ally in organizing and finding data for bots.

I am sure you get it, creating a bot involves a lot of tools, languages and features. The goal in this post is not to go deep into details on how you create a bot so I will stop here. You can find a lot of great content here :  <https://docs.botframework.com>

# Bot Builder

The [bot builder](https://docs.botframework.com/en-us/) is an **SDK** that is available for** [.NET](https://docs.botframework.com/en-us/csharp/builder/sdkreference/) and [Node.js](https://docs.botframework.com/en-us/node/builder/overview/#navtitle)**. It is helping you creating and maintaining the conversation state. You have to think of a bot as a list of paths that the conversation can take. If you create a IMDB bot for instance, it might be able to talk about movies or  actors. When you talk about actors with it, you also can have various sub-subjects like the actor&#8217;s list of movies or other stuff that he or she did. The way we design conversations today is by creating hierarchical dialogs: &#8220;_First the user can ask for an actor and get his description, then from there the user can ask for the actors&#8217; age, or movies_&#8220;. Usually you will have a small dialog trees but even there it can be complicated to understand. (Even if you are its initial coder 😉

In your bot, dialogs are going to start other dialogs and this is going to create a **dialog stack**. It is basically a way for the Bot Builder SDK to remember the state of the conversation and what to do next.

When I first started to code bots, I did not really pay attention to what this dialog stack was and how it worked. Sometimes i was trying to fix issues and understand what was happening using step by step debugging. That is useful and can help to a limit where you need to have a more visual way of seeing this stack.

We realized that with [David](http://twitter.com/davrous) and that is why we worked with the **Microsoft bot framework team** to create a plugin in Vorlon.js that will **help bot developers understand what is happening in their code**.

# The Bot Framework Inspector plugin in Vorlon.js

> You do not know how to setup Vorlon.js? It is really easy. Here is a step by step guide: <https://github.com/meulta/VorlonBotLab>

Vorlon.js is a tool designed to remote inspect JavaScript code. You can use it for front websites when it is hard to get F12 tools working (on a mobile, a tablet, a Tesla car, a connected fridge or whatever). You can also use it to inspect Node.js processes. Of course you can debug Node.js code step by step using tools like Visual Studio Code but Vorlon.js purpose is to help you using **dedicated plugins**. We have one for NodeJS, another one for XHR requests, one for Express.js, and now: One for the bot builder SDK.

This only work for the node.js version of the SDK for now.

_**Note**: The current version is in Beta, so please do not pay too much attention to the design. We will fix that when we are sure we implemented useful features for you, bot devs! 🙂_

<div style="width: 640px;" class="wp-video">
  <video class="wp-video-shortcode" id="video-220-5" width="640" height="248" loop="1" autoplay="1" preload="metadata" controls="controls"><source type="video/mp4" src="http://meulta.com/wp-content/uploads/2017/01/BotInspector-1.mp4?_=5" /><a href="http://meulta.com/wp-content/uploads/2017/01/BotInspector-1.mp4">http://meulta.com/wp-content/uploads/2017/01/BotInspector-1.mp4</a></video>
</div>

&nbsp;

The plugin is splitted into 3 parts. The upper left one is showing you the list of dialogs that are declared in your bot. Each line is a dialog and its id is composed of the library name (* if you do not have any library) and the actual dialog name.

<img class="alignnone wp-image-222" src="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-1.jpg" alt="" width="619" height="193" srcset="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-1.jpg 673w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-1-300x94.jpg 300w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-1-600x187.jpg 600w" sizes="(max-width: 619px) 100vw, 619px" />

On the right you can see the list of steps you have in each dialog. If you let your mouse over one of them you will have a quick view of its code.

<img class="alignnone wp-image-223" src="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-2.jpg" alt="" width="606" height="217" srcset="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-2.jpg 673w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-2-300x107.jpg 300w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-2-600x215.jpg 600w" sizes="(max-width: 606px) 100vw, 606px" />

On the lower left part of the plugin, you can see the live view of events happening inside your bot. You have to actually start interacting with it to see things here 🙂

In the botbuilder, each **user entry** generates one or more **events**. These events are linked to your bot code. For instance, each time a dialog start, there is a **BeginDialog** event happening. You can see all these in this view. When the bot builder is done with all the events generated by one user entry, it automatically **save the state**. This end up launching a FinalSate event.

For each event, you can see the current **dialog stack**. The dialog stack is the list of dialogs that are currently started. One dialog starts another on, which starts another one, and so on. The dialog usually only ends when EndDialog is called. The dialog stack state is memorized between 2 user entries.

<img class="alignnone wp-image-224" src="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-3.jpg" alt="" width="607" height="346" srcset="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-3.jpg 802w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-3-300x171.jpg 300w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-3-768x438.jpg 768w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-3-600x342.jpg 600w" sizes="(max-width: 607px) 100vw, 607px" />

The last part of the plugin is the **live graph**. It is generated by the bot execution and it thightly coupled with the event view. It is built live while you are using the bot. It is interesting to have a graphical overview of what is happening inside your bot and can help you discover and fix dialog stack issues.

Whenever you have 0 dialogs in the stack or you call endConversation, a new graph is created on the right.

<img class="alignnone wp-image-225" src="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-4.jpg" alt="" width="632" height="261" srcset="http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-4.jpg 785w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-4-300x124.jpg 300w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-4-768x317.jpg 768w, http://meulta.com/wp-content/uploads/2017/01/plugin-botframeworkinspector-4-600x248.jpg 600w" sizes="(max-width: 632px) 100vw, 632px" />

# What&#8217;s next

The next features we have in mind are mainly:

  * Being able to save a specific state at a given moment in time and restore it
  * Making data editable from the dashboard
  * Making it work for .NET
  * Design improvements
  * Handling more events from the bot builder

The only way to make this tool great is to test it accross a huge number of developers.
  
That is where you can help!

**Try it out today** and send feedbacks to either [me](http://twitter.com/meulta) or [davrous](http://twitter.com/davrous).