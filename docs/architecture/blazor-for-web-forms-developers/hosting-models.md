---
title: Modèles d’hébergement d’applications éblouissantes
description: Découvrez les différentes manières d’héberger une application éblouissante, y compris dans le navigateur sur webassembly ou sur le serveur.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 82628976bcb1f1cee3089aa25488396af44d0f1a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520299"
---
# <a name="blazor-app-hosting-models"></a>Modèles d’hébergement d’applications éblouissantes

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les applications éblouissantes peuvent être hébergées dans IIS comme ASP.NET Web Forms apps. Les applications éblouissantes peuvent également être hébergées de l’une des manières suivantes :

- Côté client dans le navigateur sur webassembly.
- Côté serveur dans une application ASP.NET Core. 

## <a name="blazor-webassembly-apps"></a>Applications webassembly éblouissantes

Les applications de webassembly éblouissant s’exécutent directement dans le navigateur sur un Runtime .NET basé sur webassembly. Les applications webassembly éblouissantes fonctionnent de la même façon que les infrastructures JavaScript frontales telles que l’angle ou la réaction. Toutefois, au lieu d’écrire du code C#JavaScript, vous écrivez. Le Runtime .NET est téléchargé avec l’application, ainsi que l’assembly d’application et toutes les dépendances requises. Aucun plug-in ou extension de navigateur n’est requis. 

Les assemblys téléchargés sont des assemblys .NET normaux, comme vous le feriez dans n’importe quelle autre application .NET. Étant donné que le runtime prend en charge .NET Standard, vous pouvez utiliser des bibliothèques de .NET Standard existantes avec votre application de webassembly éblouissant. Toutefois, ces assemblys continuent de s’exécuter dans le bac à sable (sandbox) de sécurité du navigateur. Certaines fonctionnalités peuvent lever une <xref:System.PlatformNotSupportedException>, comme essayer d’accéder au système de fichiers ou d’ouvrir des connexions réseau arbitraires. 

Lorsque l’application se charge, le Runtime .NET est démarré et pointe vers l’assembly de l’application. La logique de démarrage de l’application s’exécute et les composants racine sont rendus. Éblouissant calcule les mises à jour de l’interface utilisateur en fonction de la sortie rendue des composants. Les mises à jour du modèle DOM sont ensuite appliquées.

![WebAssembly Blazor](media/hosting-models/blazor-webassembly.png)

Les applications de webassembly éblouissantes s’exécutent uniquement côté client. De telles applications peuvent être déployées sur des solutions d’hébergement de site statiques, telles que les pages GitHub ou l’hébergement de sites Web Azure statiques. .NET n’est pas nécessaire sur le serveur. La liaison profonde à des parties de l’application requiert généralement une solution de routage sur le serveur. La solution de routage redirige les requêtes vers la racine de l’application. Par exemple, cette redirection peut être gérée à l’aide de règles de réécriture d’URL dans IIS.

Pour bénéficier de tous les avantages de l’environnement de développement Web .NET éblouissant et complet, hébergez votre application éblouissante webassembly avec ASP.NET Core. En utilisant .NET sur le client et le serveur, vous pouvez facilement partager du code et créer votre application à l’aide d’un ensemble cohérent de langages, d’infrastructures et d’outils. Éblouissant fournit des modèles pratiques pour configurer une solution qui contient à la fois une application éblouissante webassembly et un projet ASP.NET Core hôte. Lorsque la solution est générée, les fichiers statiques générés à partir de l’application éblouissant sont hébergés par l’application ASP.NET Core avec le routage de secours déjà configuré.

## <a name="blazor-server-apps"></a>Applications serveur éblouissantes

Rappelez-vous de la discussion sur l' [architecture éblouissant](architecture-comparison.md#blazor) pour que les composants éblouissants affichent leur sortie dans une abstraction intermédiaire appelée `RenderTree`. Le Framework éblouissant compare ensuite ce qui a été rendu avec ce qui a été précédemment rendu. Les différences sont appliquées au modèle DOM. Les composants éblouissants sont dissociés de la façon dont leur sortie rendue est appliquée. Par conséquent, les composants eux-mêmes n’ont pas besoin d’être exécutés dans le même processus que le processus mettant à jour l’interface utilisateur. En fait, ils n’ont même pas besoin d’être exécutés sur le même ordinateur.

Dans les applications serveur éblouissantes, les composants s’exécutent sur le serveur plutôt que côté client dans le navigateur. Les événements d’interface utilisateur qui se produisent dans le navigateur sont envoyés au serveur via une connexion en temps réel. Les événements sont distribués aux instances de composant correctes. Les composants sont rendus, et le diff UI calculé est sérialisé et envoyé au navigateur où il est appliqué au DOM.

![Serveur Blazor](media/hosting-models/blazor-server.png)

