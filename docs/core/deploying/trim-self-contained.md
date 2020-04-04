---
title: Couper les applications autonomes
description: Apprenez à couper les applications autonomes pour réduire leur taille. .NET Core regroupe l’heure d’exécution avec une application qui est publiée autonome et inclut généralement plus de l’exécution alors est nécessaire.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665634"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Couper les déploiements autonomes et les exécutables

Lors de la publication d’une application autonome, le temps d’exécution .NET Core est regroupé avec l’application. Ce regroupement ajoute une quantité importante de contenu à votre application emballée.

Lorsqu’il s’agit de déployer votre application, la taille est souvent un facteur important. Garder la taille de l’application de paquet aussi petite que possible est généralement un objectif pour les développeurs d’applications.

Selon la complexité de l’application, seul un sous-ensemble de l’exécution est nécessaire pour exécuter l’application. Ces parties inutilisées du temps d’exécution ne sont pas nécessaires et peuvent être extraites de l’application emballée.

> [!NOTE]
> Le rognage est une fonctionnalité expérimentale dans .NET Core 3.1 et _n’est_ disponible que pour les applications qui sont publiées autonomes.

## <a name="trim-your-application"></a>Coupez votre demande

L’exemple suivant montre comment couper votre application à l’aide de la commande [de publication dotnet](../tools/dotnet-publish.md) :

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

La fonction de coupe fonctionne en examinant les binaires d’application pour découvrir et construire un graphique des assemblages de temps d’exécution requis. Les assemblages de temps d’exécution restants qui ne sont pas référencés sont coupés.

## <a name="trimming-issues-when-using-reflection"></a>Réduire les problèmes lors de l’utilisation de la réflexion

Il existe des scénarios dans lesquels la fonctionnalité de coupe ne détectera pas les références. Par exemple, une application qui utilise la réflexion pourrait se heurter à cette question parce que la dépendance à l’égard de l’assemblage ne sera connue qu’à l’heure de fonctionnement.

Le rognage n’est qu’un problème si l’utilisation de la réflexion dépend d’un assemblage de temps d’exécution qui n’est pas référencé directement. Gardez à l’esprit que votre code d’application peut ne pas utiliser la réflexion directement, mais un assemblage tiers que vous faites référence peut l’utiliser.

Lorsque le code fait référence à une API par la réflexion et que vous ne souhaitez pas que le lien pour couper l’assemblage qui contient cette API, vous pouvez modifier votre fichier de projet pour exclure l’assemblage du processus de coupe. L’exemple suivant montre comment `System.Security` empêcher qu’un assemblage appelé ne soit coupé :

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a>Voir aussi

- [.NET Déploiement d’applications de base](index.md)
