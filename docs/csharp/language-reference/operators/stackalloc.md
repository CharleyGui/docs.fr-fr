---
title: Opérateur stackalloc - Référence C#
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9ef5f98f2b4973c5873417ecc9a71c187e7299b9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182417"
---
# <a name="stackalloc-operator-c-reference"></a>Opérateur stackalloc (Référence C#)

L’opérateur `stackalloc` alloue un bloc de mémoire dans la pile. Un bloc de mémoire alloué dans la pile pendant l’exécution de la méthode est automatiquement supprimé lorsque cette méthode retourne un résultat. Vous ne pouvez pas libérer explicitement la mémoire allouée avec l’opérateur `stackalloc`. Un bloc de mémoire alloué dans la pile n’est pas soumis au [nettoyage de la mémoire](../../../standard/garbage-collection/index.md) et ne doit pas être épinglé avec [l’instruction `fixed`](../keywords/fixed-statement.md).

Dans l’expression `stackalloc T[E]`, `T` doit être un [type non managé](../builtin-types/unmanaged-types.md) et `E` doit être une expression de type `int`.

Vous pouvez attribuer le résultat de l’opérateur `stackalloc` à une variable d’un des types suivants :

- À compter de C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, comme illustré dans l’exemple suivant :

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Vous n’avez pas l’obligation d’utiliser un contexte [unsafe](../keywords/unsafe.md) lorsque vous affectez un bloc de mémoire alloué dans la pile à une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.

  Lorsque vous travaillez avec ces types, vous pouvez utiliser une expression `stackalloc` les expressions [conditionnelles](conditional-operator.md) ou d’affectation, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  À partir C# de 8,0, vous pouvez utiliser `stackalloc` une expression dans d’autres expressions <xref:System.Span%601> chaque <xref:System.ReadOnlySpan%601> fois qu’une variable ou est autorisée, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Nous vous recommandons d’utiliser les types <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour travailler avec la mémoire allouée dans la pile quand cela est possible.

- Un [type pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md), comme illustré dans l’exemple suivant :

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Comme le montre l’exemple précédent, vous devez utiliser un contexte `unsafe` lorsque vous travaillez avec des types pointeurs.

  Dans le cas des types pointeur, vous pouvez utiliser une `stackalloc` expression uniquement dans une déclaration de variable locale pour initialiser la variable.

Le contenu de la mémoire nouvellement allouée n’est pas défini. À compter de C# 7.3, vous pouvez utiliser la syntaxe d’initialiseur de tableau pour définir le contenu de la mémoire nouvellement allouée. L’exemple suivant illustre différentes manières de le faire :

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Sécurité

L’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR). Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Allocation de piles](~/_csharplang/spec/unsafe-code.md#stack-allocation) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs associés au pointeur](pointer-related-operators.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à l’étendue](../../../standard/memory-and-spans/index.md)
