---
title: Quand choisir .NET Framework pour les conteneurs Docker
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quand choisir .NET Framework pour les conteneurs Docker
ms.date: 01/07/2019
ms.openlocfilehash: 8316d17aae09ddbd70bd80af4f06d8cb029f2752
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093766"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Quand choisir .NET Framework pour les conteneurs Docker

Si .NET Core offre des avantages significatifs pour les nouvelles applications et les modèles d’application, le .NET Framework reste un bon choix pour de nombreux scénarios existants.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migration d’applications existant directement dans un conteneur Windows Server

Vous pouvez utiliser des conteneurs Docker uniquement pour simplifier le déploiement, même si vous ne créez pas de microservices. Par exemple, vous souhaitez peut-être améliorer votre flux de travail DevOps avec Docker (les conteneurs peuvent vous offrir des environnements de test mieux isolés et même éliminer les problèmes de déploiement liés à des dépendances manquantes au moment de passer à un environnement de production). En pareil cas, même si vous déployez une application monolithique, il est judicieux d’utiliser des conteneurs Docker et Windows pour vos applications .NET Framework actuelles.

Dans la plupart des cas, pour ce scénario, vous n’aurez pas besoin de migrer vos applications existantes vers .NET Core ; vous pouvez utiliser des conteneurs Docker qui incluent le .NET Framework classique. En revanche, il est recommandé d’utiliser .NET Core quand il s’agit d’étendre une application existante, notamment en écrivant un nouveau service dans ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Utilisation de bibliothèques .NET ou de packages NuGet tiers non disponibles pour .NET Core

Les bibliothèques tierces adoptent rapidement [.NET Standard](../../../standard/net-standard.md), ce qui permet de partager du code entre toutes les versions de .NET, notamment .NET Core. Avec la bibliothèque .NET Standard version 2.0 et au-delà, la compatibilité de la surface d’API entre les différents frameworks s’est considérablement élargie et dans.NET Core 2.x, les applications peuvent aussi faire directement référence aux bibliothèques .NET Framework existantes (consultez [.NET Framework 4.6.1 supporting .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20) (.NET Framework 4.6.1 prenant en charge .NET Standard 2.0)).

En outre, le [Pack de compatibilité Windows](../../../core/porting/windows-compat-pack.md) a été publié en novembre 2017 pour étendre la surface d’API disponible pour .NET Standard 2.0 sur Windows. Ce pack permet de recompiler la plupart du code existant vers .NET Standard 2.x avec peu de modifications ou aucune, pour s’exécuter sur Windows.

Cependant, malgré cette progression exceptionnelle depuis .NET Standard 2.0 et .NET Core 2.1, certains packages NuGet peuvent avoir besoin que Windows s’exécute et peuvent ne pas prendre en charge .NET Core. Si ces packages sont indispensables à votre application, vous devez utiliser le .NET Framework dans des conteneurs Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Utilisation de technologies .NET non disponibles pour .NET Core

Certaines technologies du .NET Framework ne sont pas disponibles dans la version actuelle de .NET Core (version 2.2 au moment de la rédaction de cet article). Certaines d’entre elles seront disponibles dans les prochaines versions de .NET Core (.NET Core 2.x), tandis que d’autres, qui ne s’appliquent pas aux nouveaux modèles d’application ciblés par .NET Core, risquent de ne jamais l’être.

La liste suivante recense la plupart des technologies qui ne sont pas disponibles dans .NET Core 2.x :

- Web Forms ASP.NET : cette technologie est disponible uniquement sur le .NET Framework. Il n’est pas prévu d’intégrer Web Forms ASP.NET à .NET Core.

- Services WCF : Même si [bibliothèque cliente WCF](https://github.com/dotnet/wcf) est disponible pour utiliser des services WCF à partir de .NET Core, à compter du milieu de l’année 2017, l’implémentation serveur WCF est disponible uniquement sur .NET Framework. Ce scénario peut être pris en compte pour les versions futures de .NET Core, il y a même des API prises en compte pour l’inclusion dans le [Pack de compatibilité Windows](../../../core/porting/windows-compat-pack.md).

- Services liés aux flux de travail : Windows Workflow Foundation (WF), les services de flux de travail (WCF + WF dans un seul service) et WCF Data Services (anciennement ADO.NET Data Services) sont disponibles uniquement sur le .NET Framework. Il n’est actuellement pas prévu de les intégrer à .NET Core.

En plus des technologies listées dans la [feuille de route .NET Core](https://github.com/aspnet/Home/wiki/Roadmap) officielle, d’autres fonctionnalités pourraient être portées vers .NET Core. Pour obtenir la liste complète, examinez les éléments associés à la balise [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) sur le site GitHub CoreFX. Notez que cette liste ne constitue pas un engagement de la part de Microsoft à intégrer ces composants à .NET Core ; il s’agit simplement des demandes formulées par la communauté. Si vous vous intéressez à l’un des composants listés ci-dessus, participez éventuellement aux discussions sur GitHub pour faire entendre votre voix. Et si vous pensez que quelque chose fait défaut, veuillez [enregistrer un nouveau problème dans le dépôt CoreFX](https://github.com/dotnet/corefx/issues/new).

Même si .NET Core 3 (en préparation au moment de la rédaction) prendra en charge un grand nombre d’API du .NET Framework existant, celles-ci sont orientées bureau donc, actuellement, elles ne sont d’aucune utilité dans le domaine des conteneurs.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Utilisation d’une plateforme ou d’une API qui ne prend pas en charge .NET Core

Certaines plateformes Microsoft ou tierces ne prennent pas en charge .NET Core. Par exemple, certains services Azure proposent un kit SDK qui n’est pas encore utilisable sur .NET Core. Il s’agit d’une situation temporaire, car tous les services Azure sont appelés à utiliser .NET Core. Par exemple, le [SDK Azure DocumentDB pour .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) a été publié en préversion le 16 novembre 2016, mais il est maintenant en disponibilité générale (GA) sous forme de version stable.

En attendant, si une plateforme ou un service Azure ne prend toujours pas en charge .NET Core avec son API cliente, vous pouvez utiliser l’API REST équivalente du service Azure ou le SDK client de .NET Framework.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Guide .NET Core**  
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **Portage depuis .NET Framework vers .NET Core**  
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Guide de .NET Core sur Docker** [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Vue d’ensemble des composants .NET**  
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Précédent](net-core-container-scenarios.md)
>[Suivant](container-framework-choice-factors.md)
