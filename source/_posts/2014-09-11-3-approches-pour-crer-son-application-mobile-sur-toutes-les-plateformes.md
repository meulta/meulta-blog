---
id: 43
title: 3 approches pour créer son application mobile sur toutes les plateformes
date: 2014-09-11T00:11:40+00:00
author: Etienne-Margraff
layout: post
guid: https://blogs.msdn.microsoft.com/emargraff/2014/09/11/3-approches-pour-crer-son-application-mobile-sur-toutes-les-plateformes/
permalink: /fr/2014/09/11/3-approches-pour-crer-son-application-mobile-sur-toutes-les-plateformes/
orig_url:
  - http://blogs.msdn.microsoft.com/b/emargraff/archive/2014/09/11/3-approches-pour-cr-233-er-son-application-mobile-sur-toutes-les-plateformes.aspx
orig_site_id:
  - "16621"
orig_post_id:
  - "10557126"
orig_parent_id:
  - "10557126"
orig_thread_id:
  - "878570"
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
  - http://blogs.msdn.com/b/emargraff/archive/2014/09/11/3-approches-pour-crer-son-application-mobile-sur-toutes-les-plateformes.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="3 approches pour cr&#233;er son application mobile sur toutes les plateformes" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/emargraff/2014/09/11/3-approches-pour-crer-son-application-mobile-sur-toutes-les-plateformes/" />
    <meta property="og:site_name" content="Etienne Margraff" />
    <meta property="og:description" content="N’hésitez pas à me contacter sur twitter pour échanger à propos de cet article ! C’est un sujet très à la mode et qui anime pas mal de mes discussions au quotidien : quelle est la meilleure stratégie pour développer une application mobile ? Même si j’aimerais évidemment vivre dans un monde idéal où tout..." />
    <meta property="og:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8233.image_thumb_58953B5D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="3 approches pour cr&#233;er son application mobile sur toutes les plateformes" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/emargraff/2014/09/11/3-approches-pour-crer-son-application-mobile-sur-toutes-les-plateformes/" />
    <meta name="twitter:description" content="N’hésitez pas à me contacter sur twitter pour échanger à propos de cet article ! C’est un sujet très à la mode et qui anime pas mal de mes discussions au quotidien : quelle est la meilleure stratégie pour développer une application mobile ? Même si j’aimerais évidemment vivre dans un monde idéal où tout..." />
    <meta name="twitter:image" content="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8233.image_thumb_58953B5D.png" />
    
categories:
  - Uncategorized
tags:
  - Cordova
  - HTML5
  - Mobile
  - Responsive
  - Titanium
  - Xamarin
