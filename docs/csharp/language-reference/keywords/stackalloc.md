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
# <a name="stackalloc-c-reference"></a><span data-ttu-id="1519d-102">stackalloc (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1519d-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="1519d-103">Le mot clé `stackalloc` sert à allouer un bloc de mémoire sur la pile.</span><span class="sxs-lookup"><span data-stu-id="1519d-103">The `stackalloc` keyword is used to allocate a block of memory on the stack.</span></span>

```csharp
Span<int> block = stackalloc int[100];
```

<span data-ttu-id="1519d-104">Le fait d’affecter le bloc alloué à un <xref:System.Span%601?displayName=nameWithType> au lieu d’un `int*` permet d’effectuer des allocations de pile dans un bloc safe.</span><span class="sxs-lookup"><span data-stu-id="1519d-104">Assigning the allocated block to a <xref:System.Span%601?displayName=nameWithType> instead of an `int*` allows stack allocations in a safe block.</span></span> <span data-ttu-id="1519d-105">Le contexte `unsafe` n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1519d-105">The `unsafe` context is not required.</span></span>

## <a name="remarks"></a><span data-ttu-id="1519d-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="1519d-106">Remarks</span></span>

<span data-ttu-id="1519d-107">Le mot clé est valide uniquement dans les initialiseurs de variable locale.</span><span class="sxs-lookup"><span data-stu-id="1519d-107">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="1519d-108">Le code suivant génère des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="1519d-108">The following code causes compiler errors.</span></span>

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

<span data-ttu-id="1519d-109">Dans C# 7.3 et les versions ultérieures, vous pouvez utiliser la syntaxe d’initialiseur de tableau pour les tableaux `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="1519d-109">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="1519d-110">Toutes les déclarations suivantes déclarent un tableau de trois éléments ayant pour valeurs les entiers `1`, `2` et `3`.</span><span class="sxs-lookup"><span data-stu-id="1519d-110">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`.</span></span> <span data-ttu-id="1519d-111">La deuxième initialisation attribue la mémoire à un <xref:System.ReadOnlySpan%601>, indiquant que celle-ci n’est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="1519d-111">The second initialization assigns the memory to a <xref:System.ReadOnlySpan%601>, indicating that the memory cannot be modified.</span></span>

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="1519d-112">Quand des types pointeur sont impliqués, `stackalloc` exige un contexte [unsafe](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="1519d-112">When pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="1519d-113">Pour plus d’informations, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1519d-113">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="1519d-114">`stackalloc` est similaire à [_alloca](/cpp/c-runtime-library/reference/alloca) dans la bibliothèque Runtime C.</span><span class="sxs-lookup"><span data-stu-id="1519d-114">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="1519d-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="1519d-115">Examples</span></span>

<span data-ttu-id="1519d-116">L’exemple suivant calcule et affiche les 20 premiers nombres de la suite de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="1519d-116">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="1519d-117">Chaque nombre est la somme des deux nombres précédents.</span><span class="sxs-lookup"><span data-stu-id="1519d-117">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="1519d-118">Dans le code, un bloc de mémoire de taille suffisante pour contenir 20 éléments de type `int` est alloué sur la pile, et non sur le tas.</span><span class="sxs-lookup"><span data-stu-id="1519d-118">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="1519d-119">L’adresse du bloc est stockée dans le `Span` `fib`.</span><span class="sxs-lookup"><span data-stu-id="1519d-119">The address of the block is stored in the `Span` `fib`.</span></span> <span data-ttu-id="1519d-120">Cette mémoire n’est pas soumise au garbage collection et n’est donc pas tenue d’être épinglée (en utilisant [fixed](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="1519d-120">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="1519d-121">La durée de vie du bloc de mémoire est limitée à la durée de vie de la méthode qui le définit.</span><span class="sxs-lookup"><span data-stu-id="1519d-121">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="1519d-122">Vous ne pouvez pas libérer la mémoire avant le retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1519d-122">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="1519d-123">L’exemple suivant initialise un tableau `stackalloc` d’entiers sur un masque de bits où un bit est défini dans chaque élément.</span><span class="sxs-lookup"><span data-stu-id="1519d-123">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="1519d-124">Cela illustre la nouvelle syntaxe d’initialiseur disponible à partir de C# 7.3 :</span><span class="sxs-lookup"><span data-stu-id="1519d-124">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="1519d-125">Sécurité</span><span class="sxs-lookup"><span data-stu-id="1519d-125">Security</span></span>

<span data-ttu-id="1519d-126">Utilisez <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> dans la mesure du possible, car le code unsafe est moins sécurisé que son équivalent safe.</span><span class="sxs-lookup"><span data-stu-id="1519d-126">You should use <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> when possible because unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="1519d-127">Même avec des pointeurs, `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1519d-127">Even when used with pointers, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="1519d-128">Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.</span><span class="sxs-lookup"><span data-stu-id="1519d-128">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1519d-129">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1519d-129">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1519d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1519d-130">See also</span></span>

- [<span data-ttu-id="1519d-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1519d-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1519d-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1519d-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1519d-133">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="1519d-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1519d-134">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="1519d-134">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
