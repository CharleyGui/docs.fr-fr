---
title: foreach, instruction (C#)
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401886"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="b3ebf-102">foreach, instruction (C#)</span><span class="sxs-lookup"><span data-stu-id="b3ebf-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="b3ebf-103">L’instruction `foreach` exécute une instruction ou un bloc d’instructions pour chaque élément d’une instance du type qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="b3ebf-104">L' `foreach` instruction n’est pas limitée à ces types et peut être appliquée à une instance de n’importe quel type répondant aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b3ebf-104">The `foreach` statement isn't limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="b3ebf-105">comporte la méthode `GetEnumerator` sans paramètre publique dont le retour est de type classe, struct ou interface,</span><span class="sxs-lookup"><span data-stu-id="b3ebf-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="b3ebf-106">le type de retour de la méthode `GetEnumerator` contient la propriété publique `Current` et la méthode sans paramètre publique `MoveNext`, dont le type de retour est <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="b3ebf-107">Dans la plupart des utilisations, `foreach` itère une `IEnumerable<T>` expression où chaque élément est de type `T` .</span><span class="sxs-lookup"><span data-stu-id="b3ebf-107">In most uses, `foreach` iterates an `IEnumerable<T>` expression where each element is of type `T`.</span></span> <span data-ttu-id="b3ebf-108">Toutefois, les éléments peuvent être de n’importe quel type qui a une conversion implicite ou explicite à partir du type de la `Current` propriété.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-108">However, the elements may be any type that has an implicit or explicit conversion from the type of the `Current` property.</span></span> <span data-ttu-id="b3ebf-109">Si la `Current` propriété retourne `SomeType` , le type des éléments peut être :</span><span class="sxs-lookup"><span data-stu-id="b3ebf-109">If the `Current` property returns `SomeType`, the type of the elements may be:</span></span>

- <span data-ttu-id="b3ebf-110">Toutes les classes de base de `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="b3ebf-110">Any of the base classes of `SomeType`.</span></span>
- <span data-ttu-id="b3ebf-111">L’une des interfaces implémentées par `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="b3ebf-111">Any of the interfaces implemented by `SomeType`.</span></span>

<span data-ttu-id="b3ebf-112">En outre, si `SomeType` est un `class` ou un `interface` et non `sealed` , le type d’éléments peut inclure :</span><span class="sxs-lookup"><span data-stu-id="b3ebf-112">Furthermore, if `SomeType` is a `class` or an `interface` and not `sealed`, the type of elements may include:</span></span>

- <span data-ttu-id="b3ebf-113">Tout type dérivé de `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="b3ebf-113">Any type derived from `SomeType`.</span></span>
- <span data-ttu-id="b3ebf-114">Toute interface arbitraire.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-114">Any arbitrary interface.</span></span> <span data-ttu-id="b3ebf-115">Toute interface est autorisée, car toute interface peut être implémentée par une classe dérivée de ou implémentant `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="b3ebf-115">Any interface is allowed because any interface may be implemented by a class derived from or implementing `SomeType`.</span></span>

<span data-ttu-id="b3ebf-116">Vous pouvez déclarer la variable d’itération à l’aide de n’importe quel type qui correspond aux règles précédentes.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-116">You may declare the iteration variable using any type that matches the preceding rules.</span></span> <span data-ttu-id="b3ebf-117">Si la conversion de `SomeType` en type de la variable d’itération requiert un cast explicite, cette opération peut lever une exception <xref:System.InvalidCastException> en cas d’échec de la conversion.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-117">If the conversion from `SomeType` to the type of the iteration variable requires an explicit cast, that operation may throw an <xref:System.InvalidCastException> when the conversion fails.</span></span>

<span data-ttu-id="b3ebf-118">À compter de C# 7,3, si la propriété de l’énumérateur `Current` retourne une [valeur de retour de référence](ref.md#reference-return-values) ( `ref T` où `T` est le type de l’élément de collection), vous pouvez déclarer la variable d’itération avec le `ref` `ref readonly` modificateur ou.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-118">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="b3ebf-119">À compter de C# 8,0, l' `await` opérateur peut être appliqué à l' `foreach` instruction lorsque le type de collection implémente l' <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-119">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="b3ebf-120">Chaque itération de la boucle peut être interrompue pendant que l’élément suivant est récupéré de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-120">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="b3ebf-121">Par défaut, les éléments de flux sont traités dans le contexte capturé.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-121">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="b3ebf-122">Si vous souhaitez désactiver la capture du contexte, utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-122">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="b3ebf-123">Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, consultez l’article sur l' [utilisation du modèle asynchrone basé](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)sur des tâches.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-123">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="b3ebf-124">À tout moment dans le bloc d’instructions `foreach`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="b3ebf-124">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="b3ebf-125">Vous pouvez également quitter une `foreach` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="b3ebf-125">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="b3ebf-126">Si l’instruction `foreach` est appliquée à `null`, une <xref:System.NullReferenceException> est levée.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-126">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="b3ebf-127">Si la collection source de l' `foreach` instruction est vide, le corps de la `foreach` boucle n’est pas exécuté et ignoré.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-127">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="b3ebf-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="b3ebf-128">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="b3ebf-129">L’exemple suivant montre l’utilisation de l’instruction `foreach` avec une instance de type <xref:System.Collections.Generic.List%601> qui implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="b3ebf-129">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="b3ebf-130">L’exemple suivant utilise l’instruction `foreach` avec une instance de type <xref:System.Span%601?displayProperty=nameWithType> qui n’implémente aucune interface :</span><span class="sxs-lookup"><span data-stu-id="b3ebf-130">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="b3ebf-131">L’exemple suivant utilise une variable d’itération `ref` pour définir la valeur de chaque élément dans un tableau stackalloc.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-131">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="b3ebf-132">La version `ref readonly` effectue une itération de la collection pour imprimer toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-132">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="b3ebf-133">La déclaration `readonly` utilise une déclaration de variable locale implicite.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-133">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="b3ebf-134">Les déclarations de variable implicite peuvent être utilisées avec les déclarations `ref` ou `ref readonly`, tout comme les déclarations de variable explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="b3ebf-134">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="b3ebf-135">L’exemple suivant utilise `await foreach` pour itérer une collection qui génère chaque élément de façon asynchrone :</span><span class="sxs-lookup"><span data-stu-id="b3ebf-135">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a><span data-ttu-id="b3ebf-136">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b3ebf-136">C# language specification</span></span>

<span data-ttu-id="b3ebf-137">Pour plus d’informations, voir la section [Instruction foreach](~/_csharplang/spec/statements.md#the-foreach-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b3ebf-137">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3ebf-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3ebf-138">See also</span></span>

- [<span data-ttu-id="b3ebf-139">Référence C#</span><span class="sxs-lookup"><span data-stu-id="b3ebf-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b3ebf-140">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b3ebf-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b3ebf-141">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b3ebf-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b3ebf-142">Utilisation de foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="b3ebf-142">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="b3ebf-143">for, instruction</span><span class="sxs-lookup"><span data-stu-id="b3ebf-143">for statement</span></span>](for.md)
