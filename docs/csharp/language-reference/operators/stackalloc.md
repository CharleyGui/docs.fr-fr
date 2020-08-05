---
title: stackalloc expression-référence C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 32ac85f678912cb7e5f506244265b1bf57d0b4aa
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555604"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="948bd-102">stackalloc, expression (référence C#)</span><span class="sxs-lookup"><span data-stu-id="948bd-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="948bd-103">Une `stackalloc` expression alloue un bloc de mémoire sur la pile.</span><span class="sxs-lookup"><span data-stu-id="948bd-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="948bd-104">Un bloc de mémoire alloué dans la pile pendant l’exécution de la méthode est automatiquement supprimé lorsque cette méthode retourne un résultat.</span><span class="sxs-lookup"><span data-stu-id="948bd-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="948bd-105">Vous ne pouvez pas libérer explicitement la mémoire allouée avec `stackalloc` .</span><span class="sxs-lookup"><span data-stu-id="948bd-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="948bd-106">Un bloc de mémoire alloué à la pile n’est pas soumis à [garbage collection](../../../standard/garbage-collection/index.md) et ne doit pas être épinglé à une [ `fixed` instruction](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="948bd-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="948bd-107">Vous pouvez assigner le résultat d’une `stackalloc` expression à une variable de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="948bd-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="948bd-108">À compter de C# 7,2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> , comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="948bd-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="948bd-109">Vous n’avez pas l’obligation d’utiliser un contexte [unsafe](../keywords/unsafe.md) lorsque vous affectez un bloc de mémoire alloué dans la pile à une variable <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="948bd-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="948bd-110">Lorsque vous travaillez avec ces types, vous pouvez utiliser une expression `stackalloc` les expressions [conditionnelles](conditional-operator.md) ou d’affectation, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="948bd-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="948bd-111">À compter de C# 8,0, vous pouvez utiliser une `stackalloc` expression dans d’autres expressions chaque fois qu’une <xref:System.Span%601> <xref:System.ReadOnlySpan%601> variable ou est autorisée, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="948bd-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="948bd-112">Nous vous recommandons d’utiliser les types <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour travailler avec la mémoire allouée dans la pile quand cela est possible.</span><span class="sxs-lookup"><span data-stu-id="948bd-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="948bd-113">Un [type pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md), comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="948bd-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="948bd-114">Comme le montre l’exemple précédent, vous devez utiliser un contexte `unsafe` lorsque vous travaillez avec des types pointeurs.</span><span class="sxs-lookup"><span data-stu-id="948bd-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="948bd-115">Dans le cas des types pointeur, vous pouvez utiliser une `stackalloc` expression uniquement dans une déclaration de variable locale pour initialiser la variable.</span><span class="sxs-lookup"><span data-stu-id="948bd-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="948bd-116">La quantité de mémoire disponible sur la pile est limitée.</span><span class="sxs-lookup"><span data-stu-id="948bd-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="948bd-117">Si vous allouez une trop grande quantité de mémoire sur la pile, une <xref:System.StackOverflowException> est levée.</span><span class="sxs-lookup"><span data-stu-id="948bd-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="948bd-118">Pour éviter cela, suivez les règles ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="948bd-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="948bd-119">Limitez la quantité de mémoire allouée à l’aide de `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="948bd-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="948bd-120">Étant donné que la quantité de mémoire disponible sur la pile dépend de l’environnement dans lequel le code est exécuté, soyez prudent lorsque vous définissez la valeur limite réelle.</span><span class="sxs-lookup"><span data-stu-id="948bd-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="948bd-121">Évitez d’utiliser des `stackalloc` boucles internes.</span><span class="sxs-lookup"><span data-stu-id="948bd-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="948bd-122">Allouez le bloc de mémoire en dehors d’une boucle et réutilisez-le à l’intérieur de la boucle.</span><span class="sxs-lookup"><span data-stu-id="948bd-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="948bd-123">Le contenu de la mémoire nouvellement allouée n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="948bd-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="948bd-124">Vous devez l’initialiser avant l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="948bd-124">You should initialize it before the use.</span></span> <span data-ttu-id="948bd-125">Par exemple, vous pouvez utiliser la <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> méthode qui affecte à tous les éléments la valeur par défaut de type `T` .</span><span class="sxs-lookup"><span data-stu-id="948bd-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="948bd-126">À compter de C# 7,3, vous pouvez utiliser la syntaxe de l’initialiseur de tableau pour définir le contenu de la mémoire nouvellement allouée.</span><span class="sxs-lookup"><span data-stu-id="948bd-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="948bd-127">L’exemple suivant illustre différentes manières de le faire :</span><span class="sxs-lookup"><span data-stu-id="948bd-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="948bd-128">Dans Expression `stackalloc T[E]` , `T` doit être un [type non managé](../builtin-types/unmanaged-types.md) et `E` doit correspondre à une valeur [int](../builtin-types/integral-numeric-types.md) non négative.</span><span class="sxs-lookup"><span data-stu-id="948bd-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="948bd-129">Sécurité</span><span class="sxs-lookup"><span data-stu-id="948bd-129">Security</span></span>

<span data-ttu-id="948bd-130">L’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="948bd-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="948bd-131">Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.</span><span class="sxs-lookup"><span data-stu-id="948bd-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="948bd-132">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="948bd-132">C# language specification</span></span>

<span data-ttu-id="948bd-133">Pour plus d’informations, consultez la section [allocation de pile](~/_csharplang/spec/unsafe-code.md#stack-allocation) de la [spécification du langage C#](~/_csharplang/spec/introduction.md) et la fonctionnalité [autoriser dans les `stackalloc` contextes imbriqués](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="948bd-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="948bd-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="948bd-134">See also</span></span>

- [<span data-ttu-id="948bd-135">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="948bd-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="948bd-136">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="948bd-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="948bd-137">Opérateurs associés au pointeur</span><span class="sxs-lookup"><span data-stu-id="948bd-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="948bd-138">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="948bd-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="948bd-139">Types liés à la mémoire et à l’étendue</span><span class="sxs-lookup"><span data-stu-id="948bd-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="948bd-140">Dos et ne pas de stackalloc</span><span class="sxs-lookup"><span data-stu-id="948bd-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
