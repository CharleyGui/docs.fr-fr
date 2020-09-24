---
title: Blazor pour les développeurs ASP.NET Web Forms
description: Découvrez comment créer des applications Web à pile complète avec .NET avec Blazor et .net Core de manière simple et familière.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 3ac9a02a2f5c93cbfd9377a9f6fff4b6c5f45e93
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158173"
---
# <a name="no-locblazor-for-aspnet-web-forms-developers"></a>Blazor pour les développeurs ASP.NET Web Forms

![Capture d’écran montrant la couverture de livre électronique applications sans serveur.](./media/index/blazor-for-aspnet-web-forms-developers.png)

> TÉLÉCHARGEMENT disponible à l’adresse suivante : <https://aka.ms/blazor-ebook>

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2020 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteurs :

> **[Daniel Roth](https://github.com/danroth27)**, responsable de programme principal, Microsoft Corp.

> **[Jeff Fritz](https://github.com/csharpfritz)**, responsable de programme senior, Microsoft Corp.

> **[Taylor Southwick](https://github.com/twsouthwick)**, ingénieur logiciel senior, Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)**, développeur de contenu senior, Microsoft Corp.

> **[Steve « ardalis » Smith](https://ardalis.com)**, architecte logiciel et formateur, ARDALIS Services LLC

## <a name="introduction"></a>Introduction

.NET offre un développement d’applications Web long pris en charge via ASP.NET, un ensemble complet d’infrastructures et d’outils permettant de créer n’importe quel type d’application Web. ASP.NET a son propre lignage de frameworks et de technologies Web en commençant par les pages ASP (Classic Active Server Pages). Les infrastructures comme ASP.NET Web Forms, ASP.NET MVC, pages Web ASP.NET et les ASP.NET Core plus récentes offrent un moyen productif et puissant de créer des applications Web de type *serveur* , où le contenu de l’interface utilisateur est généré dynamiquement sur le serveur en réponse aux requêtes http. Chaque Framework ASP.NET répond à un public et une philosophie de construction d’applications différents. ASP.NET Web Forms fourni avec la version d’origine du .NET Framework et du développement Web activé à l’aide de nombreux modèles familiers pour les développeurs de bureau, comme les contrôles d’interface utilisateur réutilisables avec une gestion des événements simple. Toutefois, aucune des offres ASP.NET ne permet d’exécuter du code qui s’exécute dans le navigateur de l’utilisateur. Pour ce faire, il est nécessaire d’écrire du code JavaScript et d’utiliser l’un des nombreux frameworks et outils JavaScript qui ont été mis en avant et non en popularité au fil des années : jQuery, Knockout, angulaire, REACT, etc.

[Blazor](https://blazor.net) est une nouvelle infrastructure Web qui change ce qui est possible lors de la création d’applications Web avec .NET. Blazor est une infrastructure d’interface utilisateur Web côté client basée sur C# au lieu de JavaScript. Avec Blazor , vous pouvez écrire vos composants de logique et d’interface utilisateur côté client en C#, les compiler dans des assemblys .NET normaux, puis les exécuter directement dans le navigateur à l’aide d’une nouvelle norme Web ouverte appelée WebAssembly . Vous Blazor pouvez également exécuter vos composants de l’interface utilisateur .net sur le serveur et gérer les interactions de l’interface utilisateur de manière fluide sur une connexion en temps réel avec le navigateur. En cas de jumelage avec .NET exécuté sur le serveur, Blazor active le développement Web à pile complète avec .net. Tandis que Blazor partage de nombreux points communs avec ASP.NET Web Forms, comme le fait de disposer d’un modèle de composant réutilisable et d’un moyen simple de gérer les événements utilisateur, il s’appuie également sur les fondements de .net Core pour offrir une expérience de développement Web moderne et hautes performances.

Cet ouvrage présente ASP.NET Web Forms les développeurs à d' Blazor une manière familière et pratique. Il présente Blazor les concepts en parallèle avec les concepts analogues dans ASP.NET Web Forms tout en expliquant les nouveaux concepts qui peuvent être moins familiers. Il couvre un large éventail de sujets et de préoccupations, notamment la création de composants, le routage, la disposition, la configuration et la sécurité. Et si le contenu de ce livre est principalement destiné à l’activation d’un nouveau développement, il couvre également les instructions et les stratégies de migration des Web Forms ASP.NET existants vers Blazor pour, lorsque vous souhaitez moderniser une application existante.

## <a name="who-should-use-the-book"></a>Qui doit utiliser le livre

Ce livre est destiné aux développeurs ASP.NET Web Forms qui recherchent une introduction à Blazor ce qui concerne leurs connaissances et leurs compétences existantes. Ce livre peut vous aider à démarrer rapidement un projet basé sur de nouveaux Blazor projets ou à vous aider à créer un graphique pour la modernisation d’une application ASP.NET Web Forms existante.

## <a name="how-to-use-the-book"></a>Comment utiliser le livre

La première partie de ce livre couvre ce qui Blazor est et le compare au développement d’applications Web avec ASP.NET Web Forms. Le livre aborde ensuite une variété de Blazor sujets, le chapitre par chapitre, et met en relation chaque Blazor concept avec le concept correspondant dans ASP.NET Web Forms, ou explique entièrement tout un ensemble de concepts. Le livre fait également référence régulièrement à un exemple d’application complet implémenté à la fois dans ASP.NET Web Forms et Blazor pour illustrer les Blazor fonctionnalités et fournir une étude de cas pour la migration de ASP.NET Web Forms vers Blazor . Vous pouvez trouver les deux implémentations de l’exemple d’application (ASP.NET Web Forms et Blazor versions) sur [GitHub](https://github.com/dotnet-architecture/eshoponblazor).

## <a name="what-this-book-doesnt-cover"></a>Ce que ce livre ne couvre pas

Ce livre est une introduction à Blazor , pas un guide de migration complet. Bien qu’il inclue des conseils sur la façon d’approcher de la migration d’un projet de ASP.NET Web Forms vers Blazor , il n’essaie pas de couvrir toutes les nuances et les détails. Pour plus d’informations générales sur la migration de ASP.NET vers ASP.NET Core, reportez-vous aux [instructions de migration](/aspnet/core/migration/proper-to-2x/) dans la documentation ASP.net core.

### <a name="additional-resources"></a>Ressources supplémentaires

Vous trouverez la page d' Blazor hébergement officielle et la documentation à l’adresse <https://blazor.net> .

## <a name="send-your-feedback"></a>Envoyez votre feedback

Ce livre et les exemples associés sont en constante évolution. vos commentaires sont donc accueillis ! Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section commentaires au bas de toute page reposant sur les [problèmes GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](introduction.md)
