---
id: 255
title: Bot framework, web chat and push notifications
date: 2017-04-17T16:18:26+00:00
author: Etienne Margraff
layout: post
guid: http://meulta.com/?p=255
permalink: /en/2017/04/17/bot-framework-web-chat-and-push-notifications/
enclosure:
  - |
    http://meulta.com/wp-content/uploads/2017/04/push-notifications.mp4
    1437111
    video/mp4
    
image: /wp-content/uploads/2017/04/logopush-600x354.png
categories:
  - Bots
  - Progressive web apps
  - Web
---
_This blog article is explaining how to setup web push notifications on a bot framework web chat control. For this, we will use service workers and VAPID. All the code shown here is available in this [Github repository](https://github.com/meulta/webchat-pushnotifications) containing the full version of it. You can also try [this live sample](https://webchatpush.azurewebsites.net/web/index.html) or watch the video below._

<div style="width: 640px;" class="wp-video">
  <video class="wp-video-shortcode" id="video-255-6" width="640" height="480" loop="1" autoplay="1" preload="metadata" controls="controls"><source type="video/mp4" src="http://meulta.com/wp-content/uploads/2017/04/push-notifications.mp4?_=6" /><a href="http://meulta.com/wp-content/uploads/2017/04/push-notifications.mp4">http://meulta.com/wp-content/uploads/2017/04/push-notifications.mp4</a></video>
</div>

> If you have any question about this blog article, feel free to contact me on twitter: [@meulta](https://twitter.com/meulta)

# **Progressive web apps**

The web is in a perpetual evolution. The advantage that apps have over it on mobile platforms is slowly fading away as more and more features are available from the browser. The web community and web browsers team like Microsoft Edge, Google Chrome and Mozilla Firefox are working on enabling the next wave of native-like web experiences, where web content can have the essential capabilities and user experience of native desktop or mobile apps. These web apps can start up instantly, can run in the background and have additional APIs available for developers. We call them: [Progressive Web Apps](https://medium.com/web-on-the-edge/progressive-web-apps-on-windows-8d8eb68d524e) (PWAs).

PWAs are safe, connectivity independent, installable and responsive websites. There is a great chance that you already used one, even without knowing it. Did you already received notifications from Facebook even if the website is not opened in your browser? It is because Facebook is starting to use some of the underlining technology in PWAs. The heart of these new technologies are [**service workers**.](https://www.w3.org/TR/service-workers/)

Service workers are slowly being implemented in every browser to help web developers create web apps that are connectivity independent. You can see them as a proxy that goes between the local webpage and your server. It is used to handle caching, push notifications, and even temporary disconnection with background sync.

# **Bot framework, web chat and the need of push notifications**

The [Microsoft Bot Framework](https://dev.botframework.com/) is a platform that helps developers create a bot which works across multiple channels. You use the Node.js or C# botbuilder SDK to create the bot backend and you can almost automatically make is available on Skype, Slack, Facebook, and a lot more. The combinaison of the [**web chat**](https://github.com/Microsoft/BotFramework-WebChat) and Direct Line is one of these channels. Its name is pretty explicit: it is a web chat control that you can embed in any web page. It is very useful when, for example, you want to embed a support bot chat window directly in your website. Web clients have always been inferior to native clients in one way: background.  Your native client can be granted privileges to run in the background and engage users even when the app isn’t running.  We want to provide that same functionality for the web client

As you might be using at least one instant messaging app on a day to day basis, you should be familiar with the fact that if someone talks to you when the app is closed or reduced you will receive a notification. You can click or tap on it to view the new message and the previous conversation. Having this is important to make the chat UI usable in the long term. It is the same if you are talking with a bot. Usually it will give you an answer pretty quickly as there is no concept of a bot being “away from keyboard” or “not connected”. This said, you might get a message from a bot which:

  * Took some time to compute or get so did not arrive instantly
  * Is a proactive message from the bot at a random time
  * Is a human which took over the conversation and “replaced” the bot
  * Your network doesn’t allow for immediate communication

**Push notifications** help the user not missing an important message from you. By enabling them to the web client we will fix the gap between native and web clients.

# **Push notifications**

If you never handled push notifications in an app it is important to understand how it works.

When you receive a push notification from an app or a website, even if it looks like they sent it to you directly: it is not technically true. They used a **push notification service**. This push notification service is linked to the platform you are using. Android uses a push server and Windows another one. It is the same for push notification on a browser: Chrome has its own server, Firefox too, etc.

When you want to be able to send push to a client, you globally have to follow these steps:

  * **Step 1**: Setup an account on every platform you want to be able to send push to. The push service creates a push sender key that you will need later.
  * **Step 2**: Subscribe a client to push: this is done and handled by the platform. You do not call directly the push server but you ask the platform to do it. For it to work and for the push server to be able to identify yourself, you have to provide the key it gave you.
  * **Step 3**: The client get information related to the new subscription: an endpoint on the push server to call to send a new notification and keys for authentication
  * **Step 4**: Usually, your client code then sends that to your server code to store this subscription information
  * **Step 5+**: each time you want to send a notification to this client, you use the endpoint and keys that you got from it. The push server will then send that notification to the system which registered (a browser, a mobile, a desktop, etc.). Finally, the system displays it to the user who can see it and click on it.

<img class="alignnone size-full wp-image-300" src="http://meulta.com/wp-content/uploads/2017/04/push.png" alt="" width="1896" height="1046" srcset="http://meulta.com/wp-content/uploads/2017/04/push.png 1896w, http://meulta.com/wp-content/uploads/2017/04/push-300x166.png 300w, http://meulta.com/wp-content/uploads/2017/04/push-768x424.png 768w, http://meulta.com/wp-content/uploads/2017/04/push-1024x565.png 1024w, http://meulta.com/wp-content/uploads/2017/04/push-945x521.png 945w, http://meulta.com/wp-content/uploads/2017/04/push-600x331.png 600w" sizes="(max-width: 1896px) 100vw, 1896px" />

This is identical for native apps and web apps. However, web notifications are a newer and more progressive spec.  They allow for developers to set up push without all the overhead of accounts on each platform. Your web app will still use the push server associated with each platform but you will generate your own keys. This is done by using [VAPID (Voluntary Application Server Identification)](https://tools.ietf.org/html/draft-ietf-webpush-vapid-02).

For example, if you setup classic push notifications on chrome, you will have to give a GCM\_SENDER\_ID you got from a Firebase account. Using VAPID, chrome will still be using Firebase to register and get push events but you will give it your own key, which will also work with other browsers.

In this scenario, your server code is responsible for creating private and public keys. This is a one-time creation process. In your web client code, you use the public key to register to the push server associated with the current browser. The push service understand that you are using VAPID and you get an endpoint and an auth token. This basically only replace **step 3** and you can do everything else the same way.  VAPIDs represent the modern approach to push.

To get a deeper understanding of how VAPIDs work, you can check out any of these resources:

  * <https://rossta.net/blog/using-the-web-push-api-with-vapid.html>
  * <https://developers.google.com/web/updates/2016/07/web-push-interop-wins>
  * <https://blog.mozilla.org/services/2016/04/04/using-vapid-with-webpush/>

When you setup push on a website, you have to do it through a service worker. A service worker is a piece of code which is running side by side with your website client code. The 2 main differences are:

  * It can run even if the website is not open in a tab
  * It is dedicated to network related work such as… push!

In a push scenario, the service worker registers specifically to a “push” event. Its code will be running in the background to get and display what is pushed, and your client code will be responsible for the rest:

  * registering the service worker JavaScript file using **serviceWorker.register(…)**
  * registering to the push service and getting back the endpoint, key and secret for this push subscription
  * sending the endpoint, key and secret to your server code so it can send a push notification later

_Note: when you register for push in your client code, the browser will automatically ask for the user’s permission to enable push notifications._

**Ok, enough talking, let’s implement that!**

_Disclaimer 1: The code I am going to talk about here is from a fully working sample which is available here:_ [_https://github.com/meulta/webchat-pushnotifications_](https://github.com/meulta/webchat-pushnotifications) _You can go and have a look at the whole implementation. I will only talk about interesting pieces here._ 

_Disclaimer 2: If you do not know anything about the Bot Framework I highly recommend reading the documentation:_ <https://docs.botframework.com/en-us/>

_Disclaimer 3: concepts I talk about here will work for any website even if you are not using bot framework _

_Disclaimer 4: sorry about all these disclaimers!_ _&#x1f609;_

# **Adding push notification to an existing bot**

> You can try a live version of this sample here: <https://webchatpush.azurewebsites.net/web/index.html>

The bot we are using in this sample is a really simple one. If you say anything to it, it will start sending one message every 5 seconds. You can stop it by saying “stop”.

You can have a look at the code doing this (<https://github.com/meulta/webchat-pushnotifications/blob/master/bot.js#L84-L103>) but please do not take it as a reference to send messages proactively to a user from a bot. I tried to keep it as simple as possible as this is not the important part here. You can read more about how to send a message proactively to a user here: <https://docs.botframework.com/en-us/azure-bot-service/templates/proactive/>

This server code is responsible for creating VAPID keys and send push notification to clients.

  * **Creating Vapid keys**

If you create your server code in Node.js then you can use a very cool module created by Mozilla which will do almost all the work for you: web-push : <https://github.com/web-push-libs/web-push>

You will have to first generated Vapid keys using the **webPush.generateVapidKeys()** function. You only have to do this once or when you want to reset your keys. In our sample, we generate them and store them in a local JSON file. You might want to store this somewhere more secure.

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-bot-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-bot-js-L6" class="blob-num js-line-number" data-line-number="6">
                </td>
                
                <td id="file-bot-js-LC6" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">const</span> <span class="pl-c1">vapidKeyFilePath</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>./vapidKey.json<span class="pl-pds">"</span></span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L7" class="blob-num js-line-number" data-line-number="7">
                </td>
                
                <td id="file-bot-js-LC7" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> vapidKeys <span class="pl-k">=</span> {};
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L8" class="blob-num js-line-number" data-line-number="8">
                </td>
                
                <td id="file-bot-js-LC8" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L9" class="blob-num js-line-number" data-line-number="9">
                </td>
                
                <td id="file-bot-js-LC9" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (<span class="pl-smi">fs</span>.<span class="pl-en">existsSync</span>(vapidKeyFilePath)) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L10" class="blob-num js-line-number" data-line-number="10">
                </td>
                
                <td id="file-bot-js-LC10" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>if the vapid file exists, then we try to parse its content </span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L11" class="blob-num js-line-number" data-line-number="11">
                </td>
                
                <td id="file-bot-js-LC11" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>to retrieve the public and private key</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L12" class="blob-num js-line-number" data-line-number="12">
                </td>
                
                <td id="file-bot-js-LC12" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>more tests might be necessary here</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L13" class="blob-num js-line-number" data-line-number="13">
                </td>
                
                <td id="file-bot-js-LC13" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">try</span> {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L14" class="blob-num js-line-number" data-line-number="14">
                </td>
                
                <td id="file-bot-js-LC14" class="blob-code blob-code-inner js-file-line">
                  vapidKeys <span class="pl-k">=</span> <span class="pl-c1">JSON</span>.<span class="pl-c1">parse</span>(<span class="pl-smi">fs</span>.<span class="pl-en">readFileSync</span>(vapidKeyFilePath));
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L15" class="blob-num js-line-number" data-line-number="15">
                </td>
                
                <td id="file-bot-js-LC15" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L16" class="blob-num js-line-number" data-line-number="16">
                </td>
                
                <td id="file-bot-js-LC16" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">catch</span> (e) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L17" class="blob-num js-line-number" data-line-number="17">
                </td>
                
                <td id="file-bot-js-LC17" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">console</span>.<span class="pl-c1">error</span>(<span class="pl-s"><span class="pl-pds">"</span>There is an error with the vapid key file. Log: <span class="pl-pds">"</span></span> <span class="pl-k">+</span> <span class="pl-smi">e</span>.<span class="pl-smi">message</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L18" class="blob-num js-line-number" data-line-number="18">
                </td>
                
                <td id="file-bot-js-LC18" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c1">process</span>.<span class="pl-en">exit</span>(<span class="pl-k">-</span><span class="pl-c1">1</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L19" class="blob-num js-line-number" data-line-number="19">
                </td>
                
                <td id="file-bot-js-LC19" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L20" class="blob-num js-line-number" data-line-number="20">
                </td>
                
                <td id="file-bot-js-LC20" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L21" class="blob-num js-line-number" data-line-number="21">
                </td>
                
                <td id="file-bot-js-LC21" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">else</span> {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L22" class="blob-num js-line-number" data-line-number="22">
                </td>
                
                <td id="file-bot-js-LC22" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>if the file did not exists, we use the web-push module to create keys</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L23" class="blob-num js-line-number" data-line-number="23">
                </td>
                
                <td id="file-bot-js-LC23" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>and store them in the file for future use</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L24" class="blob-num js-line-number" data-line-number="24">
                </td>
                
                <td id="file-bot-js-LC24" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>you should copy the public key in the index.js file</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L25" class="blob-num js-line-number" data-line-number="25">
                </td>
                
                <td id="file-bot-js-LC25" class="blob-code blob-code-inner js-file-line">
                  vapidKeys <span class="pl-k">=</span> <span class="pl-smi">webPush</span>.<span class="pl-en">generateVAPIDKeys</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L26" class="blob-num js-line-number" data-line-number="26">
                </td>
                
                <td id="file-bot-js-LC26" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">fs</span>.<span class="pl-en">writeFileSync</span>(vapidKeyFilePath, <span class="pl-c1">JSON</span>.<span class="pl-c1">stringify</span>(vapidKeys));
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L27" class="blob-num js-line-number" data-line-number="27">
                </td>
                
                <td id="file-bot-js-LC27" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">console</span>.<span class="pl-c1">log</span>(<span class="pl-s"><span class="pl-pds">"</span>No vapid key file found. One was generated. Here is the public key: <span class="pl-pds">"</span></span> <span class="pl-k">+</span> <span class="pl-smi">vapidKeys</span>.<span class="pl-smi">publicKey</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L28" class="blob-num js-line-number" data-line-number="28">
                </td>
                
                <td id="file-bot-js-LC28" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/bot.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-bot-js">bot.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

You then have to call the **setVapidDetails()** function to configure the web push module to send push notifications using the vapid private key. This will ensure the push server to be sure it comes from you.

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-bot-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-bot-js-L32" class="blob-num js-line-number" data-line-number="32">
                </td>
                
                <td id="file-bot-js-LC32" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">webPush</span>.<span class="pl-en">setVapidDetails</span>(
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L33" class="blob-num js-line-number" data-line-number="33">
                </td>
                
                <td id="file-bot-js-LC33" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-s"><span class="pl-pds">'</span>mailto:example@yourdomain.org<span class="pl-pds">'</span></span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L34" class="blob-num js-line-number" data-line-number="34">
                </td>
                
                <td id="file-bot-js-LC34" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">vapidKeys</span>.<span class="pl-smi">publicKey</span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L35" class="blob-num js-line-number" data-line-number="35">
                </td>
                
                <td id="file-bot-js-LC35" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">vapidKeys</span>.<span class="pl-smi">privateKey</span>);
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/bot.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-bot-js">bot.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

  * **Handling event to register push**

A bot can receive messages from the user but it can also receive events from the client code. This is very handful to send data to your bot backend code without the user knowing it. In the web chat control it is called the backchannel.

We are going to use this backchannel for the client code to have a way of sending every user push subscription information. We just listen to incoming activities of type **event** and check that the message name is **pushsubscriptionadded** (which is one I totally imagine myself, you can pass whatever name you want).

Each time the bot receive a new push subscription, we store it in a local variable associating it to the user internal id in the bot. Note that it might be best to store it in the bot user data.

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-bot-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-bot-js-L81" class="blob-num js-line-number" data-line-number="81">
                </td>
                
                <td id="file-bot-js-LC81" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">bot</span>.<span class="pl-en">on</span>(<span class="pl-s"><span class="pl-pds">"</span>event<span class="pl-pds">"</span></span>, <span class="pl-k">function</span> (<span class="pl-smi">message</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L82" class="blob-num js-line-number" data-line-number="82">
                </td>
                
                <td id="file-bot-js-LC82" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (<span class="pl-smi">message</span>.<span class="pl-c1">name</span> <span class="pl-k">===</span> <span class="pl-s"><span class="pl-pds">"</span>pushsubscriptionadded<span class="pl-pds">"</span></span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L83" class="blob-num js-line-number" data-line-number="83">
                </td>
                
                <td id="file-bot-js-LC83" class="blob-code blob-code-inner js-file-line">
                  pushPerUser[<span class="pl-smi">message</span>.<span class="pl-smi">user</span>.<span class="pl-c1">id</span>] <span class="pl-k">=</span> <span class="pl-smi">message</span>.<span class="pl-c1">value</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L84" class="blob-num js-line-number" data-line-number="84">
                </td>
                
                <td id="file-bot-js-LC84" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L85" class="blob-num js-line-number" data-line-number="85">
                </td>
                
                <td id="file-bot-js-LC85" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/bot.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-bot-js">bot.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

  * **Catching messages going out and sending push notifications**

In our current scenario, we want to send a push notification to the user each time there is a message sent by the bot. This can easily be done with an event called **outgoing**. You subscribe to this event then check to see if there is a push notification associated with the user the outgoing message is sent to. If we do, then we use the **webPush.sendNotification()** function from the web-push module. It will use the VAPID private key and the information from the push subscription to ask the appropriate web push server to send a notification to the browser. It knows which server to talk to thanks to the endpoint property we got from the client in the **pushsubscriptionadded** event call.

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-bot-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-bot-js-L64" class="blob-num js-line-number" data-line-number="64">
                </td>
                
                <td id="file-bot-js-LC64" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">bot</span>.<span class="pl-en">on</span>(<span class="pl-s"><span class="pl-pds">"</span>outgoing<span class="pl-pds">"</span></span>, <span class="pl-k">function</span> (<span class="pl-smi">message</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L65" class="blob-num js-line-number" data-line-number="65">
                </td>
                
                <td id="file-bot-js-LC65" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (pushPerUser <span class="pl-k">&&</span> pushPerUser[<span class="pl-smi">message</span>.<span class="pl-smi">address</span>.<span class="pl-smi">user</span>.<span class="pl-c1">id</span>]) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L66" class="blob-num js-line-number" data-line-number="66">
                </td>
                
                <td id="file-bot-js-LC66" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> pushsub <span class="pl-k">=</span> pushPerUser[<span class="pl-smi">message</span>.<span class="pl-smi">address</span>.<span class="pl-smi">user</span>.<span class="pl-c1">id</span>];
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L67" class="blob-num js-line-number" data-line-number="67">
                </td>
                
                <td id="file-bot-js-LC67" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L68" class="blob-num js-line-number" data-line-number="68">
                </td>
                
                <td id="file-bot-js-LC68" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">webPush</span>.<span class="pl-en">sendNotification</span>({
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L69" class="blob-num js-line-number" data-line-number="69">
                </td>
                
                <td id="file-bot-js-LC69" class="blob-code blob-code-inner js-file-line">
                  endpoint<span class="pl-k">:</span> <span class="pl-smi">pushsub</span>.<span class="pl-smi">endpoint</span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L70" class="blob-num js-line-number" data-line-number="70">
                </td>
                
                <td id="file-bot-js-LC70" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c1">TTL</span><span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">"</span>1<span class="pl-pds">"</span></span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L71" class="blob-num js-line-number" data-line-number="71">
                </td>
                
                <td id="file-bot-js-LC71" class="blob-code blob-code-inner js-file-line">
                  keys<span class="pl-k">:</span> {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L72" class="blob-num js-line-number" data-line-number="72">
                </td>
                
                <td id="file-bot-js-LC72" class="blob-code blob-code-inner js-file-line">
                  p256dh<span class="pl-k">:</span> <span class="pl-smi">pushsub</span>.<span class="pl-smi">key</span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L73" class="blob-num js-line-number" data-line-number="73">
                </td>
                
                <td id="file-bot-js-LC73" class="blob-code blob-code-inner js-file-line">
                  auth<span class="pl-k">:</span> <span class="pl-smi">pushsub</span>.<span class="pl-smi">authSecret</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L74" class="blob-num js-line-number" data-line-number="74">
                </td>
                
                <td id="file-bot-js-LC74" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L75" class="blob-num js-line-number" data-line-number="75">
                </td>
                
                <td id="file-bot-js-LC75" class="blob-code blob-code-inner js-file-line">
                  }, <span class="pl-smi">message</span>.<span class="pl-c1">text</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L76" class="blob-num js-line-number" data-line-number="76">
                </td>
                
                <td id="file-bot-js-LC76" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-bot-js-L77" class="blob-num js-line-number" data-line-number="77">
                </td>
                
                <td id="file-bot-js-LC77" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/bot.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-bot-js">bot.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

# **Setting up push in the client**

This is the most interesting part. The first role of the client code is to register the service worker in the browser. To do this, we use the **navigator.serviceWorker.register()** function by giving it the service worker file name. This function return a Promise so you can chain a **.then()** function to execute some code once the service worker is registered. If the service worker is already registered, it will return the current one.

In our case, we take this opportunity to try to get the existing push notification manager subscription using **registration.pushManager.getSubscription()** (where registration is the service worker instance). If it does not exist, we will just have to create and return a new one create using **registration.pushManager.subscribe()** giving it an **applicationServerKey**. This applicationServerKey is the public key your server generated.

The subscription object we get from this is containing everything the server will need to send a notification to the client: the endpoint, the key and a secret.

In the current sample, all this is done in the **setupPush** function which takes a callback as a parameter and calls it back with the subscription information.

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-index-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-index-js-L68" class="blob-num js-line-number" data-line-number="68">
                </td>
                
                <td id="file-index-js-LC68" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> <span class="pl-en">setupPush</span> <span class="pl-k">=</span> <span class="pl-k">function</span> (<span class="pl-smi">done</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L69" class="blob-num js-line-number" data-line-number="69">
                </td>
                
                <td id="file-index-js-LC69" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L70" class="blob-num js-line-number" data-line-number="70">
                </td>
                
                <td id="file-index-js-LC70" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>first step is registering the service worker file</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L71" class="blob-num js-line-number" data-line-number="71">
                </td>
                
                <td id="file-index-js-LC71" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c1">navigator</span>.<span class="pl-smi">serviceWorker</span>.<span class="pl-en">register</span>(<span class="pl-s"><span class="pl-pds">'</span>service-worker.js<span class="pl-pds">'</span></span>)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L72" class="blob-num js-line-number" data-line-number="72">
                </td>
                
                <td id="file-index-js-LC72" class="blob-code blob-code-inner js-file-line">
                  .<span class="pl-c1">then</span>(<span class="pl-k">function</span> (<span class="pl-smi">registration</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L73" class="blob-num js-line-number" data-line-number="73">
                </td>
                
                <td id="file-index-js-LC73" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L74" class="blob-num js-line-number" data-line-number="74">
                </td>
                
                <td id="file-index-js-LC74" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>once the sw is registered, we try to get an existing push subscription </span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L75" class="blob-num js-line-number" data-line-number="75">
                </td>
                
                <td id="file-index-js-LC75" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">return</span> <span class="pl-smi">registration</span>.<span class="pl-smi">pushManager</span>.<span class="pl-en">getSubscription</span>()
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L76" class="blob-num js-line-number" data-line-number="76">
                </td>
                
                <td id="file-index-js-LC76" class="blob-code blob-code-inner js-file-line">
                  .<span class="pl-c1">then</span>(<span class="pl-k">function</span> (<span class="pl-smi">subscription</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L77" class="blob-num js-line-number" data-line-number="77">
                </td>
                
                <td id="file-index-js-LC77" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L78" class="blob-num js-line-number" data-line-number="78">
                </td>
                
                <td id="file-index-js-LC78" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>if the subscription exists, then we pass is to the next chained .then function using return</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L79" class="blob-num js-line-number" data-line-number="79">
                </td>
                
                <td id="file-index-js-LC79" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (subscription) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L80" class="blob-num js-line-number" data-line-number="80">
                </td>
                
                <td id="file-index-js-LC80" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">return</span> subscription;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L81" class="blob-num js-line-number" data-line-number="81">
                </td>
                
                <td id="file-index-js-LC81" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L82" class="blob-num js-line-number" data-line-number="82">
                </td>
                
                <td id="file-index-js-LC82" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L83" class="blob-num js-line-number" data-line-number="83">
                </td>
                
                <td id="file-index-js-LC83" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>if the subscription does not exists, we wrap the VAPID public key and create a new one</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L84" class="blob-num js-line-number" data-line-number="84">
                </td>
                
                <td id="file-index-js-LC84" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>we pass this new once to the next chaind .then function using return</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L85" class="blob-num js-line-number" data-line-number="85">
                </td>
                
                <td id="file-index-js-LC85" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">const</span> <span class="pl-c1">convertedVapidKey</span> <span class="pl-k">=</span> <span class="pl-en">urlBase64ToUint8Array</span>(<span class="pl-c1">VAPID_PUBLICKEY</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L86" class="blob-num js-line-number" data-line-number="86">
                </td>
                
                <td id="file-index-js-LC86" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">return</span> <span class="pl-smi">registration</span>.<span class="pl-smi">pushManager</span>.<span class="pl-en">subscribe</span>({
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L87" class="blob-num js-line-number" data-line-number="87">
                </td>
                
                <td id="file-index-js-LC87" class="blob-code blob-code-inner js-file-line">
                  userVisibleOnly<span class="pl-k">:</span> <span class="pl-c1">true</span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L88" class="blob-num js-line-number" data-line-number="88">
                </td>
                
                <td id="file-index-js-LC88" class="blob-code blob-code-inner js-file-line">
                  applicationServerKey<span class="pl-k">:</span> convertedVapidKey
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L89" class="blob-num js-line-number" data-line-number="89">
                </td>
                
                <td id="file-index-js-LC89" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L90" class="blob-num js-line-number" data-line-number="90">
                </td>
                
                <td id="file-index-js-LC90" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L91" class="blob-num js-line-number" data-line-number="91">
                </td>
                
                <td id="file-index-js-LC91" class="blob-code blob-code-inner js-file-line">
                  })
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L92" class="blob-num js-line-number" data-line-number="92">
                </td>
                
                <td id="file-index-js-LC92" class="blob-code blob-code-inner js-file-line">
                  .<span class="pl-c1">then</span>(<span class="pl-k">function</span> (<span class="pl-smi">subscription</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L93" class="blob-num js-line-number" data-line-number="93">
                </td>
                
                <td id="file-index-js-LC93" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L94" class="blob-num js-line-number" data-line-number="94">
                </td>
                
                <td id="file-index-js-LC94" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>wrapping the key and secret</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L95" class="blob-num js-line-number" data-line-number="95">
                </td>
                
                <td id="file-index-js-LC95" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">const</span> <span class="pl-c1">rawKey</span> <span class="pl-k">=</span> <span class="pl-smi">subscription</span>.<span class="pl-smi">getKey</span> <span class="pl-k">?</span> <span class="pl-smi">subscription</span>.<span class="pl-en">getKey</span>(<span class="pl-s"><span class="pl-pds">'</span>p256dh<span class="pl-pds">'</span></span>) <span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">'</span><span class="pl-pds">'</span></span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L96" class="blob-num js-line-number" data-line-number="96">
                </td>
                
                <td id="file-index-js-LC96" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">const</span> <span class="pl-c1">key</span> <span class="pl-k">=</span> rawKey <span class="pl-k">?</span> <span class="pl-en">btoa</span>(<span class="pl-c1">String</span>.<span class="pl-smi">fromCharCode</span>.<span class="pl-c1">apply</span>(<span class="pl-c1">null</span>, <span class="pl-k">new</span> <span class="pl-en">Uint8Array</span>(rawKey))) <span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">'</span><span class="pl-pds">'</span></span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L97" class="blob-num js-line-number" data-line-number="97">
                </td>
                
                <td id="file-index-js-LC97" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">const</span> <span class="pl-c1">rawAuthSecret</span> <span class="pl-k">=</span> <span class="pl-smi">subscription</span>.<span class="pl-smi">getKey</span> <span class="pl-k">?</span> <span class="pl-smi">subscription</span>.<span class="pl-en">getKey</span>(<span class="pl-s"><span class="pl-pds">'</span>auth<span class="pl-pds">'</span></span>) <span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">'</span><span class="pl-pds">'</span></span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L98" class="blob-num js-line-number" data-line-number="98">
                </td>
                
                <td id="file-index-js-LC98" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">const</span> <span class="pl-c1">authSecret</span> <span class="pl-k">=</span> rawAuthSecret <span class="pl-k">?</span> <span class="pl-en">btoa</span>(<span class="pl-c1">String</span>.<span class="pl-smi">fromCharCode</span>.<span class="pl-c1">apply</span>(<span class="pl-c1">null</span>, <span class="pl-k">new</span> <span class="pl-en">Uint8Array</span>(rawAuthSecret))) <span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">'</span><span class="pl-pds">'</span></span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L99" class="blob-num js-line-number" data-line-number="99">
                </td>
                
                <td id="file-index-js-LC99" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L100" class="blob-num js-line-number" data-line-number="100">
                </td>
                
                <td id="file-index-js-LC100" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">const</span> <span class="pl-c1">endpoint</span> <span class="pl-k">=</span> <span class="pl-smi">subscription</span>.<span class="pl-smi">endpoint</span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L101" class="blob-num js-line-number" data-line-number="101">
                </td>
                
                <td id="file-index-js-LC101" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L102" class="blob-num js-line-number" data-line-number="102">
                </td>
                
                <td id="file-index-js-LC102" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>we call back the code that asked to register push notification with the subscription information</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L103" class="blob-num js-line-number" data-line-number="103">
                </td>
                
                <td id="file-index-js-LC103" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">done</span>({
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L104" class="blob-num js-line-number" data-line-number="104">
                </td>
                
                <td id="file-index-js-LC104" class="blob-code blob-code-inner js-file-line">
                  endpoint<span class="pl-k">:</span> <span class="pl-smi">subscription</span>.<span class="pl-smi">endpoint</span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L105" class="blob-num js-line-number" data-line-number="105">
                </td>
                
                <td id="file-index-js-LC105" class="blob-code blob-code-inner js-file-line">
                  key<span class="pl-k">:</span> key,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L106" class="blob-num js-line-number" data-line-number="106">
                </td>
                
                <td id="file-index-js-LC106" class="blob-code blob-code-inner js-file-line">
                  authSecret<span class="pl-k">:</span> authSecret
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L107" class="blob-num js-line-number" data-line-number="107">
                </td>
                
                <td id="file-index-js-LC107" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L108" class="blob-num js-line-number" data-line-number="108">
                </td>
                
                <td id="file-index-js-LC108" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L109" class="blob-num js-line-number" data-line-number="109">
                </td>
                
                <td id="file-index-js-LC109" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/index.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-index-js">index.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

This **setupPush** function is called right after we setup the Web Chat control. In the callback function we give to it, we use the Direct Line SDK to send an event of type **pushsubscriptionadded** to the bot, through the back channel.

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-index-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-index-js-L38" class="blob-num js-line-number" data-line-number="38">
                </td>
                
                <td id="file-index-js-LC38" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-en">setupPush</span>((<span class="pl-smi">subscriptionInfo</span>) <span class="pl-k">=></span> {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L39" class="blob-num js-line-number" data-line-number="39">
                </td>
                
                <td id="file-index-js-LC39" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L40" class="blob-num js-line-number" data-line-number="40">
                </td>
                
                <td id="file-index-js-LC40" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>once push notifications are setup, we get the subscription info back in this callback</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L41" class="blob-num js-line-number" data-line-number="41">
                </td>
                
                <td id="file-index-js-LC41" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>we use the backchannel to send this info back to the bot using an 'event' activity</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L42" class="blob-num js-line-number" data-line-number="42">
                </td>
                
                <td id="file-index-js-LC42" class="blob-code blob-code-inner js-file-line">
                  botConnection
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L43" class="blob-num js-line-number" data-line-number="43">
                </td>
                
                <td id="file-index-js-LC43" class="blob-code blob-code-inner js-file-line">
                  .<span class="pl-en">postActivity</span>({
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L44" class="blob-num js-line-number" data-line-number="44">
                </td>
                
                <td id="file-index-js-LC44" class="blob-code blob-code-inner js-file-line">
                  type<span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">"</span>event<span class="pl-pds">"</span></span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L45" class="blob-num js-line-number" data-line-number="45">
                </td>
                
                <td id="file-index-js-LC45" class="blob-code blob-code-inner js-file-line">
                  name<span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">"</span>pushsubscriptionadded<span class="pl-pds">"</span></span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L46" class="blob-num js-line-number" data-line-number="46">
                </td>
                
                <td id="file-index-js-LC46" class="blob-code blob-code-inner js-file-line">
                  value<span class="pl-k">:</span> subscriptionInfo,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L47" class="blob-num js-line-number" data-line-number="47">
                </td>
                
                <td id="file-index-js-LC47" class="blob-code blob-code-inner js-file-line">
                  from<span class="pl-k">:</span> { id<span class="pl-k">:</span> <span class="pl-smi">botConnection</span>.<span class="pl-smi">conversationId</span> } <span class="pl-c"><span class="pl-c">//</span>you could define your own userId here</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L48" class="blob-num js-line-number" data-line-number="48">
                </td>
                
                <td id="file-index-js-LC48" class="blob-code blob-code-inner js-file-line">
                  })
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L49" class="blob-num js-line-number" data-line-number="49">
                </td>
                
                <td id="file-index-js-LC49" class="blob-code blob-code-inner js-file-line">
                  .<span class="pl-en">subscribe</span>(<span class="pl-smi">id</span> <span class="pl-k">=></span> {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L50" class="blob-num js-line-number" data-line-number="50">
                </td>
                
                <td id="file-index-js-LC50" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L51" class="blob-num js-line-number" data-line-number="51">
                </td>
                
                <td id="file-index-js-LC51" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>we store the conversation id which we get back from postActivity(...) in the LocalStorage</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L52" class="blob-num js-line-number" data-line-number="52">
                </td>
                
                <td id="file-index-js-LC52" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>we will need this in case of conversation resuming</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L53" class="blob-num js-line-number" data-line-number="53">
                </td>
                
                <td id="file-index-js-LC53" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">localStorage</span>.<span class="pl-c1">setItem</span>(<span class="pl-s"><span class="pl-pds">"</span>pushsample.botConnection.conversationId<span class="pl-pds">"</span></span>, <span class="pl-smi">botConnection</span>.<span class="pl-smi">conversationId</span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L54" class="blob-num js-line-number" data-line-number="54">
                </td>
                
                <td id="file-index-js-LC54" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L55" class="blob-num js-line-number" data-line-number="55">
                </td>
                
                <td id="file-index-js-LC55" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L56" class="blob-num js-line-number" data-line-number="56">
                </td>
                
                <td id="file-index-js-LC56" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/index.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-index-js">index.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

As you can see in the code above, we also store the **conversationid** in the browser **localStorage** so it will persist. We need this to be able to resume the conversation when the user clicks on a notification after the tab was closed. We handle this by adding a get parameter to the webpage url: **?isBack=y**. To resume a conversation using Direct Line, you just have to give back the **conversationid** as we do here:

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-index-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-index-js-L9" class="blob-num js-line-number" data-line-number="9">
                </td>
                
                <td id="file-index-js-LC9" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (<span class="pl-en">getParameterByName</span>(<span class="pl-s"><span class="pl-pds">"</span>isback<span class="pl-pds">"</span></span>) <span class="pl-k">===</span> <span class="pl-s"><span class="pl-pds">'</span>y<span class="pl-pds">'</span></span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L10" class="blob-num js-line-number" data-line-number="10">
                </td>
                
                <td id="file-index-js-LC10" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L11" class="blob-num js-line-number" data-line-number="11">
                </td>
                
                <td id="file-index-js-LC11" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>if we are resuming an existing conversation, we get back the conversationid from LocalStorage</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L12" class="blob-num js-line-number" data-line-number="12">
                </td>
                
                <td id="file-index-js-LC12" class="blob-code blob-code-inner js-file-line">
                  botConnection <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">DirectLine.DirectLine</span>({
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L13" class="blob-num js-line-number" data-line-number="13">
                </td>
                
                <td id="file-index-js-LC13" class="blob-code blob-code-inner js-file-line">
                  secret<span class="pl-k">:</span> <span class="pl-c1">DIRECTLINE_SECRET</span>,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L14" class="blob-num js-line-number" data-line-number="14">
                </td>
                
                <td id="file-index-js-LC14" class="blob-code blob-code-inner js-file-line">
                  conversationId<span class="pl-k">:</span> <span class="pl-smi">localStorage</span>.<span class="pl-c1">getItem</span>(<span class="pl-s"><span class="pl-pds">"</span>pushsample.botConnection.conversationId<span class="pl-pds">"</span></span>),
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L15" class="blob-num js-line-number" data-line-number="15">
                </td>
                
                <td id="file-index-js-LC15" class="blob-code blob-code-inner js-file-line">
                  webSocket<span class="pl-k">:</span> <span class="pl-c1">false</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-index-js-L16" class="blob-num js-line-number" data-line-number="16">
                </td>
                
                <td id="file-index-js-LC16" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/index.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-index-js">index.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

# **Listening to push notification in the background with the service worker**

Last but not least, we need to write the code that will sit in the browser and handle push notification event even if the website is not opened.

  * **Registering to push**

The first piece of code is the one handling the push events.  To do this we use the self.addEventListener() function. It takes an event name (here “push”) and a callback. Each time a new push notification is received, this callback is going to be called. Here, we just call **registration.showNotification()** which displays it using a nice image and some text. The payload variable is built using the event data (which is the notification text we send from the server).

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-service-worker-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-service-worker-js-L3" class="blob-num js-line-number" data-line-number="3">
                </td>
                
                <td id="file-service-worker-js-LC3" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">self</span>.<span class="pl-c1">addEventListener</span>(<span class="pl-s"><span class="pl-pds">'</span>push<span class="pl-pds">'</span></span>, <span class="pl-k">function</span> (<span class="pl-c1">event</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L4" class="blob-num js-line-number" data-line-number="4">
                </td>
                
                <td id="file-service-worker-js-LC4" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L5" class="blob-num js-line-number" data-line-number="5">
                </td>
                
                <td id="file-service-worker-js-LC5" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>creating the notification message (we should never be in the "no message" case)</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L6" class="blob-num js-line-number" data-line-number="6">
                </td>
                
                <td id="file-service-worker-js-LC6" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> payload <span class="pl-k">=</span> <span class="pl-c1">event</span>.<span class="pl-c1">data</span> <span class="pl-k">?</span> <span class="pl-c1">event</span>.<span class="pl-c1">data</span>.<span class="pl-c1">text</span>() <span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">'</span>No message...<span class="pl-pds">'</span></span>;
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L7" class="blob-num js-line-number" data-line-number="7">
                </td>
                
                <td id="file-service-worker-js-LC7" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L8" class="blob-num js-line-number" data-line-number="8">
                </td>
                
                <td id="file-service-worker-js-LC8" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>we show a notification to the user with the text message</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L9" class="blob-num js-line-number" data-line-number="9">
                </td>
                
                <td id="file-service-worker-js-LC9" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>and an icon which is hosted as a resource on the website</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L10" class="blob-num js-line-number" data-line-number="10">
                </td>
                
                <td id="file-service-worker-js-LC10" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c1">event</span>.<span class="pl-en">waitUntil</span>(
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L11" class="blob-num js-line-number" data-line-number="11">
                </td>
                
                <td id="file-service-worker-js-LC11" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">self</span>.<span class="pl-smi">registration</span>.<span class="pl-en">showNotification</span>(<span class="pl-s"><span class="pl-pds">'</span>Chat bot!<span class="pl-pds">'</span></span>, {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L12" class="blob-num js-line-number" data-line-number="12">
                </td>
                
                <td id="file-service-worker-js-LC12" class="blob-code blob-code-inner js-file-line">
                  body<span class="pl-k">:</span> payload,
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L13" class="blob-num js-line-number" data-line-number="13">
                </td>
                
                <td id="file-service-worker-js-LC13" class="blob-code blob-code-inner js-file-line">
                  icon<span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">'</span>/web/img/thinking_morphi.png<span class="pl-pds">'</span></span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L14" class="blob-num js-line-number" data-line-number="14">
                </td>
                
                <td id="file-service-worker-js-LC14" class="blob-code blob-code-inner js-file-line">
                  })
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L15" class="blob-num js-line-number" data-line-number="15">
                </td>
                
                <td id="file-service-worker-js-LC15" class="blob-code blob-code-inner js-file-line">
                  );
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L16" class="blob-num js-line-number" data-line-number="16">
                </td>
                
                <td id="file-service-worker-js-LC16" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/service-worker.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-service-worker-js">service-worker.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

  * **Handling click on notifications**

By default, clicking on a browser notification does nothing. You can add a custom behavior using the ‘notificationclick’ event in the service worker code. Its code is pretty straightforward as we list all the clients (a tab being also seen as a client), we look if one is displaying our web page. If yes and the focus is on another one, we switch to it. If yes and the focus is on it, we do nothing. And finally, if no, we reopen the page adding the **?isBack=y** parameter.

<div id="gist46734744" class="gist">
  <div class="gist-file">
    <div class="gist-data">
      <div class="js-gist-file-update-container js-task-list-container file-box">
        <div id="file-service-worker-js" class="file">
          <div itemprop="text" class="blob-wrapper data type-javascript ">
            <table class="highlight tab-size js-file-line-container" data-tab-size="8">
              <tr class="line">
                <td id="file-service-worker-js-L18" class="blob-num js-line-number" data-line-number="18">
                </td>
                
                <td id="file-service-worker-js-LC18" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">self</span>.<span class="pl-c1">addEventListener</span>(<span class="pl-s"><span class="pl-pds">'</span>notificationclick<span class="pl-pds">'</span></span>, <span class="pl-k">function</span> (<span class="pl-c1">event</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L19" class="blob-num js-line-number" data-line-number="19">
                </td>
                
                <td id="file-service-worker-js-LC19" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span> Android doesn't close the notification when you click on it </span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L20" class="blob-num js-line-number" data-line-number="20">
                </td>
                
                <td id="file-service-worker-js-LC20" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span> See: http://crbug.com/463146 </span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L21" class="blob-num js-line-number" data-line-number="21">
                </td>
                
                <td id="file-service-worker-js-LC21" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c1">event</span>.<span class="pl-smi">notification</span>.<span class="pl-c1">close</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L22" class="blob-num js-line-number" data-line-number="22">
                </td>
                
                <td id="file-service-worker-js-LC22" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L23" class="blob-num js-line-number" data-line-number="23">
                </td>
                
                <td id="file-service-worker-js-LC23" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span> This looks to see if the current is already open and </span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L24" class="blob-num js-line-number" data-line-number="24">
                </td>
                
                <td id="file-service-worker-js-LC24" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span> focuses if it is </span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L25" class="blob-num js-line-number" data-line-number="25">
                </td>
                
                <td id="file-service-worker-js-LC25" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c1">event</span>.<span class="pl-en">waitUntil</span>(
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L26" class="blob-num js-line-number" data-line-number="26">
                </td>
                
                <td id="file-service-worker-js-LC26" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L27" class="blob-num js-line-number" data-line-number="27">
                </td>
                
                <td id="file-service-worker-js-LC27" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>searching for all clients / tab opened in the browser</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L28" class="blob-num js-line-number" data-line-number="28">
                </td>
                
                <td id="file-service-worker-js-LC28" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-smi">clients</span>.<span class="pl-en">matchAll</span>({
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L29" class="blob-num js-line-number" data-line-number="29">
                </td>
                
                <td id="file-service-worker-js-LC29" class="blob-code blob-code-inner js-file-line">
                  type<span class="pl-k">:</span> <span class="pl-s"><span class="pl-pds">"</span>window<span class="pl-pds">"</span></span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L30" class="blob-num js-line-number" data-line-number="30">
                </td>
                
                <td id="file-service-worker-js-LC30" class="blob-code blob-code-inner js-file-line">
                  })
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L31" class="blob-num js-line-number" data-line-number="31">
                </td>
                
                <td id="file-service-worker-js-LC31" class="blob-code blob-code-inner js-file-line">
                  .<span class="pl-c1">then</span>(<span class="pl-k">function</span> (<span class="pl-smi">clientList</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L32" class="blob-num js-line-number" data-line-number="32">
                </td>
                
                <td id="file-service-worker-js-LC32" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L33" class="blob-num js-line-number" data-line-number="33">
                </td>
                
                <td id="file-service-worker-js-LC33" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>going through the list of clients/tab and trying to find our website</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L34" class="blob-num js-line-number" data-line-number="34">
                </td>
                
                <td id="file-service-worker-js-LC34" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">for</span> (<span class="pl-k">var</span> i <span class="pl-k">=</span> <span class="pl-c1"></span>; i <span class="pl-k"><</span> <span class="pl-smi">clientList</span>.<span class="pl-c1">length</span>; i<span class="pl-k">++</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L35" class="blob-num js-line-number" data-line-number="35">
                </td>
                
                <td id="file-service-worker-js-LC35" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">var</span> client <span class="pl-k">=</span> clientList[i];
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L36" class="blob-num js-line-number" data-line-number="36">
                </td>
                
                <td id="file-service-worker-js-LC36" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L37" class="blob-num js-line-number" data-line-number="37">
                </td>
                
                <td id="file-service-worker-js-LC37" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>if we find it, we put focus back on the tab</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L38" class="blob-num js-line-number" data-line-number="38">
                </td>
                
                <td id="file-service-worker-js-LC38" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> ((<span class="pl-smi">client</span>.<span class="pl-smi">url</span>.<span class="pl-c1">toLowerCase</span>() <span class="pl-k">==</span> baseurl <span class="pl-k">+</span> <span class="pl-s"><span class="pl-pds">'</span>/web/index.html<span class="pl-pds">'</span></span> <span class="pl-k">||</span> <span class="pl-smi">client</span>.<span class="pl-smi">url</span>.<span class="pl-c1">toLowerCase</span>() <span class="pl-k">==</span> baseurl <span class="pl-k">+</span> <span class="pl-s"><span class="pl-pds">'</span>/web/index.html?isback=y<span class="pl-pds">'</span></span>) <span class="pl-k">&&</span> <span class="pl-s"><span class="pl-pds">'</span>focus<span class="pl-pds">'</span></span> <span class="pl-k">in</span> client)
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L39" class="blob-num js-line-number" data-line-number="39">
                </td>
                
                <td id="file-service-worker-js-LC39" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">return</span> <span class="pl-smi">client</span>.<span class="pl-c1">focus</span>();
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L40" class="blob-num js-line-number" data-line-number="40">
                </td>
                
                <td id="file-service-worker-js-LC40" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L41" class="blob-num js-line-number" data-line-number="41">
                </td>
                
                <td id="file-service-worker-js-LC41" class="blob-code blob-code-inner js-file-line">
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L42" class="blob-num js-line-number" data-line-number="42">
                </td>
                
                <td id="file-service-worker-js-LC42" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">if</span> (<span class="pl-smi">clients</span>.<span class="pl-smi">openWindow</span>) {
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L43" class="blob-num js-line-number" data-line-number="43">
                </td>
                
                <td id="file-service-worker-js-LC43" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>if we did not find it, then we re-open it with the isback=y parameter</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L44" class="blob-num js-line-number" data-line-number="44">
                </td>
                
                <td id="file-service-worker-js-LC44" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-c"><span class="pl-c">//</span>to ensure that we resume the conversation using the conversationid</span>
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L45" class="blob-num js-line-number" data-line-number="45">
                </td>
                
                <td id="file-service-worker-js-LC45" class="blob-code blob-code-inner js-file-line">
                  <span class="pl-k">return</span> <span class="pl-smi">clients</span>.<span class="pl-en">openWindow</span>(<span class="pl-s"><span class="pl-pds">'</span>/web/index.html?isback=y<span class="pl-pds">'</span></span>);
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L46" class="blob-num js-line-number" data-line-number="46">
                </td>
                
                <td id="file-service-worker-js-LC46" class="blob-code blob-code-inner js-file-line">
                  }
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L47" class="blob-num js-line-number" data-line-number="47">
                </td>
                
                <td id="file-service-worker-js-LC47" class="blob-code blob-code-inner js-file-line">
                  })
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L48" class="blob-num js-line-number" data-line-number="48">
                </td>
                
                <td id="file-service-worker-js-LC48" class="blob-code blob-code-inner js-file-line">
                  );
                </td>
              </tr>
              
              <tr class="line">
                <td id="file-service-worker-js-L49" class="blob-num js-line-number" data-line-number="49">
                </td>
                
                <td id="file-service-worker-js-LC49" class="blob-code blob-code-inner js-file-line">
                  });
                </td>
              </tr>
            </table>
          </div>
        </div>
      </div>
    </div>
    
    <div class="gist-meta">
      <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44/raw/64a0672115af3a06c0d4bd84e4dd3b8f8051d582/service-worker.js" style="float:right">view raw</a> <a href="https://gist.github.com/meulta/8feb9ae9bc4e7a448361393a45c28f44#file-service-worker-js">service-worker.js</a> hosted with &#10084; by <a href="https://github.com">GitHub</a>
    </div>
  </div>
</div>

# **What’s next?**

Using **web push notifications** in a web chat control is obvious. There are a lot of other cases in which it can be really helpful. It can help you notify someone about a trending news, an update on your website or a new friend connection.

Understanding how web notifications are working and adding them to one of your projects is a great first step. Implementing more PWAs’ features can be simpler than you think. At Microsoft, we have recently introduced [PWA Builder](http://preview.pwabuilder.com/generator), which simplifies and automates building a manifest so it’s as easy as providing resources and a description for your app. It will also help you in the process of adding service workers features to your app, such as cache management. In a future version, it will certainly also help you create the service worker code needed to handle push notifications.

In a very near future, service workers will be available in [every modern browser](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/serviceworker/?q=service%20workers): **take this opportunity and be part of the Progressive Web Apps world!**

> If you have any question about this blog article, feel free to contact me on twitter: [@meulta](https://twitter.com/meulta)