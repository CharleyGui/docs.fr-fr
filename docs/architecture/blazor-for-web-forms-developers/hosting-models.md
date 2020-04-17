---
title: Modèles d’hébergement de l’application Blazor
description: Découvrez les différentes façons d’héberger une application Blazor, y compris dans le navigateur sur WebAssembly ou sur le serveur.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 77a022b01efba01038790c9601ea03f315a28fdf
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607930"
---
# <a name="blazor-app-hosting-models"></a>Modèles d’hébergement de l’application Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les applications Blazor peuvent être hébergées dans l’IIS tout comme ASP.NET applications Web Forms. Les applications Blazor peuvent également être hébergées de l’une des façons suivantes :

- Côté client dans le navigateur sur WebAssembly.
- Côté serveur dans une application ASP.NET Core.

## <a name="blazor-webassembly-apps"></a>Applications Blazor WebAssembly

Les applications Blazor WebAssembly s’exécutent directement dans le navigateur sur un runtime .NET basé sur WebAssembly. Les applications Blazor WebAssembly fonctionnent de la même manière que les cadres JavaScript front-end comme Angulaire ou Réagir. Cependant, au lieu d’écrire JavaScript vous écrivez C . L’exécution .NET est téléchargée avec l’application avec l’assemblage de l’application et toutes les dépendances requises. Aucun plugins ou extensions de navigateur n’est requis.

Les assemblages téléchargés sont des assemblages .NET normaux, comme vous l’utiliseriez dans n’importe quelle autre application .NET. Parce que le temps d’exécution prend en charge .NET Standard, vous pouvez utiliser les bibliothèques standard .NET existantes avec votre application Blazor WebAssembly. Cependant, ces assemblages s’exécuteront toujours dans le bac à sable de sécurité du navigateur. Certaines fonctionnalités peuvent <xref:System.PlatformNotSupportedException>jeter un , comme essayer d’accéder au système de fichiers ou d’ouvrir des connexions réseau arbitraires.

Lorsque l’application se charge, l’heure d’exécution .NET est commencée et pointée vers l’assemblage de l’application. La logique de démarrage de l’application s’exécute, et les composants root sont rendus. Blazor calcule les mises à jour de l’interface utilisateur en fonction de la sortie rendue des composants. Les mises à jour DOM sont ensuite appliquées.

![WebAssembly Blazor](media/hosting-models/blazor-webassembly.png)

Les applications Blazor WebAssembly fonctionnent uniquement du côté client. Ces applications peuvent être déployées sur des solutions d’hébergement de sites statiques comme GitHub Pages ou Azure Static Website Hosting. .NET n’est pas nécessaire sur le serveur du tout. Un lien profond vers des parties de l’application nécessite généralement une solution de routage sur le serveur. La solution de routage redirige les demandes vers la racine de l’application. Par exemple, cette redirection peut être traitée à l’aide de règles de réécriture d’URL dans l’IIS.

Pour obtenir tous les avantages de Blazor et le développement web .NET complet, hébergez votre application Blazor WebAssembly avec ASP.NET Core. En utilisant .NET sur le client et le serveur, vous pouvez facilement partager du code et construire votre application à l’aide d’un ensemble cohérent de langues, de cadres et d’outils. Blazor fournit des modèles pratiques pour la mise en place d’une solution qui contient à la fois une application Blazor WebAssembly et un projet d’hôte ASP.NET Core. Lorsque la solution est construite, les fichiers statiques intégrés de l’application Blazor sont hébergés par l’application ASP.NET Core avec routage de repli déjà configuration.

## <a name="blazor-server-apps"></a>Applications Blazor Server