Le modèle d’hébergement de serveur éblouissant peut paraître familier si vous avez utilisé ASP.NET AJAX et le contrôle <xref:System.Web.UI.UpdatePanel>. Le contrôle `UpdatePanel` gère l’application de mises à jour de pages partielles en réponse aux événements de déclencheur sur la page. Lorsqu’il est déclenché, le `UpdatePanel` demande une mise à jour partielle, puis l’applique sans avoir à actualiser la page. L’état de l’interface utilisateur est géré à l’aide de `ViewState`. Les applications de serveur éblouissantes sont légèrement différentes en ce que l’application nécessite une connexion active avec le client. En outre, l’état de l’interface utilisateur est conservé sur le serveur. Hormis ces différences, les deux modèles sont similaires de manière conceptuelle.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Comment choisir le modèle d’hébergement éblouissant approprié

Comme décrit dans les [documents du modèle d’hébergement éblouissant](https://docs.microsoft.com/aspnet/core/blazor/hosting-models#server-side), les différents modèles d’hébergement de éblouissants présentent des compromis différents.

Le modèle d’hébergement de webassembly éblouissant offre les avantages suivants :

- Il n’existe aucune dépendance côté serveur .NET. L’application fonctionne entièrement après son téléchargement sur le client.
- Les ressources et les fonctionnalités du client sont pleinement exploitées.
- Le travail est déchargé du serveur vers le client.
- Un serveur Web ASP.NET Core n’est pas requis pour héberger l’application. Les scénarios de déploiement sans serveur sont possibles (par exemple, pour servir l’application à partir d’un CDN).

Les inconvénients du modèle d’hébergement de webassembly éblouissant sont les suivants :

- Les fonctionnalités du navigateur restreignent l’application.
- Le matériel et le logiciel client compatibles (par exemple, la prise en charge de webassembly) sont requis.
- La taille du téléchargement est supérieure, et les applications prennent plus de temps à se charger.
- Le Runtime .NET et la prise en charge des outils sont moins matures. Par exemple, il existe des limitations en matière de prise en charge et de débogage [.NET standard](../../standard/net-standard.md) .

Inversement, le modèle d’hébergement de serveur éblouissant offre les avantages suivants :

- La taille du téléchargement est beaucoup plus petite qu’une application côté client et l’application est chargée beaucoup plus rapidement.
- L’application tire pleinement parti des fonctionnalités du serveur, notamment de l’utilisation de toutes les API compatibles avec .NET Core.
- .NET Core sur le serveur est utilisé pour exécuter l’application, de sorte que les outils .NET existants, tels que le débogage, fonctionnent comme prévu.
- Les clients légers sont pris en charge. Par exemple, les applications côté serveur fonctionnent avec des navigateurs qui ne prennent pas en charge webassembly et sur des appareils à ressources restreintes.
- Le .NET/C# base de code de l’application, y compris le code du composant de l’application, n’est pas pris en charge par les clients.

Les inconvénients du modèle d’hébergement de serveurs éblouissants sont les suivants :

- Latence accrue de l’interface utilisateur. Chaque interaction utilisateur implique un tronçon réseau.
- Il n’existe aucune prise en charge hors connexion. Si la connexion cliente échoue, l’application cesse de fonctionner.
- L’évolutivité est difficile pour les applications avec de nombreux utilisateurs. Le serveur doit gérer plusieurs connexions clientes et gérer l’état du client.
- Un serveur de ASP.NET Core est requis pour servir l’application. Les scénarios de déploiement sans serveur ne sont pas possibles. Par exemple, vous ne pouvez pas servir l’application à partir d’un CDN.

La liste précédente des compromis peut être intimidante, mais votre modèle d’hébergement peut être modifié ultérieurement. Quel que soit le modèle d’hébergement éblouissant sélectionné, le modèle de composant est *le même*. En principe, les mêmes composants peuvent être utilisés avec un modèle d’hébergement. Votre code d’application ne change pas ; Toutefois, il est recommandé d’introduire des abstractions afin que vos composants restent hébergeant des modèles indépendants. Les abstractions permettent à votre application d’adopter plus facilement un modèle d’hébergement différent.

## <a name="deploy-your-app"></a>Déployer votre application

Les applications ASP.NET Web Forms sont généralement hébergées sur IIS sur un ordinateur ou un cluster Windows Server. Les applications éblouissantes peuvent également :

- Être hébergé sur IIS, soit sous forme de fichiers statiques, soit en tant qu’application ASP.NET Core.
- Tirez parti de la flexibilité de ASP.NET Core pour être hébergée sur différentes plateformes et infrastructures de serveurs. Par exemple, vous pouvez héberger une application éblouissant à l’aide de [Nginx](/aspnet/core/host-and-deploy/linux-nginx) ou d' [Apache](/aspnet/core/host-and-deploy/linux-apache) sur Linux. Pour plus d’informations sur la publication et le déploiement d’applications éblouissantes, consultez la documentation sur l' [hébergement et le déploiement](/aspnet/core/host-and-deploy/blazor/) de éblouissant.

Dans la section suivante, nous allons étudier la configuration des projets pour les applications de l’assembly et du serveur éblouissantes.

>[!div class="step-by-step"]
>[Précédent](architecture-comparison.md)
>[Suivant](project-structure.md)
