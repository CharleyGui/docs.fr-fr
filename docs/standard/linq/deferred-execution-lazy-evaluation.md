---
title: Exécution différée et évaluation différée-LINQ to XML
description: Découvrez les avantages et les exigences de l’exécution différée et comment l’implémenter à l’aide d’opérations de requête et d’axe.
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 21b1c7b7d54e7f787919f1e1601fc36bc8c1caff
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552385"
---
# <a name="deferred-execution-and-lazy-evaluation-linq-to-xml"></a>Exécution différée et évaluation différée (LINQ to XML)

Les opérations de requête et d'axe sont souvent implémentées pour utiliser l'exécution différée. Cet article explique les conditions requises et les avantages de l’exécution différée, ainsi que certaines considérations relatives à l’implémentation.

## <a name="deferred-execution"></a>Exécution différée

Le terme "exécution différée" signifie que l’évaluation d’une expression est retardée jusqu’à ce que sa valeur *réalisée* soit réellement nécessaire. L'exécution différée peut améliorer sensiblement les performances lorsque vous devez manipuler de grandes collectes de données, en particulier dans les programmes qui contiennent une série de manipulations ou de requêtes chaînées. Dans le meilleur cas, l'exécution différée autorise une seule itération dans la collection source.

Les technologies LINQ utilisent beaucoup l'exécution différée dans les membres des classes <xref:System.Linq?displayProperty=nameWithType> principales et dans les méthodes d'extension dans les différents espaces de noms LINQ, tels que <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.

L’exécution différée est prise en charge directement dans le langage C# par le mot clé [yield (référence C#)](../../csharp/language-reference/keywords/yield.md) (sous la forme de l' `yield-return` instruction) lorsqu’elle est utilisée dans un bloc itérateur. Un tel itérateur doit renvoyer une collection de type <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> (ou un type dérivé).

## <a name="eager-vs-lazy-evaluation"></a>Évaluation des versions hâtif et tardive

Lorsque vous écrivez une méthode qui implémente l'exécution différée, vous devez également décider s'il faut implémenter la méthode à l'aide de l'évaluation différée ou de l'évaluation stricte.

- Avec l’*évaluation différée*, un seul élément de la collection source est traité pendant chaque appel à l’itérateur. Il s'agit du mode d'implémentation par défaut des itérateurs.
- Avec l’*évaluation stricte*, le premier appel à l’itérateur entraîne le traitement de l’ensemble de la collection. Une copie temporaire de la collection source peut également être nécessaire. Par exemple, la méthode <xref:System.Linq.Enumerable.OrderBy%2A> doit trier l'ensemble de la collection avant de renvoyer le premier élément.

L'évaluation différée procure en général de meilleures performances car elle répartit le traitement de surcharge de manière égale durant l'évaluation de la collection et limite l'utilisation des données temporaires. Bien entendu, pour certaines opérations il est impossible d'éviter la matérialisation de résultats intermédiaires.

Pour obtenir un exemple de programmation de l’exécution différée en C# et Visual Basic, consultez [exemple d’exécution différée](deferred-execution-example.md) .

## <a name="see-also"></a>Voir aussi

- [Didacticiel : chaîner des requêtes en C #](chain-queries-example.md)
- [Concepts et terminologie (transformation fonctionnelle)](concepts-terminology-functional-transformation.md)
- [Opérations d’agrégation (C#)](../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [Opérations d’agrégation (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
- [yield (Référence C#)](../../csharp/language-reference/keywords/yield.md)
