---
id: 121
title: Débuguer Node.js avec VS Code
date: 2015-11-24T00:00:00+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/11/24/dbuguer-node-js-avec-vs-code/
permalink: /fr/2015/11/24/dbuguer-node-js-avec-vs-code/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/11/24/d-233-buguer-node-js-avec-vs-code.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10656207"
orig_post_name:
  - d 233 buguer node js avec vs code
orig_parent_id:
  - "10656207"
orig_thread_id:
  - "899777"
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
  - "1477"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="D&#233;buguer Node.js avec VS Code" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/11/24/dbuguer-node-js-avec-vs-code/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter: http://twitter.com/meulta Quand on se lance dans le développement web, on démarre par une longue phase d’apprentissage des languages. A ce moment-là, on ne se pose pas trop la question du logiciel qu’on utilise pour écrire son code. On..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8546.image_thumb_2A2E4770.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="D&#233;buguer Node.js avec VS Code" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/11/24/dbuguer-node-js-avec-vs-code/" />
    <meta name="twitter:description" content="Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter: http://twitter.com/meulta Quand on se lance dans le développement web, on démarre par une longue phase d’apprentissage des languages. A ce moment-là, on ne se pose pas trop la question du logiciel qu’on utilise pour écrire son code. On..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8546.image_thumb_2A2E4770.png" />
    
categories:
  - Uncategorized
tags:
  - Debug
  - Node.js
  - Visual Studio Code
---
> _Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)

Quand on se lance dans le développement web, on démarre par une longue phase d’apprentissage des languages. A ce moment-là, on ne se pose pas trop la question du logiciel qu’on utilise pour écrire son code. On prend ce qu’on nous conseille à droite ou à gauche, généralement celui du premier tutoriel qu’on a suivi.

Dès qu’on progresse et qu’on arrive à un stade on maîtrise le code qu’on écrit, on commence à faire attention aux outils qu’on utilise. On démarre l’utilisation de **Gulp** ou **Grunt** pour minifier ses fichiers automatiquement ou vérifier son code JavaScript avec JSLint. Et dans ce processus d’amélioration de sa propre expérience de développement se pose la question de l’éditeur de code qu’on utilise. SublimeText ? Notepad++ ? Autre chose ? Le choix n’est pas simple et les défenseurs de l’un ou de l’autre vous donnerons leur point de vue un peu partout sur le net. 🙂

## Enter Visual Studio Code !

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8546.image_thumb_2A2E4770.png" alt="image" width="683" height="389" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0804.image_5D67F028.png)

<a href="https://www.microsoft.com/france/visual-studio/code/" target="_blank">Visual Studio Code</a> est une alternative très intéressante à ces outils. Il faut le voir comme un éditeur de code idéal pour un développeur web full stack. Parmi ses fonctionnalités les plus intéressantes on peut noter :

  * L’auto-complétion et l’intelliSense
  * La coloration syntaxique
  * Son extensibilité via des plugins accessibles au sein d’<a href="https://code.visualstudio.com/docs/editor/extension-gallery" target="_blank">une gallerie</a>
  * La gestion de nombreux langages tels que HTML, CSS / Sass / Less, JavaScript, C#, JSON, DockerFile, Markdown, TypeScript
  * L’intégration à Git (et donc GitHub)
  * L’éxécution de tâches Gulp, Grunt et autres systèmes de workflow
  * Le **debug de code côté serveur** tels que ASP.net et **Node.js**

