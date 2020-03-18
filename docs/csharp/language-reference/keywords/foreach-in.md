---
title: foreach, instruction (C#)
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: dbe4f4e95c2b99f1be47885e39d51db81ba3a97d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173703"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="6a3e5-102">foreach, instruction (C#)</span><span class="sxs-lookup"><span data-stu-id="6a3e5-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="6a3e5-103">L’instruction `foreach` exécute une instruction ou un bloc d’instructions pour chaque élément d’une instance du type qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="6a3e5-104">L’instruction `foreach` n’est pas limitée à ces types et peut être appliquée à une instance de n’importe quel type répondant aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a3e5-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="6a3e5-105">comporte la méthode `GetEnumerator` sans paramètre publique dont le retour est de type classe, struct ou interface,</span><span class="sxs-lookup"><span data-stu-id="6a3e5-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="6a3e5-106">le type de retour de la méthode `GetEnumerator` contient la propriété publique `Current` et la méthode sans paramètre publique `MoveNext`, dont le type de retour est <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="6a3e5-107">En commençant par le C 7.3, si `Current` la propriété de l’énumérateur retourne une valeur de [rendement de référence](ref.md#reference-return-values) (où`ref T` `T` est le type de l’élément de collecte), vous pouvez déclarer la variable d’itération avec le ou `ref` `ref readonly` le modificateur.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="6a3e5-108">À partir de C 8.0, l’opérateur `await` peut être appliqué à l’instruction `foreach` lorsque le type de collection implémente l’interface. <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6a3e5-108">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="6a3e5-109">Chaque itération de la boucle peut être suspendue pendant que l’élément suivant est récupéré asynchronement.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-109">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="6a3e5-110">Par défaut, les éléments de flux sont traités dans le contexte capturé.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-110">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="6a3e5-111">Si vous souhaitez désactiver la capture du <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> contexte, utilisez la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-111">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="6a3e5-112">Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, voir [l’article sur la consommation du modèle asynchrone basé sur les tâches](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="6a3e5-112">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="6a3e5-113">À tout moment dans le bloc d’instructions `foreach`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="6a3e5-113">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="6a3e5-114">Vous pouvez également quitter une boucle `foreach` en utilisant les instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="6a3e5-114">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="6a3e5-115">Si l’instruction `foreach` est appliquée à `null`, une <xref:System.NullReferenceException> est levée.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-115">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="6a3e5-116">Si la collecte `foreach` source de la déclaration `foreach` est vide, le corps de la boucle n’est pas exécuté et ignoré.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-116">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="6a3e5-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="6a3e5-117">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="6a3e5-118">L’exemple suivant montre l’utilisation de l’instruction `foreach` avec une instance de type <xref:System.Collections.Generic.List%601> qui implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="6a3e5-118">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="6a3e5-119">L’exemple suivant utilise l’instruction `foreach` avec une instance de type <xref:System.Span%601?displayProperty=nameWithType> qui n’implémente aucune interface :</span><span class="sxs-lookup"><span data-stu-id="6a3e5-119">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="6a3e5-120">L’exemple suivant utilise une variable d’itération `ref` pour définir la valeur de chaque élément dans un tableau stackalloc.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-120">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="6a3e5-121">La version `ref readonly` effectue une itération de la collection pour imprimer toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-121">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="6a3e5-122">La déclaration `readonly` utilise une déclaration de variable locale implicite.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-122">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="6a3e5-123">Les déclarations de variable implicite peuvent être utilisées avec les déclarations `ref` ou `ref readonly`, tout comme les déclarations de variable explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="6a3e5-123">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

<span data-ttu-id="6a3e5-124">L’exemple `await foreach` suivant utilise pour itérer une collection qui génère chaque élément asynchronement:</span><span class="sxs-lookup"><span data-stu-id="6a3e5-124">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a><span data-ttu-id="6a3e5-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6a3e5-125">C# language specification</span></span>

<span data-ttu-id="6a3e5-126">Pour plus d’informations, voir la section [Instruction foreach](~/_csharplang/spec/statements.md#the-foreach-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="6a3e5-126">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a3e5-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a3e5-127">See also</span></span>

- [<span data-ttu-id="6a3e5-128">Référence C</span><span class="sxs-lookup"><span data-stu-id="6a3e5-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6a3e5-129">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6a3e5-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6a3e5-130">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="6a3e5-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6a3e5-131">Utilisation de l’avant-car avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="6a3e5-131">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="6a3e5-132">pour déclaration</span><span class="sxs-lookup"><span data-stu-id="6a3e5-132">for statement</span></span>](for.md)
