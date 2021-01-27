---
title: Kit SDK .NET Compiler Platform (API Roslyn)
description: Apprenez à utiliser le Kit de développement logiciel (SDK) .NET Compiler Platform (également appelé API Roslyn) pour comprendre le code .NET, identifier les erreurs et les corriger.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: cd81551234a1bc955323e392f473cd01180f6dc5
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899241"
---
# <a name="the-net-compiler-platform-sdk"></a>Kit SDK .NET Compiler Platform

Les compilateurs génèrent un modèle détaillé du code applicatif lorsqu’ils en valident la syntaxe et la sémantique. Ce modèle permet de générer la sortie exécutable à partir du code source. Le Kit SDK .NET Compiler Platform donne accès à ce modèle. Nous nous appuyons de plus en plus sur des fonctionnalités d’environnements de développement intégré (IDE) telles qu’IntelliSense, la refactorisation, le renommage intelligent, la recherche de l’ensemble des références et l’accès direct aux définitions pour augmenter notre productivité. Nous utilisons des outils d’analyse du code pour améliorer la qualité de notre code et des générateurs de code pour faciliter la construction des applications. Plus ces outils gagnent en intelligence, plus ils ont besoin d’accéder à une grande part du modèle que seuls les compilateurs créent lorsqu’ils traitent le code applicatif. Il s’agit de la mission principale des API Roslyn : l’ouverture des zones opaques et l’autorisation des outils et des utilisateurs finaux à partager au sein de la multitude de compilateurs d’informations sur notre code.
Au lieu de rester d’opaques traducteurs de code source en code objet, les compilateurs deviennent des plateformes avec Roslyn : des API utilisables pour les tâches portant sur le code dans les outils et les applications souhaités.

## <a name="net-compiler-platform-sdk-concepts"></a>Concepts du Kit SDK .NET Compiler Platform

Le Kit SDK .NET Compiler Platform réduit considérablement la barrière à l’entrée pour la création d’applications et d’outils axés sur le code. Il crée de nombreuses opportunités d’innovation dans des domaines tels que la méta-programmation, la génération et la transformation de code, l’utilisation interactive des langages C# et Visual Basic, ainsi que l’incorporation de C# et de Visual Basic dans des langages spécifiques à un domaine.

Le kit de développement logiciel (SDK) .NET Compiler Platform vous permet de générer des ***analyseurs** et des _*_correctifs de code_*_ qui recherchent et corrigent les erreurs de codage. Les _*_analyseurs_*_ comprennent la syntaxe (structure de code) et la sémantique pour détecter les pratiques qui doivent être corrigées. Les _*_correctifs de code_*_ fournissent un ou plusieurs correctifs suggérés pour résoudre les erreurs de codage détectées par les analyseurs ou les diagnostics du compilateur. En règle générale, un analyseur et les correctifs de code associés sont regroupés dans un seul projet.

Les analyseurs et les correctifs de code utilisent l’analyse statique pour comprendre le code. Ils n’exécutent pas le code, et n’offrent aucun autre avantage en matière de tests. Toutefois, ils peuvent signaler des pratiques qui mènent souvent à des bogues, à un code non gérable ou à une violation des indications standard.

En plus des analyseurs et des correctifs de code, le kit de développement logiciel (SDK) .NET Compiler Platform vous permet également de créer des _*_refactorisations de code_*_.
Il fournit également un ensemble unique d’API qui vous permettent d’examiner et de comprendre un code base C# ou Visual Basic. Grâce à ce codebase unique, il est plus facile d’écrire des analyseurs et des correctifs de code en utilisant les API d’analyse syntaxique et sémantique fournies par le Kit SDK .NET Compiler Platform. Une fois libéré de la tâche chronophage qui consiste à répliquer l’analyse effectuée par le compilateur, vous pouvez vous concentrer sur la tâche, plus ciblée, de recherche et de résolution des erreurs de codage courantes de votre projet ou de votre bibliothèque.

Autre avantage, plus modeste, vos analyseurs et vos correctifs de code sont plus petits et utilisent beaucoup moins de mémoire une fois chargés dans Visual Studio que si vous aviez écrit votre propre codebase pour comprendre le code d’un projet. En exploitant les mêmes classes que le compilateur et Visual Studio, vous pouvez créer vos propres outils d’analyse statique. Votre équipe a donc la possibilité d’utiliser des analyseurs et des correctifs de code sans impact perceptible sur les performances de l’IDE.

Il existe trois grands scénarios d’écriture d’analyseurs et de correctifs de code :

