---
title: Conversions de pointeur - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 663599ab9ba6755388603d5d3cc5a9ee522f3c9f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345651"
---
# <a name="pointer-conversions-c-programming-guide"></a>Conversions de pointeur (Guide de programmation C#)
Le tableau suivant présente les conversions de pointeur implicites prédéfinies. Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.  
  
## <a name="implicit-pointer-conversions"></a>Conversions de pointeur implicites  
  
|À partir de|Vers|  
|----------|--------|  
|Tout type pointeur|void*|  
|null|Tout type pointeur|  
  
 La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast. Le tableau suivant liste ces conversions.  
  
## <a name="explicit-pointer-conversions"></a>Conversions de pointeur explicites  
  
|À partir de|Vers|  
|----------|--------|  
|Tout type pointeur|Tout autre type pointeur|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Tout type pointeur|  
|Tout type pointeur|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`. Notez que le pointeur pointe vers l’octet traité le plus faible de la variable. Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Types de pointeur](pointer-types.md)
- [Types référence](../../language-reference/keywords/reference-types.md)
- [Types valeur](../../language-reference/keywords/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed, instruction](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
