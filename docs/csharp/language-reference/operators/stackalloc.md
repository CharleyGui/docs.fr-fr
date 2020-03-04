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
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="4b3dd-102">Opérateur stackalloc (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="4b3dd-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="4b3dd-103">L’opérateur `stackalloc` alloue un bloc de mémoire dans la pile.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="4b3dd-104">Un bloc de mémoire alloué dans la pile pendant l’exécution de la méthode est automatiquement supprimé lorsque cette méthode retourne un résultat.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="4b3dd-105">Vous ne pouvez pas libérer explicitement la mémoire allouée avec l’opérateur `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="4b3dd-106">Un bloc de mémoire alloué à la pile n’est pas soumis à [garbage collection](../../../standard/garbage-collection/index.md) et n’a pas besoin d’être épinglé avec une [instruction`fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4b3dd-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="4b3dd-107">Vous pouvez attribuer le résultat de l’opérateur `stackalloc` à une variable d’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="4b3dd-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="4b3dd-108">À partir C# de 7,2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4b3dd-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="4b3dd-109">Vous n’avez pas l’obligation d’utiliser un contexte [unsafe](../keywords/unsafe.md) lorsque vous affectez un bloc de mémoire alloué dans la pile à une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="4b3dd-110">Lorsque vous travaillez avec ces types, vous pouvez utiliser une expression `stackalloc` les expressions [conditionnelles](conditional-operator.md) ou d’affectation, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4b3dd-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="4b3dd-111">À partir C# de 8,0, vous pouvez utiliser une expression `stackalloc` dans d’autres expressions chaque fois qu’une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> est autorisée, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4b3dd-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="4b3dd-112">Nous vous recommandons d’utiliser les types <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour travailler avec la mémoire allouée dans la pile quand cela est possible.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="4b3dd-113">Un [type pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md), comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4b3dd-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="4b3dd-114">Comme le montre l’exemple précédent, vous devez utiliser un contexte `unsafe` lorsque vous travaillez avec des types pointeurs.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="4b3dd-115">Dans le cas des types pointeur, vous pouvez utiliser une expression `stackalloc` uniquement dans une déclaration de variable locale pour initialiser la variable.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="4b3dd-116">Le contenu de la mémoire nouvellement allouée n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="4b3dd-117">À partir C# de 7,3, vous pouvez utiliser la syntaxe de l’initialiseur de tableau pour définir le contenu de la mémoire nouvellement allouée.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="4b3dd-118">L’exemple suivant illustre différentes manières de le faire :</span><span class="sxs-lookup"><span data-stu-id="4b3dd-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/snippets/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="4b3dd-119">Dans expression `stackalloc T[E]`, `T` doit être un [type non managé](../builtin-types/unmanaged-types.md) et `E` doit être une expression de type [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="4b3dd-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="4b3dd-120">Sécurité</span><span class="sxs-lookup"><span data-stu-id="4b3dd-120">Security</span></span>

<span data-ttu-id="4b3dd-121">L’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4b3dd-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="4b3dd-122">Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.</span><span class="sxs-lookup"><span data-stu-id="4b3dd-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4b3dd-123">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4b3dd-123">C# language specification</span></span>

<span data-ttu-id="4b3dd-124">Pour plus d’informations, consultez la section [allocation de pile](~/_csharplang/spec/unsafe-code.md#stack-allocation) de la [ C# spécification de langage](~/_csharplang/spec/introduction.md) et la fonctionnalité [autoriser `stackalloc` dans les contextes imbriqués](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="4b3dd-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b3dd-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b3dd-125">See also</span></span>

- [<span data-ttu-id="4b3dd-126">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="4b3dd-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4b3dd-127">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="4b3dd-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="4b3dd-128">Opérateurs associés au pointeur</span><span class="sxs-lookup"><span data-stu-id="4b3dd-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="4b3dd-129">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="4b3dd-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="4b3dd-130">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="4b3dd-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