1. [_Enforce les normes de codage d’équipe *](#enforce-team-coding-standards)
1. [*Offrir de l’aide sur les packages de bibliothèque*](#provide-guidance-with-library-packages)
1. [*Proposer des conseils généraux*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Appliquer des normes de codage pour l’équipe

De nombreuses équipes ont des normes de codage, qui sont appliquées par le biais des révisions du code effectuées avec d’autres membres de l’équipe. Les analyseurs et les correctifs de code peuvent rendre ce processus beaucoup plus efficace. Les revues de code se produisent quand un développeur partage son travail avec d’autres membres de l’équipe. Le développeur aura investi tout le temps nécessaire pour terminer une nouvelle fonctionnalité avant de recevoir le moindre commentaire. Plusieurs semaines peuvent s’écouler, au cours desquelles le développeur renforce des habitudes qui ne correspondent pas aux pratiques de l’équipe.

Les analyseurs s’exécutent au moment même où il écrit du code. Le développeur obtient immédiatement des commentaires qui l’encouragent à suivre les instructions sans attendre. Le développeur prend l’habitude d’écrire du code conforme dès qu’il commence le prototypage. Lorsque la fonctionnalité est prête à être révisée par des humains, toutes les instructions standard ont été appliquées.

Les équipes peuvent créer des analyseurs et des correctifs de code permettant de rechercher les pratiques les plus courantes qui enfreignent les pratiques de codage de l’équipe. Ils peuvent être installés sur l’ordinateur de chaque développeur pour appliquer les normes.

> [!TIP]
> Avant de créer votre propre analyseur, consultez les éléments intégrés. Pour plus d’informations, consultez [règles de style de code](../../fundamentals/code-analysis/overview.md#code-style-analysis).

## <a name="provide-guidance-with-library-packages"></a>Offrir de l’aide sur les packages de bibliothèque

De nombreuses bibliothèques sont disponibles pour les développeurs .NET sur NuGet.
Certaines proviennent de Microsoft ou de sociétés tierces, d’autres sont proposées par des membres de la communauté et des bénévoles. Ces bibliothèques sont plus souvent utilisées et sont mieux notées lorsque les développeurs réussissent à les exploiter.

En plus de la documentation, vous pouvez proposer des analyseurs et des correctifs de code qui recherchent et corrigent les mauvais emplois courants de votre bibliothèque. Ces corrections immédiates aident les développeurs à en tirer parti plus rapidement.

Vous pouvez ajouter les analyseurs et les correctifs de code au package de votre bibliothèque sur NuGet. Dans ce scénario, un développeur qui installe votre package NuGet installera également le package de l’analyseur. Tous les développeurs qui utilisent votre bibliothèque obtiennent immédiatement de l’aide de la part de votre équipe sous la forme de commentaires immédiats sur les erreurs et de suggestions de corrections.

## <a name="provide-general-guidance"></a>Proposer des conseils généraux

La communauté de développeurs .NET a découvert, par l’expérience, des modèles qui fonctionnent correctement et des modèles qui sont mieux évités. Plusieurs membres de la communauté ont créé des analyseurs qui appliquent ces modèles recommandés. Plus nous gagnons en expérience, plus il y a de place pour de nouvelles idées.

Ces analyseurs peuvent être chargés sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) et téléchargés par les développeurs avec Visual Studio. Ceux qui débutent avec le langage et la plateforme apprennent rapidement les pratiques acceptées et deviennent plus vite productifs, dès le début de leur parcours d’apprentissage de .NET. Comme ils sont de plus en plus utilisés, la communauté adopte ces pratiques.

## <a name="next-steps"></a>Étapes suivantes

Le Kit SDK .NET Compiler Platform inclut les derniers modèles objet du langage pour la génération, l’analyse et la refactorisation de code. Cette section offre une vue d’ensemble conceptuelle du Kit SDK .NET Compiler Platform. Vous trouverez plus de détails dans les sections Démarrages rapides, exemples et didacticiels.

Pour en savoir plus sur les concepts du Kit SDK .NET Compiler Platform, consultez ces cinq rubriques :

- [Explorer le code avec le visualiseur de syntaxe](syntax-visualizer.md)
- [Comprendre le modèle de l’API du compilateur](compiler-api-model.md)
- [Utiliser la syntaxe](work-with-syntax.md)
- [Utiliser la sémantique](work-with-semantics.md)
- [Utiliser un espace de travail](work-with-workspace.md)

Pour commencer, vous devez installer le kit **.NET Compiler Platform SDK** :

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
