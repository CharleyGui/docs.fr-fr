---
title: Comment concatenate plusieurs cordes (Guide de C)
description: Il existe plusieurs façons de concaténer des chaînes dans C#. Découvrez les options et les raisons de les choisir.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: bbdeba4ee3526140de29ac0d7c97e9a593729d47
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389535"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="70de0-104">Comment concatenate plusieurs cordes (Guide de C)</span><span class="sxs-lookup"><span data-stu-id="70de0-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="70de0-105">La *concaténation* consiste à ajouter une chaîne à la fin d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="70de0-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="70de0-106">Vous concaténez les chaînes à l’aide de l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="70de0-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="70de0-107">Pour les littéraux de chaîne et les constantes de chaîne, la concaténation se produit au moment de la compilation ; aucune concaténation ne se produit au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="70de0-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="70de0-108">Pour les variables de chaîne, la concaténation se produit uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="70de0-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="70de0-109">L’exemple suivant utilise la concaténation pour diviser un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source.</span><span class="sxs-lookup"><span data-stu-id="70de0-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="70de0-110">Les diverses parties sont concaténées en une chaîne unique lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="70de0-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="70de0-111">Il n’y a aucune incidence sur les performances d’exécution, quel que soit le nombre de chaînes impliquées.</span><span class="sxs-lookup"><span data-stu-id="70de0-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="70de0-112">Pour concatenate variables de chaîne, `+=` vous pouvez utiliser <xref:System.String.Format%2A?displayProperty=nameWithType>le <xref:System.String.Concat%2A?displayProperty=nameWithType> `+` <xref:System.String.Join%2A?displayProperty=nameWithType> ou les opérateurs, [l’interpolation de chaîne](../language-reference/tokens/interpolated.md) ou le , , ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> des méthodes.</span><span class="sxs-lookup"><span data-stu-id="70de0-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="70de0-113">L’opérateur `+` est facile à utiliser et convient au code intuitif.</span><span class="sxs-lookup"><span data-stu-id="70de0-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="70de0-114">Même si vous utilisez plusieurs opérateurs `+` dans une instruction, le contenu de la chaîne est copié une seule fois.</span><span class="sxs-lookup"><span data-stu-id="70de0-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="70de0-115">Le code suivant montre des exemples d’utilisation des opérateurs `+` et `+=` pour concaténer des chaînes :</span><span class="sxs-lookup"><span data-stu-id="70de0-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="70de0-116">Dans certaines expressions, il est plus facile de concaténer des chaînes à l’aide de l’interpolation de chaînes, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="70de0-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="70de0-117">Dans les opérations de concaténation de chaîne, le compilateur C# traite une chaîne null de la même manière qu’une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70de0-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="70de0-118">Une autre méthode permettant de concaténer des chaînes est <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70de0-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="70de0-119">Cette méthode fonctionne bien quand vous créez une chaîne à partir d’un petit nombre de chaînes de composant.</span><span class="sxs-lookup"><span data-stu-id="70de0-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="70de0-120">Dans d’autres cas, vous combinez peut-être des chaînes dans une boucle où vous ne savez pas combien de chaînes de source vous combinez, et le nombre réel de chaînes de source peut être grand.</span><span class="sxs-lookup"><span data-stu-id="70de0-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="70de0-121">La classe <xref:System.Text.StringBuilder> a été conçue pour ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="70de0-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="70de0-122">Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="70de0-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="70de0-123">Vous pouvez en savoir plus sur les [raisons `StringBuilder` de choisir la concatenation des cordes ou la classe](xref:System.Text.StringBuilder#StringAndSB).</span><span class="sxs-lookup"><span data-stu-id="70de0-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="70de0-124">Une autre option permettant de joindre les chaînes d’une collection consiste à utiliser la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70de0-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="70de0-125">Utilisez <xref:System.String.Join%2A?displayProperty=nameWithType> la méthode si les chaînes de source doivent être séparées par un délimitant.</span><span class="sxs-lookup"><span data-stu-id="70de0-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="70de0-126">Le code suivant combine un tableau de mots en utilisant ces deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="70de0-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="70de0-127">Enfin, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) et la méthode <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> pour joindre les chaînes d’une collection.</span><span class="sxs-lookup"><span data-stu-id="70de0-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="70de0-128">Cette méthode combine les chaînes sources en utilisant une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="70de0-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="70de0-129">L’expression lambda effectue le travail d’ajouter chaque chaîne à l’accumulation existante.</span><span class="sxs-lookup"><span data-stu-id="70de0-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="70de0-130">L’exemple suivant combine un tableau de mots en ajoutant un espace entre chaque mot du tableau :</span><span class="sxs-lookup"><span data-stu-id="70de0-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="70de0-131">Vous pouvez essayer ces échantillons en regardant le [code de l’échantillon](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="70de0-131">You can try these samples by looking at the [sample code](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="70de0-132">Ou, vous pouvez télécharger les échantillons [comme un fichier zip](../../../samples/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="70de0-132">Or, you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="70de0-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70de0-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="70de0-134">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="70de0-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="70de0-135">Chaînes</span><span class="sxs-lookup"><span data-stu-id="70de0-135">Strings</span></span>](../programming-guide/strings/index.md)
