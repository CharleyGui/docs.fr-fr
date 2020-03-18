---
title: Présentation des délégués
description: Explorez les délégués dans cette rubrique de vue d’ensemble qui présente les concepts de base et décrit les objectifs de conception de langage pour les délégués.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146227"
---
# <a name="introduction-to-delegates"></a>Présentation des délégués

Les délégués fournissent un mécanisme de *liaison tardive* dans .NET. La liaison tardive signifie que vous créez un algorithme où l’appelant fournit également au moins une méthode qui implémente une partie de l’algorithme.

Par exemple, prenez le tri d’une liste d’étoiles dans une application d’astronomie.
Vous pouvez choisir de trier les étoiles d’après leur distance par rapport à la terre, d’après leur magnitude ou d’après leur luminosité perçue.

Dans tous ces cas-là, la méthode Sort() effectue essentiellement la même chose : elle organise les éléments dans la liste en se basant sur une comparaison. Le code qui compare deux étoiles est différent pour chacun des ordres de tri.

Ces genres de solutions sont utilisés dans les logiciels depuis un demi siècle.
Le concept de délégué du langage C# fournit une prise en charge linguistique de première classe et la sécurité de type autour du concept.

Comme vous le verrez plus loin dans cette série, le code C# que vous écrivez pour des algorithmes comme celui-ci est de type sécurisé. Il s’appuie sur le langage et le compilateur pour s’assurer que les types correspondent à des arguments et des types de retour.

## <a name="language-design-goals-for-delegates"></a>Objectifs de conception de langage pour les délégués

Les concepteurs de langage ont énuméré plusieurs objectifs pour la fonctionnalité qui est finalement devenue celle des délégués.

L’équipe souhaitait une construction de langage commune pouvant être utilisée pour tout algorithme à liaison tardive. Cela permet aux développeurs d’apprendre un concept et d’utiliser ce même concept pour résoudre de nombreux problèmes logiciels différents.

Ensuite, l’équipe souhaitait prendre en charge les appels de méthodes uniques et multicasts (les délégués multicasts sont des délégués qui chaînent plusieurs appels de méthode.
Vous en verrez des exemples [plus loin dans cette série](delegate-class.md)).

L’équipe souhaitait que les délégués prennent en charge la même sécurité de type que celle attendue par les développeurs pour toutes les constructions C#.

Pour finir, l’équipe a reconnu qu’un modèle d’événement était un modèle spécifique où les délégués (ou tout algorithme de liaison tardive) étaient très utiles. L’équipe souhaitait s’assurer que le code pour les délégués pouvait fournir la base pour le modèle d’événement .NET.

Le résultat de tout ce travail est la prise en charge des délégués et des événements en C# et .NET. Les autres articles de cette section traitent des fonctionnalités de langage, de la prise en charge de la bibliothèque, et des idiomes courants utilisés quand vous travaillez avec des délégués.

Vous découvrirez le mot clé `delegate` et le code qu’il génère. Vous découvrirez les fonctionnalités de la classe `System.Delegate` et comment elles sont utilisées. Vous découvrirez comment créer des délégués de type sécurisé et comment créer des méthodes qui peuvent être appelées par l’intermédiaire de délégués. Vous découvrirez aussi comment utiliser des délégués et des événements à l’aide d’expressions lambda. Vous verrez où les délégués deviennent l’un des blocs de construction de LINQ. Vous découvrirez que les délégués sont la base du modèle d’événement .NET, et comment ils diffèrent.

Globalement, vous verrez comment les délégués forment une partie intégrante de la programmation dans .NET et de l’utilisation des API du framework.

Nous pouvons commencer.

[Suivant](delegate-class.md)
