---
title: stackalloc, mot clé - Référence C#
ms.custom: seodec18
ms.date: 04/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: c72daa58d2fceb05d9cc9c388a9d2e5dbe062796
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422440"
---
# <a name="stackalloc-c-reference"></a>stackalloc (référence C#)

Le mot clé `stackalloc` sert à allouer un bloc de mémoire sur la pile.

```csharp
Span<int> block = stackalloc int[100];
```

Le fait d’affecter le bloc alloué à un <xref:System.Span%601?displayName=nameWithType> au lieu d’un `int*` permet d’effectuer des allocations de pile dans un bloc safe. Le contexte `unsafe` n’est pas obligatoire.

## <a name="remarks"></a>Remarques

Le mot clé est valide uniquement dans les initialiseurs de variable locale. Le code suivant génère des erreurs de compilation.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

Dans C# 7.3 et les versions ultérieures, vous pouvez utiliser la syntaxe d’initialiseur de tableau pour les tableaux `stackalloc`. Toutes les déclarations suivantes déclarent un tableau de trois éléments ayant pour valeurs les entiers `1`, `2` et `3`. La deuxième initialisation attribue la mémoire à un <xref:System.ReadOnlySpan%601>, indiquant que celle-ci n’est pas modifiable.

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

Quand des types pointeur sont impliqués, `stackalloc` exige un contexte [unsafe](unsafe.md). Pour plus d’informations, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).

`stackalloc` est similaire à [_alloca](/cpp/c-runtime-library/reference/alloca) dans la bibliothèque Runtime C.

## <a name="examples"></a>Exemples

L’exemple suivant calcule et affiche les 20 premiers nombres de la suite de Fibonacci. Chaque nombre est la somme des deux nombres précédents. Dans le code, un bloc de mémoire de taille suffisante pour contenir 20 éléments de type `int` est alloué sur la pile, et non sur le tas. L’adresse du bloc est stockée dans le `Span` `fib`. Cette mémoire n’est pas soumise au garbage collection et n’est donc pas tenue d’être épinglée (en utilisant [fixed](fixed-statement.md)). La durée de vie du bloc de mémoire est limitée à la durée de vie de la méthode qui le définit. Vous ne pouvez pas libérer la mémoire avant le retour de la méthode.

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

L’exemple suivant initialise un tableau `stackalloc` d’entiers sur un masque de bits où un bit est défini dans chaque élément. Cela illustre la nouvelle syntaxe d’initialiseur disponible à partir de C# 7.3 :

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Sécurité

Utilisez <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> dans la mesure du possible, car le code unsafe est moins sécurisé que son équivalent safe. Même avec des pointeurs, `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR). Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.

## <a name="c-language-specification"></a>spécification du langage C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md)
