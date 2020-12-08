---
title: Architecturer des applications web modernes avec ASP.NET Core et Azure
description: Un guide qui fournit une aide de bout en bout sur la création d’applications web monolithiques avec ASP.NET Core et Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/07/2020
ms.openlocfilehash: 90d092b2269315e5b6734430e82cc7211324479b
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851293"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Architecturer des applications web modernes avec ASP.NET Core et Azure

![Image de couverture du livre du Guide des applications Web modernes de l’architecte.](./media/index/web-application-guide-cover-image.png)

**Édition v 5.0** -mise à jour vers ASP.net Core 5,0

Reportez-vous à [Journal des modifications](https://aka.ms/aspnet-ebook-changelog) pour les mises à jour de livres et les contributions de la communauté.

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2020 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteur :

> **Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)

Rédacteurs :

> **Maira Wenzel**

## <a name="action-links"></a>Liens d'action

- Ce livre électronique est également disponible au [Téléchargement](https://aka.ms/webappebook) au format PDF (version anglaise uniquement).

- Cloner/Dupliquer l’application [de référence eShopOnWeb sur GitHub](https://github.com/dotnet-architecture/eShopOnWeb)

## <a name="introduction"></a>Introduction

.NET 5 et ASP.NET Core offrent plusieurs avantages par rapport au développement .NET traditionnel. Vous devez utiliser .NET 5 pour vos applications serveur si une partie ou la totalité des éléments suivants sont importants pour la réussite de votre application :

- Prise en charge multiplateforme.

- Utilisation de microservices.

- Utilisation de conteneurs Docker.

- Exigences en matière de hautes performances et de scalabilité.

- Gestion côte à côte des versions de .NET par application sur le même serveur.

Les applications .NET traditionnelles peuvent et prennent en charge un grand nombre de ces exigences, mais ASP.NET Core et .NET 5 ont été optimisés pour offrir une meilleure prise en charge des scénarios ci-dessus.

De plus en plus d’organisations choisissent d’héberger leurs applications web dans le cloud en utilisant des services comme Microsoft Azure. Envisagez d’héberger votre application dans le cloud si les points suivants sont importants pour votre application ou votre organisation :

- Réduction des investissements dans les coûts des centres de données (matériel, logiciel, espace, utilitaires, administration du serveur, etc.)

- Tarification flexible (paiement basé sur l’utilisation et non pas pour une capacité inactive).

- Fiabilité extrême.

- Mobilité accrue de l’application ; changement facile de l’endroit et de la façon dont votre application est déployée.

- Capacité flexible ; montée ou descente en puissance en fonction des besoins réels.

La création d’applications web avec ASP.NET Core, hébergées dans Azure, offre de nombreux avantages concurrentiels par rapport aux alternatives classiques. ASP.NET Core est optimisé pour les pratiques de développement d’applications web modernes et les scénarios d’hébergement cloud. Dans ce guide, vous découvrez comment architecturer vos applications ASP.NET Core pour tirer le meilleur parti de ces fonctionnalités.

## <a name="version"></a>Version

Ce guide a été révisé pour couvrir la version **5,0 de .net** , ainsi que de nombreuses mises à jour supplémentaires liées aux mêmes « vagues » de technologies (c’est-à-dire, Azure et des technologies tierces) qui coïncident avec la version .net 5,0. C’est la raison pour laquelle la version du livre a également été mise à jour vers la version **5,0**.

## <a name="purpose"></a>Objectif

Ce guide fournit des conseils de bout en bout sur la création d’applications Web *monolithiques* à l’aide d’ASP.net Core et d’Azure. Dans ce contexte, « monolithiques » fait référence au fait que ces applications sont déployées comme une seule unité, pas comme une collection d’applications et de services qui interagissent.

Ce guide est complémentaire aux [_microservices .net. Architecture pour les applications .NET en conteneur_»](../microservices/index.md), qui se concentre sur l’ancrage, les microservices et le déploiement de conteneurs pour héberger des applications d’entreprise.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Microservices .NET. Architecture pour les applications .NET en conteneur

- **livre électronique**  
  <https://aka.ms/MicroservicesEbook>
- **Exemple d’application**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Le public visé par ce guide est principalement constitué de développeurs, de responsables du développement et d’architectes qui sont intéressés par la création d’applications web modernes avec des technologies et des services Microsoft dans le cloud.

Il s’adresse aussi aux décideurs techniques qui connaissent déjà ASP.NET ou Azure, et qui recherchent des informations sur la pertinence d’un passage à ASP.NET Core pour des projets nouveaux ou existants.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Ce guide a été condensé dans un document relativement petit qui se concentre sur la création d’applications Web avec des technologies .NET modernes et Azure. Il peut ainsi être lu dans sa totalité, et permet de comprendre ces applications et les considérations techniques qui s’y rattachent. Le guide, ainsi que son exemple d’application, peut aussi servir de point de départ ou de référence. Utilisez l’exemple d’application associé comme modèle pour vos propres applications, ou pour voir comment organiser les composants de votre application. Reportez-vous aux principes exposés dans le guide, à la couverture des options d’architecture et de technologie, et aux considérations sur les décisions à prendre quand vous évaluez ces choix pour votre propre application.

N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités. Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.

## <a name="references"></a>References

- **Choix entre .NET 5 et .NET Framework pour les applications serveur**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Next](modern-web-applications-characteristics.md)
