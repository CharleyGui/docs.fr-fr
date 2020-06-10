---
title: Comment concaténer plusieurs chaînes (Guide C#)
description: Il existe plusieurs façons de concaténer des chaînes dans C#. Découvrez les options et les raisons de les choisir.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: ef3d79c5b40d08cb76e58eba1c8831c468fd1fc0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663016"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="14439-104">Comment concaténer plusieurs chaînes (Guide C#)</span><span class="sxs-lookup"><span data-stu-id="14439-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="14439-105">La *concaténation* consiste à ajouter une chaîne à la fin d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="14439-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="14439-106">Vous concaténez les chaînes à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="14439-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="14439-107">Pour les littéraux de chaîne et les constantes de chaîne, la concaténation se produit au moment de la compilation ; aucune concaténation ne se produit au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="14439-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="14439-108">Pour les variables de chaîne, la concaténation se produit uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="14439-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="14439-109">L’exemple suivant utilise la concaténation pour diviser un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source.</span><span class="sxs-lookup"><span data-stu-id="14439-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="14439-110">Les diverses parties sont concaténées en une chaîne unique lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="14439-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="14439-111">Il n’y a aucune incidence sur les performances d’exécution, quel que soit le nombre de chaînes impliquées.</span><span class="sxs-lookup"><span data-stu-id="14439-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

<span data-ttu-id="14439-112">Pour concaténer des variables de chaîne, vous pouvez utiliser les `+` `+=` opérateurs ou, l’interpolation de [chaîne](../language-reference/tokens/interpolated.md) ou les <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> méthodes, <xref:System.String.Join%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="14439-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="14439-113">L’opérateur `+` est facile à utiliser et convient au code intuitif.</span><span class="sxs-lookup"><span data-stu-id="14439-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="14439-114">Même si vous utilisez plusieurs opérateurs `+` dans une instruction, le contenu de la chaîne est copié une seule fois.</span><span class="sxs-lookup"><span data-stu-id="14439-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="14439-115">Le code suivant montre des exemples d’utilisation des opérateurs `+` et `+=` pour concaténer des chaînes :</span><span class="sxs-lookup"><span data-stu-id="14439-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

<span data-ttu-id="14439-116">Dans certaines expressions, il est plus facile de concaténer des chaînes à l’aide de l’interpolation de chaînes, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="14439-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> <span data-ttu-id="14439-117">Dans les opérations de concaténation de chaîne, le compilateur C# traite une chaîne null de la même manière qu’une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="14439-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="14439-118">Une autre méthode permettant de concaténer des chaînes est <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14439-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="14439-119">Cette méthode fonctionne bien quand vous créez une chaîne à partir d’un petit nombre de chaînes de composant.</span><span class="sxs-lookup"><span data-stu-id="14439-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="14439-120">Dans d’autres cas, vous pouvez combiner des chaînes dans une boucle où vous ne connaissez pas le nombre de chaînes sources que vous combinez et le nombre réel de chaînes sources peut être élevé.</span><span class="sxs-lookup"><span data-stu-id="14439-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="14439-121">La classe <xref:System.Text.StringBuilder> a été conçue pour ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="14439-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="14439-122">Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="14439-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

<span data-ttu-id="14439-123">Vous pouvez en savoir plus sur les [raisons pour choisir la concaténation de chaînes ou la `StringBuilder` classe](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span><span class="sxs-lookup"><span data-stu-id="14439-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span></span>

<span data-ttu-id="14439-124">Une autre option permettant de joindre les chaînes d’une collection consiste à utiliser la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14439-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="14439-125">Utilisez <xref:System.String.Join%2A?displayProperty=nameWithType> la méthode si les chaînes sources doivent être séparées par un délimiteur.</span><span class="sxs-lookup"><span data-stu-id="14439-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="14439-126">Le code suivant combine un tableau de mots en utilisant ces deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="14439-126">The following code combines an array of words using both methods:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

<span data-ttu-id="14439-127">Enfin, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) et la méthode <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> pour joindre les chaînes d’une collection.</span><span class="sxs-lookup"><span data-stu-id="14439-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="14439-128">Cette méthode combine les chaînes sources en utilisant une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="14439-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="14439-129">L’expression lambda effectue le travail d’ajouter chaque chaîne à l’accumulation existante.</span><span class="sxs-lookup"><span data-stu-id="14439-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="14439-130">L’exemple suivant combine un tableau de mots en ajoutant un espace entre chaque mot du tableau :</span><span class="sxs-lookup"><span data-stu-id="14439-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a><span data-ttu-id="14439-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14439-131">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="14439-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="14439-132">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="14439-133">Chaînes</span><span class="sxs-lookup"><span data-stu-id="14439-133">Strings</span></span>](../programming-guide/strings/index.md)