Vous pouvez le télécharger gratuitement ici : [https://www.microsoft.com/france/visual-studio/code/](https://www.microsoft.com/france/visual-studio/code/ "https://www.microsoft.com/france/visual-studio/code/")

## Ne pas confondre avec Visual Studio

Visual Studio est un environnement de développement très complet proposé par Microsoft depuis des années. Il permet de faire toutes sortes de dev, que ce soit pour le web, pour le serveur, pour créer des applications Win32, des applications Android, iOS, Windows et développer pour le Cloud.

Visual Studio **Code** est un logiciel complétement différent. Il fonctionne sur **Linux**, **Mac** et **Windows** et est Open-Source ([https://github.com/Microsoft/vscode](https://github.com/Microsoft/vscode "https://github.com/Microsoft/vscode")).

Et surtout : Il est **extrêmement plus** léger que son cousin historique!

C’est cet outil que nous utilisons au quotidien pour développer l’outil de débug web open-source Vorlon.js (<http://www.vorlonjs.io>).

## Développer avec VS Code

Le fonctionnement de VS Code est très simple. Vous effectuez un clic droit sur un répertoire et demandez **Ouvrir avec Code.** Le répertoire et l’intégralité des fichiers qui s’y trouvent sont alors ouvert dans une instance de VS Code.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8738.image_thumb_2DD183AF.png" alt="image" width="338" height="195" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8132.image_300B7BBA.png)  [<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2311.image_thumb_1D5912B4.png" alt="image" width="271" height="199" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5224.image_0220B9B3.png)

Le langage est automatiquement découvert par l’outil et la coloration syntaxique se met en place.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8233.image_thumb_1C833D7B.png" alt="image" width="597" height="374" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7140.image_31722F3D.png)

## Intégrer votre outil de workflow

Quand on fait du développement web, même dans le cas d’une application Node.js, on a toujours des tâches à exécuter avant chaque test. Généralement, on utilise un outil comme Grunt ou Gulp pour automatiser ces tâches. Ces outils de workflow (ou “ordonnanceurs de tâches”) s’intègrent parfaitement à VS Code.

Dans l’exemple très basic disponible ici : [https://github.com/meulta/meultasamples/tree/master/debugNodeVSCode](https://github.com/meulta/meultasamples/tree/master/debugNodeVSCode "https://github.com/meulta/meultasamples/tree/master/debugNodeVSCode") vous trouverez un fichier gulpfile.js qui execute une tâche JSLint pour vérifier la syntaxe du code JavaScript de mes différents fichiers.

Vous pouvez l’exécuter en ligne de commande:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6165.image_thumb_0F41D5CA.png" alt="image" width="699" height="143" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5164.image_326F407C.png)

_Note : n’oubliez pas d’effectuer un **npm install** dans le répertoire au préalable pour installer les dépendances nécessaires. Et d’effectuer un **npm install –g gulp** si Gulp n’est pas installé sur votre poste._

Pour vous simplifier la vie, vous pourriez évidemment créer une tâche **watch** qui exécuterait tout votre workflow à chaque modification de fichier.

Une version intermédiaire existe dans Visual Studio Code. L’exécution du workflow se fait avec le raccourci clavier **Ctrl+Maj.+B**. La première fois il n’est pas configuré et VS Code vous propose de le faire pour vous:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3225.image_thumb_7C8F6CC3.png" alt="image" width="687" height="114" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/3365.image_33D5F3FF.png)

Cela a pour effet de créer le répertoire **.vscode**. Celui-ci contient toute la configuration spécifique à VS Code et notamment le fichier **tasks.json** qui défini vos tâches et comment les exécuter.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0726.image_thumb_1B687153.png" alt="image" width="686" height="303" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6560.image_1E7ACF48.png)

Vous n’avez plus qu’à ajouter la configuration décrivant la tâche qui doit être exécutée (ici **default**). Chaque fois que vous ferez le raccourci Ctrl+Shift+B le processus sera exécuté avec un retour direct dans VS Code!

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1108.image_thumb_5F41C70C.png" alt="image" width="690" height="271" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6471.image_71F43012.png)

## Débuguer son application Node.js

### Configuration

Vous avez maintenant un environnement simple à utiliser pour créer votre code, pour vérifier sa qualité et effectuer n’importe quel traitement tel que de la minification ou du bundling.

Un des aspects intéressants de VS Code est que vous pouvez réaliser du debug live et pas à pas de votre code.

Le debug et toutes les fonctionnalités associées sont regroupées dans le dernier onglet situé dans le bandeau gauche. Lorsque vous cliquez sur le bouton en forme de triangle vert (le bouton “play”) cela aura pour effet de démarrer le debug:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5861.image_thumb_29CB9598.png" alt="image" width="514" height="426" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5074.image_15B2790F.png)

Au tout premier lancement VS Code vous demande le type d’application que vous souhaitez débuguer:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0447.image_thumb_36C8065A.png" alt="image" width="524" height="273" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0574.image_46D44460.png)

Peu importe votre choix, cela aura pour effet de créer le fichier .**vscode/launch.json** qui contient tous les paramètres de débug avancés. Vous pouvez y configurer par exemple le type de debug (ici : “node”), le fichier JavaScript à exécuter : ici, je l’ai modifié en **server.js:**

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0118.image_thumb_173DD7E7.png" alt="image" width="757" height="688" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6710.image_52005F5B.png)

Dans ce fichier, vous pouvez définir deux configurations.

  * **Launch :** démarre le processus node et s’y attache
  * **Attach** : permet de s’attacher à un processus node déjà démarré.

Pour chacun de ces modes de démarrage, vous pouvez choisir les paramètres associés.

Quand vous démarrez le débug (en **launch** ou en **attach**), une console apparaît et vous donne les logs générés par votre application Node. Vous avez également accès à un panneau de contrôle en haut de l’outil qui vous permet de naviguer dans l’exécution du code ou d’arrêter le debug avec le bouton stop (carré rouge).[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4048.image_thumb_2B148E32.png" alt="image" width="774" height="368" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0044.image_6A4D966D.png)

### Les points d’arrêt

Lorsque l’on effectue une session de debug, un des objectifs est de pouvoir jeter un œil à l’exécution du code à un instant T. On évite généralement de parcourir tout le code ligne à ligne, on a plutôt tendance à laisser libre cours et à l’arrêter à la ligne de code choisie. C’est tout l’intérêt des points d’arrêt.

Pour positionner un point d’arrêt vous pouvez :

  * Cliquer dans la marge à la hauteur de la ligne pour laquelle vous souhaitez le définir
  * Positionner le curseur dans le code et appuyer sur la touche F9

Dans tous les cas cela à pour effet d’ajouter une pastille rouge au niveau de votre ligne de code.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8204.image_thumb_62E96306.png" alt="image" width="476" height="115" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6786.image_0F065FF8.png)

Vous pouvez également modifier cette liste de points d’arrêt dans le panneau de débug à gauche de VS Code. Si vous décochez un point d’arrêt, il ne sera temporairement plus pris en compte:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0333.image_thumb_2968E3C0.png" alt="image" width="388" height="178" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7167.image_12A70B86.png)

Dans notre exemple, il suffit de naviguer sur la page <http://127.0.0.1:8000/> et cela appellera le code pour lequel nous avons défini un point d’arrêt. L’exécution de l’application est alors stoppée (la ligne sur laquelle on est arrêté est surlignée en jaune):

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4135.image_thumb_02312B3C.png" alt="image" width="708" height="277" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2804.image_728E8F79.png)

_Note : La ligne surlignée n’est pas encore exécutée. C’est la prochaine qui sera lancée._

Vous pouvez alors vous déplacer dans le code et demander l’exécution des lignes suivantes grâce aux boutons situés dans la barre supérieure, de gauche à droite:

  * **Continue (F5)**: reprend l’exécution du code jusqu’au prochain point d’arrêt ou jusqu’à ce que l’application s’arrête ou soit en standby.
  * **Step Over (F10)**: Exécute la ligne de code courante mais reste dans le scope de code actuel (si c’est une fonction, le débug exécute toute la fonction dans entrer dans le code en pas à pas).
  * **Step Into** **(F11)**: Exécute la ligne de code courante et s’il s’agit d’une fonction, arrête l’exécution à la première ligne de code dans cette fonction. Cela permet de parcourir en pas à pas le contenu de la fonction également.
  * **Step Out** **(Maj.+F11)**: Exécute la ligne courante et toutes les lignes de la fonction actuelle jusqu’à en sortir.
  * **Stop**: Arrête la session de débug et arrête l’application Node.

### 

### Comprendre le contexte d’exécution

L’intérêt du débug ne se limite pas à exécuter les lignes de codes les unes après les autres. L’objectif principal est de consulter l’état des variables au fil de l’eau ainsi que la pile d’appel (i.e. l’enchainement des fonctions les unes dans les autres).

Pour visualiser une variable, vous avez plusieurs solutions.

**Survoler quelques instants la variable dans le code pour voir apparaître un popup**

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4705.image_thumb_3C4288CC.png" alt="image" width="608" height="362" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/4606.image_714C874B.png)

**Parcourir l’intégralité des variables présentes via le volet de débug**

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5706.image_thumb_44C878C7.png" alt="image" width="499" height="443" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1184.image_74EFC38A.png)

_Notez que vous pouvez déplier l’arborescence pour découvrir l’ensemble des variables et leurs propriétés/enfants._

**Ajouter une variable à l’onglet watch pour en suivre de prêt l’évolution**:

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5008.image_thumb_4AA5AD11.png" alt="image" width="568" height="331" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5633.image_3A96DE5A.png)

L’onglet **CALL STACK** quand à lui vous permet de connaître l’enchaînement des appels de fonctions qui ont permis d’arriver à la ligne de code à laquelle vous vous trouvez.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0880.image_thumb_1C4EB815.png" alt="image" width="579" height="251" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0456.image_681A8ECE.png)

Dans l’exemple ci-dessus, on remarque que la fonction dans laquelle on est arrêtée a en réalité été appelée par la fonction **emitTwo** située dans le fichier **events.js** qui elle-même avait été appelée par **emit** située dans le même fichier.

Si vous cliquez sur une de ces lignes, un volet s’ouvre sur la droite et vous indique le code exact qui a effectué l’appel :

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/7384.image_thumb_61228E5C.png" alt="image" width="728" height="331" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0068.image_16FFD164.png)

# Et pour finir…

Je vous ai donné ici un premier aperçu de ce que vous pouvez réaliser avec VS Code et surtout son débuguer. C’est maintenant à vous de jouer pour dénicher les bugs les plus tenaces dans votre code.

Téléchargez Visual Studio Code gratuitement ici : [https://www.microsoft.com/france/visual-studio/code/](https://www.microsoft.com/france/visual-studio/code/ "https://www.microsoft.com/france/visual-studio/code/") et démarrez votre première session de débug ! 🙂

Vous pouvez également aller plus loin dans le débug web avec Vorlon.js. C’est un outil qui permet de reproduire l’expérience des outils F12 qu’on trouve dans tous les navigateurs mais à distance et entre tous les navigateurs. C’est un outil open source disponible sur <http://www.vorlonjs.io> !

> _Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)