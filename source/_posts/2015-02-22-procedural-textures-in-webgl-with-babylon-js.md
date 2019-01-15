---
id: 53
title: Procedural textures in WebGL with Babylon.JS
date: 2015-02-22T13:49:51+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/02/22/procedural-textures-in-webgl-with-babylon-js/
permalink: /en/2015/02/22/procedural-textures-in-webgl-with-babylon-js/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/02/22/use-procedural-textures-in-webgl-with-babylon-js.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10595060"
orig_parent_id:
  - "10595060"
orig_thread_id:
  - "887210"
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
  - http://blogs.msdn.com/b/emargraff/archive/2015/02/22/procedural-textures-in-webgl-with-babylon-js.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Procedural textures in WebGL with Babylon.JS" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/02/22/procedural-textures-in-webgl-with-babylon-js/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="This article talks about procedural textures in WebGL and how Babylon.JS can help you using and creating them. This feature is part of the Babylon.JS v2.0 release. Read more about it here : http://blogs.msdn.com/b/eternalcoding/archive/2015/02/18/what-s-new-in-babylon-js-v2-0.aspx Feel free to contact me on twitter (@meulta) to ask me any question about this article. What are Procedural Textures ?..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2438.clip_image002_thumb.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Procedural textures in WebGL with Babylon.JS" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/02/22/procedural-textures-in-webgl-with-babylon-js/" />
    <meta name="twitter:description" content="This article talks about procedural textures in WebGL and how Babylon.JS can help you using and creating them. This feature is part of the Babylon.JS v2.0 release. Read more about it here : http://blogs.msdn.com/b/eternalcoding/archive/2015/02/18/what-s-new-in-babylon-js-v2-0.aspx Feel free to contact me on twitter (@meulta) to ask me any question about this article. What are Procedural Textures ?..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2438.clip_image002_thumb.jpg" />
    
image: /wp-content/uploads/2015/02/Capture.png
categories:
  - Babylon.js
tags:
  - BabylonJS
  - Game
  - HTML5
  - WebGL
