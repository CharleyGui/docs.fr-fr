---
title: Quand choisir .NET Framework pour les conteneurs Docker
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quand choisir .NET Framework pour les conteneurs Docker
ms.date: 01/30/2020
ms.openlocfilehash: 116ba02878a60487f1af3c2b2e084307fad29618
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414420"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Quand choisir .NET Framework pour les conteneurs Docker

Si .NET Core offre des avantages significatifs pour les nouvelles applications et les modèles d’application, le .NET Framework reste un bon choix pour de nombreux scénarios existants.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migration d’applications existant directement dans un conteneur Windows Server

Vous pouvez utiliser des conteneurs Docker uniquement pour simplifier le déploiement, même si vous ne créez pas de microservices. Par exemple, vous souhaitez peut-être améliorer votre flux de travail DevOps avec Docker (les conteneurs peuvent vous offrir des environnements de test mieux isolés et même éliminer les problèmes de déploiement liés à des dépendances manquantes au moment de passer à un environnement de production). En pareil cas, même si vous déployez une application monolithique, il est judicieux d’utiliser des conteneurs Docker et Windows pour vos applications .NET Framework actuelles.

Dans la plupart des cas, pour ce scénario, vous n’aurez pas besoin de migrer vos applications existantes vers .NET Core ; vous pouvez utiliser des conteneurs Docker qui incluent le .NET Framework classique. En revanche, il est recommandé d’utiliser .NET Core quand il s’agit d’étendre une application existante, notamment en écrivant un nouveau service dans ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Utilisation de bibliothèques .NET ou de packages NuGet tiers non disponibles pour .NET Core

Les bibliothèques tierces adoptent rapidement [.NET standard](../../../standard/net-standard.md), qui permet le partage de code sur toutes les versions de .net, y compris .net core. Avec .NET Standard 2,0 et versions ultérieures, la compatibilité de la surface de l’API entre différents frameworks a été considérablement plus importante. En outre, .NET Core 2. x et les applications plus récentes peuvent également référencer directement des bibliothèques de .NET Framework existantes (consultez [.NET Framework 4.6.1 prenant en charge .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

En outre, le [Pack de compatibilité Windows](../../../core/porting/windows-compat-pack.md) étend la surface de l’API disponible pour .NET standard 2,0 sur Windows. Ce pack permet de recompiler la plupart du code existant vers .NET Standard 2.x avec peu de modifications ou aucune, pour s’exécuter sur Windows.

Cependant, malgré cette progression exceptionnelle depuis .NET Standard 2.0 et .NET Core 2.1, certains packages NuGet peuvent avoir besoin que Windows s’exécute et peuvent ne pas prendre en charge .NET Core. Si ces packages sont indispensables à votre application, vous devez utiliser le .NET Framework dans des conteneurs Windows.

## <a name="using-net-technologies-not-available-for-net-core"></a>Utilisation de technologies .NET non disponibles pour .NET Core

Certaines technologies de .NET Framework ne sont pas disponibles dans la version actuelle de .NET Core (version 3,1 à la rédaction de cet article). Certaines d’entre elles peuvent devenir disponibles dans les versions ultérieures, mais d’autres ne conviennent pas aux nouveaux modèles d’application ciblés par .NET Core et peuvent ne jamais être disponibles.

La liste suivante présente la plupart des technologies qui ne sont pas disponibles dans .NET Core 3,1 :

- Web Forms ASP.NET : cette technologie est disponible uniquement sur le .NET Framework. Il n’est pas prévu d’intégrer Web Forms ASP.NET à .NET Core.

- Services WCF : Même lorsqu’une [bibliothèque cliente WCF](https://github.com/dotnet/wcf) est disponible pour consommer des services WCF à partir de .net Core, à compter de février-2020, l’implémentation de serveur WCF est disponible uniquement sur .NET Framework. Ce scénario peut être pris en compte pour les versions futures de .NET Core, il y a même des API prises en compte pour l’inclusion dans le [Pack de compatibilité Windows](../../../core/porting/windows-compat-pack.md).

- Services liés aux flux de travail : Windows Workflow Foundation (WF), les services de flux de travail (WCF + WF dans un seul service) et WCF Data Services (anciennement ADO.NET Data Services) sont disponibles uniquement sur le .NET Framework. Il n’est actuellement pas prévu de les intégrer à .NET Core.

En plus des technologies listées dans la feuille de [route officielle .net Core](https://github.com/dotnet/core/blob/master/roadmap.md), d’autres fonctionnalités peuvent être reportées sur .net Core ou sur la nouvelle [plateforme .net unifiée](https://devblogs.microsoft.com/dotnet/introducing-net-5/). Vous pouvez envisager de participer aux discussions sur GitHub pour que votre voix puisse être entendue. Et si vous pensez que quelque chose manque, envoyez un nouveau problème dans le dépôt github [dotnet/Runtime](https://github.com/dotnet/runtime/issues/new) .

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>Utilisation d’une plateforme ou d’une API qui ne prend pas en charge .NET Core

Certaines plateformes Microsoft et tierces ne prennent pas en charge .NET Core. Par exemple, certains services Azure fournissent un kit de développement logiciel (SDK) qui n’est pas encore disponible pour la consommation sur .NET Core. La plupart des kits de développement logiciel (SDK) Azure doivent finalement être portés dans .NET Core/standard, mais certains ne peuvent pas pour diverses raisons. Vous pouvez consulter les kits de développement logiciel (SDK) Azure disponibles dans la page [versions les plus récentes du kit SDK Azure](https://azure.github.io/azure-sdk/releases/latest/index.html) .

En attendant, si une plateforme ou un service Azure ne prend toujours pas en charge .NET Core avec son API cliente, vous pouvez utiliser l’API REST équivalente du service Azure ou le SDK client de .NET Framework.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Notions de base de .NET** \
  [https://docs.microsoft.com/dotnet/fundamentals](../../../fundamentals/index.yml)

- **Portage à partir de .NET Framework vers .NET Core** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Guide de .NET Core sur l’ancrage** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Vue d’ensemble des composants .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Précédent](net-core-container-scenarios.md) 
> [Suivant](container-framework-choice-factors.md)
