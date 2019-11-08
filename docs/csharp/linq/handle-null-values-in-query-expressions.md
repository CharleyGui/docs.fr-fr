---
title: Gérer des valeurs Null dans des expressions de requête (LINQ en C#)
description: Découvrez comment gérer des valeurs Null dans des expressions de requête LINQ en C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736860"
---
# <a name="handle-null-values-in-query-expressions"></a>Gérer des valeurs Null dans des expressions de requête

Cet exemple montre comment gérer d’éventuelles valeurs Null dans des collections sources. Une collection d’objets telle qu’un <xref:System.Collections.Generic.IEnumerable%601> peut contenir des éléments dont la valeur est [null](../language-reference/keywords/null.md). Si une collection source est null ou contient un élément dont la valeur est null et que votre requête ne gère pas les valeurs null, une <xref:System.NullReferenceException> est levée quand vous exécutez la requête.

## <a name="example"></a>Exemple

Vous pouvez écrire du code en prévention pour éviter une exception de référence Null, comme indiqué dans l’exemple suivant :

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

Dans l’exemple précédent, la clause `where` exclut tous les éléments Null de la séquence de catégories. Cette technique est indépendante de la vérification de valeur Null de la clause join. Dans cet exemple, l’expression conditionnelle avec une valeur Null fonctionne, car `Products.CategoryID` est de type `int?`, qui est le raccourci de `Nullable<int>`.

## <a name="example"></a>Exemple

Dans une clause join, si seulement l’une des clés de comparaison est un type valeur Nullable, vous pouvez caster l’autre clé en type Nullable dans l’expression de requête. Dans l’exemple suivant, supposons que `EmployeeID` soit une colonne qui contienne des valeurs de type `int?` :

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Nullable%601>
- [LINQ (Language Integrated Query)](index.md)
- [Types valeur Nullable](../language-reference/builtin-types/nullable-value-types.md)
