---
title: Architecture des applications .NET natives Cloud pour Azure
description: Guide pour la création d’applications Cloud natives tirant parti de conteneurs, de microservices et de fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 67e235b051702308d2455b2501bfb59a4317635b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214168"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Architecture des applications .NET natives Cloud pour Azure

![image de couverture](./media/cover.png)

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs. Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Le logo de Docker représentant une baleine est une marque déposée de Docker, Inc. Utilisé sous autorisation.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Extrait

> **Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)
>
> **Rob** -Guide-Microsoft-principal Cloud System Architect/IP architect- [RobVettor.com](https://robvettor.com)

Participants et réviseurs :

> **Cesar de la Torre**, responsable de programme principal, équipe .net, Microsoft
>
> **Nish Anil**, responsable de programme senior, équipe .NET, Microsoft

Rédacteurs :

> **Maira Wenzel**, développeur de service de contenu, équipe .net, Microsoft

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
>[Next](introduction.md)
