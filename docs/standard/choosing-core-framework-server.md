---
title: Choisir entre .NET Core et .NET Framework pour les applications serveur
description: Guide sur l’implémentation de .NET à envisager pour générer une application serveur dans .NET.
author: cartermp
ms.date: 06/19/2018
ms.openlocfilehash: c202e42a46c4a72bdceca1fb250170d381603a8d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124622"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Choix entre .NET Core et .NET Framework pour les applications serveur

Il existe deux implémentations pour générer des applications serveur avec .NET : .NET Framework et .NET Core. Toutes deux partagent de nombreux composants et vous permettent de partager du code entre les deux. Toutefois, il existe des différences fondamentales entre les deux et votre choix dépend de ce que vous souhaitez accomplir.  Cet article fournit des conseils sur l’utilisation de chacune.

Utilisez .NET Core pour votre application serveur quand :

- vous avez des besoins multiplateformes ;
- vous ciblez des microservices ;
- vous utilisez des conteneurs Docker ;
- Vous avez besoin de systèmes scalables et hautes performances.
- Vous avez besoin de versions .NET côte à côte par application.

Utilisez .NET Framework pour votre application serveur quand :

- Votre application utilise le .NET Framework (nous vous recommandons de privilégier l’extension à la migration).
- Votre application utilise des packages NuGet ou des bibliothèques .NET tiers non disponibles pour .NET Core.
- Votre application utilise des technologies .NET non disponibles pour .NET Core.
- Votre application utilise une plateforme qui ne prend pas en charge .NET Core. Windows, macOS et Linux prennent en charge .NET Core.

## <a name="when-to-choose-net-core"></a>Quand choisir .NET Core

Les sections suivantes donnent une explication plus détaillée des raisons indiquées précédemment justifiant le choix de .NET Core.

### <a name="cross-platform-needs"></a>Besoins multiplateformes

Si votre application (web/service) doit s’exécuter sur plusieurs plateformes (Windows, Linux et macOS), utilisez .NET Core.

