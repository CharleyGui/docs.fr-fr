---
title: ASP.NET Core gRPC pour WCF Developers - gRPC pour les développeurs WCF
description: Introduction à la construction de services gRPC dans ASP.NET Core 3.0 pour les développeurs WCF
ms.date: 09/02/2019
ms.openlocfilehash: 175dfbf1880a0937615543c248fba3bed0e25c23
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988958"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>gRPC ASP.NET Core pour les développeurs WCF

![image de couverture](./media/cover.png)

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur https://www.microsoft.com sont des marques du groupe Microsoft.

Le logo de la baleine Docker est une marque déposée de Docker, Inc. Utilisée par permission.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteurs :

> **Mark Rendle** - Directeur Technique - [Code visuel](https://visualrecode.com)
>
> **Miranda Steiner** - Auteur technique

Éditeur :

> **Maira Wenzel** - Développeur de contenu Sr. - Microsoft

## <a name="introduction"></a>Introduction

gRPC est un cadre moderne pour la construction de services en réseau et d’applications distribuées. Imaginez les performances des liaisons NetTCP de la Windows Communication Foundation (WCF), combinées à l’interopérabilité multiplateforme de SOAP. gRPC s’appuie sur HTTP/2 et le protocole d’encodage de messages Protobuf pour fournir une communication haute performance et à faible bande passante entre les applications et les services. Il prend en charge la génération de code serveur et client à travers les langages de programmation les plus populaires et les plates-formes, y compris .NET, Java, Python, Node.js, Go, et C . Avec le soutien de première classe pour gRPC dans ASP.NET Core 3.0, aux côtés des outils et des bibliothèques gRPC existants pour .NET 4.x, c’est une excellente alternative à WCF pour les équipes de développement qui cherchent à adopter .NET Core dans leurs organisations.

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Ce guide a été écrit pour les développeurs travaillant dans .NET Framework ou .NET Core qui ont déjà utilisé WCF, et qui cherchent à migrer leurs applications vers un environnement RPC moderne pour .NET Core 3.0 et les versions ultérieures. Plus généralement, si vous améliorez, ou envisagez de mise à niveau, à .NET Core 3.0, et que vous souhaitez utiliser les outils gRPC intégrés, ce guide est également utile.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Il s’agit d’une brève introduction à la construction de services gRPC dans ASP.NET Core 3.0, avec une référence particulière à WCF comme une plate-forme analogue. Il explique les principes de gRPC, reliant chaque concept aux caractéristiques équivalentes de WCF, et offre des conseils pour la migration d’une application WCF existante à gRPC. Il est également utile pour les développeurs qui ont de l’expérience avec WCF et cherchent à apprendre gRPC pour construire de nouveaux services. Vous pouvez utiliser les applications d’exemple comme modèle ou référence pour vos propres projets, et vous êtes libre de copier et de réutiliser le code du livre ou de ses échantillons.

N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités. Le fait que tout le monde travaille à partir d’un ensemble commun de termes et de principes sous-jacents permet d’assurer une application cohérente des modèles et des pratiques architecturales.

## <a name="references"></a>References

- **site Web de gRPC**
  <https://grpc.io>
- **Choisir entre .NET Core et .NET Framework pour les applications serveur**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Suivant](introduction.md)
