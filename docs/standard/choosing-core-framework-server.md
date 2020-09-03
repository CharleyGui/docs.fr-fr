---
title: Choisir entre .NET Core et .NET Framework pour les applications serveur
description: Guide pour vous aider à choisir l’implémentation de .NET à utiliser lors de la création d’une application serveur.
author: cartermp
ms.date: 04/28/2020
ms.openlocfilehash: a3c15e8f2198b1bcc4e623a7dc7f5cddca9c83f6
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89415017"
---
# <a name="net-core-vs-net-framework-for-server-apps"></a>.NET Core et .NET Framework pour les applications serveur

Il existe deux implémentations .NET prises en charge pour la création d’applications côté serveur : .NET Framework et .NET Core. Toutes deux partagent de nombreux composants et vous permettent de partager du code entre les deux. Toutefois, il existe des différences fondamentales entre les deux et votre choix dépend de ce que vous souhaitez accomplir. Cet article fournit des conseils sur l’utilisation de chacune.

Utilisez .NET Core pour votre application serveur quand :

- vous avez des besoins multiplateformes ;
- Vous ciblez des microservices.
- Vous utilisez des conteneurs d’ancrage.
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

### <a name="high-performance-and-scalable-systems"></a>Systèmes hautes performances et évolutifs

Quand votre système a besoin de performances et d’une scalabilité optimales, .NET Core et ASP.NET Core sont vos meilleures options. Un runtime serveur hautes performances pour Windows Server et Linux fait de .NET un framework web particulièrement attractif d’après les [bancs d’essai TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Niveau de performance et scalabilité sont particulièrement pertinents pour les architectures en microservices, où des centaines de microservices peuvent être en cours d’exécution. Avec ASP.NET Core, les systèmes sont exécutés avec un nombre bien inférieur de serveurs/machines virtuelles. Cette réduction engendre une baisse des coûts d’infrastructure et d’hébergement.

### <a name="side-by-side-net-versions-per-application-level"></a>Versions .NET côte à côte par niveau d’application

Pour installer des applications avec des dépendances sur différentes versions de .NET, nous vous recommandons .NET Core. .NET Core prend en charge l’installation côte à côte de différentes versions du Runtime .NET Core sur le même ordinateur. Ainsi, plusieurs services peuvent cohabiter sur le même serveur, chacun d’eux sur sa propre version de .NET Core. De plus, les risques et les coûts liés aux opérations informatiques et aux mises à niveau des applications s’en trouvent réduits.

L’installation côte à côte n’est pas possible avec .NET Framework. Il s’agit d’un composant Windows, et une seule version peut exister sur un ordinateur à la fois. Chaque version de .NET Framework remplace la version précédente. Si vous installez une nouvelle application qui cible une version ultérieure de .NET Framework, vous pouvez interrompre les applications existantes qui s’exécutent sur l’ordinateur, car la version précédente a été remplacée.

## <a name="when-to-choose-net-framework"></a>Quand choisir .NET Framework

.NET Core offre des avantages significatifs pour les nouvelles applications et les nouveaux modèles d’application. Toutefois, .NET Framework reste le choix naturel pour de nombreux scénarios existants et, par conséquent, .NET Framework n’est pas remplacé par .NET Core pour toutes les applications serveur.

### <a name="current-net-framework-applications"></a>Applications .NET Framework actuelles

Dans la plupart des cas, vous ne devez pas migrer vos applications existantes vers .NET Core. Il est plutôt recommandé d’utiliser .NET Core quand vous étendez une application existante, telle que l’écriture d’un service web dans ASP.NET Core.

### <a name="aspnet-core-on-net-framework"></a>ASP.NET Core sur .NET Framework

Pour plus d’informations sur la prise en charge de ASP.NET Core sur .NET Framework, consultez [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-core"></a>Des bibliothèques tierces ou des packages NuGet ne sont pas disponibles pour .NET Core

Les bibliothèques adoptent rapidement .NET Standard. .NET Standard permet de partager du code dans toutes les implémentations .NET, y compris .NET Core. Avec .NET 2.0 Standard, cela est encore plus simple :

- La surface de l’API est désormais beaucoup plus grande.
- Il a introduit un mode de compatibilité .NET Framework.

  Ce mode de compatibilité permet aux projets .NET Standard et .NET Core de référencer des bibliothèques .NET Framework. Pour en savoir plus sur le mode de compatibilité, consultez [Annonce de .NET 2.0 Standard](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Vous devez utiliser .NET Framework uniquement dans les cas où les bibliothèques ou les packages NuGet utilisent des technologies qui ne sont pas disponibles dans .NET Standard ou .NET Core.

### <a name="net-technologies-not-available-for-net-core"></a>Technologies .NET non disponibles pour .NET Core

Certaines technologies du .NET Framework ne sont pas disponibles dans .NET Core. Il se peut que certaines d’entre elles soient disponibles dans les prochaines versions release de .NET Core. D’autres, qui ne s’appliquent pas aux nouveaux modèles d’application ciblés par .NET Core, risquent de ne jamais être disponibles. La liste suivante présente les technologies les plus courantes absentes dans .NET Core :

- ASP.NET Web Forms applications : ASP.NET Web Forms sont disponibles uniquement dans .NET Framework. ASP.NET Core ne peut pas être utilisé pour Web Forms ASP.NET. Il n’est pas prévu d’intégrer Web Forms ASP.NET à .NET Core.

- Applications Pages Web ASP.NET : le framework Pages Web ASP.NET n’est pas inclus dans ASP.NET Core.

- Implémentation des services WCF. Même s’il existe une [bibliothèque cliente WCF](https://github.com/dotnet/wcf) pour utiliser des services WCF à partir de .net Core, l’implémentation de serveur WCF n’est actuellement disponible que dans .NET Framework. Ce scénario ne fait pas partie du plan actuel pour .NET Core, mais il est envisagé à l’avenir.

- Services liés aux flux de travail : Windows Workflow Foundation (WF), les services de workflow (WCF + WF dans un seul service) et les WCF Data Services (anciennement « ADO.NET Data Services ») sont disponibles uniquement dans .NET Framework. Il n’est pas prévu d’intégrer ces technologies à .NET Core.

- Prise en charge des langages : Visual Basic et F# sont pris en charge dans .NET Core, mais pas pour tous les types de projet. Pour obtenir la liste des modèles de projet pris en charge, consultez [Options de modèle pour dotnet new](../core/tools/dotnet-new.md#arguments).

### <a name="platform-doesnt-support-net-core"></a>La plateforme ne prend pas en charge .NET Core

Certaines plateformes Microsoft ou tierces ne prennent pas en charge .NET Core. Certains services Azure fournissent un kit SDK qui n’est pas encore utilisable sur .NET Core. Il s’agit d’une circonstance transitoire, car tous les services Azure utilisent .NET Core. En attendant, vous pouvez utiliser l’API REST équivalente au lieu du kit de développement logiciel (SDK) client.

## <a name="see-also"></a>Voir aussi

- [Choisir entre ASP.NET et ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core ciblant .NET Framework](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [Frameworks cibles](frameworks.md)
- [Présentation de .NET Core](../core/introduction.md)
- [Portage vers .NET Core à partir du .NET Framework](../core/porting/index.md)
- [Introduction à .NET et à Docker](../core/docker/introduction.md)
- [Vue d’ensemble des composants .NET](components.md)
- [Microservices .NET. Architecture pour les applications .NET en conteneur](../architecture/microservices/index.md)
