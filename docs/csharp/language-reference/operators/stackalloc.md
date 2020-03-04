---
title: Opérateur stackalloc - Référence C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: b2188bc94db42ab6d581c339f046ed81eb42d297
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238999"
---
# <a name="stackalloc-operator-c-reference"></a>Opérateur stackalloc (Référence C#)

L’opérateur `stackalloc` alloue un bloc de mémoire dans la pile. Un bloc de mémoire alloué dans la pile pendant l’exécution de la méthode est automatiquement supprimé lorsque cette méthode retourne un résultat. Vous ne pouvez pas libérer explicitement la mémoire allouée avec l’opérateur `stackalloc`. Un bloc de mémoire alloué à la pile n’est pas soumis à [garbage collection](../../../standard/garbage-collection/index.md) et n’a pas besoin d’être épinglé avec une [instruction`fixed`](../keywords/fixed-statement.md).

Vous pouvez attribuer le résultat de l’opérateur `stackalloc` à une variable d’un des types suivants :

- À partir C# de 7,2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc span](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Vous n’avez pas l’obligation d’utiliser un contexte [unsafe](../keywords/unsafe.md) lorsque vous affectez un bloc de mémoire alloué dans la pile à une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.

  Lorsque vous travaillez avec ces types, vous pouvez utiliser une expression `stackalloc` les expressions [conditionnelles](conditional-operator.md) ou d’affectation, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc expression](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  À partir C# de 8,0, vous pouvez utiliser une expression `stackalloc` dans d’autres expressions chaque fois qu’une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> est autorisée, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc in nested expressions](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Nous vous recommandons d’utiliser les types <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour travailler avec la mémoire allouée dans la pile quand cela est possible.

- Un [type pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md), comme illustré dans l’exemple suivant :

  [!code-csharp[stackalloc pointer](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Comme le montre l’exemple précédent, vous devez utiliser un contexte `unsafe` lorsque vous travaillez avec des types pointeurs.

  Dans le cas des types pointeur, vous pouvez utiliser une expression `stackalloc` uniquement dans une déclaration de variable locale pour initialiser la variable.

Le contenu de la mémoire nouvellement allouée n’est pas défini. À partir C# de 7,3, vous pouvez utiliser la syntaxe de l’initialiseur de tableau pour définir le contenu de la mémoire nouvellement allouée. L’exemple suivant illustre différentes manières de le faire :

[!code-csharp[stackalloc initialization](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

Dans expression `stackalloc T[E]`, `T` doit être un [type non managé](../builtin-types/unmanaged-types.md) et `E` doit être une expression de type [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Sécurité

L’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR). Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [allocation de pile](~/_csharplang/spec/unsafe-code.md#stack-allocation) de la [ C# spécification de langage](~/_csharplang/spec/introduction.md) et la fonctionnalité [autoriser `stackalloc` dans les contextes imbriqués](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs associés au pointeur](pointer-related-operators.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à l’étendue](../../../standard/memory-and-spans/index.md)
