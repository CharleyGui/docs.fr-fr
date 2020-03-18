---
title: Opérateur stackalloc - Référence C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846248"
---
# <a name="stackalloc-operator-c-reference"></a>Opérateur stackalloc (Référence C#)

L’opérateur `stackalloc` alloue un bloc de mémoire dans la pile. Un bloc de mémoire alloué dans la pile pendant l’exécution de la méthode est automatiquement supprimé lorsque cette méthode retourne un résultat. Vous ne pouvez pas libérer explicitement la mémoire allouée avec l’opérateur `stackalloc`. Un bloc de mémoire de pile attribué n’est pas sujet à [la collecte des ordures](../../../standard/garbage-collection/index.md) et n’a pas besoin d’être épinglé avec une [ `fixed` déclaration](../keywords/fixed-statement.md).

Vous pouvez attribuer le résultat de l’opérateur `stackalloc` à une variable d’un des types suivants :

- Commençant par C 7.2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  Vous n’avez pas l’obligation d’utiliser un contexte [unsafe](../keywords/unsafe.md) lorsque vous affectez un bloc de mémoire alloué dans la pile à une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.

  Lorsque vous travaillez avec ces types, vous pouvez utiliser une expression `stackalloc` les expressions [conditionnelles](conditional-operator.md) ou d’affectation, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  En commençant par le C 8.0, vous pouvez utiliser une `stackalloc` expression à l’intérieur d’autres expressions chaque fois qu’une ou <xref:System.Span%601> <xref:System.ReadOnlySpan%601> une variable est autorisée, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Nous vous recommandons d’utiliser les types <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour travailler avec la mémoire allouée dans la pile quand cela est possible.

- Un [type pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md), comme illustré dans l’exemple suivant :

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  Comme le montre l’exemple précédent, vous devez utiliser un contexte `unsafe` lorsque vous travaillez avec des types pointeurs.

  Dans le cas des types de `stackalloc` pointeurs, vous ne pouvez utiliser une expression que dans une déclaration variable locale pour initialiser la variable.

Le contenu de la mémoire nouvellement allouée n’est pas défini. En commençant par le C 7.3, vous pouvez utiliser la syntaxe initialise de tableau pour définir le contenu de la mémoire nouvellement allouée. L’exemple suivant illustre différentes manières de le faire :

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

Dans `stackalloc T[E]`l’expression, `T` doit être un `E` type non gestion [et](../builtin-types/unmanaged-types.md) doit être une expression de type [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Sécurité

L’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR). Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.

## <a name="c-language-specification"></a>spécification du langage C#

Pour de plus amples renseignements, consultez la section [d’attribution](~/_csharplang/spec/unsafe-code.md#stack-allocation) de la pile des [spécifications linguistiques Cmd](~/_csharplang/spec/introduction.md) et la note de proposition [du permis `stackalloc` dans les contextes imbriqués.](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Opérateurs associés au pointeur](pointer-related-operators.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à la travée](../../../standard/memory-and-spans/index.md)
