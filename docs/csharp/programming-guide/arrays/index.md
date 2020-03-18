---
title: Tableaux - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715055"
---
# <a name="arrays-c-programming-guide"></a>Tableaux (guide de programmation C#)

Vous pouvez stocker plusieurs variables du même type dans une structure de données de type tableau. Vous déclarez un tableau en spécifiant le type de ses éléments. Si vous voulez que le tableau stocke `object` des éléments de n’importe quel type, vous pouvez spécifier comme son type. Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>.

```csharp
type[] arrayName;
```

## <a name="example"></a> Exemple

L’exemple suivant crée des tableaux unidimensionnels, multidimensionnels et en escalier :

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Aperçu du tableau

Un tableau possède les propriétés suivantes :

- Un tableau peut être [unidimensionnel](single-dimensional-arrays.md), [multidimensionnel](multidimensional-arrays.md) ou [en escalier](jagged-arrays.md).
- Le nombre de dimensions et la longueur de chaque dimension sont établis lors de la création de l’instance de tableau. Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l’instance.
- Les valeurs par défaut des éléments de tableau numériques sont définies sur zéro et les éléments de référence sont définis sur Null.
- Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.
- Les tableaux sont indexés sur zéro : un tableau avec `n` éléments est indexée de `0` à `n-1`.
- Les éléments de tableau peuvent être de n’importe quel type, y compris un type tableau.
- Les types tableau sont des [types référence](../../language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>. Étant donné que ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l’itération [foreach](../../language-reference/keywords/foreach-in.md) sur tous les tableaux en C#.

## <a name="related-sections"></a>Sections connexes

- [Tableaux comme objets](arrays-as-objects.md)
- [Utiliser foreach avec des tableaux](using-foreach-with-arrays.md)
- [Passage de tableaux en tant qu’arguments](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Collections](../concepts/collections.md)
