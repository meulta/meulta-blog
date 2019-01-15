---
id: 101
title: Une liste de bonnes pratiques pour le web moderne !
date: 2015-12-11T09:09:00+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2015/12/11/une-liste-de-bonnes-pratiques-pour-le-web-moderne/
permalink: /fr/2015/12/11/une-liste-de-bonnes-pratiques-pour-le-web-moderne/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2015/12/11/une-liste-de-bonnes-pratiques-pour-le-web-moderne.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10659959"
orig_post_name:
  - une liste de bonnes pratiques pour le web moderne
orig_parent_id:
  - "10659959"
orig_thread_id:
  - "900565"
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
  - "1132"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Une liste de bonnes pratiques pour le web moderne !" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/12/11/une-liste-de-bonnes-pratiques-pour-le-web-moderne/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter: http://twitter.com/meulta Le web est parti d&#8217;un rêve simple : partager. Partager de l&#8217;information, du contenu, des images, et plus tard des vidéos et des contenus plus riches. C&#8217;est pour cela que les langages du web ont toujours permis..." />
    <meta property="og:image" content="http://geekcommunicant.com/blog/wp-content/uploads/2014/04/logo_html5.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Une liste de bonnes pratiques pour le web moderne !" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2015/12/11/une-liste-de-bonnes-pratiques-pour-le-web-moderne/" />
    <meta name="twitter:description" content="Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter: http://twitter.com/meulta Le web est parti d&#8217;un rêve simple : partager. Partager de l&#8217;information, du contenu, des images, et plus tard des vidéos et des contenus plus riches. C&#8217;est pour cela que les langages du web ont toujours permis..." />
    <meta name="twitter:image" content="http://geekcommunicant.com/blog/wp-content/uploads/2014/04/logo_html5.png" />
    
categories:
  - Uncategorized
tags:
  - Accessibility
  - HTML5
---
> _Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)

Le web est parti d&#8217;un rêve simple : partager. Partager de l&#8217;information, du contenu, des images, et plus tard des vidéos et des contenus plus riches. C&#8217;est pour cela que les langages du web ont toujours permis d&#8217;écrire du code une seule fois et le voir affiché agréablement sur tous les écrans du monde.

<img src="http://geekcommunicant.com/blog/wp-content/uploads/2014/04/logo_html5.png" alt="Afficher l'image d'origine" width="668" height="391" />

HTML, CSS, JavaScript et tous les langages et outils qui gravitent autour permettent de créer ce code qui fonctionnera sur tous les navigateurs de la planète.

La manière dont on écrit ce code a beaucoup évolué à travers le temps. A une certaine époque, tout le monde trouvait normal de faire de la mise en page en utilisant des tableaux. C&#8217;est une hérésie aujourd&#8217;hui, de nombreuses fonctionnalités HTML et CSS nous permettent de gérer la mise en page et la mise en forme d&#8217;un contenu de façon plus souple. Et pour JavaScript, on est passé en quelques années de code écrit exclusivement pas le développeur du site à une liste interminable de frameworks qu&#8217;il faut connaître, sélectionner et mettre à jour.

Depuis les années 90 le W3C est là pour définir les standards. Sa mission est principalement de permettre l&#8217;accès de l&#8217;information à tous. Il faut d&#8217;ailleurs voir ces standards comme des recommandations que l&#8217;on choisit de suivre ou pas. Cela a un côté parfois gênant puisqu&#8217;il est possible d&#8217;écrire du code pour le web qui fonctionnera parfaitement sans pour autant suivre toutes les recommandations d&#8217;accessibilité par exemple. On peut également créer un site web qui s&#8217;exécute correctement alors qu&#8217;il utilise une librairie JavaScript obsolète. Pire, on peut ne tester que sur un seul navigateur, et ne pas considérer les autres…

Un développeur web d&#8217;aujourd&#8217;hui doit avoir en tête un ensemble de bonne pratiques, qui lui permettent de façonner ses créations web comme un artisan cherche un juste équilibre entre le l&#8217;art et le côté pratique.

