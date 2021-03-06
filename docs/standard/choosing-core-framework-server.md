---
title: Choisir entre .NET 5 et .NET Framework pour les applications serveur
description: Guide pour vous aider à choisir l’implémentation de .NET à utiliser lors de la création d’une application serveur.
author: cartermp
ms.date: 10/06/2020
ms.openlocfilehash: d9dce0343f9d37e976472b818e896a5b0a661e76
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160449"
---
# <a name="net-5-vs-net-framework-for-server-apps"></a>.NET 5 et .NET Framework pour les applications serveur

Il existe deux implémentations .NET prises en charge pour la création d’applications côté serveur : .NET Framework et .NET 5 (y compris .NET Core). Toutes deux partagent de nombreux composants et vous permettent de partager du code entre les deux. Toutefois, il existe des différences fondamentales entre les deux et votre choix dépend de ce que vous souhaitez accomplir. Cet article fournit des conseils sur l’utilisation de chacune.

Utilisez .NET 5 pour votre application serveur dans les cas suivants :

- vous avez des besoins multiplateformes ;
- Vous ciblez des microservices.
- Vous utilisez des conteneurs d’ancrage.
- Vous avez besoin de systèmes scalables et hautes performances.
- Vous avez besoin de versions .NET côte à côte par application.

Utilisez .NET Framework pour votre application serveur quand :

- Votre application utilise le .NET Framework (nous vous recommandons de privilégier l’extension à la migration).
- Votre application utilise des bibliothèques .NET tierces ou des packages NuGet qui ne sont pas disponibles pour .NET 5.
- Votre application utilise des technologies .NET qui ne sont pas disponibles pour .NET 5.
- Votre application utilise une plateforme qui ne prend pas en charge .NET 5.

## <a name="when-to-choose-net-5"></a>Quand choisir .NET 5

Les sections suivantes fournissent une explication plus détaillée des raisons indiquées précédemment pour choisir .NET 5.

### <a name="cross-platform-needs"></a>Besoins multiplateformes

Si votre application (Web/service) doit s’exécuter sur plusieurs plateformes (Windows, Linux et macOS), utilisez .NET 5.

