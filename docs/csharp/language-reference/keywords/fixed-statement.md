---
title: fixed, instruction - Référence C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d743daca2fa779e300c7e8ab430b1ffff10b434c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401912"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="94bf3-102">fixed, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="94bf3-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="94bf3-103">L’instruction `fixed` empêche le récupérateur de mémoire de déplacer une variable mobile.</span><span class="sxs-lookup"><span data-stu-id="94bf3-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="94bf3-104">L’instruction `fixed` est uniquement autorisée dans un contexte [unsafe](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="94bf3-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="94bf3-105">Vous pouvez également utiliser le mot clé `fixed` pour créer des [mémoires tampons de taille fixe](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="94bf3-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="94bf3-106">L’instruction `fixed` définit un pointeur vers une variable managée et épingle cette variable pendant l’exécution de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="94bf3-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="94bf3-107">Les pointeurs vers des variables managées ne sont utiles que dans un contexte `fixed`.</span><span class="sxs-lookup"><span data-stu-id="94bf3-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="94bf3-108">Sans contexte `fixed`, le garbage collection peut déplacer les variables de manière imprévisible.</span><span class="sxs-lookup"><span data-stu-id="94bf3-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="94bf3-109">Le compilateur C# permet seulement d’assigner un pointeur à une variable managée dans une instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="94bf3-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

<span data-ttu-id="94bf3-110">Vous pouvez initialiser un pointeur à l’aide d’un tableau, d’une chaîne, d’un tampon de taille fixe ou de l’adresse d’une variable.</span><span class="sxs-lookup"><span data-stu-id="94bf3-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="94bf3-111">L’exemple suivant montre l’utilisation des adresses de variables, des tableaux et des chaînes :</span><span class="sxs-lookup"><span data-stu-id="94bf3-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

<span data-ttu-id="94bf3-112">À compter de C# 7.3, l’instruction `fixed` s’applique à d’autres types au-delà des tableaux, chaînes, mémoires tampons de taille fixe ou variables non managées.</span><span class="sxs-lookup"><span data-stu-id="94bf3-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="94bf3-113">Tout type qui implémente une méthode nommée `GetPinnableReference` peut être épinglé.</span><span class="sxs-lookup"><span data-stu-id="94bf3-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="94bf3-114">`GetPinnableReference` doit retourner une variable `ref` d’un [type non managé](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="94bf3-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="94bf3-115">Les types .NET <xref:System.Span%601?displayProperty=nameWithType> et <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduits dans .NET Core 2.0 utilisent ce modèle et peuvent être épinglés.</span><span class="sxs-lookup"><span data-stu-id="94bf3-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="94bf3-116">Ceci est illustré dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="94bf3-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="94bf3-117">Si vous créez des types qui doivent être inclus dans ce modèle, consultez <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> pour obtenir un exemple d’implémentation du modèle.</span><span class="sxs-lookup"><span data-stu-id="94bf3-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="94bf3-118">Plusieurs pointeurs peuvent être initialisés dans une instruction s’ils sont tous du même type :</span><span class="sxs-lookup"><span data-stu-id="94bf3-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="94bf3-119">Pour initialiser des pointeurs de types différents, imbriquez des instructions `fixed`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="94bf3-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

<span data-ttu-id="94bf3-120">Une fois que le code de l’instruction est exécuté, toutes les variables épinglées sont libérées et soumises au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="94bf3-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="94bf3-121">Par conséquent, ne pointez pas vers ces variables en dehors de l’instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="94bf3-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="94bf3-122">La portée des variables déclarées dans l’instruction `fixed` est limitée à cette instruction, ce qui facilite les choses :</span><span class="sxs-lookup"><span data-stu-id="94bf3-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="94bf3-123">Les pointeurs initialisés dans des instructions `fixed` sont des variables en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="94bf3-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="94bf3-124">Pour modifier la valeur du pointeur, vous devez déclarer une deuxième variable de pointeur et la modifier.</span><span class="sxs-lookup"><span data-stu-id="94bf3-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="94bf3-125">La variable déclarée dans l’instruction `fixed` ne peut pas être modifiée :</span><span class="sxs-lookup"><span data-stu-id="94bf3-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="94bf3-126">Vous pouvez allouer de la mémoire à la pile, où elle n’est pas soumise au nettoyage de la mémoire et n’a donc pas besoin d’être épinglée.</span><span class="sxs-lookup"><span data-stu-id="94bf3-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="94bf3-127">Pour ce faire, utilisez une [ `stackalloc` expression](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="94bf3-127">To do that, use a [`stackalloc` expression](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="94bf3-128">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="94bf3-128">C# language specification</span></span>

<span data-ttu-id="94bf3-129">Pour plus d’informations, consultez la section [Instructions fixes](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="94bf3-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94bf3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94bf3-130">See also</span></span>

- [<span data-ttu-id="94bf3-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="94bf3-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="94bf3-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="94bf3-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="94bf3-133">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="94bf3-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="94bf3-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="94bf3-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="94bf3-135">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="94bf3-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="94bf3-136">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="94bf3-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
