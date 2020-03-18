---
title: Règle générale
description: Architecture de microservices .NET pour les applications .NET en conteneur | Recommandations générales
ms.date: 09/11/2018
ms.openlocfilehash: 2fa66d7593b764a8df4d9acc20f93d3f8fb26174
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089651"
---
# <a name="general-guidance"></a>Règle générale

Cette section indique brièvement dans quels cas choisir .NET Core ou .NET Framework. Vous trouverez des détails complémentaires sur ces choix dans les sections suivantes.

Vous avez tout intérêt à utiliser .NET Core, avec des conteneurs Windows ou Linux, pour votre application serveur Docker en conteneur dans les cas suivants :

- vous avez des besoins multiplateformes ; Par exemple, vous souhaitez utiliser à la fois des conteneurs Linux et Windows.

- L’architecture de votre application est basée sur des microservices.

- Vous avez besoin de démarrer les conteneurs rapidement et souhaitez un faible encombrement par conteneur pour profiter d’une meilleure densité ou davantage de conteneurs par unité matérielle afin de réduire les coûts.

En somme, quand il s’agit de créer des applications .NET en conteneur, vous devez envisager .NET Core comme le choix par défaut. Il offre de nombreux avantages et correspond le mieux à la philosophie et au type de fonctionnement des conteneurs.

L’autre avantage de .NET Core est lié au fait que vous pouvez exécuter différentes versions de .NET côte à côte pour les applications présentes sur une même machine. Cet avantage est plus important pour les serveurs ou les machines virtuelles qui n’utilisent pas de conteneurs, car les conteneurs isolent les versions de .NET dont l’application a besoin. (Du moment qu’elles sont compatibles avec le système d’exploitation sous-jacent.)

Vous avez tout intérêt à utiliser le .NET Framework pour votre application serveur Docker en conteneur dans les cas suivants :

- Votre application utilise actuellement le .NET Framework et présente de fortes dépendances vis-à-vis de Windows.

- Vous avez besoin d’utiliser des API Windows qui ne sont pas prises en charge par .NET Core.

- Vous avez besoin d’utiliser des bibliothèques .NET ou des packages NuGet tiers qui ne sont pas disponibles pour .NET Core.

Le fait d’utiliser le .NET Framework sur Docker peut améliorer vos expériences de déploiement en limitant les problèmes de déploiement. Ce [scénario « lift-and-shift »](https://aka.ms/liftandshiftwithcontainersebook) est important pour la mise en conteneur d’applications existantes qui ont été développées à l’origine avec le .NET Framework classique, comme les applications Web Forms ASP.NET, les applications web MVC ou les services WCF (Windows Communication Foundation).

### <a name="additional-resources"></a>Ressources supplémentaires

- **E-book: Moderniser les applications cadres .NET existantes avec Azure et Windows Containers**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Exemples d’application : Modernisation d’applications web ASP.NET héritées à l’aide de conteneurs Windows**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](net-core-container-scenarios.md)
