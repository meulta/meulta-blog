---
id: 23
title: 7 raisons pour lesquelles Visual Studio 2015 est le meilleur outil pour développer une application Cordova
date: 2014-11-17T15:10:00+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2014/11/17/7-raisons-pour-lesquelles-visual-studio-2015-est-le-meilleur-outil-pour-dvelopper-une-application-cordova/
permalink: /fr/2014/11/17/7-raisons-pour-lesquelles-visual-studio-2015-est-le-meilleur-outil-pour-dvelopper-une-application-cordova/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2014/11/18/7-raisons-pour-lesquelles-visual-studio-2015-est-le-meilleurs-outil-pour-d-233-velopper-une-application-cordova.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10573683"
orig_parent_id:
  - "10573683"
orig_thread_id:
  - "882420"
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
  - http://blogs.msdn.com/b/emargraff/archive/2014/11/17/7-raisons-pour-lesquelles-visual-studio-2015-est-le-meilleur-outil-pour-dvelopper-une-application-cordova.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="7 raisons pour lesquelles Visual Studio 2015 est le meilleur outil pour d&#233;velopper une application Cordova" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2014/11/17/7-raisons-pour-lesquelles-visual-studio-2015-est-le-meilleur-outil-pour-dvelopper-une-application-cordova/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="N’hésitez pas à me contacter sur twitter (@emargraff) pour échanger à propos de cet article Il y a quelque temps, je vous donnais mon point de vue quant aux différentes possibilités qui s’offrent à vous pour créer une application multi-plateformes. Dans cet article, je vous propose de creuser un peu l’approche web avec Apache Cordova...." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4118.Capture_thumb_587DBD61.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="7 raisons pour lesquelles Visual Studio 2015 est le meilleur outil pour d&#233;velopper une application Cordova" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2014/11/17/7-raisons-pour-lesquelles-visual-studio-2015-est-le-meilleur-outil-pour-dvelopper-une-application-cordova/" />
    <meta name="twitter:description" content="N’hésitez pas à me contacter sur twitter (@emargraff) pour échanger à propos de cet article Il y a quelque temps, je vous donnais mon point de vue quant aux différentes possibilités qui s’offrent à vous pour créer une application multi-plateformes. Dans cet article, je vous propose de creuser un peu l’approche web avec Apache Cordova...." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4118.Capture_thumb_587DBD61.png" />
    
categories:
  - Uncategorized
tags:
  - Cordova
  - HTML5
  - Visual Studio 2015
---
> N’hésitez pas à me contacter sur twitter (@emargraff) pour échanger à propos de cet article