.NET Core prend en charge les systèmes d’exploitation précédemment mentionnés comme station de travail de développement. Visual Studio fournit un environnement de développement intégré (IDE) pour Windows et macOS. Vous pouvez également utiliser Visual Studio Code, qui s’exécute sur macOS, Linux et Windows. Visual Studio Code prend en charge .NET Core, notamment IntelliSense et le débogage. La plupart des éditeurs tiers, tels que Sublime, Emacs et VI, fonctionnent avec .NET Core. Ces éditeurs tiers obtiennent l’éditeur IntelliSense en utilisant [Omnisharp](https://www.omnisharp.net/). Vous pouvez également éviter tout éditeur de code et utiliser directement le [CLI .net Core](../core/tools/index.md), disponible pour toutes les plateformes prises en charge.

### <a name="microservices-architecture"></a>Architecture de microservices

Une architecture en microservices permet une combinaison de technologies au-delà des limites d’un service. Cette combinaison de technologies favorise l’adoption progressive de .NET Core pour les nouveaux microservices qui utilisent d’autres microservices ou services. Par exemple, vous pouvez combiner des microservices ou services développés avec .NET Framework, Java, Ruby ou d’autres technologies monolithiques.

Il existe de nombreuses plateformes d’infrastructure. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) est conçu pour les systèmes de microservice volumineux et complexes. [Azure App Service](https://azure.microsoft.com/services/app-service/) est un bon choix pour les microservices sans état. Les alternatives aux microservices basées sur Docker s’intègrent à tout type d’approche des microservices, comme expliqué dans la section [Conteneurs](#containers). Toutes ces plateformes prennent en charge .NET Core et s’avèrent idéales pour l’hébergement de vos microservices.

Pour plus d’informations sur l’architecture de microservices, consultez [microservices .net. Architecture pour les applications .NET en conteneur](../architecture/microservices/index.md).

### <a name="containers"></a>Containers

Les conteneurs sont couramment utilisés conjointement avec une architecture en microservices. Les conteneurs peuvent également servir à mettre en conteneur des applications ou services web qui suivent un modèle d’architecture. Le .NET Framework peut être utilisé pour les conteneurs Windows, mais par sa modularité et sa légèreté, .NET Core est un meilleur choix pour les conteneurs. Quand vous créez et déployez un conteneur, la taille de son image est beaucoup plus petite avec .NET Core qu’avec le .NET Framework. Grâce à sa nature multiplateforme, vous pouvez déployer des applications serveur sur des conteneurs Docker Linux, par exemple.

Vous pouvez héberger les conteneurs Docker dans votre propre infrastructure Windows ou Linux, ou dans un service cloud comme [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/). Azure Kubernetes Service permet de gérer, d’orchestrer et de mettre à l’échelle des applications sur conteneur dans le cloud.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Besoin de systèmes scalables et hautes performances

Quand votre système a besoin de performances et d’une scalabilité optimales, .NET Core et ASP.NET Core sont vos meilleures options. Un runtime serveur hautes performances pour Windows Server et Linux fait de .NET un framework web particulièrement attractif d’après les [bancs d’essai TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Niveau de performance et scalabilité sont particulièrement pertinents pour les architectures en microservices, où des centaines de microservices peuvent être en cours d’exécution. Avec ASP.NET Core, les systèmes sont exécutés avec un nombre bien inférieur de serveurs/machines virtuelles. Cette réduction engendre une baisse des coûts d’infrastructure et d’hébergement.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Besoin d’une installation côte à côte de versions .NET par niveau d’application

Pour installer des applications avec des dépendances sur différentes versions de .NET, nous vous recommandons .NET Core. .NET Core permet d’installer côte à côte différentes versions du runtime .NET Core sur le même ordinateur. Ainsi, plusieurs services peuvent cohabiter sur le même serveur, chacun d’eux sur sa propre version de .NET Core. De plus, les risques et les coûts liés aux opérations informatiques et aux mises à niveau des applications s’en trouvent réduits.

## <a name="when-to-choose-net-framework"></a>Quand choisir .NET Framework

.NET Core offre des avantages significatifs pour les nouvelles applications et les nouveaux modèles d’application. Toutefois, le .NET Framework est toujours le choix naturel pour de nombreux scénarios existants, et par conséquent il n’est pas remplacé par .NET Core pour toutes les applications serveur.

### <a name="current-net-framework-applications"></a>Applications .NET Framework actuelles

Dans la plupart des cas, vous ne devez pas migrer vos applications existantes vers .NET Core. Il est plutôt recommandé d’utiliser .NET Core quand vous étendez une application existante, telle que l’écriture d’un service web dans ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Besoin d’utiliser des packages NuGet ou des bibliothèques .NET tiers non disponibles pour .NET Core

Les bibliothèques adoptent rapidement .NET Standard. .NET standard permet de partager du code sur toutes les implémentations de .NET, y compris .NET Core. Avec .NET 2.0 Standard, cela est encore plus simple :

- La surface de l’API est désormais beaucoup plus grande. 
- Un mode de compatibilité du .NET Framework a été introduit. Ce mode de compatibilité permet aux projets .NET Standard/.NET Core de référencer des bibliothèques .NET Framework. Pour en savoir plus sur le mode de compatibilité, consultez [Annonce de .NET 2.0 Standard](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Ainsi, seulement dans les cas où les bibliothèques ou les packages NuGet utilisent des technologies qui ne sont pas disponibles dans .NET Standard/.NET Core, vous devez utiliser le .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Besoin d’utiliser des technologies .NET non disponibles pour .NET Core

Certaines technologies du .NET Framework ne sont pas disponibles dans .NET Core. Il se peut que certaines d’entre elles soient disponibles dans les prochaines versions release de .NET Core. D’autres, qui ne s’appliquent pas aux nouveaux modèles d’application ciblés par .NET Core, risquent de ne jamais être disponibles. La liste suivante présente les technologies les plus courantes absentes dans .NET Core :

- Applications Web Forms ASP.NET : Web Forms ASP.NET n’est disponible que dans le .NET Framework. ASP.NET Core ne peut pas être utilisé pour Web Forms ASP.NET. Il n’est pas prévu d’intégrer Web Forms ASP.NET à .NET Core.

- Applications Pages Web ASP.NET : le framework Pages Web ASP.NET n’est pas inclus dans ASP.NET Core. 

- Implémentation des services WCF. Même s’il existe une [bibliothèque cliente WCF](https://github.com/dotnet/wcf) pour utiliser des services WCF à partir de .NET Core, l’implémentation serveur WCF est disponible uniquement sur le .NET Framework. Ce scénario ne fait pas partie du plan actuel pour .NET Core, mais il est envisagé pour l’avenir.

- Services liés aux flux de travail : Windows Workflow Foundation (WF), les services de flux de travail (WCF + WF dans un seul service) et les Services de données WCF (anciennement « ADO.NET Data Services ») sont disponibles uniquement dans le .NET Framework.  Il n’est pas prévu d’intégrer WF/WCF+WF/WCF Data Services à .NET Core.

- Prise en charge des langages : Visual Basic et F# sont pris en charge dans .NET Core, mais pas pour tous les types de projet. Pour obtenir la liste des modèles de projet pris en charge, consultez [Options de modèle pour dotnet new](../core/tools/dotnet-new.md#arguments).

En plus de la feuille de route officielle, il existe d’autres frameworks à porter vers .NET Core. Pour obtenir la liste complète, consultez les problèmes CoreFX portant l’étiquette [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Cette liste ne représente pas un engagement de Microsoft à intégrer les composants concernés à .NET Core. Elle reflète simplement le souhait de la communauté de les intégrer. Si un des composants portant l’étiquette `port-to-core` vous intéresse, participez aux discussions sur GitHub. Et si vous pensez que quelque chose manque, envoyez un nouveau problème dans le [référentiel .net](https://github.com/dotnet/runtime/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Besoin d’utiliser une plateforme qui ne prend pas en charge .NET Core

Certaines plateformes Microsoft ou tierces ne prennent pas en charge .NET Core. Certains services Azure fournissent un kit SDK qui n’est pas encore utilisable sur .NET Core. Il s’agit d’une circonstance transitoire, car tous les services Azure utilisent .NET Core. En attendant, vous pouvez toujours utiliser l’API REST équivalente au lieu du SDK client.

## <a name="see-also"></a>Voir aussi

- [Choisir entre ASP.NET et ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core ciblant .NET Framework](/aspnet/core#aspnet-core-targeting-net-framework)
- [Frameworks cibles](frameworks.md)
- [Guide .NET Core](../core/index.md)
- [Portage depuis .NET Framework vers .NET Core](../core/porting/index.md)
- [Introduction à .NET et à Docker](../core/docker/introduction.md)
- [Vue d’ensemble des composants .NET](components.md)
- [Microservices .NET. Architecture pour les applications .NET en conteneur](../architecture/microservices/index.md)
