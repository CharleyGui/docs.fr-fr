---
title: ASP.NET Core gRPC pour les développeurs WCF-gRPC pour les développeurs WCF
description: Introduction à la création de services gRPC dans ASP.NET Core 3,0 pour les développeurs WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543233"
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

Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.

Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteurs :

> **Mark Rendle** -directeur technique – rédacteur [visuel](https://visualrecode.com)
>
> **Miranda Steiner** -auteur technique

Éditeur :

> **Maira Wenzel** -SR. Content Developer-Microsoft

## <a name="introduction"></a>Introduction

gRPC est une infrastructure moderne pour la création de services en réseau et d’applications distribuées. Imaginez les performances Windows Communication Foundation des liaisons NetTCP (WCF), combinées avec l’interopérabilité multiplateforme de SOAP. gRPC s’appuie sur HTTP/2 et le protocole d’encodage de message Protobuf pour fournir une communication haute performance et à faible bande passante entre les applications et les services. Il prend en charge la génération de code serveur et client dans les langages et plateformes de programmation les plus populaires, notamment .NET, Java, C++Python, node. js, Go et. Avec la prise en charge de première classe de gRPC dans ASP.NET Core 3,0, en plus des outils et bibliothèques gRPC existants pour .NET 4. x, il s’agit d’une excellente alternative à WCF pour les équipes de développement souhaitant adopter .NET Core dans leurs organisations.

## <a name="who-should-use-this-guide"></a>À qui s'adresse ce guide ?

Ce guide a été rédigé pour les développeurs qui travaillent dans .NET Framework ou .NET Core qui ont déjà utilisé WCF et qui cherchent à migrer leurs applications vers un environnement RPC moderne pour .NET Core 3,0 et versions ultérieures. Plus généralement, si vous effectuez une mise à niveau ou si vous envisagez une mise à niveau vers .NET Core 3,0 et que vous souhaitez utiliser les outils intégrés gRPC, ce guide est également utile.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Il s’agit d’une brève introduction à la création de services gRPC dans ASP.NET Core 3,0, avec une référence particulière à WCF en tant que plateforme analogue. Il explique les principes de gRPC, en associant chaque concept aux fonctionnalités équivalentes de WCF, et fournit des conseils pour la migration d’une application WCF existante vers gRPC. Elle est également utile pour les développeurs qui ont une expérience de WCF et qui cherchent à apprendre gRPC à créer de nouveaux services. Vous pouvez utiliser les exemples d’applications comme modèle ou référence pour vos propres projets, et vous êtes libre de copier et réutiliser le code du livre ou de ses exemples.

N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités. Faire en sorte que tout le monde travaille à partir d’un ensemble commun de termes et de principes sous-jacents permet d’assurer une application cohérente des modèles et des pratiques d’architecture.

## <a name="references"></a>References

- 
  du **site Web gRPC** <https://grpc.io>
- **Choix entre .net Core et .NET Framework pour les applications serveur**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