Il y a quelque temps, je vous donnais [mon point de vue](http://blogs.msdn.com/b/emargraff/archive/2014/09/11/3-approches-pour-cr-233-er-son-application-mobile-sur-toutes-les-plateformes.aspx) quant aux différentes possibilités qui s’offrent à vous pour créer une application multi-plateformes. Dans cet article, je vous propose de creuser un peu l’approche web avec [Apache Cordova](http://cordova.apache.org/).

Je ne vais pas revenir en détails sur ce qu’est Cordova. Je vous invite à lire l’article que je cite plus haut pour en comprendre les tenants et aboutissants. Pour le décrire en une phrase, il s’agit d’un framework qui vous permet d’utiliser les technologies web HTML5 et Javascript pour :

  * Créer une application mobile (i.e. packager un ensemble de pages html dans une application native grâce à un composant de type WebView)
  * Donner accès au développeur aux fonctionnalités du téléphone à l’aide d’une librairie Javascript commune à toutes les plateformes

&nbsp;

**Cordova : fonctionnement standard.**

Comme je l’explique dans mon précédent article concernant la création de jeux avec [WebGL, BabylonJS et Cordova (en anglais)](http://blogs.msdn.com/b/emargraff/archive/2014/11/12/easy-way-to-create-a-crossplatform-mobile-game-with-webgl-using-babylonjs-and-apache-cordova.aspx) : il y a un certain nombre d’étapes à réaliser pour configurer une plateforme qui permettra de compiler des applications **Windows**, **Android** et **iOS** avec Cordova. Il faut installer Android SDK, les outils iOS sur Mac, le JDK Java, les émulateurs, Cordova lui même avec NodeJS par exemple. Bref, c’est complexe et long. Une fois que c’est fait cependant, Cordova est relativement simple à utiliser. Quelques lignes de commandes permettent de réaliser les opérations classiques.

<pre class="code">cordova create myprojet</pre>

Créé un projet Cordova.

<pre class="code">cordova platform add windows</pre>

Ajoute la plateforme Windows.

<pre class="code">cordova platform add android</pre>

Ajoute la plateforme Android.

<pre class="code">cordova build windows</pre>

Build la version windows

<pre class="code">cordova run windows</pre>

Exécute la version Windows sur un périphérique connecté.

C’est simple, n’est-ce pas ? Simple oui: mais naviguer entre l’éditeur de code et la ligne de commande ne plait pas à tout le monde. Et surtout: comment faire pour déboguer l’application? Comment faire pour la tester sur iOS alors qu’on est sur Windows et qu’il faut le faire sur un Mac? Même si on a un mac à côté de soi, il faut transférer le code, relancer les lignes de commandes, et même là: comment déboguer ? Et le débug sur Android se fait systématiquement sur un vrai téléphone car l’émulateur est tellement lent…

**Des outils pour Cordova dans Visual Studio 2015?**

Les outils pour Cordova ne sont pas neufs dans Visual Studio. Il existe une extension qui s’appelle **Multi Devices Hybrid Apps** disponible depuis quelques temps pour la version 2013. La version 2015 apporte un grand nombre de nouveautés pour [le développement dans l’univers Windows](http://blogs.msdn.com/b/somasegar/archive/2014/11/12/opening-up-visual-studio-and-net-to-every-developer-any-application-net-server-core-open-source-and-cross-platform-visual-studio-community-2013-and-preview-of-visual-studio-2015-and-net-2015.aspx), notamment pour .NET. Mais ce n’est pas tout puisqu’un effort considérable est fait pour rendre les développeurs multi-plateformes plus productifs, notamment dans le cas de Cordova.

L’outil Multi Device Hybrid apps est renommé en **Cordova Tools for Visual Studio.** Il est téléchargeable en tant qu’extension pour Visual Studio 2013 et inclus en standard pour Visual Studio 2015. Parmi la longue liste d’intérêts que vous allez découvrir dans cet article, le premier n’est pas le moindre: l’installation de tous les éléments nécessaires au développement et à la compilation de projets avec Cordova.

Voici une capture d’écran de l’installeur qui vous donne une idée des outils automatiquement téléchargés et configurés pour vous :

[<img style="display: inline; border-width: 0px;" title="Capture" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4118.Capture_thumb_587DBD61.png" alt="Capture" width="447" height="628" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7774.Capture_7B3EF51E.png)

# Raison 1. Les fonctionnalités d’un éditeur de logiciels moderne

Une fois les outils installés, Visual Studio vous permet de créer un nouveau projet de type **Apache Cordova Apps**.

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3225.image_thumb_01A76F34.png" alt="image" width="626" height="456" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2577.image_717685D8.png)

Ce template est disponible en deux langages:

  * **Javascript**: pour les personnes qui souhaitent rester avec un langage familier et qui maîtrise déjà
  * [TypeScript](http://www.typescriptlang.org/): pour les personnes qui veulent conserver une syntaxe d’un langage typé tout en créant du Javascript standard et propre

> TypeScript n’est pas le sujet de cet article. Si vous voulez comprendre les avantages de ce langage, je vous invite à lire l’article de **David Catuhe** : [http://blogs.msdn.com/b/eternalcoding/archive/2014/04/28/why-we-decided-to-move-from-plain-javascript-to-typescript-for-babylon-js.aspx](http://blogs.msdn.com/b/eternalcoding/archive/2014/04/28/why-we-decided-to-move-from-plain-javascript-to-typescript-for-babylon-js.aspx "http://blogs.msdn.com/b/eternalcoding/archive/2014/04/28/why-we-decided-to-move-from-plain-javascript-to-typescript-for-babylon-js.aspx")

Une fois le projet créé, vous disposez d’une arborescence de fichiers claire et de la puissance de Visual Studio pour l’édition avec l’intelliSense dans le code CSS, Javascript et HTML.

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2860.image_thumb_2D15D2F2.png" alt="image" width="645" height="366" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4214.image_5999E176.png)

# Raison 2. Compiler pour la plateforme qu’on veut, rapidement

Le contenu du projet correspond grosso modo à ce que vous retrouvez normalement dans le répertoire **www** d’un projet Cordova. Le fichier index.html est le fichier principal qui sera exécuté au lancement de l’application.

Pour compiler vers la plateforme de notre choix, plus de lignes de commandes mais un choix dans une simple liste déroulante:

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2783.image_thumb_6007F40A.png" alt="image" width="453" height="257" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1817.image_70806505.png)

Dès lors qu’on compile, la plateforme est ajoutée, préparée et compilée. Rien de magique là dedans, tout est disponible dans le répertoire **bldDebug** (où ‘debug’ est à remplacer par la cible de compilation).

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5482.image_thumb_5815730A.png" alt="image" width="510" height="206" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6445.image_0F5BFA46.png)

> Dans le cas d’une application Windows, il est possible de choisir **Windows Phone (Universal).** Ce qui génère une application universelle Windows **Javascript**. Ceci signifie que dans le cas de la plateforme Windows, l’application générée tourne directement dans le téléphone et non pas dans une WebView. Javascript et HTML sont compris par le système comme langages “natifs”. Les applications Cordova sont donc plus rapides par définition sur ces environnements.

# Raison 3. Un émulateur Android ultra performant est disponible par défaut

Et quand je dis **ultra performant**, je pèse mes mots. Il boot en quelques secondes, comme c’est le cas pour celui de Windows Phone depuis plusieurs années. La principale raison de cette rapidité c’est qu’il tourne sous **Hyper-V**.

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2364.image_thumb_5CB32FD7.png" alt="image" width="645" height="491" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3108.image_10C2ADC9.png)

Il permet entre autres de simuler un mouvement du téléphone pour tester l’usage de l’accéléromètre :

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6663.image_thumb_3BE989E7.png" alt="image" width="653" height="370" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6740.image_468235E7.png)

Si vous travaillez sur une application qui utilise la géolocalisation, vous pouvez facilement changer celle de l’émulateur :

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7875.image_thumb_101B0502.png" alt="image" width="444" height="397" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2022.image_1F058674.png)

# Raison 4. Les outils de débogage

Un des points cruciaux quand on fait du développement c’est de pouvoir comprendre les problèmes qui surviennent lors de l’exécution de son code. Cela évite de faire des suppositions fausses, ou d’ajouter de la trace inutile partout dans son code au risque de créer un bruit inutile.

Pour pouvoir déboguer, on attache un débogueur à son code de manière à être prévenu quand une erreur survient, de faire du pas à pas, ou encore de positionner des points d’arrêt pour inspecter certaines variables.

Dans le cas du développement Web, on utilise l’explorateur de Dom et le débogueur de son navigateur préféré. Par exemple les outils accessibles en appuyant sur F12 dans IE 11 permettent de parcourir l’arborescence HTML, de visualiser le code Javascript, et comprendre les problèmes de performance, de tester en simulant un autre navigateur, etc.

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2248.image_thumb_5D997699.png" alt="image" width="613" height="332" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6131.image_57B9B19E.png)

Les outils de Visual Studio 2015 pour Cordova offrent la même expérience dans le cas d’une application qui tourne dans un émulateur ou sur un périphérique physique.

Quand on lance l’application par défaut dans l’émulateur Android, deux outils sont utilisables :

  * Le débogueur Javascript qui permet de positionner des points d’arrêt et voir l’état des variables

&nbsp;

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3716.image_thumb_62A0D5AA.png" alt="image" width="468" height="142" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2671.image_2510E730.png)

  * Le DOM explorer qui permet de visualiser le code HTML, de comprendre les styles CSS qui s’appliquent à chaque balise et de **<span style="text-decoration: underline;">modifier</span>** le code et les styles CSS avec un aperçu **<span style="text-decoration: underline;">en direct sans avoir besoin de relancer l’application</span>**

&nbsp;

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5125.image_thumb_3AB7F342.png" alt="image" width="785" height="445" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6505.image_2D2AA436.png)

> Pour avoir un bon exemple pour tester les outils, vous pouvez télécharger les samples officiels avec 3 versions proposées:
> 
>   * [Exemple avec AngularJS](http://go.microsoft.com/fwlink/?LinkID=398516)
>   * [Exemple avec BackboneJS](http://go.microsoft.com/fwlink/?LinkID=398517)
>   * [Exemple avec WinJS](http://go.microsoft.com/fwlink/?LinkID=398518)

# Raison 5. La gestion simplifiée des paramètres et des plugins

Visual Studio 2015 propose un fichier **config.xml** qui contient la liste des paramètres de configuration de l’application en cours de développement et la liste des plugins à installer à chaque fois que le développeur demande de compiler pour une plateforme donnée.

Les paramètres sont notamment : le nom de l’application, la page de démarrage (pour changer si vous ne voulez pas que ce soit index.html), la version de l’application, l’orientation possible, etc. Quand on ouvre le fichier **config.xml**, c’est un éditeur graphique qui est proposé par défaut, pour simplifier notre vie 🙂

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4300.image_thumb_79699E50.png" alt="image" width="680" height="482" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6661.image_032C7518.png)

Certains paramètres sont également disponibles par plateforme pour **Windows**, **Android** et **iOS**. Il est possible par exemple d’indiquer la version de Windows à cibler :

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5635.image_thumb_40776CA3.png" alt="image" width="368" height="110" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7838.image_3E3AE3E7.png)

la version minimum et maximum du SDK android supportée:

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2541.image_thumb_4B3754A9.png" alt="image" width="367" height="161" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1537.image_650B8AD8.png)

ou encore les informations relatives à iOS  (type d’application, version de l’OS, etc.):

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1263.image_thumb_41747DE2.png" alt="image" width="490" height="165" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6523.image_01A806AC.png)

Le fonctionnement classique de Cordova pour donner accès aux fonctionnalités du téléphone est de proposer d’ajouter le plugin correspondant. Il existe un plugin pour l’accéléromètre, un pour la géolocalisation, un autre pour l’accès à l’appareil photo, un pour les contacts du téléphone, etc.

> <span style="background-color: #ffffff;">La liste complète des plugins officiels est disponible ici : <a title="http://plugins.cordova.io/" href="http://plugins.cordova.io/">http://plugins.cordova.io/</a></span>

Il est possible d’ajouter des plugins officiels ou à partir de git avec la ligne de commande:

<pre class="code">cordova plugin add {nom du plugin ou url git}</pre>

Cela demande de connaître les noms des plugins et surtout de les ajouter manuellement, chacun en ligne de commande.

Visual Studio 2015 permet de modifier cette liste de plugins à partir du fichier de configuration, à l’aide de l’éditeur graphique. On a accès à la liste complète des plugins standards, à l’ajout de plugins personnalisés stockés localement ou à partir de Git et à la liste des plugins déjà installés dans le projet:

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1220.image_thumb_302637AE.png" alt="image" width="710" height="234" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4073.image_42D8A0B4.png)

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6747.image_thumb_5C67DFF4.png" alt="image" width="720" height="243" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8030.image_3D22A870.png)

# Raison 6. Le débogage iOS à partir de Visual Studio

Rien de tel pour un développeur que de tout faire à partir de son poste et à partir de son éditeur de code préféré. Avec Visual Studio, c’était déjà possible pour les plateformes Android et Windows. Depuis Visual Studio 2015, c’est possible pour iOS également.

Le principe est très simple : il faut installer sur votre Mac le logiciel **vs-mda-remote** développé par l’équipe qui créé les outils Cordova pour Visual Studio. Il est [disponible sur NPM](https://www.npmjs.org/package/vs-mda-remote) donc l’installation se fait avec une seule ligne de commande :

<pre class="code">sudo npm install –g vs-mda-remote</pre>

Une fois que c’est fait, vous avez besoin de configurer Visual Studio pour indiquer le service auquel se connecter. Cela se passe dans les Options (Tools > Options).

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3225.image_thumb_63ABC7C1.png" alt="image" width="588" height="343" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0880.image_3457C186.png)

Et voilà ! Vous n’avez plus qu’à lancer en débug, en choisissant l’émulateur cible :

[<img style="display: inline; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3630.image_thumb_626C5044.png" alt="image" width="563" height="397" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6888.image_254894BF.png)

# Raison 7. Visual Studio 2013 Community Edition est gratuit !

Si vous êtes développeur Open Source ou étudiant, la version Community Edition est gratuite pour vous ! C’est également le cas si vous travaillez dans une société de moins de 250 personnes, 5 licences sont offertes. (plus d’infos : [http://www.microsoft.com/fr-fr/download/details.aspx?id=13350](http://www.microsoft.com/fr-fr/download/details.aspx?id=13350 "http://www.microsoft.com/fr-fr/download/details.aspx?id=13350"))

Vous pouvez installer les outils pour Cordova aussi sur cette version 2013 : [http://www.visualstudio.com/en-us/explore/cordova-vs.aspx](http://www.visualstudio.com/en-us/explore/cordova-vs.aspx "http://www.visualstudio.com/en-us/explore/cordova-vs.aspx")

Pour Visual Studio 2015, pour l’instant c’est en preview, donc gratuit. Aucune raison de ne pas essayer 🙂

A télécharger ici : [http://www.visualstudio.com/news/vs2015-preview-vs](http://www.visualstudio.com/news/vs2015-preview-vs "http://www.visualstudio.com/news/vs2015-preview-vs")

Visual Studio 2013 community edition: [http://www.visualstudio.com/news/vs2013-community-vs](http://www.visualstudio.com/news/vs2013-community-vs "http://www.visualstudio.com/news/vs2013-community-vs")

> <span style="background-color: #ffffff;">N’hésitez pas à me contacter sur twitter (@emargraff) pour échanger à propos de cet article</span>