---
_N’hésitez pas à me contacter sur_ [_twitter_](https://twitter.com/emargraff) _pour échanger à propos de cet article !_

C’est un sujet très à la mode et qui anime pas mal de mes discussions au quotidien : quelle est la meilleure stratégie pour développer une application mobile ?

Même si j’aimerais évidemment vivre dans un monde idéal où tout le monde utiliserait des Windows Phone, il faut accepter la réalité : les gens ont accès à 3 plateformes majeures en terme de mobilité. Si je décide de créer une application et que j’ai pour objectif d’être le prochain **Yo** ou **Instagram,** je n’ai pas d’autres choix que d’adresser ces 3 cibles pour ne pas me couper d’une partie du monde.

C’est là que la prise de décision importante a lieu : **quelle stratégie adopter pour rendre mon application multiplateformes ?**

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8233.image_thumb_58953B5D.png" alt="image" width="321" height="322" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1778.image_6FC0B5DB.png)

Ce qu’on voit le plus souvent, notamment dans l’univers des startups, c’est l’impression que le choix a été écarté très rapidement pour se concentrer sur une seule plateforme pendant les premiers mois (et parfois années). Je pense que c’est une erreur et qu’il faut choisir avec soin l’approche que l’on va avoir en ayant toujours pour objectif d’être disponible sur toutes les cibles **le plus tôt possible**.

Chaque système d’exploitation mobile à ses propres conventions, ses propres règles de design et d’ergonomie. Les utilisateurs s’attendent à retrouver ses codes familiers. La difficulté est là : **on doit penser générique dans le développement mais spécifique dans le résultat**. Il faut donner à l’utilisateur l’impression qu’on a créé l’application pour lui et uniquement pour lui.

Pour ça, 3 approches : le **natif**, le **quasi-natif** permettant de partager du code et le **web** embarqué dans une application native.

Contrairement à ce que j’entend parfois, le choix n’est pas si évident et il faut prendre un peu de recul pour faire celui qui répondra au mieux à ses propres objectifs (et moyens).

# 1. Le natif

C’est l’approche la plus naturelle. On développe séparément pour chacune des plateformes dans le langage prévu pour elles.

Cette technique permet d’obtenir le résultat le plus proche du système ciblé. On utilise les outils dédiés à chacun des environnements et on dispose des meilleures conditions pour la réalisation et les tests de notre application.

Dans le cas de Windows Phone par exemple, on utilisera la [barre d’application](http://msdn.microsoft.com/en-us/library/windows/apps/ff431813(v=vs.105).aspx) alors que cette fonctionnalité est représentée différemment sur Android. Sur Windows Phone toujours, on utilisera le [principe du pivot](http://msdn.microsoft.com/en-us/library/windows/apps/ff941098(v=vs.105).aspx) alors que la tendance sur iOS est de présenter des onglets plus classiques.

Faire du natif, c’est faire 3 développements distincts. Très peu de choses sont mutualisées (peut-être la créa graphique ?) et chaque mise à jour ou correctif devra être réalisé 3 fois.

Cependant, cela offre :

  * La souplesse nécessaire à la réalisation d’une application qui colle parfaitement à l’écosystème de chaque téléphone
  * Des performances qui _peuvent_ êtres excellentes (relatif à la qualité du développement, évidemment !)

&nbsp;

C’est l’approche la plus chère et qui nécessite le plus de compétences et de connaissances mais c’est celle qui donne souvent la meilleure garantie de qualité.

A noter cependant que C++ peut être une alternative aux langages classiques de chaque plateforme. On retrouve même des outils comme ceux fournis par [embarcadero](http://www.embarcadero.com/fr/products/cbuilder/ios-development) pour partager ce code. C++ a par exemple été adopté par [dropbox](http://oleb.net/blog/2014/05/how-dropbox-uses-cplusplus-cross-platform-development/) pour partager le code métier (i.e. non lié à l’interface graphique) entre iOS et Android. Même si l’expérience n’a pas été poussée jusqu’à Windows Phone pour l’instant, c’est tout à fait possible car les plateformes Windows supportent C++ comme langage de développement mobile.

Pour faire du natif dans l’univers Microsoft, vous utilisez [Visual Studio](http://www.visualstudio.com/) et vous avez le choix entre plusieurs technos comme le C#, C++ ou HTML/Javascript (qui sera interprétée nativement par le système).

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/8117.image_thumb_25C7C59A.png" alt="image" width="481" height="395" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5037.image_286DF09A.png)

_**Note** : dans certains cas particuliers où il est acceptable de ne développer que pour une plateforme, on peut développer (nativement) une seule fois pour deux environnements si on reste dans le même univers. Par exemple, si la société ‘’A’’ développe une application pour ses commerciaux à la fois sur tablette et sur téléphone, elle peut choisir uniquement l’écosystème Microsoft car elle maitrise le parc matériel. Il est alors possible de partager une très grande partie du code entre la version Windows 8 (tablette) et Windows Phone (téléphone) avec le principe des_ [_applications universelles_](http://msdn.microsoft.com/fr-fr/library/windows/apps/dn609832.aspx) _tout en restant sur une version native_.

# **2. Le quasi-natif**

Si on écarte la solution native pour des raisons de coût et de réactivité lors des mises à jour et des correctifs, il faut se diriger vers une approche qui permet de partager le maximum de code possible.

Une des manières d’arriver à ce résultat est ce qu’on va appeler le ‘’quasi-natif’’. Le principe est simple : on utilise un seul langage de programmation et on développe une seule fois mais on utilise un ensemble d’outils pour compiler et packager une version de l’application adaptée à chaque cible. Pour cela, soit le code ‘’générique’’ est traduit dans le langage compris par la plateforme puis compilé nativement, soit il est compris et exécuté par une [machine virtuelle](http://fr.wikipedia.org/wiki/Machine_virtuelle#Machine_virtuelle_de_haut_niveau_2) lors de l’exécution.

Deux frameworks/outils sortent du lot pour atteindre cet objectif : **Xamarin** et **Titanium**.

[**Xamarin**](http://xamarin.com/), permet de développer une application pour iOS, Android et Windows/Windows Phone en utilisant le [langage de programmation C](http://msdn.microsoft.com/fr-fr/library/kx37x362.aspx)#. Le développement de l’interface graphique se fait dans le langage de chaque plateforme ce qui permet de se caler sur l’ergonomie attendue par les utilisateurs. Depuis quelques temps, il est également possible d’utiliser des contrôles graphiques communs avec [Xamarin.Forms](http://xamarin.com/forms). Les contrôles seront adaptés à chaque plateforme lui donner le look and feel adapté.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="example-app" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/0160.example-app_thumb_006062DD.png" alt="example-app" width="569" height="374" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/5342.example-app_2E4B24E4.png)

Même si ces composants Xamarin.Forms sont assez jeunes, ça laisse supposer qu’on pourra bientôt partager le code entre différentes plateformes sans pour autant trop lisser l’ergonomie.

_Bonus ultime :_ on utilise l’environnement de développement [Visual Studio](http://visualstudio.com/) qui permet d’avoir accès notamment à des éditeurs [WYSIWYG](http://fr.wikipedia.org/wiki/What_you_see_is_what_you_get) pour la création de l’interface graphique. On profite également de tous les outils puissants qui nous assistent dans la création d’applications dans cet outil ([IntelliSense](http://msdn.microsoft.com/fr-fr/library/hcw1s69b.aspx) et [Debug](http://msdn.microsoft.com/fr-fr/library/sc65sadd.aspx) notamment).

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6646.image_thumb_2D77E05C.png" alt="image" width="569" height="339" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1018.image_36D114DF.png)

[**Titanium**](http://www.appcelerator.com/titanium/) quant à lui repose sur un concept proche de Xamarin mais qui s’appuie sur le langage Javascript. Le code est traduit en partie lors de l’exécution et en partie à la génération de l’application dans l’équivalent en langage natif, donc très proche de ce qui est compris par le téléphone. On imagine donc un avantage en termes de performances.

Ce qu’on constate en premier lieu, quand on aborde Titanium, c’est que l’interface graphique est définie en créant des objets Javascript et non pas en utilisant un langage de description comme c’est le cas notamment pour Android et Windows Phone. C’est à mon sens un peu fastidieux et complexe à maintenir. On peut cependant le coupler à [Alloy](http://docs.appcelerator.com/titanium/3.0/#!/guide/Alloy_XML_Markup) qui permet de définir l’interface graphique en XML.

Un autre aspect important à noter est que Titanium n’offre pour l’instant pas le support quasi-natif sur Windows Phone, puisque dans ce cas c’est une webview qui est utilisée (sur le même principe que la stratégie 3.).

Si l’équipe de développement ne maîtrise que Javascript, c’est une alternative intéressante. Si vous maîtrisez C# ou ne craignez pas un léger apprentissage je ne peux que vous conseiller Xamarin.

**Par où commencer** si vous ne connaissez pas C# mais vous voulez vous lancer dans Xamarin ? Je vous invite à suivre la très bonne introduction proposée par [Sébastien](https://twitter.com/sebastienpertus) à travers ce cours gratuit : [http://www.microsoftvirtualacademy.com/training-courses/les-fondamentaux-du-developpement-en-c-sharp](http://www.microsoftvirtualacademy.com/training-courses/les-fondamentaux-du-developpement-en-c-sharp "http://www.microsoftvirtualacademy.com/training-courses/les-fondamentaux-du-developpement-en-c-sharp") et pour découvrir les bases de Xamarin, [Thomas](https://twitter.com/thomas_lebrun) et [Stéphanie](https://twitter.com/stepheup/) vous proposent ce cours : [http://www.microsoftvirtualacademy.com/training-courses/developper-une-application-cross-plateformes-avec-xamarin](http://www.microsoftvirtualacademy.com/training-courses/developper-une-application-cross-plateformes-avec-xamarin "http://www.microsoftvirtualacademy.com/training-courses/developper-une-application-cross-plateformes-avec-xamarin")

# 3. Le web

La 3ème approche est une extension naturelle d’une des fonctions premières des smartphones depuis leur apparition : l’accès au world wide web. Accéder au web à partir d’un mobile signifie notamment une chose : il y a un navigateur web sur le téléphone et on peut y exécuter de l’HTML et du Javascript.

Depuis toujours, on essaye de rendre nos sites web accessibles sur les mobiles. On a commencé en développant une version Mobile distincte puis en appliquant tous les principes qu’on regroupe derrière le terme **responsive**.

En partant de ces deux constats (le web marche sur tous les mobiles et on sait faire des sites qui s’affichent correctement sur un mobile) on peut se demander : pourquoi ne pas packager nos sites dans une application ? Cela aurait plein d’avantages : elle serait disponible sur les stores, en jouant un peu avec le CSS on peut donner l’impression que c’est une application classique et comme c’est de l’HTML c’est multiplateforme par définition.

Créer une application web/mobile c’est très simple : on créé une application native vide, qui contient un composant ‘’_navigateur web_’’ et on y affiche les fichiers HTML/Javascript qui correspondent à l’application. Une fois qu’on a cette **coquille native**, il suffit de mettre à jour les fichiers web dans l’application pour la faire évoluer. On crée cette coquille pour chaque plateforme, on utilise le même code HTML à l’intérieur et on a notre application multi-devices. Très simple, et très rapide à mettre en œuvre !

Là où l’idée se corse, c’est quand on veut utiliser des fonctionnalités du téléphone. La sauvegarde de fichier en local par exemple, l’utilisation de l’appareil photo ou encore l’accès aux contacts. C’est possible, mais complexe à réaliser. C’est là qu’entrent en jeu les frameworks comme **PhoneGap**.

PhoneGap est à l’origine une technologie créée par une société indépendante, puis rachetée par **Adobe**. Quand Adobe acquiert PhoneGap, elle décide de ne conserver que les services payants et confie le cœur de la technologie à la fondation Apache. C’est là qu’est né **Cordova**. Au final, PhoneGap s’appuie sur une version de Cordova et c’est donc exactement la même chose (modulo les offres proposées par Adobe, notamment de compilation et packaging automatisés).

A quoi sert PhoneGap/Cordova ? C’est ce qui va nous permettre de passer d’un mode “je bricole mon application web à la main” à un mode industriel ou “Cordova génère la coquille pour chaque plateforme”. Et en plus de générer la coquille, Cordova fourni un framework Javascript qui nous permet de communiquer avec les fonctionnalités du téléphone.

[<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" src="https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/6201.image_thumb_2CA20B23.png" alt="image" width="327" height="429" border="0" />](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/01/66/21/metablogapi/1300.image_35FB3FA6.png)

J’apprécie particulièrement cette approche car elle permet de rendre possible des scénarios où on partage un code quasi-identique entre un site web responsive et une application mobile qui apporte des fonctionnalités supplémentaires (le push, la géoloc, etc.).

[Microsoft OpenTech](http://msopentech.com/) propose un plugin à Visual Studio ([Multi-Device Hybrid Apps](http://msdn.microsoft.com/en-us/vstudio/dn722381.aspx)) qui simplifie la création d’applications Cordova. Cela permet entre autre de pouvoir faire du debugging pas à pas dans votre émulateur Android par exemple. Pour le débug dans l’émulateur de Windows Phone, je vous invite à lire l’article de [David](https://twitter.com/davrous/) : [http://blogs.msdn.com/b/davrous/archive/2014/07/21/how-to-remotely-debug-and-profile-the-performance-of-your-html5-websites-amp-apps-on-windows-phone.aspx](http://blogs.msdn.com/b/davrous/archive/2014/07/21/how-to-remotely-debug-and-profile-the-performance-of-your-html5-websites-amp-apps-on-windows-phone.aspx "http://blogs.msdn.com/b/davrous/archive/2014/07/21/how-to-remotely-debug-and-profile-the-performance-of-your-html5-websites-amp-apps-on-windows-phone.aspx")

Cependant, même si c’est une stratégie que j’affectionne, il faut avouer qu’elle n’est pas adaptée à tous les cas de figure et qu’elle a l’inconvénient de demander un travail d’intégration et de CSS particulièrement poussé pour obtenir un résultat qui ne ‘’fait pas site web’’.

Si vous voulez apprendre un peu plus en détail comment créer une application multi plateformes en vous basant sur Cordova (et AngularJS et BootStrap), je vous propose de suivre ce cours gratuit : [http://www.microsoftvirtualacademy.com/training-courses/creer-une-application-mobile-avec-cordova-phonegap-angularjs-et-bootstrap](http://www.microsoftvirtualacademy.com/training-courses/creer-une-application-mobile-avec-cordova-phonegap-angularjs-et-bootstrap "http://www.microsoftvirtualacademy.com/training-courses/creer-une-application-mobile-avec-cordova-phonegap-angularjs-et-bootstrap")

# Conclusion

L’objectif de cet article est avant tout de donner mon point de vue sur les approches majeures pour créer une application multiplateformes. Ce que je veux mettre en avant, c’est que le choix n’est pas si évident et qu’il est à faire en prenant en compte tous les aspects du contexte dans lequel on se trouve. Quand on maitrise les technos web, c’est très probable qu’on arrive à générer un résultat excellent avec la 3ème approche alors que des développeurs .NET seront certainement plus à l’aise avec Xamarin. Si on a déjà une application développée en natif dans le langage d’une des plateformes, il est tout à fait légitime de ne pas se lancer dans un redéveloppement complet avec Xamarin ou Titanium.

Une alternative qui transparait légèrement dans ce billet est de ne pas réaliser d’application mais un site web complètement responsive. Dans de nombreux cas, les seuls réels besoins sont : donner accès à l’information sur toutes les tailles d’écrans, et utiliser certaines fonctionnalités comme le partage vers les réseaux sociaux ou la géolocalisation. C’est possible en web pur, directement à partir d’un site web et c’est un choix adopté notamment par [The Verge](http://www.theverge.com/2014/9/2/6096609/welcome-to-verge-2-0) très récemment.

Permettre de donner accès aux fonctionnalités du matériel est d’ailleurs un sujet pris très au sérieux par les organismes qui travaillent sur les standards. Un tour rapide sur la page qui fait un état des lieu de ces travaux ([http://www.w3.org/2012/05/mobile-web-app-state/](http://www.w3.org/2012/05/mobile-web-app-state/ "http://www.w3.org/2012/05/mobile-web-app-state/")) permet de comprendre ce qu’on peut faire dans le monde du mobile avec le web. Dans cette mouvance, on peut noter l’approche super intéressante de [Mozilla](https://www.mozilla.org/) avec [Firefox OS](https://www.mozilla.org/fr/firefox/os/) qui est construit pour le web en s’appuyant sur ces standards destinés au mobile.

Ce qui est vraiment très intéressant c’est qu’il y a une solution pour tout le monde. Et qu’on arrive à un stade ou chacune est viable et permet d’obtenir quelque chose d’excellent.

Bien entendu, nous n’avons parlé que du côté client mais il faut garder à l’esprit que pour que tout cela tienne la route, il est nécessaire d’avoir un backend bien construit et qui soit utilisable partout. Cela signifie qu’il doit être consommable facilement à partir de chaque plateforme et pour ça, adopter une architecture REST est une bonne idée. Je vous conseille d’aller jeter un œil du côté des [Web API](http://www.asp.net/web-api) et / ou d’[Azure Mobile Services](http://azure.microsoft.com/en-us/documentation/services/mobile-services/) qui génère pour vous un backend prêt à consommer 🙂

&#8212;

A bientôt,

Etienne

_Nb :_ C_ertaines images utilisées dans ce billet sont tirées du site de Xamarin ou de certaines de leurs présentations._