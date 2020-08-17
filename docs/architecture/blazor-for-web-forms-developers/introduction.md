---
title: Présentation de Blazor pour les développeurs ASP.NET Web Forms
description: Présentation Blazor et écriture d’applications Web à pile complète avec .net
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: a5aae6cf02ccec84ac8642b6ce8d9c919755e868
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267566"
---
# <a name="an-introduction-to-no-locblazor-for-aspnet-web-forms-developers"></a>Présentation de Blazor pour les développeurs ASP.NET Web Forms

ASP.NET Web Forms Framework a été une agrafe de développement Web .NET depuis le début de la .NET Framework dans 2002. De retour lorsque le Web était en grande partie dans son ASP.NET, nous avons Web Forms rendu la création d’applications Web simple et productive en adoptant un grand nombre des modèles qui ont été utilisés pour le développement de postes de travail. Dans ASP.NET Web Forms, les pages Web peuvent être composées rapidement de contrôles d’interface utilisateur réutilisables. Les interactions de l’utilisateur sont gérées naturellement comme des événements. Il existe un écosystème riche de Web Forms contrôles d’interface utilisateur fournis par Microsoft et des fournisseurs de contrôle. Les contrôles facilitent la connexion aux sources de données et l’affichage de visualisations de données enrichies. Pour une inclinaison visuelle, le concepteur Web Forms fournit une interface de glisser-déplacer simple pour la gestion des contrôles.

Au fil des années, Microsoft a introduit de nouvelles infrastructures Web basées sur ASP.NET pour résoudre les tendances de développement Web. Parmi ces frameworks web, citons ASP.NET MVC, pages Web ASP.NET et plus récemment ASP.NET Core. Avec chaque nouvelle infrastructure, certaines ont prédit le déclin imminent de ASP.NET Web Forms et l’ont prédit comme un Framework Web obsolète obsolète. Malgré ces prédictions, de nombreux développeurs Web .NET continuent à trouver des ASP.NET Web Forms un moyen simple, stable et productif de faire leur travail.

Au moment de la rédaction du présent article, presque deux millions de développeurs Web utilisent ASP.NET Web Forms chaque mois. Le ASP.NET Web Forms Framework est stable jusqu’à ce que les documents, les exemples, les livres et les billets de blog de plus de dix ans restent utiles et pertinents. Pour de nombreux développeurs Web .NET, « ASP.NET » est toujours synonyme de « ASP.NET Web Forms » comme c’était le cas lors de la première création de .NET. Les arguments sur les avantages et les inconvénients de ASP.NET Web Forms comparés aux autres nouveaux frameworks web .NET peuvent se faire sur. ASP.NET Web Forms reste un Framework populaire pour la création d’applications Web.

Même dans ce cas, les innovations en matière de développement de logiciels ne ralentissent pas. Tous les développeurs de logiciels doivent rester au courant des nouvelles technologies et tendances. Deux tendances en particulier méritent d’être envisagées :

1. Passage à open source et multiplateforme
2. Déplacement de la logique de l’application vers le client

## <a name="an-open-source-and-cross-platform-net"></a>.NET Open source et multiplateforme

Quand .NET et ASP.NET Web Forms d’abord expédiés, l’écosystème de la plateforme a été très différent de ce qu’il fait aujourd’hui. Les marchés des postes de travail et des serveurs étaient dominés par Windows. D’autres plateformes, telles que macOS et Linux, ont toujours des difficultés à gagner en traction. ASP.NET Web Forms est fourni avec le .NET Framework en tant que composant Windows uniquement, ce qui signifie que les applications Web Forms ASP.NET peuvent s’exécuter uniquement sur des ordinateurs Windows Server. De nombreux environnements modernes utilisent à présent différents types de plateformes pour les serveurs et les ordinateurs de développement, de sorte que la prise en charge entre plateformes pour de nombreux utilisateurs est une exigence absolue.

La plupart des infrastructures Web modernes sont désormais également open-source, qui présente un certain nombre d’avantages. Les utilisateurs ne sont pas tenus à un seul propriétaire de projet pour corriger les bogues et ajouter des fonctionnalités. Les projets open source offrent une meilleure transparence sur la progression du développement et les modifications à venir. Les projets open source bénéficient des contributions d’une communauté entière et favorisent un écosystème Open source de support. Malgré les risques liés à open source, de nombreux consommateurs et contributeurs ont trouvé des mesures d’atténuation appropriées qui leur permettent de profiter des avantages d’un écosystème Open source de manière sûre et raisonnable. Les contrats de licence de contributeur, les licences conviviales, les analyses généalogiques et les bases de la prise en charge sont des exemples de ces mesures.

