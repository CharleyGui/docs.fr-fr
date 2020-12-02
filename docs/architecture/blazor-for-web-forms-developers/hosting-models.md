---
title: Blazor modèles d’hébergement d’applications
description: Découvrez les différentes manières d’héberger une Blazor application, y compris dans le navigateur sur WebAssembly ou sur le serveur.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: 5d80b28642ee1e975d334f89504a1748d13dea8f
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509778"
---
# <a name="no-locblazor-app-hosting-models"></a>Blazor modèles d’hébergement d’applications

Blazor les applications peuvent être hébergées dans IIS comme ASP.NET Web Forms apps. Blazor les applications peuvent également être hébergées de l’une des manières suivantes :

- Côté client dans le navigateur WebAssembly .
- Côté serveur dans une application ASP.NET Core.

## <a name="no-locblazor-no-locwebassembly-apps"></a>BlazorWebAssemblyapplications

BlazorWebAssemblyles applications s’exécutent directement dans le navigateur sur un WebAssembly Runtime .net basé sur. Blazorles WebAssembly applications fonctionnent de la même façon que les infrastructures JavaScript frontales comme l’angle ou la réaction. Toutefois, au lieu d’écrire du code JavaScript, vous écrivez du code C#. Le Runtime .NET est téléchargé avec l’application, ainsi que l’assembly d’application et toutes les dépendances requises. Aucun plug-in ou extension de navigateur n’est requis.

Les assemblys téléchargés sont des assemblys .NET normaux, comme vous le feriez dans n’importe quelle autre application .NET. Étant donné que le runtime prend en charge .NET Standard, vous pouvez utiliser des bibliothèques de .NET Standard existantes avec votre Blazor WebAssembly application. Toutefois, ces assemblys continuent de s’exécuter dans le bac à sable (sandbox) de sécurité du navigateur. Certaines fonctionnalités peuvent lever une <xref:System.PlatformNotSupportedException> , comme essayer d’accéder au système de fichiers ou d’ouvrir des connexions réseau arbitraires.

Lorsque l’application se charge, le Runtime .NET est démarré et pointe vers l’assembly de l’application. La logique de démarrage de l’application s’exécute et les composants racine sont rendus. Blazor calcule les mises à jour de l’interface utilisateur en fonction de la sortie rendue des composants. Les mises à jour du modèle DOM sont ensuite appliquées.

![::: No-Loc (éblouissant) :::::: No-Loc (webassembly) :::](media/hosting-models/blazor-webassembly.png)

BlazorWebAssemblyles applications s’exécutent uniquement côté client. De telles applications peuvent être déployées sur des solutions d’hébergement de site statiques, telles que les pages GitHub ou l’hébergement de sites Web Azure statiques. .NET n’est pas nécessaire sur le serveur. La liaison profonde à des parties de l’application requiert généralement une solution de routage sur le serveur. La solution de routage redirige les requêtes vers la racine de l’application. Par exemple, cette redirection peut être gérée à l’aide de règles de réécriture d’URL dans IIS.

Pour bénéficier de tous les avantages du Blazor développement Web .net complet et de Stack, hébergez votre Blazor WebAssembly application avec ASP.net core. En utilisant .NET sur le client et le serveur, vous pouvez facilement partager du code et créer votre application à l’aide d’un ensemble cohérent de langages, d’infrastructures et d’outils. Blazor fournit des modèles pratiques pour configurer une solution qui contient à la fois une Blazor WebAssembly application et un projet ASP.net Core hôte. Lorsque la solution est générée, les fichiers statiques générés à partir de l' Blazor application sont hébergés par l’application ASP.net core avec le routage de secours déjà configuré.

## <a name="no-locblazor-server-apps"></a>Blazor Applications serveur

Rappelez-vous de la discussion sur l' [ Blazor architecture](architecture-comparison.md#blazor) qui Blazor permet aux composants d’afficher leur sortie dans une abstraction intermédiaire appelée `RenderTree` . Le Blazor Framework compare ensuite ce qui a été rendu avec ce qui a été précédemment rendu. Les différences sont appliquées au modèle DOM. Blazor les composants sont dissociés de la façon dont leur sortie rendue est appliquée. Par conséquent, les composants eux-mêmes n’ont pas besoin d’être exécutés dans le même processus que le processus mettant à jour l’interface utilisateur. En fait, ils n’ont même pas besoin d’être exécutés sur le même ordinateur.

Dans les Blazor applications serveur, les composants s’exécutent sur le serveur plutôt que côté client dans le navigateur. Les événements d’interface utilisateur qui se produisent dans le navigateur sont envoyés au serveur via une connexion en temps réel. Les événements sont distribués aux instances de composant correctes. Les composants sont rendus, et le diff UI calculé est sérialisé et envoyé au navigateur où il est appliqué au DOM.

![::: No-Loc (éblouissant) ::: serveur](media/hosting-models/blazor-server.png)

