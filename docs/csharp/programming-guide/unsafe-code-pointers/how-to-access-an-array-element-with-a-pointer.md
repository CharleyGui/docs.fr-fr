---
title: Guide pratique pour accéder à un élément de tableau à l’aide d’un pointeur - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: b1538068f3ba37a7637e7dc3913e9511d4380daf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635186"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Guide pratique pour accéder à un élément de tableau à l’aide d’un pointeur (guide de programmation C#)

Dans un contexte unsafe, vous pouvez accéder à un élément en mémoire en utilisant l’accès à un élément de pointeur, comme illustré dans l’exemple suivant :

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

L’expression entre crochets doit être implicitement convertible en `int`, `uint`, `long` ou `ulong`. L’opération `p[e]` équivaut à `*(p+e)`. Comme C et C++, l’accès à un élément de pointeur ne recherche pas les erreurs de dépassement des limites.

## <a name="example"></a>Exemple

Dans cet exemple, 123 emplacements de mémoire sont alloués à un tableau de caractères, `charPointer`. Le tableau est utilisé pour afficher les lettres minuscules et les lettres majuscules dans deux boucles [for](../../../csharp/language-reference/keywords/for.md).

Remarquez que l’expression `charPointer[i]` équivaut à l’expression `*(charPointer + i)`, et vous pouvez obtenir le même résultat en utilisant l’une ou l’autre expression.

 [!code-csharp[csProgGuidePointers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#11)]

 [!code-csharp[csProgGuidePointers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#12)]

**Lettres majuscules :**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Lettres minuscules :**  
**abcdefghijklmnopqrstuvwxyz**  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Types](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