La communauté .NET a adopté la prise en charge multiplateforme et open source. .NET Core est une implémentation Open source et multiplateforme de .NET qui s’exécute sur une multitude de plateformes, notamment Windows, macOS et diverses distributions Linux. Xamarin fournit mono, une version open source de .NET. Mono s’exécute sur Android, iOS et divers autres facteurs de forme, notamment les montres et les téléviseurs intelligents. Microsoft a annoncé que [.net 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/) réconciliera .net Core et mono en « un seul Runtime et Framework .net qui peut être utilisé partout et avec des comportements d’exécution et des expériences de développement uniformes ».

ASP.NET Web Forms tirer parti du passage à la prise en charge des plateformes Open source et multiplateforme ? La réponse, malheureusement, est non, ou au moins la même étendue que le reste de la plateforme. L’équipe .NET a [récemment rendu clair](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/) que ASP.NET Web Forms ne sera pas porté sur .net Core ou .net 5. Pourquoi ?

Il y a eu des efforts au cours des premiers jours de .NET Core vers le port ASP.NET Web Forms. Le nombre de modifications importantes nécessaires est trop important. Il y a également une admission ici, même pour Microsoft, il existe une limite au nombre d’infrastructures Web qu’il peut prendre en charge simultanément. Une personne de la communauté aura peut-être la cause de la création d’une version open source et multiplateforme de ASP.NET Web Forms. Le [code source de ASP.NET Web Forms](https://github.com/microsoft/referencesource) a été rendu accessible publiquement sous forme de référence. Mais pour le moment, il semble ASP.NET Web Forms restera Windows uniquement et sans modèle de contribution Open source. Si la prise en charge multiplateforme ou open source devient important pour vos scénarios, vous devez rechercher d’autres éléments.

Cela signifie-t-il que la Web Forms ASP.NET est *morte* et ne doit plus être utilisée ? Bien sûr que non! Tant que la .NET Framework est fournie dans le cadre de Windows, ASP.NET Web Forms sera un Framework pris en charge. Pour de nombreux développeurs de Web Forms, l’absence de prise en charge multiplateforme et open source n’est pas un problème. Si vous n’avez pas besoin d’une prise en charge multiplateforme, open source, ou l’une des autres nouvelles fonctionnalités de .NET Core ou de .NET 5, Web Forms ASP.NET est parfait. ASP.NET Web Forms continuera à être un moyen productif d’écrire des applications Web pendant de nombreuses années.

Mais il y a une autre tendance à prendre en compte, et c’est le passage au client.

## <a name="client-side-web-development"></a>Développement Web côté client

Tout. Les frameworks Web basés sur .net, y compris les ASP.NET Web Forms, ont historiquement une chose en commun : ils sont *rendus par le serveur*. Dans les applications Web avec affichage serveur, le navigateur envoie une demande au serveur, qui exécute du code (code .NET dans les applications ASP.NET) pour produire une réponse. Cette réponse est renvoyée au navigateur pour gérer. Dans ce modèle, le navigateur est utilisé en tant que moteur de rendu fin. Le travail qui consiste à générer l’interface utilisateur, à exécuter la logique métier et à gérer l’État se produit sur le serveur.

Toutefois, les navigateurs sont devenus des plateformes polyvalentes. Ils implémentent un nombre toujours plus important de normes Web ouvertes qui accordent l’accès aux fonctionnalités de l’ordinateur de l’utilisateur. Pourquoi ne pas tirer parti de la puissance de calcul, du stockage, de la mémoire et d’autres ressources de l’appareil client ? Les interactions de l’interface utilisateur en particulier peuvent bénéficier d’une sensation plus riche et plus interactive lorsqu’elles sont gérées au moins partiellement ou complètement côté client. La logique et les données qui doivent être gérées sur le serveur peuvent toujours être gérées côté serveur. Vous pouvez utiliser des appels d’API Web, voire des protocoles en temps réel, tels que WebSockets. Ces avantages sont disponibles gratuitement pour les développeurs Web s’ils sont prêts à écrire du code JavaScript. Les infrastructures d’interface utilisateur côté client, telles que angulaire, REACT et vue, simplifient le développement Web côté client et ont augmenté en popularité. ASP.NET Web Forms les développeurs peuvent également tirer parti du client et même disposer d’une prise en charge prête à l’emploi avec des infrastructures JavaScript intégrées comme ASP.NET AJAX.

Mais le pontage de deux plateformes et écosystèmes différents (.NET et JavaScript) est un coût. L’expertise est requise dans deux mondes parallèles avec différents langages, infrastructures et outils. Le code et la logique ne peuvent pas être facilement partagés entre le client et le serveur, ce qui entraîne des surcharges de duplication et d’ingénierie. Il peut également être difficile de suivre l’écosystème JavaScript, qui a un historique de évolution à la vitesse très. Les préférences du Framework frontal et de l’outil de build changent rapidement. Le secteur a observé la progression de Grunt à Gulp vers WebPack, et ainsi de suite. La même évolution de Restless s’est produite avec des infrastructures frontales telles que jQuery, Knockout, angulaire, REACT et vue. Mais étant donné le monopole du navigateur JavaScript, il n’y avait que peu de choix. C’est le cas, jusqu’à ce que la communauté Web s’est réunie et a provoqué un *miracle* !

## <a name="no-locwebassembly-fulfills-a-need"></a>WebAssembly a besoin

Dans 2015, les principaux fournisseurs de navigateurs rejoignent des forces dans un groupe de la communauté W3C pour créer une nouvelle norme Web ouverte appelée WebAssembly . WebAssembly est un code d’octet pour le Web. Si vous pouvez compiler votre code dans WebAssembly , il peut s’exécuter sur n’importe quel navigateur sur n’importe quelle plateforme à une vitesse proche de la vitesse native. Premiers efforts sur C/C++. Le résultat était une démonstration spectaculaire de l’exécution de moteurs graphiques 3D natifs directement dans le navigateur sans plug-ins. WebAssembly a depuis été standardisé et implémenté par tous les principaux navigateurs.

Les travaux d’exécution de .NET sur WebAssembly ont été annoncés au plus tard le 2017 et sont censés être livrés dans 2020, y compris la prise en charge de .net 5. La possibilité d’exécuter du code .NET directement dans le navigateur permet le développement Web à pile complète avec .NET.

## <a name="no-locblazor-full-stack-web-development-with-net"></a>Blazor: développement Web à pile complète avec .NET

En soi, la possibilité d’exécuter du code .NET dans un navigateur ne fournit pas d’expérience de bout en bout pour la création d’applications Web côté client. C’est là qu' Blazor intervient. Blazor est une infrastructure d’interface utilisateur Web côté client basée sur C# au lieu de JavaScript. Blazor peut s’exécuter directement dans le navigateur via WebAssembly . Aucun plug-in de navigateur n’est requis. BlazorLes applications peuvent également exécuter côté serveur sur .net Core et gérer toutes les interactions utilisateur sur une connexion en temps réel avec le navigateur.

Blazor offre une excellente prise en charge des outils dans Visual Studio et Visual Studio Code. Le Framework inclut également un modèle de composant d’interface utilisateur complet et des fonctionnalités intégrées pour :

- Formulaires et validation
- Injection de dépendances
- Routage côté client
- Dispositions
- Débogage dans le navigateur
- Interopérabilité JavaScript

Blazor a beaucoup de choses en commun avec ASP.NET Web Forms. Les deux infrastructures offrent des modèles de programmation d’interface utilisateur basés sur des composants et pilotés par les événements. La principale différence architecturale est que ASP.NET Web Forms s’exécute uniquement sur le serveur. Blazor peut s’exécuter sur le client dans le navigateur. Mais si vous êtes à la base d’un ASP.NET Web Forms, il y a beaucoup de choses Blazor qui vous sembleront familières. Blazor est une solution naturelle pour ASP.NET Web Forms les développeurs qui cherchent un moyen de tirer parti du développement côté client et du futur .NET interplateforme Open source.

Ce livre fournit une introduction à Blazor qui est fournie spécifiquement à ASP.NET Web Forms les développeurs. Chaque Blazor concept est présenté dans le contexte de ASP.net et de pratiques Web Forms analogues. À la fin de ce livre, vous aurez compris les éléments suivants :

- Comment créer des Blazor applications.
- Comment Blazor fonctionne.
- BlazorRelation avec .net core.
- Stratégies raisonnables pour la migration des applications Web Forms ASP.NET existantes vers Blazor , le cas échéant.

## <a name="get-started-with-no-locblazor"></a>Prise en main des Blazor

La prise en main de Blazor est simple. Accédez à <https://blazor.net> et suivez les liens pour installer les kit SDK .net Core et les Blazor modèles de projet appropriés. Vous trouverez également des instructions sur la configuration des Blazor outils dans Visual Studio ou Visual Studio code.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](architecture-comparison.md)
