---
title: Architecting Cloud Native .NET Applications pour Azure
description: Un guide pour la construction d’applications cloud-natives tirant parti des conteneurs, des microservices et des fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: cf3be07f0d37aacf4f0252ef2f4d922b7be93eee
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989062"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Architecting Cloud Native .NET Applications pour Azure

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

Le logo de la baleine Docker est une marque déposée de Docker, Inc. Utilisée par permission.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteurs :

> **Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)
>
> **Rob Vettor** - Microsoft - Architecte principal du système Cloud/IP Architecte - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)

Participants et évaluateurs :

> **Cesar De la Torre**, Gestionnaire principal de programme, équipe .NET, Microsoft
>
> **Nish Anil**, responsable de programme senior, équipe .NET, Microsoft

Rédacteurs :

> **Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Le public de ce guide est principalement des développeurs, des responsables du développement et des architectes qui sont intéressés à apprendre à construire des applications conçues pour le cloud.

Un public secondaire est celui des décideurs techniques qui prévoient choisir de construire ou non leurs applications en utilisant une approche cloud-native.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Ce guide commence par définir le cloud natif et l’introduction d’une application de référence construite en utilisant des principes et des technologies cloud-native. Au-delà de ces deux premiers chapitres, le reste du livre est divisé en chapitres spécifiques axés sur des sujets communs à la plupart des applications cloud-natives. Vous pouvez sauter à l’un de ces chapitres pour en apprendre davantage sur les approches cloud-native à:

- Accès aux données et aux données
- Modèles de communication
- Mise à l’échelle et évolutivité
- Résilience de la demande
- Supervision et intégrité
- Identité et sécurité
- DevOps

Ce guide est disponible en format PDF et en ligne. N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe pour vous aider à assurer une compréhension commune de ces sujets. La plupart de ces sujets bénéficient d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions liées à ces sujets. Notre objectif avec ce document est d’équiper les équipes et leurs dirigeants avec les informations dont ils ont besoin pour prendre des décisions bien informées pour l’architecture, le développement et l’hébergement de leurs applications.

>[!div class="step-by-step"]
>[Suivant](introduction.md)
