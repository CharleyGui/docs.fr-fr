---
title: ASP.NET Core gRPC pour les développeurs WCF-gRPC pour les développeurs WCF
description: À ÉCRIRE
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7d02d7914aed39613b4a41da55515df80abddfe8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184448"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>ASP.NET Core gRPC pour les développeurs WCF

![image de couverture](./media/cover.png)

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs. Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.

Le logo de Docker représentant une baleine est une marque déposée de Docker, Inc. Utilisé sous autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteur :

> **Mark Rendle** -directeur technique – rédacteur [visuel](https://visualrecode.com)
>
> **Miranda Steiner** -auteur technique

Rédacteurs :

> Développeur de contenu **Maira Wenzel** -SR-Microsoft

## <a name="introduction"></a>Introduction

TODO

## <a name="purpose"></a>Objectif

TODO

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

**METTRE À JOUR**

Ce guide est destiné aux développeurs WCF, aux responsables du développement et aux architectes qui souhaitent migrer des solutions WCF sur .NET 4 et versions antérieures vers ASP.NET Core 3,0 à l’aide des services gRPC.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

**METTRE À JOUR**

Il s’agit d’une brève introduction à la création de services gRPC dans ASP.NET Core 3,0 avec une référence particulière à WCF en tant que plateforme analogue. Il explique les principes de gRPC, en associant chaque concept aux fonctionnalités équivalentes de WCF, et fournit des conseils pour la migration d’une application WCF existante vers gRPC. Elle est également utile pour les développeurs qui ont une expérience de WCF et qui cherchent à apprendre gRPC à créer de nouveaux services. L’exemple d’application peut être utilisé comme modèle ou référence pour vos propres projets, et vous êtes libre de copier et réutiliser le code du livre ou de ses exemples.

N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités. Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.

## <a name="references"></a>Références

- **site Web gRPC**  
  <https://grpc.io>
- **Choix entre .NET Core et .NET Framework pour les applications serveur**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
