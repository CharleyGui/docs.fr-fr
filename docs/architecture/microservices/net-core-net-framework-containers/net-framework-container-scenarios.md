---
title: Quand choisir .NET Framework pour les conteneurs Docker
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quand choisir .NET Framework pour les conteneurs Docker
ms.date: 01/30/2020
ms.openlocfilehash: 2697ae56eda104a0ee8e7bfcd79d3972943d1f79
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344993"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Quand choisir .NET Framework pour les conteneurs Docker

Si .NET Core offre des avantages significatifs pour les nouvelles applications et les modèles d’application, le .NET Framework reste un bon choix pour de nombreux scénarios existants.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migration d’applications existant directement dans un conteneur Windows Server

Vous pouvez utiliser des conteneurs Docker uniquement pour simplifier le déploiement, même si vous ne créez pas de microservices. Par exemple, vous souhaitez peut-être améliorer votre flux de travail DevOps avec Docker (les conteneurs peuvent vous offrir des environnements de test mieux isolés et même éliminer les problèmes de déploiement liés à des dépendances manquantes au moment de passer à un environnement de production). En pareil cas, même si vous déployez une application monolithique, il est judicieux d’utiliser des conteneurs Docker et Windows pour vos applications .NET Framework actuelles.

Dans la plupart des cas, pour ce scénario, vous n’aurez pas besoin de migrer vos applications existantes vers .NET Core ; vous pouvez utiliser des conteneurs Docker qui incluent le .NET Framework classique. En revanche, il est recommandé d’utiliser .NET Core quand il s’agit d’étendre une application existante, notamment en écrivant un nouveau service dans ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Utilisation de bibliothèques .NET ou de packages NuGet tiers non disponibles pour .NET Core

Les bibliothèques tierces adoptent rapidement [.NET Standard](../../../standard/net-standard.md), qui permet le partage de code à travers toutes les saveurs .NET, y compris .NET Core. Avec .NET Standard 2.0 et plus tard, la compatibilité de surface API entre différents cadres est devenue significativement plus grande. Plus encore, .NET Core 2.x et les applications plus récents peuvent également faire directement référence aux bibliothèques cadres .NET existantes (voir [.NET Framework 4.6.1 support .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

En outre, le [pack de compatibilité Windows](../../../core/porting/windows-compat-pack.md) étend la surface API disponible pour .NET Standard 2.0 sur Windows. Ce pack permet de recompiler la plupart du code existant vers .NET Standard 2.x avec peu de modifications ou aucune, pour s’exécuter sur Windows.

Cependant, malgré cette progression exceptionnelle depuis .NET Standard 2.0 et .NET Core 2.1, certains packages NuGet peuvent avoir besoin que Windows s’exécute et peuvent ne pas prendre en charge .NET Core. Si ces packages sont indispensables à votre application, vous devez utiliser le .NET Framework dans des conteneurs Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Utilisation de technologies .NET non disponibles pour .NET Core

Certaines technologies cadre .NET ne sont pas disponibles dans la version actuelle de .NET Core (version 3.1 à partir de cette écriture). Certains d’entre eux peuvent devenir disponibles dans les versions ultérieures, mais d’autres ne correspondent pas aux nouveaux modèles d’application ciblés par .NET Core et pourrait ne jamais être disponible.

La liste suivante montre la plupart des technologies qui ne sont pas disponibles dans .NET Core 3.1:

- Web Forms ASP.NET : cette technologie est disponible uniquement sur le .NET Framework. Il n’est pas prévu d’intégrer Web Forms ASP.NET à .NET Core.

- Services WCF : Même lorsqu’une [bibliothèque WCF-Client](https://github.com/dotnet/wcf) est disponible pour consommer les services WCF à partir de .NET Core, à partir de février-2020, la mise en œuvre du serveur WCF n’est disponible que sur .NET Framework. Ce scénario peut être pris en compte pour les versions futures de .NET Core, il y a même des API prises en compte pour l’inclusion dans le [Pack de compatibilité Windows](../../../core/porting/windows-compat-pack.md).

- Services liés aux flux de travail : Windows Workflow Foundation (WF), les services de flux de travail (WCF + WF dans un seul service) et WCF Data Services (anciennement ADO.NET Data Services) sont disponibles uniquement sur le .NET Framework. Il n’est actuellement pas prévu de les intégrer à .NET Core.

En plus des technologies énumérées dans la feuille de route officielle [.NET Core](https://github.com/dotnet/core/blob/master/roadmap.md), d’autres fonctionnalités pourraient être portées à .NET Core ou la nouvelle [plate-forme unifiée .NET](https://devblogs.microsoft.com/dotnet/introducing-net-5/). Vous pourriez envisager de participer aux discussions sur GitHub afin que votre voix puisse être entendue. Et si vous pensez que quelque chose manque, déposez un nouveau numéro dans le référentiel [GitHub pointnet/runtime.](https://github.com/dotnet/runtime/issues/new)

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Utilisation d’une plate-forme ou d’un API qui ne prend pas en charge .NET Core

Certains Microsoft et les plates-formes tierces ne prennent pas en charge .NET Core. Par exemple, certains services Azure fournissent un SDK qui n’est pas encore disponible à la consommation sur .NET Core. La plupart des Azure SDK devraient éventuellement être portés à .NET Core/Standard, mais certains pourraient ne pas pour diverses raisons. Vous pouvez voir les SDK Azure disponibles dans la page [Azure SDK Dernières Versions.](https://azure.github.io/azure-sdk/releases/latest/index.html)

En attendant, si une plateforme ou un service Azure ne prend toujours pas en charge .NET Core avec son API cliente, vous pouvez utiliser l’API REST équivalente du service Azure ou le SDK client de .NET Framework.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Guide de base .NET** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.yml)

- **Portage de .NET Framework à .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **.NET Core sur Docker Guide** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Vue d’ensemble des composants .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Suivant précédent](net-core-container-scenarios.md)
>[Next](container-framework-choice-factors.md)
