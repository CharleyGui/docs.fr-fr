---
title: Architecture des applications .NET natives Cloud pour Azure
description: Guide pour la création d’applications Cloud natives tirant parti de conteneurs, de microservices et de fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 11/10/2020
ms.openlocfilehash: 673bfef27c3767f68b1c30d4383cee010ba377f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506647"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Architecture des applications .NET natives Cloud pour Azure

![image de couverture](./media/cover.png)

**ÉDITION v 1.0**

Reportez-vous à [Journal des modifications](https://aka.ms/cn-ebook-changelog) pour les mises à jour de livres et les contributions de la communauté.

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2020 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteurs :

> **Rob** distribuateur, architecte du système Cloud principal/architecte IP- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft
>
> **Steve « ardalis » Smith** , architecte logiciel et formateur- [Ardalis.com](https://ardalis.com)

Participants et réviseurs :

> **Cesar de la Torre** , responsable de programme principal, équipe .net, Microsoft
>
> **Nish Anile** , responsable de programme senior, équipe .net, Microsoft
>
> **Jeremy Likness** , responsable de programme senior, équipe .net, Microsoft
>
> **Cecil Phillip** , avocat du Cloud senior, Microsoft

Rédacteurs :

> **Maira Wenzel** , responsable de programme, équipe .net, Microsoft

## <a name="version"></a>Version

Ce guide a été écrit de façon à couvrir la version **3,1 de .net Core** , ainsi que de nombreuses mises à jour supplémentaires liées aux mêmes « vagues » de technologies (c’est-à-dire, Azure et des technologies tierces) qui coïncident avec la version 3,1 de .net core.

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Le public concerné par ce guide est principalement les développeurs, les responsables du développement et les architectes qui souhaitent apprendre à créer des applications conçues pour le Cloud.

Un public secondaire est un décideur technique qui prévoit de choisir s’il faut créer ses applications à l’aide d’une approche Cloud native.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Ce guide commence par définir le Cloud native et introduit une application de référence créée à l’aide de principes et de technologies Cloud natifs. Au-delà de ces deux premiers chapitres, le reste du livre est divisé en chapitres spécifiques axés sur les sujets communs à la plupart des applications Cloud natives. Vous pouvez accéder à l’un de ces chapitres pour en savoir plus sur les approches Cloud-natives pour :

- Données et accès aux données
- Modèles de communication
- Mise à l’échelle et évolutivité
- Résilience des applications
- Supervision et intégrité
- Identité et sécurité
- DevOps

Ce guide est disponible au format [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) et en ligne. N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe afin de garantir une compréhension commune de ces sujets. La plupart de ces rubriques tirent parti d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions relatives à ces sujets. L’objectif de ce document est de fournir aux équipes et à leurs dirigeants les informations dont elles ont besoin pour prendre des décisions bien informées sur l’architecture, le développement et l’hébergement de leurs applications.

## <a name="send-your-feedback"></a>Envoyez votre feedback

Ce livre et les exemples associés sont en constante évolution. vos commentaires sont donc accueillis ! Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section commentaires au bas de toute page reposant sur les [problèmes GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](introduction.md)
