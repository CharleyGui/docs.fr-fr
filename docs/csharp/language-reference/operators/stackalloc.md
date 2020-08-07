---
title: stackalloc expression-référence C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 4f20f3262b77cc2fe16480e53d13960e68d230b5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916678"
---
# <a name="stackalloc-expression-c-reference"></a>stackalloc, expression (référence C#)

Une `stackalloc` expression alloue un bloc de mémoire sur la pile. Un bloc de mémoire alloué dans la pile pendant l’exécution de la méthode est automatiquement supprimé lorsque cette méthode retourne un résultat. Vous ne pouvez pas libérer explicitement la mémoire allouée avec `stackalloc` . Un bloc de mémoire alloué à la pile n’est pas soumis à [garbage collection](../../../standard/garbage-collection/index.md) et ne doit pas être épinglé à une [ `fixed` instruction](../keywords/fixed-statement.md).

Vous pouvez assigner le résultat d’une `stackalloc` expression à une variable de l’un des types suivants :

- À compter de C# 7,2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> , comme le montre l’exemple suivant :

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  Vous n’avez pas l’obligation d’utiliser un contexte [unsafe](../keywords/unsafe.md) lorsque vous affectez un bloc de mémoire alloué dans la pile à une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.

  Lorsque vous travaillez avec ces types, vous pouvez utiliser une expression `stackalloc` les expressions [conditionnelles](conditional-operator.md) ou d’affectation, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  À compter de C# 8,0, vous pouvez utiliser une `stackalloc` expression dans d’autres expressions chaque fois qu’une <xref:System.Span%601> <xref:System.ReadOnlySpan%601> variable ou est autorisée, comme le montre l’exemple suivant :

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Nous vous recommandons d’utiliser les types <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour travailler avec la mémoire allouée dans la pile quand cela est possible.

- Un [type pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md), comme illustré dans l’exemple suivant :

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  Comme le montre l’exemple précédent, vous devez utiliser un contexte `unsafe` lorsque vous travaillez avec des types pointeurs.

  Dans le cas des types pointeur, vous pouvez utiliser une `stackalloc` expression uniquement dans une déclaration de variable locale pour initialiser la variable.

La quantité de mémoire disponible sur la pile est limitée. Si vous allouez une trop grande quantité de mémoire sur la pile, une <xref:System.StackOverflowException> est levée. Pour éviter cela, suivez les règles ci-dessous :

- Limitez la quantité de mémoire allouée à l’aide de `stackalloc` :

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  Étant donné que la quantité de mémoire disponible sur la pile dépend de l’environnement dans lequel le code est exécuté, soyez prudent lorsque vous définissez la valeur limite réelle.

- Évitez d’utiliser des `stackalloc` boucles internes. Allouez le bloc de mémoire en dehors d’une boucle et réutilisez-le à l’intérieur de la boucle.

Le contenu de la mémoire nouvellement allouée n’est pas défini. Vous devez l’initialiser avant l’utilisation. Par exemple, vous pouvez utiliser la <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> méthode qui affecte à tous les éléments la valeur par défaut de type `T` .

À compter de C# 7,3, vous pouvez utiliser la syntaxe de l’initialiseur de tableau pour définir le contenu de la mémoire nouvellement allouée. L’exemple suivant illustre différentes manières de le faire :

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

Dans Expression `stackalloc T[E]` , `T` doit être un [type non managé](../builtin-types/unmanaged-types.md) et `E` doit correspondre à une valeur [int](../builtin-types/integral-numeric-types.md) non négative.

## <a name="security"></a>Sécurité

L’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR). Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [allocation de pile](~/_csharplang/spec/unsafe-code.md#stack-allocation) de la [spécification du langage C#](~/_csharplang/spec/introduction.md) et la fonctionnalité [autoriser dans les `stackalloc` contextes imbriqués](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [Opérateurs associés au pointeur](pointer-related-operators.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à l’étendue](../../../standard/memory-and-spans/index.md)
- [Dos et ne pas de stackalloc](https://vcsjones.dev/2020/02/24/stackalloc/)
