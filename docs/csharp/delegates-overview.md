---
title: Présentation des délégués
description: En savoir plus sur les délégués dans cet article de présentation qui présente les concepts de base et décrit les objectifs de conception de langage pour les délégués.
ms.date: 02/02/2021
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 72086301a6dd0552ab25baf732978802ad62669b
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548342"
---
# <a name="introduction-to-delegates"></a>Présentation des délégués

Les délégués fournissent un mécanisme de *liaison tardive* dans .NET. La liaison tardive signifie que vous créez un algorithme où l’appelant fournit également au moins une méthode qui implémente une partie de l’algorithme.

Par exemple, prenez le tri d’une liste d’étoiles dans une application d’astronomie.
Vous pouvez choisir de trier les étoiles d’après leur distance par rapport à la terre, d’après leur magnitude ou d’après leur luminosité perçue.

Dans tous ces cas-là, la méthode Sort() effectue essentiellement la même chose : elle organise les éléments dans la liste en se basant sur une comparaison. Le code qui compare deux étoiles est différent pour chacun des ordres de tri.

Ces genres de solutions sont utilisés dans les logiciels depuis un demi siècle.
Le concept de délégué du langage C# fournit une prise en charge linguistique de première classe et la sécurité de type autour du concept.

Comme vous le verrez plus loin dans cette série, le code C# que vous écrivez pour les algorithmes comme celui-ci est de type sécurisé et utilise les règles de langage et le compilateur pour s’assurer que les types correspondent pour les arguments et les types de retour.

Des [pointeurs de fonction](~/_csharplang/proposals/csharp-9.0/function-pointers.md) ont été ajoutés à C# 9 pour des scénarios similaires, où vous avez besoin de davantage de contrôle sur la Convention d’appel. Le code associé à un délégué est appelé à l’aide d’une méthode virtuelle ajoutée à un type délégué. À l’aide de pointeurs de fonction, vous pouvez spécifier différentes conventions.

## <a name="language-design-goals-for-delegates"></a>Objectifs de conception de langage pour les délégués

Les concepteurs de langage ont énuméré plusieurs objectifs pour la fonctionnalité qui est finalement devenue celle des délégués.

L’équipe souhaitait une construction de langage commune pouvant être utilisée pour tout algorithme à liaison tardive. Les délégués permettent aux développeurs d’apprendre un concept et d’utiliser ce même concept dans de nombreux problèmes logiciels différents.

Ensuite, l’équipe souhaitait prendre en charge les appels de méthodes uniques et multicasts (les délégués multicasts sont des délégués qui chaînent plusieurs appels de méthode.
Vous en verrez des exemples [plus loin dans cette série](delegate-class.md)).

L’équipe souhaitait que les délégués prennent en charge la même sécurité de type que celle attendue par les développeurs pour toutes les constructions C#.

Enfin, l’équipe a reconnu qu’un modèle d’événement est un modèle spécifique où les délégués, ou tout algorithme de liaison tardive, sont très utiles. L’équipe souhaitait s’assurer que le code des délégués pouvait fournir la base du modèle d’événement .NET.

Le résultat de tout ce travail est la prise en charge des délégués et des événements en C# et .NET. Les autres Articles de cette section traitent des fonctionnalités de langage, de la prise en charge de la bibliothèque et des idiomes courants utilisés lorsque vous travaillez avec des délégués.

Vous découvrirez le mot clé `delegate` et le code qu’il génère. Vous découvrirez les fonctionnalités de la classe `System.Delegate` et comment elles sont utilisées. Vous découvrirez comment créer des délégués de type sécurisé et comment créer des méthodes qui peuvent être appelées par l’intermédiaire de délégués. Vous découvrirez aussi comment utiliser des délégués et des événements à l’aide d’expressions lambda. Vous verrez où les délégués deviennent l’un des blocs de construction de LINQ. Vous apprendrez comment les délégués constituent la base du modèle d’événement .NET et comment ils sont différents.

C’est parti !

[Next](delegate-class.md)
