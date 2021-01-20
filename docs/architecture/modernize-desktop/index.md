---
title: Moderniser des applications de bureau sur Windows 10 avec .NET 5
description: Découvrez comment moderniser les applications de bureau existantes avec .NET 5
ms.date: 01/06/2021
ms.openlocfilehash: de8a451b0598b5eabd99028d377c161dace61623
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615700"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-5"></a>Moderniser des applications de bureau sur Windows 10 avec .NET 5

![Capture d’écran illustrant le livre électronique « Modern Desktop apps ».](./media/modernizing-existing-desktop-apps-ebook-cover.png)

**Edition v 1.0.1** -mise à jour vers .net 5

Reportez-vous à [Journal des modifications](https://aka.ms/desktop-ebook-changelog) pour les mises à jour de livres et les contributions de la communauté.

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2021 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Coauteurs :

> **Olia Gavrysh**, responsable de programme, équipe .net, Microsoft

> **Miguel Angel Castejón Dominguez**, architecte d’innovation, Kabel

Participants et réviseurs :

> **Maira Wenzel**, responsable de programme senior, équipe .net, Microsoft

> **Andy gorge**, développeur de contenu senior, équipe .net docs, Microsoft

> **Miguel Ramos**, responsable de programme senior, équipe Windows Developer Platform, Microsoft

> **Adam Braden**, responsable de programme principal, équipe de plateforme de développement Windows, Microsoft

> **Ricardo Minguez Pablos**, responsable de programme senior, équipe Azure IOT, Microsoft

> **Nish Anile**, responsable de programme senior, équipe .net, Microsoft

> **Beth Massei**, responsable marketing produit senior, Microsoft

> **Scott Hunter**, responsable partenaire directeur de programme, équipe .net, Microsoft

> **Marta Fuentes Lara**, Kabel

> **Raúl Fernández de nicaraguayen**, Kabel

> **Antonio Manuel Fernández Cantos**, Kabel

## <a name="introduction"></a>Introduction

Ce livre concerne les stratégies que vous pouvez adopter pour déplacer vos applications de bureau existantes à travers le chemin de modernisation et intégrer les dernières fonctionnalités de Runtime, de langage et de plateforme. Vous découvrirez qu’il n’existe pas de recette unique dans la mesure où chaque application est différente, et donc vos exigences et vos préférences. La bonne nouvelle, c’est qu’il existe des approches courantes que vous pouvez appliquer pour ajouter de nouvelles fonctionnalités à vos applications. Certaines d’entre elles ne nécessitent même pas de modifications majeures de votre code. Dans cet ouvrage, nous allons vous montrer comment toutes ces fonctionnalités fonctionnent en arrière-plan et expliquent les mécanismes de leurs implémentations. En outre, vous trouverez des scénarios courants pour la modernisation des applications de bureau existantes en détail, ce qui vous permet de trouver de l’inspiration pour l’évolution de vos projets.

L’approche de Microsoft pour la modernisation des applications existantes est de vous offrir la possibilité de créer votre propre chemin personnalisé. Toutes les stratégies de modernisation décrites dans cet ouvrage sont principalement indépendantes. Vous pouvez choisir ceux qui sont pertinents pour votre application et ignorer d’autres qui ne sont pas importants pour vous. En d’autres termes, vous pouvez mélanger et faire correspondre les stratégies pour répondre au mieux aux besoins de votre application.

## <a name="who-should-use-the-book"></a>Qui doit utiliser le livre

Cet ouvrage destiné aux développeurs et aux architectes de solutions qui veulent moderniser les applications de bureau Windows Forms et WPF existantes pour tirer parti des avantages de .NET et Windows 10.

Ce livre peut également être utile si vous êtes un décideur technique, tel qu’un architecte d’entreprise ou un responsable ou directeur de développement qui souhaite une vue d’ensemble des avantages de la mise à jour des applications de bureau existantes.

## <a name="how-to-use-the-book"></a>Comment utiliser le livre

Ce livre aborde le « pourquoi », pour vous aider à moderniser vos applications existantes et les avantages spécifiques que vous pouvez vous procurer en utilisant NET et MSIX pour moderniser vos applications de bureau. Le contenu du livre est conçu pour les architectes et les décideurs techniques qui souhaitent une vue d’ensemble, mais qui n’ont pas besoin de se concentrer sur la mise en œuvre et les détails techniques, pas à pas.

Dans les différents chapitres, des exemples d’extraits de code d’implémentation et des captures d’écran sont fournis, le chapitre 5 étant destiné à présenter un processus de migration complet pour les exemples d’applications.

## <a name="what-this-book-doesnt-cover"></a>Ce que ce livre ne couvre pas

Ce livre couvre un sous-ensemble spécifique de scénarios qui se concentrent sur les scénarios d’élévation et de déplacement, en soulignant la façon d’obtenir les avantages de la modernisation sans l’effort de réécriture du code.

Ce livre ne s’intéresse pas au développement d’applications modernes avec .NET à partir de zéro ou à la prise en main de Windows Forms et de WPF. Il se concentre sur la façon dont vous pouvez mettre à jour les applications de bureau existantes avec les dernières technologies pour le développement de postes de travail.

## <a name="samples-used-in-this-book"></a>Exemples utilisés dans ce livre

Pour mettre en évidence les étapes nécessaires pour effectuer une modernisation, nous allons utiliser un exemple d’application appelé `eShopModernizing` . Cette application a deux versions, Windows Forms et WPF, et nous vous présenterons un processus pas à pas sur la façon d’effectuer la modernisation des deux à la fois sur .NET.

En outre, sur le référentiel GitHub pour ce livre, vous trouverez les résultats du processus, que vous pouvez consulter si vous décidez de suivre le didacticiel pas à pas.

## <a name="send-your-feedback"></a>Envoyez votre feedback

Ce livre et les exemples associés sont en constante évolution. vos commentaires sont donc accueillis ! Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section commentaires au bas de toute page reposant sur les [problèmes GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](why-modern-applications.md)
