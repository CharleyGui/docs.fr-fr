---
title: Règle générale
description: Architecture de microservices .NET pour les applications .NET en conteneur | Recommandations générales
ms.date: 01/13/2021
ms.openlocfilehash: 4fd2d936c524cb3e5ae463038eaffe88b459d2bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187949"
---
# <a name="general-guidance"></a>Règle générale

Cette section fournit un résumé de la sélection de .NET 5 ou .NET Framework. Vous trouverez des détails complémentaires sur ces choix dans les sections suivantes.

Utilisez .NET 5, avec des conteneurs Linux ou Windows, pour votre application serveur d’amarrage en conteneur lorsque :

- vous avez des besoins multiplateformes ; Par exemple, vous souhaitez utiliser à la fois des conteneurs Linux et Windows.

- L’architecture de votre application est basée sur des microservices.

- Vous avez besoin de démarrer les conteneurs rapidement et souhaitez un faible encombrement par conteneur pour profiter d’une meilleure densité ou davantage de conteneurs par unité matérielle afin de réduire les coûts.

En résumé, lorsque vous créez des applications .NET en conteneur, vous devez envisager .NET 5 comme choix par défaut. Il offre de nombreux avantages et correspond le mieux à la philosophie et au type de fonctionnement des conteneurs.

L’avantage supplémentaire de .NET 5 est que vous pouvez exécuter des versions .NET côte à côte pour des applications au sein du même ordinateur. Cet avantage est plus important pour les serveurs ou les machines virtuelles qui n’utilisent pas de conteneurs, car les conteneurs isolent les versions de .NET dont l’application a besoin. (Du moment qu’elles sont compatibles avec le système d’exploitation sous-jacent.)

Utilisez .NET Framework pour votre application serveur d’amarrage en conteneur lorsque :

- Votre application utilise actuellement le .NET Framework et présente de fortes dépendances vis-à-vis de Windows.

- Vous devez utiliser des API Windows qui ne sont pas prises en charge par .NET 5.

- Vous devez utiliser des bibliothèques .NET tierces ou des packages NuGet qui ne sont pas disponibles pour .NET 5.

Le fait d’utiliser le .NET Framework sur Docker peut améliorer vos expériences de déploiement en limitant les problèmes de déploiement. Ce [scénario « lift-and-shift »](https://aka.ms/liftandshiftwithcontainersebook) est important pour la mise en conteneur d’applications existantes qui ont été développées à l’origine avec le .NET Framework classique, comme les applications Web Forms ASP.NET, les applications web MVC ou les services WCF (Windows Communication Foundation).

### <a name="additional-resources"></a>Ressources supplémentaires

- **Livre électronique : moderniser les applications .NET Framework existantes avec des conteneurs Windows et Azure**  
    <https://aka.ms/liftandshiftwithcontainersebook>

- **Exemples d’application : Modernisation d’applications web ASP.NET héritées à l’aide de conteneurs Windows**  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](net-core-container-scenarios.md)
