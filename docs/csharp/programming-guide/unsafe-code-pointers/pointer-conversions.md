---
title: Conversions de pointeur - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745365"
---
# <a name="pointer-conversions-c-programming-guide"></a>Conversions de pointeur (Guide de programmation C#)
Le tableau suivant présente les conversions de pointeur implicites prédéfinies. Les conversions implicites peuvent se produire dans de nombreuses situations, comme les appels de méthode et les instructions d’assignation.  
  
## <a name="implicit-pointer-conversions"></a>Conversions de pointeur implicites  
  
|À partir|À|  
|----------|--------|  
|Tout type pointeur|void*|  
|null|Tout type pointeur|  
  
 La conversion de pointeur explicite permet d’effectuer des conversions, pour lesquelles il n’existe pas de conversion implicite, à l’aide d’une expression de cast. Le tableau suivant liste ces conversions.  
  
## <a name="explicit-pointer-conversions"></a>Conversions de pointeur explicites  
  
|À partir|À|  
|----------|--------|  
|Tout type pointeur|Tout autre type pointeur|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Tout type pointeur|  
|Tout type pointeur|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## <a name="example"></a> Exemple  
 Dans l’exemple suivant, un pointeur vers `int` est converti en pointeur vers `byte`. Notez que le pointeur pointe vers l’octet traité le plus faible de la variable. Quand vous incrémentez successivement le résultat, jusqu’à la taille de `int` (4 octets), vous pouvez afficher les octets restants de la variable.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Types de pointeur](pointer-types.md)
- [Types référence](../../language-reference/keywords/reference-types.md)
- [Types de valeur](../../language-reference/builtin-types/value-types.md)
- [Dangereux](../../language-reference/keywords/unsafe.md)
- [fixed, instruction](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