.NET 5 prend en charge les systèmes d’exploitation précédemment mentionnés comme station de travail de développement. Visual Studio fournit un environnement de développement intégré (IDE) pour Windows et macOS. Vous pouvez également utiliser Visual Studio Code, qui s’exécute sur macOS, Linux et Windows. Visual Studio Code prend en charge .NET 5, notamment IntelliSense et le débogage. La plupart des éditeurs tiers, tels que sublime, Emacs et VI, fonctionnent avec .NET 5. Ces éditeurs tiers obtiennent l’éditeur IntelliSense en utilisant [Omnisharp](https://www.omnisharp.net/). Vous pouvez également éviter tout éditeur de code et utiliser directement le [CLI .net Core](../core/tools/index.md), disponible pour toutes les plateformes prises en charge.

### <a name="microservices-architecture"></a>Architecture de microservices

Une architecture en microservices permet une combinaison de technologies au-delà des limites d’un service. Cette combinaison de technologies permet une adoption progressive de .NET 5 pour les nouveaux microservices qui fonctionnent avec d’autres microservices ou services. Par exemple, vous pouvez combiner des microservices ou services développés avec .NET Framework, Java, Ruby ou d’autres technologies monolithiques.

Il existe de nombreuses plateformes d’infrastructure. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) est conçu pour les systèmes de microservice volumineux et complexes. [Azure App Service](https://azure.microsoft.com/services/app-service/) est un bon choix pour les microservices sans état. Les alternatives aux microservices basées sur Docker s’intègrent à tout type d’approche des microservices, comme expliqué dans la section [Conteneurs](#containers). Toutes ces plateformes prennent en charge .NET 5 et les rendent idéales pour l’hébergement de vos microservices.

Pour plus d’informations sur l’architecture de microservices, consultez [microservices .net. Architecture pour les applications .NET en conteneur](../architecture/microservices/index.md).

### <a name="containers"></a>Containers

Les conteneurs sont couramment utilisés conjointement avec une architecture en microservices. Les conteneurs peuvent également servir à mettre en conteneur des applications ou services web qui suivent un modèle d’architecture. .NET Framework peut être utilisé sur des conteneurs Windows, mais la modularité et la nature légère de .NET 5 en font un meilleur choix pour les conteneurs. Lorsque vous créez et déployez un conteneur, la taille de son image est plus petite avec .NET 5 qu’avec .NET Framework. Grâce à sa nature multiplateforme, vous pouvez déployer des applications serveur sur des conteneurs Docker Linux, par exemple.

Vous pouvez héberger les conteneurs Docker dans votre propre infrastructure Windows ou Linux, ou dans un service cloud comme [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/). Azure Kubernetes Service permet de gérer, d’orchestrer et de mettre à l’échelle des applications sur conteneur dans le cloud.

### <a name="high-performance-and-scalable-systems"></a>Systèmes hautes performances et évolutifs

Si votre système a besoin des meilleures performances et évolutivité, .NET 5 et ASP.NET Core sont vos meilleures options. Un runtime serveur hautes performances pour Windows Server et Linux fait de .NET un framework web particulièrement attractif d’après les [bancs d’essai TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Niveau de performance et scalabilité sont particulièrement pertinents pour les architectures en microservices, où des centaines de microservices peuvent être en cours d’exécution. Avec ASP.NET Core, les systèmes sont exécutés avec un nombre bien inférieur de serveurs/machines virtuelles. Cette réduction engendre une baisse des coûts d’infrastructure et d’hébergement.

### <a name="side-by-side-net-versions-per-application-level"></a>Versions .NET côte à côte par niveau d’application

Pour installer des applications avec des dépendances sur différentes versions de .NET, nous vous recommandons .NET 5. .NET 5 prend en charge l’installation côte à côte de différentes versions du Runtime .NET 5 sur le même ordinateur. Cette installation côte à côte autorise plusieurs services sur le même serveur, chacun d’eux sur sa propre version de .NET 5 (ou .NET Core 2,1 ou 3,1). De plus, les risques et les coûts liés aux opérations informatiques et aux mises à niveau des applications s’en trouvent réduits.

L’installation côte à côte n’est pas possible avec .NET Framework. Il s’agit d’un composant Windows, et une seule version peut exister sur un ordinateur à la fois. Chaque version de .NET Framework remplace la version précédente. Si vous installez une nouvelle application qui cible une version ultérieure de .NET Framework, vous pouvez interrompre les applications existantes qui s’exécutent sur l’ordinateur, car la version précédente a été remplacée.

## <a name="when-to-choose-net-framework"></a>Quand choisir .NET Framework

.NET 5 offre des avantages significatifs pour les nouvelles applications et les modèles d’application. Toutefois, .NET Framework reste le choix naturel pour de nombreux scénarios existants et, par conséquent, .NET Framework n’est pas remplacé par .NET 5 pour toutes les applications serveur.

### <a name="current-net-framework-applications"></a>Applications .NET Framework actuelles

Dans la plupart des cas, vous n’avez pas besoin de migrer vos applications existantes vers .NET 5. Au lieu de cela, une approche recommandée consiste à utiliser .NET 5 lorsque vous étendez une application existante, telle que l’écriture d’un nouveau service Web dans ASP.NET Core.

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-5"></a>Des bibliothèques tierces ou des packages NuGet ne sont pas disponibles pour .NET 5

.NET Standard permet de partager du code entre toutes les implémentations .NET, y compris .NET 5. Avec .NET Standard 2,0, un mode de compatibilité permet aux projets .NET Standard et .NET 5 de référencer des bibliothèques .NET Framework. Pour plus d’informations, consultez [prise en charge des bibliothèques de .NET Framework](whats-new/whats-new-in-dotnet-standard.md#support-for-net-framework-libraries).

Vous devez utiliser .NET Framework uniquement dans les cas où les bibliothèques ou les packages NuGet utilisent des technologies qui ne sont pas disponibles dans .NET Standard ou .NET 5.

### <a name="net-technologies-not-available-for-net-5"></a>Technologies .NET non disponibles pour .NET 5

Certaines technologies de .NET Framework ne sont pas disponibles dans .NET 5. La liste suivante présente les technologies les plus courantes introuvables dans .NET 5 :

- ASP.NET Web Forms applications : ASP.NET Web Forms sont disponibles uniquement dans .NET Framework. ASP.NET Core ne peut pas être utilisé pour Web Forms ASP.NET.

- Applications Pages Web ASP.NET : le framework Pages Web ASP.NET n’est pas inclus dans ASP.NET Core.

- Implémentation des services WCF. Même s’il existe une [bibliothèque cliente WCF](https://github.com/dotnet/wcf) pour utiliser des services WCF à partir de .net 5, l’implémentation de serveur WCF n’est actuellement disponible que dans .NET Framework.

- Services liés aux flux de travail : Windows Workflow Foundation (WF), les services de workflow (WCF + WF dans un seul service) et les WCF Data Services (anciennement « ADO.NET Data Services ») sont disponibles uniquement dans .NET Framework.

- Prise en charge linguistique : Visual Basic et F # sont actuellement pris en charge dans .NET 5, mais pas pour tous les types de projets. Pour obtenir la liste des modèles de projet pris en charge, consultez [Options de modèle pour dotnet new](../core/tools/dotnet-new.md#arguments).

Pour plus d’informations, consultez [.NET Framework technologies non disponibles dans .net 5](../core/porting/net-framework-tech-unavailable.md).

### <a name="platform-doesnt-support-net-5"></a>La plateforme ne prend pas en charge .NET 5

Certaines plateformes Microsoft ou tierces ne prennent pas en charge .NET 5. Certains services Azure fournissent un kit de développement logiciel (SDK) qui n’est pas encore disponible pour la consommation sur .NET 5. Dans ce cas, vous pouvez utiliser l’API REST équivalente au lieu du kit de développement logiciel (SDK) client.

## <a name="see-also"></a>Voir aussi

- [Choisir entre ASP.NET et ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core ciblant .NET Framework](/aspnet/core/introduction-to-aspnet-core?view=aspnetcore-2.2&preserve-view=true#aspnet-core-targeting-net-framework)
- [Frameworks cibles](frameworks.md)
- [Présentation de .NET](../core/introduction.md)
- [Portage à partir de .NET Framework vers .NET 5](../core/porting/index.md)
- [Introduction à .NET et à Docker](../core/docker/introduction.md)
- [Vue d’ensemble des composants .NET](components.md)
- [Microservices .NET. Architecture pour les applications .NET en conteneur](../architecture/microservices/index.md)
