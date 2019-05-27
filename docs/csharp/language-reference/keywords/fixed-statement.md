---
title: fixed, instruction - Référence C#
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: a852f36c05075365ced8ec39457b15601ca3c3fb
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877086"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="803e5-102">fixed, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="803e5-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="803e5-103">L’instruction `fixed` empêche le récupérateur de mémoire de déplacer une variable mobile.</span><span class="sxs-lookup"><span data-stu-id="803e5-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="803e5-104">L’instruction `fixed` est uniquement autorisée dans un contexte [unsafe](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="803e5-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="803e5-105">Vous pouvez également utiliser le mot clé `fixed` pour créer des [mémoires tampons de taille fixe](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="803e5-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="803e5-106">L’instruction `fixed` définit un pointeur vers une variable managée et épingle cette variable pendant l’exécution de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="803e5-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="803e5-107">Les pointeurs vers des variables managées ne sont utiles que dans un contexte `fixed`.</span><span class="sxs-lookup"><span data-stu-id="803e5-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="803e5-108">Sans contexte `fixed`, le garbage collection peut déplacer les variables de manière imprévisible.</span><span class="sxs-lookup"><span data-stu-id="803e5-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="803e5-109">Le compilateur C# permet seulement d’assigner un pointeur à une variable managée dans une instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="803e5-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="803e5-110">Vous pouvez initialiser un pointeur à l’aide d’un tableau, d’une chaîne, d’un tampon de taille fixe ou de l’adresse d’une variable.</span><span class="sxs-lookup"><span data-stu-id="803e5-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="803e5-111">L’exemple suivant montre l’utilisation des adresses de variables, des tableaux et des chaînes :</span><span class="sxs-lookup"><span data-stu-id="803e5-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="803e5-112">À compter de C# 7.3, l’instruction `fixed` s’applique à d’autres types au-delà des tableaux, chaînes, mémoires tampons de taille fixe ou variables non managées.</span><span class="sxs-lookup"><span data-stu-id="803e5-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed-size buffers, or unmanaged variables.</span></span> <span data-ttu-id="803e5-113">Tout type qui implémente une méthode nommée `GetPinnableReference` peut être épinglé.</span><span class="sxs-lookup"><span data-stu-id="803e5-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="803e5-114">`GetPinnableReference` doit retourner une variable `ref` d’un type non géré.</span><span class="sxs-lookup"><span data-stu-id="803e5-114">The `GetPinnableReference` must return a `ref` variable to an unmanaged type.</span></span> <span data-ttu-id="803e5-115">Consultez la rubrique consacrée aux [types pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="803e5-115">See the topic on [pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md) for more information.</span></span> <span data-ttu-id="803e5-116">Les types .NET <xref:System.Span%601?displayProperty=nameWithType> et <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduits dans .NET Core 2.0 utilisent ce modèle et peuvent être épinglés.</span><span class="sxs-lookup"><span data-stu-id="803e5-116">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="803e5-117">Ceci est illustré dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="803e5-117">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="803e5-118">Si vous créez des types qui doivent être inclus dans ce modèle, consultez <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> pour obtenir un exemple d’implémentation du modèle.</span><span class="sxs-lookup"><span data-stu-id="803e5-118">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="803e5-119">Plusieurs pointeurs peuvent être initialisés dans une instruction s’ils sont tous du même type :</span><span class="sxs-lookup"><span data-stu-id="803e5-119">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="803e5-120">Pour initialiser des pointeurs de types différents, imbriquez des instructions `fixed`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="803e5-120">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="803e5-121">Une fois que le code de l’instruction est exécuté, toutes les variables épinglées sont libérées et soumises au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="803e5-121">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="803e5-122">Par conséquent, ne pointez pas vers ces variables en dehors de l’instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="803e5-122">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="803e5-123">La portée des variables déclarées dans l’instruction `fixed` est limitée à cette instruction, ce qui facilite les choses :</span><span class="sxs-lookup"><span data-stu-id="803e5-123">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="803e5-124">Les pointeurs initialisés dans des instructions `fixed` sont des variables en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="803e5-124">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="803e5-125">Pour modifier la valeur du pointeur, vous devez déclarer une deuxième variable de pointeur et la modifier.</span><span class="sxs-lookup"><span data-stu-id="803e5-125">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="803e5-126">La variable déclarée dans l’instruction `fixed` ne peut pas être modifiée :</span><span class="sxs-lookup"><span data-stu-id="803e5-126">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="803e5-127">Vous pouvez allouer de la mémoire à la pile, où elle n’est pas soumise au nettoyage de la mémoire et n’a donc pas besoin d’être épinglée.</span><span class="sxs-lookup"><span data-stu-id="803e5-127">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="803e5-128">Pour plus d’informations, consultez [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="803e5-128">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="803e5-129">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="803e5-129">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="803e5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="803e5-130">See also</span></span>

- [<span data-ttu-id="803e5-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="803e5-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="803e5-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="803e5-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="803e5-133">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="803e5-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="803e5-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="803e5-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="803e5-135">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="803e5-135">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
