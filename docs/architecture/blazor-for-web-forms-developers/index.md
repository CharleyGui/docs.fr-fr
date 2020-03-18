---
title: Blazor pour les développeurs ASP.NET Web Forms
description: Apprenez à créer des applications Web pleine pile avec .NET en utilisant Blazor et .NET Core d’une manière simple et familière.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 394d11038b59f4cbe9e9955df43b6198eb5daaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73088132"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>Blazor pour les développeurs ASP.NET Web Forms

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![Capture d’écran qui montre la couverture du livre électronique Serverless Apps.](./media/index/blazor-for-web-forms-developers-cover.png)

> TÉLÉCHARGEMENT disponible à l’adresse suivante : <https://aka.ms/blazor-ebook>

PUBLIÉ PAR

Division Développeurs Microsoft, équipes produit .NET et Visual Studio

Division de Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 par Microsoft Corporation

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

 Certains exemples sont fournis à titre indicatif uniquement et sont fictifs. Toute association ou lien est purement involontaire ou fortuit.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.

Mac et macOS sont des marques commerciales d’Apple Inc.

Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.

Auteurs :

> **[Daniel Roth](https://github.com/danroth27)**, Gestionnaire principal de programme, Microsoft Corp.

> **[Jeff Fritz](https://github.com/csharpfritz)**, Senior Program Manager, Microsoft Corp.

> **[Taylor Southwick](https://github.com/twsouthwick)**, Ingénieur Logiciel Senior, Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)**, Développeur de contenu senior, Microsoft Corp.

## <a name="introduction"></a>Introduction

.NET a longtemps pris en charge le développement d’applications Web par le biais de ASP.NET, un ensemble complet de cadres et d’outils pour la construction de tout type d’application web. ASP.NET possède sa propre lignée de cadres web et de technologies qui reprennent tout le chemin du retour avec des pages de serveur actif classiques (ASP). Des cadres comme ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages et, plus récemment, ASP.NET Core, fournissent un moyen productif et puissant de créer des applications Web *rendues par le serveur,* où le contenu de l’interface utilisateur est généré dynamiquement sur le serveur en réponse aux demandes HTTP. Chaque ASP.NET cadre s’adresse à un public différent et à une philosophie de construction d’applications. ASP.NET Web Forms expédiés avec la version originale du cadre .NET et a permis le développement Web en utilisant de nombreux modèles familiers aux développeurs de bureau, comme les contrôles réutilisables de l’interface utilisateur avec une simple gestion d’événements. Cependant, aucune des offres ASP.NET ne fournit un moyen d’exécuter le code qui a été exécuté dans le navigateur de l’utilisateur. Pour ce faire, il faut écrire JavaScript et utiliser l’un des nombreux cadres et outils JavaScript qui ont progressivement entrer et hors de popularité au fil des ans: jQuery, Knockout, Angular, Réagir, et ainsi de suite.

[Blazor](https://blazor.net) est un nouveau cadre web qui change ce qui est possible lors de la création d’applications Web avec .NET. Blazor est un cadre d’interface utilisateur web côté client basé sur C au lieu de JavaScript. Avec Blazor, vous pouvez écrire votre logique client-côté et les composants d’interface utilisateur dans C, les compiler dans les assemblages .NET normaux, puis les exécuter directement dans le navigateur à l’aide d’une nouvelle norme Web ouverte appelée WebAssembly. Ou alternativement, Blazor peut exécuter vos composants d’interface utilisateur .NET sur le serveur et gérer toutes les interactions d’interface utilisateur fluidement sur une connexion en temps réel avec le navigateur. Lorsqu’il est jumelé avec .NET en cours d’exécution sur le serveur, Blazor permet le développement web pleine pile avec .NET. Alors que Blazor partage de nombreuses points communs avec ASP.NET Web Forms, comme avoir un modèle de composants réutilisables et une façon simple de gérer les événements des utilisateurs, il s’appuie également sur les fondations de .NET Core pour fournir une expérience de développement Web moderne et haute performance.

Ce livre présente ASP.NET développeurs Web Forms à Blazor d’une manière qui est familière et pratique. Il introduit des concepts Blazor en parallèle avec des concepts analogues dans ASP.NET Web Forms tout en expliquant de nouveaux concepts qui peuvent être moins familiers. Il couvre un large éventail de sujets et de préoccupations, y compris la rédaction de composants, le routage, la mise en page, la configuration et la sécurité. Et tandis que le contenu de ce livre est principalement pour permettre de nouveaux développements, il couvre également les lignes directrices et les stratégies pour migrer les formulaires Web ASP.NET existants à Blazor pour quand vous voulez moderniser une application existante.

## <a name="who-should-use-the-book"></a>Qui devrait utiliser le livre

Ce livre est destiné aux développeurs de formulaires Web ASP.NET à la recherche d’une introduction à Blazor qui se rapporte à leurs connaissances et compétences existantes. Ce livre peut aider à démarrer rapidement sur un nouveau projet basé sur Blazor ou à aider à tracer une feuille de route pour la modernisation d’une application existante ASP.NET Web Forms.

## <a name="how-to-use-the-book"></a>Comment utiliser le livre

La première partie de ce livre couvre ce qu’est Blazor et le compare au développement d’applications Web avec ASP.NET Web Forms. Le livre couvre ensuite une variété de sujets Blazor, chapitre par chapitre, et relie chaque concept Blazor au concept correspondant dans ASP.NET Web Forms, ou explique pleinement tous les concepts complètement nouveaux. Le livre fait également référence régulièrement à une application complète d’échantillons mise en œuvre dans ASP.NET Web Forms et Blazor pour démontrer les fonctionnalités de Blazor et pour fournir une étude de cas pour la migration de ASP.NET formulaires Web à Blazor. Vous pouvez trouver les deux implémentations de l’application d’échantillon (ASP.NET Web Forms et versions Blazor) sur [GitHub](https://github.com/dotnet-architecture/eshoponblazor).

## <a name="what-this-book-doesnt-cover"></a>Ce que ce livre ne couvre pas

Ce livre est une introduction à Blazor, pas un guide complet de migration. Bien qu’il inclue des conseils sur la façon d’aborder la migration d’un projet de ASP.NET Web Forms à Blazor, il ne tente pas de couvrir toutes les nuances et les détails. Pour obtenir des directives plus générales sur la migration de ASP.NET à ASP.NET Core, consultez les [orientations migratoires](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) de la documentation de base ASP.NET.

### <a name="additional-resources"></a>Ressources supplémentaires

Vous pouvez trouver la page d’accueil <https://blazor.net>officielle Blazor et la documentation à .

## <a name="send-your-feedback"></a>Envoyez votre feedback

Ce livre et les échantillons connexes sont en constante évolution, de sorte que vos commentaires sont les bienvenus! Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section de rétroaction au bas de n’importe quelle page construite sur [les questions GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Suivant](introduction.md)