Rappelez-vous de la discussion [d’architecture Blazor](architecture-comparison.md#blazor) que les composants `RenderTree`Blazor rendent leur sortie à une abstraction intermédiaire appelée a . Le cadre Blazor compare ensuite ce qui a été rendu avec ce qui avait été rendu auparavant. Les différences s’appliquent au DOM. Les composants Blazor sont découplés de la façon dont leur sortie rendue est appliquée. Par conséquent, les composants eux-mêmes n’ont pas à fonctionner dans le même processus que le processus de mise à jour de l’interface utilisateur. En fait, ils n’ont même pas à courir sur la même machine.

Dans les applications Blazor Server, les composants s’exécutent sur le serveur au lieu du côté client dans le navigateur. Les événements d’interface utilisateur qui se produisent dans le navigateur sont envoyés au serveur sur une connexion en temps réel. Les événements sont envoyés aux instances de composants correctes. Les composants rendent, et le diff d’interface utilisateur calculé est sérialisé et envoyé au navigateur où il est appliqué au DOM.

![Serveur Blazor](media/hosting-models/blazor-server.png)

Le modèle d’hébergement Blazor Server peut sembler familier si <xref:System.Web.UI.UpdatePanel> vous avez utilisé ASP.NET AJAX et le contrôle. Le `UpdatePanel` contrôle gère l’application de mises à jour partielles de page en réponse aux événements déclencheurs sur la page. Lorsqu’elle `UpdatePanel` est déclenchée, la demande une mise à jour partielle et l’applique ensuite sans avoir besoin de rafraîchir la page. L’état de l’interface `ViewState`utilisateur est géré à l’aide de . Les applications Blazor Server sont légèrement différentes en ce que l’application nécessite une connexion active avec le client. En outre, tout l’état de l’interface utilisateur est maintenu sur le serveur. Mis à part ces différences, les deux modèles sont conceptuellement similaires.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Comment choisir le bon modèle d’hébergement Blazor

Comme décrit dans les [docs modèle d’hébergement Blazor](/aspnet/core/blazor/hosting-models), les différents modèles d’hébergement Blazor ont des compromis différents.

Le modèle d’hébergement Blazor WebAssembly présente les avantages suivants :

- Il n’y a pas de dépendance .NET côté serveur. L’application fonctionne pleinement après avoir été téléchargée sur le client.
- Les ressources et les capacités des clients sont pleinement exploitées.
- Le travail est déchargé du serveur au client.
- Un serveur web ASP.NET Core n’est pas nécessaire pour héberger l’application. Des scénarios de déploiement sans serveur sont possibles (par exemple, au service de l’application à partir d’un CDN).

Les inconvénients du modèle d’hébergement Blazor WebAssembly sont les :

- Les capacités du navigateur limitent l’application.
- Le matériel et les logiciels clients compétents (par exemple, le support WebAssembly) sont nécessaires.
- La taille du téléchargement est plus grande, et les applications prennent plus de temps à charger.
- .NET runtime et le support d’outillage est moins mature. Par exemple, il y a des limites dans le support et le débogage [.NET Standard.](../../standard/net-standard.md)

Inversement, le modèle d’hébergement Blazor Server offre les avantages suivants :

- La taille du téléchargement est beaucoup plus petite qu’une application côté client, et l’application se charge beaucoup plus rapidement.
- L’application tire pleinement parti des capacités du serveur, y compris l’utilisation de toutes les API compatibles avec le noyau .NET.
- .NET Core sur le serveur est utilisé pour exécuter l’application, de sorte que l’outillage .NET existant, comme le débogage, fonctionne comme prévu.
- Les clients minces sont pris en charge. Par exemple, les applications côté serveur fonctionnent avec des navigateurs qui ne prennent pas en charge WebAssembly et sur les périphériques à ressources limitées.
- La base de code .NET/CMD de l’application, y compris le code composant de l’application, n’est pas servie aux clients.

Les inconvénients du modèle d’hébergement Blazor Server sont les :

- Latence d’interface utilisateur plus élevée. Chaque interaction utilisateur implique un saut réseau.
- Il n’y a pas de support hors ligne. Si la connexion client échoue, l’application cesse de fonctionner.
- L’évolutivité est difficile pour les applications avec de nombreux utilisateurs. Le serveur doit gérer plusieurs connexions client et gérer l’état du client.
- Un serveur ASP.NET Core est nécessaire pour servir l’application. Les scénarios de déploiement sans serveur ne sont pas possibles. Par exemple, vous ne pouvez pas servir l’application à partir d’un CDN.

La liste précédente des compromis peut être intimidante, mais votre modèle d’hébergement peut être modifié plus tard. Quel que soit le modèle d’hébergement Blazor sélectionné, le modèle de composant est *le même*. En principe, les mêmes composants peuvent être utilisés avec l’un ou l’autre modèle d’hébergement. Votre code d’application ne change pas ; cependant, c’est une bonne pratique d’introduire des abstractions afin que vos composants restent d’hébergement modèle-agnostique. Les abstractions permettent à votre application d’adopter plus facilement un modèle d’hébergement différent.

## <a name="deploy-your-app"></a>Déployer votre application

ASP.NET applications Web Forms sont généralement hébergées sur IIS sur une machine ou un cluster Windows Server. Les applications Blazor peuvent également :

- Soyez hébergé sur IIS, soit sous forme de fichiers statiques, soit sous forme d’application ASP.NET Core.
- Tirer parti ASP.NET la flexibilité de Core à héberger sur diverses plateformes et infrastructures de serveurs. Par exemple, vous pouvez héberger une application Blazor à l’aide de [Nginx](/aspnet/core/host-and-deploy/linux-nginx) ou [Apache](/aspnet/core/host-and-deploy/linux-apache) sur Linux. Pour plus d’informations sur la façon de publier et de déployer des applications Blazor, consultez la documentation [Blazor Hosting et déploiement.](/aspnet/core/host-and-deploy/blazor/)

Dans la section suivante, nous examinerons comment les projets pour les applications Blazor WebAssembly et Blazor Server sont mis en place.

>[!div class="step-by-step"]
>[Suivant précédent](architecture-comparison.md)
>[Next](project-structure.md)
