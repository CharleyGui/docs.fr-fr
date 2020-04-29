---
title: Architecture des applications .NET natives Cloud pour Azure
description: Guide pour la création d’applications Cloud natives tirant parti de conteneurs, de microservices et de fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 04/23/2020
ms.openlocfilehash: 24d5c75fc5d2e5623892e8f83daea52553d13765
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507388"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Architecture des applications .NET natives Cloud pour Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![image de couverture](./media/cover.png)

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2019 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur https://www.microsoft.com sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteurs :

> **Rob**distribuateur, architecte du système Cloud principal/architecte IP- [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft
>
> **Steve « ardalis » Smith**, architecte logiciel et formateur- [Ardalis.com](https://ardalis.com)

Participants et réviseurs :

> **Cesar de la Torre**, responsable de programme principal, équipe .net, Microsoft
>
> **Nish Anile**, responsable de programme senior, équipe .net, Microsoft
>
> **Jeremy Likness**, responsable de programme senior, équipe .net, Microsoft
>
> **Cecil Phillip**, avocat du Cloud senior, Microsoft

En savoir plus sur eShopOnContainers

Rédacteurs :

> **Maira Wenzel**, responsable de programme, équipe .net, Microsoft

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

Ce guide est disponible au format PDF et en ligne. N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe afin de garantir une compréhension commune de ces sujets. La plupart de ces rubriques tirent parti d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions relatives à ces sujets. L’objectif de ce document est de fournir aux équipes et à leurs dirigeants les informations dont elles ont besoin pour prendre des décisions bien informées sur l’architecture, le développement et l’hébergement de leurs applications.

>[!div class="step-by-step"]
>[Suivant](introduction.md)
