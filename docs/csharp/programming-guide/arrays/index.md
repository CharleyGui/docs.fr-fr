---
title: Tableaux - Guide de programmation C#
description: Stocker plusieurs variables du même type dans une structure de données de tableau en C#. Déclarez un tableau en spécifiant un type ou spécifiez un objet pour stocker tout type.
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794766"
---
# <a name="arrays-c-programming-guide"></a>Tableaux (guide de programmation C#)

Vous pouvez stocker plusieurs variables du même type dans une structure de données de type tableau. Vous déclarez un tableau en spécifiant le type de ses éléments. Si vous souhaitez que le tableau stocke des éléments de n’importe quel type, vous pouvez spécifier `object` en tant que type. Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>.

```csharp
type[] arrayName;
```

## <a name="example"></a>Exemple

L’exemple suivant crée des tableaux unidimensionnels, multidimensionnels et en escalier :

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Présentation du tableau

Un tableau possède les propriétés suivantes :

- Un tableau peut être [unidimensionnel](single-dimensional-arrays.md) [, multidimensionnel ou en](multidimensional-arrays.md) [escalier](jagged-arrays.md).
- Le nombre de dimensions et la longueur de chaque dimension sont établis lors de la création de l’instance de tableau. Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l’instance.
- Les valeurs par défaut des éléments de tableau numériques sont définies sur zéro et les éléments de référence sont définis sur Null.
- Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.
- Les tableaux sont indexés sur zéro : un tableau avec `n` éléments est indexée de `0` à `n-1`.
- Les éléments de tableau peuvent être de n’importe quel type, y compris un type tableau.
- Les types tableau sont des [types référence](../../language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>. Étant donné que ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l’itération [foreach](../../language-reference/keywords/foreach-in.md) sur tous les tableaux en C#.

### <a name="arrays-as-objects"></a>Tableaux comme objets

En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++. <xref:System.Array> est le type de base abstrait de tous les types de tableau. Vous pouvez utiliser les propriétés et d’autres membres de classe qui <xref:System.Array> possèdent. Par exemple, l’utilisation de la <xref:System.Array.Length%2A> propriété pour récupérer la longueur d’un tableau. Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux. L’exemple suivant utilise la <xref:System.Array.Rank%2A> propriété pour afficher le nombre de dimensions d’un tableau.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Voir aussi

- [Comment utiliser des tableaux unidimensionnels](single-dimensional-arrays.md)
- [Comment utiliser des tableaux multidimensionnels](multidimensional-arrays.md)
- [Comment utiliser des tableaux en escalier](jagged-arrays.md)
- [Utilisation de foreach avec des tableaux](using-foreach-with-arrays.md)
- [Passage de tableaux en tant qu’arguments](passing-arrays-as-arguments.md)
- [Tableaux implicitement typés](implicitly-typed-arrays.md)
- [Guide de programmation C#](../index.md)
- [Regroupements](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