---
This article talks about procedural textures in WebGL and how [Babylon.JS](http://babylonjs.com/) can help you using and creating them.

This feature is part of the Babylon.JS v2.0 release. Read more about it here : [http://blogs.msdn.com/b/eternalcoding/archive/2015/02/18/what-s-new-in-babylon-js-v2-0.aspx](http://blogs.msdn.com/b/eternalcoding/archive/2015/02/18/what-s-new-in-babylon-js-v2-0.aspx "http://blogs.msdn.com/b/eternalcoding/archive/2015/02/18/what-s-new-in-babylon-js-v2-0.aspx")

> _Feel free to contact me on twitter ([@meulta](https://twitter.com/meulta)) to ask me any question about this article._

## What are Procedural Textures ?

[<img style="display: inline; border-width: 0px;" title="clip_image002" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2438.clip_image002_thumb.jpg" alt="clip_image002" width="538" height="377" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0116.clip_image002_2.jpg)

In classic texturing, we use 2D images, often pictures that have been shaped specifically to match an object. Let’s imagine you are creating a medieval fantasy game, working on a dwarf pub, where there are multiple, big, &#8220;old school&#8221; wooden tables.

With classic 2D texturing, you have 3 choices:

  * Create a single texture and use it on all of the tables (but every table is going to look the same)
  * Create a collection of various wood textures and apply them randomly to each table
  * Create a separate texture for each table, insuring that they each look different

No choice seems to be a good one. Enter **procedural textures**.

> Procedural texturing is a way to programmatically create a texture.

There are 2 types of procedural textures: **code-only**, and **code that references some classic 2D images**, sometimes called &#8216;refMaps&#8217; or &#8216;sampler&#8217; images.

One main advantage of procedural textures is that they are written using a **fragment shader** (using GLSL in the case of Babylon.js). That means that the code generating the texture is executed by the GPU and not the CPU (that is to say, NOT executed in JavaScript code). This has a huge performance impact in a positive way because in WebGL, JavaScript/CPU time is a critical resource: the more is done by the GPU, the better.

Procedural textures can be generated only once to create the texture which is put into cache **or** every 1, 2, 3, or 4, or more frames to be able to create an animated texture (like fire).

You can get more information about procedural textures here : [http://en.wikipedia.org/wiki/Procedural_texture](http://en.wikipedia.org/wiki/Procedural_texture "http://en.wikipedia.org/wiki/Procedural_texture")

&nbsp;

## **How to use standard procedural textures in Babylon.JS ?**

Like any other feature in Babylon.JS, the best way to test procedural textures (PT) is to use our playground (<http://www.babylonjs-playground.com>).

You can find a full sample using all standard procedural textures under the **Custom** menu :

[<img style="display: inline; border-width: 0px;" title="clip_image003" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0285.clip_image003_thumb.png" alt="clip_image003" width="337" height="184" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0246.clip_image003_2.png)

Using a procedural texture is done the exact same way it is done for classic textures.

You first have to create a Material object, attached to the current scene :

<pre class="code">var marbleMaterial = new BABYLON.StandardMaterial("marbleMat", scene);</pre>

Then you create the PT using one provided by default, or one you created yourself :

<pre class="code">var marbleTexture = new BABYLON.MarbleProceduralTexture("marbleText", 512, scene);</pre>

Finally, you have to set the material associated to the mesh you want to apply the texture to :

<pre class="code">square.material = marbleMaterial;</pre>

The result in this case is a random marble texture :

[<img style="display: inline; border-width: 0px;" title="clip_image005" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3731.clip_image005_thumb.jpg" alt="clip_image005" width="425" height="241" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2388.clip_image005_2.jpg)

If you want to see the whole code and play with it, you can go there : <http://www.babylonjs-playground.com/#1XPCZC#3>

You will also see that some procedural textures have additionnal custom properties. For the marble PT, you can set the number of tiles you want to generate in height and width. Default is 3 but you can go far more than that :

<pre class="code">marbleTexture.numberOfTilesHeight = 6;
marbleTexture.numberOfTilesWidth = 6;</pre>

[<img style="display: inline; border-width: 0px;" title="clip_image007" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6443.clip_image007_thumb.jpg" alt="clip_image007" width="428" height="234" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6087.clip_image007_2.jpg)

There are a lot more standard PT available by default with Babylon.JS like Fire, Wood or Road.

[<img style="display: inline; border-width: 0px;" title="clip_image009" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0827.clip_image009_thumb.png" alt="clip_image009" width="240" height="178" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8308.clip_image009_2.png) [<img style="display: inline; border-width: 0px;" title="clip_image011" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3821.clip_image011_thumb.png" alt="clip_image011" width="361" height="178" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5050.clip_image011_2.png)

&nbsp;

## How to create a custom procedural texture in Babylon.JS ?

As I told you earlier, a procedural texture is an image generated by the GPU using a pixel shader.

If you do not know what a **Pixel Shader** is I recommend you read this great article by my friend David Catuhe : <http://blogs.msdn.com/b/eternalcoding/archive/2014/04/17/learning-shaders-create-your-own-shaders-with-babylon-js.aspx>

Basically : it is a piece of code that will be called for each pixel the GPU need to render on a specific surface. The syntax is close to C and it always contains at least the **main** function. The role of this function is to define the color for the current pixel using the **gl_FragColor** variable.

Here is a really simple sample where we use the pixel position in the texture (vUV.x / vUV.y) to define the pixel color :

<pre class="code">#ifdef GL_ES
    precision highp float;
#endif
varying vec2 vUV;
void main(void) {
    gl_FragColor = vec4(vUV.x,vUV.y,-vUV.x, 1.0);
}</pre>

This will result in a beautiful gradient :

[<img style="display: inline; border-width: 0px;" title="clip_image013" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1157.clip_image013_thumb.jpg" alt="clip_image013" width="444" height="274" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0636.clip_image013_2.jpg)

The main difficulty when creating PTs is that in the pixel shader code, you only know the current pixel you need to choose a color for. You do not have access to the other pixel colors. So you need to use simple and complex algorithm to generate what you want such as the FBM one : [http://en.wikipedia.org/wiki/Fractional\_Brownian\_motion](http://en.wikipedia.org/wiki/Fractional_Brownian_motion).

You can find a lot of samples on <https://www.shadertoy.com/>

> **So now** : How can you create a custom procedural texture that use this Pixel Shader ?

You have to 3 solutions :

  * Embed this pixel shader in the JavaScript code using the ShaderStore
  * Store the shader as a Dom Element in your HTML code
  * Use a file based custom PT

## How to embed the pixel shader in the store ?

This can be done easily using the BABYLON.Effect.ShaderStore array :

<pre class="code">BABYLON.Effect.ShadersStore["LinesPixelShader"] =
    "#ifdef GL_ESn" +
   "precision highp float;n" +
    "#endifnn" +
    "varying vec2 vUV; n" +
   "void main(void) {n" +
    " gl_FragColor = vec4(vUV.x,vUV.y,-vUV.x, 1.0);n" +
    "}n" +
  "";</pre>

Note that your shader name should be suffixed with **PixelShader** as the procedural texture shader is always a pixel shader. **Babylon.JS** will automatically understand it is a pixel shader.

To use this shader, you just have to create a **CustomProceduralTexture** and put the name of your shader in the store. Note that the name of the Shader does not contains the &#8220;_PixelShader_&#8221; part as when defined in the store.

<pre class="code">var customProcText = new BABYLON.CustomProceduralTexture(
    "customtext", 
    "Lines", 
    1024, scene);</pre>

You can find and play with a full sample in the playground : <http://www.babylonjs-playground.com/#1XPCZC#5>.

## What is a file based Procedural Texture and why to use it ?

Until now we only used code generated textures. All standards PTs are done this way so you do not have to get images or some other resources for it to work.

When you want to create a PT which is using one or more images and/or you want to package this PT to share it with the community, it is a good idea to create a file based one.

A file based PT is a folder containing at least two files :

  * **config.json**
  * **custom.fragment.fx**

The config.json file reference the files needed by the texture and the parameters if any. The fragment file contains the shader code.

To use it, specify the folder path instead of the Pixel Shader name :

<pre class="code">var customProcText = new BABYLON.CustomProceduralTexture(
    "customtext", 
    "./textures/customProceduralTextures/land", 
    1024, scene);</pre>

**Find the full code here : <http://www.babylonjs-playground.com/#1XPCZC#4>**

In this sample we use to textures (dirt and grass) and mix them using an FBM algorithm to create a random ground.

[<img style="display: inline; border-width: 0px;" title="clip_image015" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4505.clip_image015_thumb.jpg" alt="clip_image015" width="544" height="286" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3755.clip_image015_2.jpg)****

## Want to go further ?

Now that you know the basics, the next step is to read the whole procedural texture documentation on the Babylon.JS wiki : <https://github.com/BabylonJS/Babylon.js/wiki/How-to-use-procedural-textures%3F>

Then, play with it on the playground or on your own code. I would love to hear feedback from you !

And do not hesitate to share your creation on the forum : <http://www.html5gamedevs.com/forum/16-babylonjs/>.

A lot of people will be happy to use your textures !

> _Feel free to contact me on twitter ([@meulta](https://twitter.com/meulta)) to ask me any question about this article._