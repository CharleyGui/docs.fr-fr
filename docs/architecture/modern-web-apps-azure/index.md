---
title: Architecturer des applications web modernes avec ASP.NET Core et Azure
description: Un guide qui fournit une aide de bout en bout sur la création d’applications web monolithiques avec ASP.NET Core et Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77449324"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Architecturer des applications web modernes avec ASP.NET Core et Azure

![Image de couverture de livre du guide Architect Modern Web Applications.](./media/index/web-application-guide-cover-image.png)

**EDITION v3.1** - Mis à jour pour ASP.NET Core 3.1

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2020 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de la baleine Docker est une marque déposée de Docker, Inc. Utilisée par permission.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteur :

> **Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)

Rédacteurs :

> **Maira Wenzel**

## <a name="introduction"></a>Introduction

.NET Core et ASP.NET Core offrent plusieurs avantages par rapport au développement .NET classique. Il est recommandé d’utiliser .NET Core pour vos applications serveur si tout ou partie des éléments suivants sont importants pour la réussite de votre application :

- Prise en charge multiplateforme.

- Utilisation de microservices.

- Utilisation de conteneurs Docker.

- Exigences en matière de hautes performances et de scalabilité.

- Gestion côte à côte des versions de .NET par application sur le même serveur.

Les applications .NET classiques prennent en charge nombre de ces spécifications, mais ASP.NET Core et .NET Core ont été optimisés pour offrir une prise en charge améliorée des scénarios ci-dessus.

De plus en plus d’organisations choisissent d’héberger leurs applications web dans le cloud en utilisant des services comme Microsoft Azure. Envisagez d’héberger votre application dans le cloud si les points suivants sont importants pour votre application ou votre organisation :

- Réduction des investissements dans les coûts des centres de données (matériel, logiciel, espace, utilitaires, administration du serveur, etc.)

- Tarification flexible (paiement basé sur l’utilisation et non pas pour une capacité inactive).

- Fiabilité extrême.

- Mobilité accrue de l’application ; changement facile de l’endroit et de la façon dont votre application est déployée.

- Capacité flexible ; montée ou descente en puissance en fonction des besoins réels.

La création d’applications web avec ASP.NET Core, hébergées dans Azure, offre de nombreux avantages concurrentiels par rapport aux alternatives classiques. ASP.NET Core est optimisé pour les pratiques de développement d’applications web modernes et les scénarios d’hébergement cloud. Dans ce guide, vous découvrez comment architecturer vos applications ASP.NET Core pour tirer le meilleur parti de ces fonctionnalités.

## <a name="purpose"></a>Objectif

Ce guide fournit des conseils de bout en bout sur la construction d’applications web *monolithiques* à l’aide de ASP.NET Core et Azure. Dans ce contexte, « monolithiques » fait référence au fait que ces applications sont déployées comme une seule unité, pas comme une collection d’applications et de services qui interagissent.

Ce guide est complémentaire aux [_microservices .NET. Architecture for Containerized .NET Applications_"](../microservices/index.md) qui se concentre davantage sur Docker, Microservices, et le déploiement de conteneurs pour héberger des applications d’entreprise.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Microservices .NET. Architecture pour les applications .NET en conteneur

- **e-book**  
  <https://aka.ms/MicroservicesEbook>
- **Exemple d’application**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Le public visé par ce guide est principalement constitué de développeurs, de responsables du développement et d’architectes qui sont intéressés par la création d’applications web modernes avec des technologies et des services Microsoft dans le cloud.

Il s’adresse aussi aux décideurs techniques qui connaissent déjà ASP.NET ou Azure, et qui recherchent des informations sur la pertinence d’un passage à ASP.NET Core pour des projets nouveaux ou existants.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Ce guide a été condensé en un document relativement court, qui est consacré à la création d’applications web avec des technologies .NET modernes et Microsoft Azure. Il peut ainsi être lu dans sa totalité, et permet de comprendre ces applications et les considérations techniques qui s’y rattachent. Le guide, ainsi que son exemple d’application, peut aussi servir de point de départ ou de référence. Utilisez l’exemple d’application associé comme modèle pour vos propres applications, ou pour voir comment organiser les composants de votre application. Reportez-vous aux principes exposés dans le guide, à la couverture des options d’architecture et de technologie, et aux considérations sur les décisions à prendre quand vous évaluez ces choix pour votre propre application.

N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités. Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.

## <a name="references"></a>References

- **Choix entre .NET Core et .NET Framework pour les applications serveur**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Suivant](modern-web-applications-characteristics.md)
