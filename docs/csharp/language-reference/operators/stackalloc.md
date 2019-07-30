---
title: Opérateur stackalloc - Référence C#
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: f211acaa8c47ab42a1f7f06cff6c35570cd22b75
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433826"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="79342-102">Opérateur stackalloc (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="79342-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="79342-103">L’opérateur `stackalloc` alloue un bloc de mémoire dans la pile.</span><span class="sxs-lookup"><span data-stu-id="79342-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="79342-104">Un bloc de mémoire alloué dans la pile pendant l’exécution de la méthode est automatiquement supprimé lorsque cette méthode retourne un résultat.</span><span class="sxs-lookup"><span data-stu-id="79342-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="79342-105">Vous ne pouvez pas libérer explicitement la mémoire allouée avec l’opérateur `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="79342-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="79342-106">Un bloc de mémoire alloué dans la pile n’est pas soumis au [nettoyage de la mémoire](../../../standard/garbage-collection/index.md) et ne doit pas être épinglé avec [l’instruction `fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="79342-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="79342-107">Dans l’expression `stackalloc T[E]`, `T` doit être un [type non managé](../builtin-types/unmanaged-types.md) et `E` doit être une expression de type `int`.</span><span class="sxs-lookup"><span data-stu-id="79342-107">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type `int`.</span></span>

<span data-ttu-id="79342-108">Vous pouvez attribuer le résultat de l’opérateur `stackalloc` à une variable d’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="79342-108">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="79342-109">À compter de C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="79342-109">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="79342-110">Vous n’avez pas l’obligation d’utiliser un contexte [unsafe](../keywords/unsafe.md) lorsque vous affectez un bloc de mémoire alloué dans la pile à une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="79342-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="79342-111">Lorsque vous travaillez avec ces types, vous pouvez utiliser une expression `stackalloc` les expressions [conditionnelles](conditional-operator.md) ou d’affectation, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="79342-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > <span data-ttu-id="79342-112">Nous vous recommandons d’utiliser les types <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour travailler avec la mémoire allouée dans la pile quand cela est possible.</span><span class="sxs-lookup"><span data-stu-id="79342-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="79342-113">Un [type pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md), comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="79342-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="79342-114">Comme le montre l’exemple précédent, vous devez utiliser un contexte `unsafe` lorsque vous travaillez avec des types pointeurs.</span><span class="sxs-lookup"><span data-stu-id="79342-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

<span data-ttu-id="79342-115">Le contenu de la mémoire nouvellement allouée n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="79342-115">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="79342-116">À compter de C# 7.3, vous pouvez utiliser la syntaxe d’initialiseur de tableau pour définir le contenu de la mémoire nouvellement allouée.</span><span class="sxs-lookup"><span data-stu-id="79342-116">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="79342-117">L’exemple suivant illustre différentes manières de le faire :</span><span class="sxs-lookup"><span data-stu-id="79342-117">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="79342-118">Sécurité</span><span class="sxs-lookup"><span data-stu-id="79342-118">Security</span></span>

<span data-ttu-id="79342-119">L’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="79342-119">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="79342-120">Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.</span><span class="sxs-lookup"><span data-stu-id="79342-120">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="79342-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="79342-121">C# language specification</span></span>

<span data-ttu-id="79342-122">Pour plus d’informations, voir la section [Allocation de piles](~/_csharplang/spec/unsafe-code.md#stack-allocation) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="79342-122">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79342-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79342-123">See also</span></span>

- [<span data-ttu-id="79342-124">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="79342-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="79342-125">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="79342-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="79342-126">Opérateurs associés au pointeur</span><span class="sxs-lookup"><span data-stu-id="79342-126">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="79342-127">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="79342-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="79342-128">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="79342-128">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