Nous avons essayé de regrouper un ensemble de bonnes pratiques à suivre comme une sorte de checklist. Pour cela, nous avons identifié 5 points distincts. Cette liste n&#8217;est évidemment pas exhaustive et n&#8217;hésitez pas à proposer des modifications ou ajout !

Pour vous éviter de devoir tout vérifier à la main, vous pouvez utiliser l&#8217;outil de scan disponible en ligne :

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1004.image_thumb_1C3C56CB.png" alt="image" width="716" height="409" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/2043.image_0652E47B.png)

[https://dev.windows.com/fr-fr/microsoft-edge/tools/staticscan/](https://dev.windows.com/fr-fr/microsoft-edge/tools/staticscan/ "https://dev.windows.com/fr-fr/microsoft-edge/tools/staticscan/")

Notez que si vous scannez mon blog vous allez trouver quelques erreurs 😉 La plateforme que nous utilisons est en cours de migration ça ne devrait plus être long ! 🙂

# Vérification 1 : Est-ce que vous utilisez correctement les préfixes CSS ?

Le principe de CSS est très simple: on sélectionne un élément HTML et on y applique un style et des effets particuliers grâce à une liste de propriétés. Ces propriétés ne sont pas toujours finalisées et parfois, elle ne sont pas disponibles dans tous les navigateurs.

Généralement, elle sont implémentées dans un navigateur en premier et pour ne pas perturber les autres, un préfixe vendeur est utilisé. Par exemple, si Mozilla ajoute une propriété qui n&#8217;est pas encore standardisée, la mettre en oeuvre nécessitera d&#8217;utiliser le préfixe -moz-NOMDELAPROPRIETE. En faisant cela, le dev a conscience que ça ne fonctionnera que dans Firefox et qu&#8217;il faudra ajouter par la suite les propriétés -ms, -webkist, -o (pour Opéra), et finalement la version standardisée non préfixée quand chacun d&#8217;entre eux seront disponibles. Il faut toujours conserver l&#8217;intégralité des préfixes pour être certain que la propriété est appliquée dans le cas d&#8217;un navigateur un peu ancien qui ne supporterait pas encore la version non préfixée.

Le problème, c&#8217;est que bien souvent les développeurs ne précisent pas l&#8217;intégralité des préfixes. Ils se contentent souvent de -webkit. Et un navigateur a beau gérer une fonctionnalité, si on ne lui demande pas de l&#8217;utiliser, il ne l&#8217;utilisera pas. Et dans ce cas le site ne s&#8217;affichera pas correctement.

Même si nous continuons à expliquer cela à l&#8217;ensemble des développeurs dès que nous en avons l&#8217;occasion, nous avons décidé de corriger automatiquement ces erreurs dans Microsoft Edge dès que possible. Si on constate qu&#8217;une version préfixée est précisée mais que la version -ms n&#8217;est pas présente, nous l&#8217;ajoutons automatiquement avant d&#8217;interpréter la page. De cette manière, oublier un préfixe est moins gênant.

Essayez d&#8217;y faire attention quand même 😉

# Vérification 2 : Générez-vous un contenu différent pour chaque navigateur ?

C&#8217;est un point très important. Par le passé il était fréquent de vérifier le navigateur qui demande d&#8217;afficher notre site web et de potentiellement réagir à cela en envoyer un balisage HTML (ou pire: un contenu) différent. C&#8217;est une pratique très peu adaptée dans le cadre du web moderne. Il vaut mieux envoyer le même code et le même contenu et tester la présence des fonctionnalités qu’on souhaite utiliser.

C&#8217;est un sujet très important car la détection de navigateur ne permet pas d&#8217;avoir un site web pérenne. Cela part d&#8217;une bonne idée: essayer de deviner les fonctionnalités qu&#8217;on peut utiliser en fonction de l&#8217;environnement dans lequel on est rendu. Mais comment gérer l&#8217;évolution des navigateurs ? Comment faire en sorte que dès qu&#8217;ils supportent ce qu&#8217;il ne supportaient pas avant, la version qui lui est dédiée l&#8217;utilise bien?

C&#8217;est exactement pour cela que l&#8217;on choisit maintenant de détecter la présence de la fonctionnalité plutôt que d&#8217;essayer de le deviner. A l&#8217;aide de JavaScript, on peut par exemple détecter dynamiquement que le stockage local est supporté. Si c&#8217;est le cas, parfait, utilisons-le ! Sinon, il faut trouver une alternative ou prévenir l&#8217;utilisateur qu&#8217;il n&#8217;aura pas accès à cette fonctionnalité.

Pour vous simplifier la vie et détecter facilement ce que le navigateur gère en termes de fonctionnalités web, vous pouvez utiliser une librairie telle que Modernizr.

# Vérification 3: utilisez-vous des plugins ?

Le web est crossplateformes. C&#8217;est même certainement la technologie la plus crossplateformes au monde. Grâce à ça, un site web que vous écrivez pourra être exécuté sur une quantité incroyable de navigateurs et de périphériques.

Les plugins (activex, applet Java, etc.) ont été imaginées dans un monde ou accéder à un site web ne se faisait que sur desktop. Cela permettait notamment de combler facilement certains manques de la plateforme web. Quelque chose est impossible à faire en HTML ? Faisons un activeX ! JavaScript n&#8217;est pas assez performant ? Créons un applet Java !

Nous vivons désormais dans un monde ou HTML couplé à CSS est un langage extrêmement puissant, ou tout ou presque est possible. Nous vivons également dans un monde ou V8, le moteur JavaScript de Chrome ou Chakra, celui de Microsoft Edge atteignent des performances excellentes.

Plus de raisons dans ce cas d&#8217;utiliser des plugins. D&#8217;autant que ceux-ci ne sont pas accessibles et que leur contenu est très complexe à référencer.

C&#8217;est pour cette raison que le web moderne, dans notre esprit, est un web ne contenant aucun de ces plugins.

# Vérification 4: Est-ce que vous avez mis à jour vos frameworks?

Le web est génial pour une raison simple: si vous voulez faire quelque chose il y a de fortes chances que quelqu&#8217;un l&#8217;a déjà fait avant vous. Et il y a même une probabilité qu&#8217;il ou elle ait packagé son code sous forme d&#8217;un framework réutilisable simplement.

Quand ces frameworks sont complexes comme par exemple jQuery, Angular.js ou React, ils sont mis à jour fréquemment. Au fil des versions, certaines fonctionnalités peuvent ne plus être supportées. Chaque framework a une liste de versions qui sont obsolètes.

C&#8217;est très important de s&#8217;assurer que l&#8217;on utilise bien des versions à jour de ces différents frameworks.

# Vérification 5 : Est-ce que vous forcez une version particulière du moteur de rendu?

Depuis Internet Explorer 8 il est possible de choisir le mode de rendu de son site dans le navigateur. Le principe est très simple: vous ajoutez la balise x-ua-compatible et vous pouvez indiquer quel moteur doit être utilisé. Cela par d&#8217;une bonne intention : permettre à un développeur de ne pas avoir à changer son code à chaque fois qu&#8217;il y a une nouvelle version du navigateur.

Avec les versions modernes des navigateurs, il vaut mieux cependant ne pas fonctionner comme ça. Il est préférable de partir du principe que le navigateur va gérer correctement l&#8217;affichage du site et de lui faire confiance.

Pour pouvoir gérer la transition correctement, dans Microsoft Edge il y a désormais une valeur à ajouter au tag x-ua-compatible. Elle s&#8217;appelle &#8220;Edge&#8221; et elle permet de faire en sorte que dans le cas d&#8217;un navigateur moderne, le moteur utilisé soit le dernier. Vous pouvez temporairement conserver vos tags pour les anciens navigateurs si cela est vraiment nécessaire. Pensez à mettre à jour votre code rapidement cependant !

> _Si vous avez une question à propos de cet article, n&#8217;hésitez pas à me contacter via Twitter:_ [_http://twitter.com/meulta_](http://twitter.com/meulta)