Le Blazor modèle d’hébergement de serveur peut paraître familier si vous avez utilisé ASP.NET AJAX et le <xref:System.Web.UI.UpdatePanel> contrôle. Les `UpdatePanel` Handles de contrôle appliquant des mises à jour de pages partielles en réponse aux événements de déclencheur sur la page. Lorsqu’il est déclenché, le `UpdatePanel` demande une mise à jour partielle, puis l’applique sans avoir à actualiser la page. L’état de l’interface utilisateur est géré à l’aide de `ViewState` . Blazor Les applications serveur sont légèrement différentes en ce que l’application nécessite une connexion active avec le client. En outre, l’état de l’interface utilisateur est conservé sur le serveur. Hormis ces différences, les deux modèles sont similaires de manière conceptuelle.

## <a name="how-to-choose-the-right-no-locblazor-hosting-model"></a>Comment choisir le modèle d' Blazor hébergement approprié

Comme décrit dans les [ Blazor documents du modèle d’hébergement](/aspnet/core/blazor/hosting-models), les différents modèles d' Blazor hébergement ont des compromis différents.

Le Blazor WebAssembly modèle d’hébergement présente les avantages suivants :

- Il n’existe aucune dépendance côté serveur .NET. L’application fonctionne entièrement après son téléchargement sur le client.
- Les ressources et les fonctionnalités du client sont pleinement exploitées.
- Le travail est déchargé du serveur vers le client.
- Un serveur Web ASP.NET Core n’est pas requis pour héberger l’application. Les scénarios de déploiement sans serveur sont possibles (par exemple, pour servir l’application à partir d’un CDN).

Les inconvénients du modèle d' Blazor WebAssembly hébergement sont les suivants :

- Les fonctionnalités du navigateur restreignent l’application.
- Le matériel et le logiciel client compatibles (par exemple, la WebAssembly prise en charge) sont requis.
- La taille du téléchargement est supérieure, et les applications prennent plus de temps à se charger.
- Le Runtime .NET et la prise en charge des outils sont moins matures. Par exemple, il existe des limitations en matière de prise en charge et de débogage [.NET standard](../../standard/net-standard.md) .

À l’inverse, le Blazor modèle d’hébergement de serveur offre les avantages suivants :

- La taille du téléchargement est beaucoup plus petite qu’une application côté client et l’application est chargée beaucoup plus rapidement.
- L’application tire pleinement parti des fonctionnalités du serveur, notamment de l’utilisation de toutes les API compatibles .NET.
- .NET sur le serveur est utilisé pour exécuter l’application, de sorte que les outils .NET existants, tels que le débogage, fonctionnent comme prévu.
- Les clients légers sont pris en charge. Par exemple, les applications côté serveur fonctionnent avec des navigateurs qui ne prennent pas en charge WebAssembly et sur des appareils à ressources restreintes.
- La base de code .NET/C# de l’application, y compris le code du composant de l’application, n’est pas traitée aux clients.

Les inconvénients du modèle d' Blazor Hébergement de serveur sont les suivants :

- Latence accrue de l’interface utilisateur. Chaque interaction utilisateur implique un tronçon réseau.
- Il n’existe aucune prise en charge hors connexion. Si la connexion cliente échoue, l’application cesse de fonctionner.
- L’évolutivité est difficile pour les applications avec de nombreux utilisateurs. Le serveur doit gérer plusieurs connexions clientes et gérer l’état du client.
- Un serveur de ASP.NET Core est requis pour servir l’application. Les scénarios de déploiement sans serveur ne sont pas possibles. Par exemple, vous ne pouvez pas servir l’application à partir d’un CDN.

La liste précédente des compromis peut être intimidante, mais votre modèle d’hébergement peut être modifié ultérieurement. Quel que soit le Blazor modèle d’hébergement sélectionné, le modèle de composant est *le même*. En principe, les mêmes composants peuvent être utilisés avec un modèle d’hébergement. Votre code d’application ne change pas ; Toutefois, il est recommandé d’introduire des abstractions afin que vos composants restent hébergeant des modèles indépendants. Les abstractions permettent à votre application d’adopter plus facilement un modèle d’hébergement différent.

## <a name="deploy-your-app"></a>Déployer votre application

Les applications ASP.NET Web Forms sont généralement hébergées sur IIS sur un ordinateur ou un cluster Windows Server. Blazor les applications peuvent également :

- Être hébergé sur IIS, soit sous forme de fichiers statiques, soit en tant qu’application ASP.NET Core.
- Tirez parti de la flexibilité de ASP.NET Core pour être hébergée sur différentes plateformes et infrastructures de serveurs. Par exemple, vous pouvez héberger une Blazor application à l’aide de [Nginx](/aspnet/core/host-and-deploy/linux-nginx) ou d' [Apache](/aspnet/core/host-and-deploy/linux-apache) sur Linux. Pour plus d’informations sur la publication et le déploiement d' Blazor applications, consultez la documentation sur l' Blazor [hébergement et le déploiement](/aspnet/core/host-and-deploy/blazor/) .

Dans la section suivante, nous allons voir comment les projets pour Blazor WebAssembly et les Blazor applications serveur sont configurés.

>[!div class="step-by-step"]
>[Précédent](architecture-comparison.md) 
> [Suivant](project-structure.md)
