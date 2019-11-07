---
title: ASP.NET Core gRPC pour les développeurs WCF-gRPC pour les développeurs WCF
description: Introduction à la création de services gRPC dans ASP.NET Core 3,0 pour les développeurs WCF
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b89f5974dd18e7005c6479c5b9eead039364e654
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738069"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>gRPC ASP.NET Core pour les développeurs WCF

![image de couverture](./media/cover.png)

PUBLIÉ PAR

Division Développeur Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs. Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.

Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteur :

> **Mark Rendle** -directeur technique – rédacteur [visuel](https://visualrecode.com)
>
> **Miranda Steiner** -auteur technique

Rédacteurs :

> Développeur de contenu **Maira Wenzel** -SR-Microsoft

## <a name="introduction"></a>Introduction

gRPC est une infrastructure moderne pour la création de services en réseau et d’applications distribuées. Imaginez les performances des liaisons NetTCP de WCF avec l’interopérabilité multiplateforme de SOAP. gRPC s’appuie sur HTTP/2 et le protocole d’encodage de message Protobuf pour fournir une communication haute performance et à faible bande passante entre les applications et les services. Il prend en charge la génération de code serveur et client dans les langages et plateformes de programmation les plus populaires, notamment .NET, Java C++ , Python, node. js, Go, etc. Avec la prise en charge de première classe de gRPC dans ASP.NET Core 3,0, en plus des outils et bibliothèques gRPC existants pour .NET 4. x, nous pensons qu’il s’agit d’une excellente alternative à WCF pour les équipes de développement souhaitant adopter .NET Core dans leurs organisations.

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Ce guide a été rédigé pour les développeurs qui travaillent dans .NET Framework ou .NET Core qui ont déjà utilisé WCF et qui cherchent à migrer leurs applications vers un environnement RPC moderne pour .NET Core 3,0 et versions ultérieures. Le guide peut également être utilisé plus généralement pour les développeurs qui effectuent la mise à niveau vers .NET Core 3,0 qui souhaitent utiliser les outils gRPC intégrés.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Il s’agit d’une brève introduction à la création de services gRPC dans ASP.NET Core 3,0 avec une référence particulière à WCF en tant que plateforme analogue. Il explique les principes de gRPC, en associant chaque concept aux fonctionnalités équivalentes de WCF, et fournit des conseils pour la migration d’une application WCF existante vers gRPC. Elle est également utile pour les développeurs qui ont une expérience de WCF et qui cherchent à apprendre gRPC à créer de nouveaux services. Les exemples d’applications peuvent être utilisés comme modèle ou référence pour vos propres projets, et vous êtes libre de copier et réutiliser le code du livre ou de ses exemples.

N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités. Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.

## <a name="references"></a>Références

- **site Web gRPC**  
  <https://grpc.io>
- **Choix entre .NET Core et .NET Framework pour les applications serveur**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Suivant](introduction.md)
