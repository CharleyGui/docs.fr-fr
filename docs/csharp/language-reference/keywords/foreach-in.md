---
description: foreach, instruction (C#)
title: foreach, instruction (C#)
ms.date: 09/18/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: ea8a6f86595348a32b707caf9782f84147fefc87
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828888"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="bba25-103">foreach, instruction (C#)</span><span class="sxs-lookup"><span data-stu-id="bba25-103">foreach, in (C# reference)</span></span>

<span data-ttu-id="bba25-104">L' `foreach` instruction exécute une instruction ou un bloc d’instructions pour chaque élément d’une instance du type qui implémente l' <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface ou, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bba25-104">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="bba25-105">L' `foreach` instruction n’est pas limitée à ces types.</span><span class="sxs-lookup"><span data-stu-id="bba25-105">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="bba25-106">Vous pouvez l’utiliser avec une instance de n’importe quel type répondant aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="bba25-106">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="bba25-107">Un type a la méthode sans paramètre public `GetEnumerator` dont le type de retour est de type classe, struct ou interface.</span><span class="sxs-lookup"><span data-stu-id="bba25-107">A type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type.</span></span> <span data-ttu-id="bba25-108">À compter de C# 9,0, la `GetEnumerator` méthode peut être la [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md)d’un type.</span><span class="sxs-lookup"><span data-stu-id="bba25-108">Beginning with C# 9.0, the `GetEnumerator` method can be a type's [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>
- <span data-ttu-id="bba25-109">Le type de retour de la `GetEnumerator` méthode a la `Current` propriété publique et la méthode sans paramètre public `MoveNext` dont le type de retour est <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="bba25-109">The return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="bba25-110">L’exemple suivant utilise l' `foreach` instruction avec une instance du <xref:System.Span%601?displayProperty=nameWithType> type, qui n’implémente aucune interface :</span><span class="sxs-lookup"><span data-stu-id="bba25-110">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="bba25-111">À compter de C# 7,3, si la propriété de l’énumérateur `Current` retourne une [valeur de retour de référence](ref.md#reference-return-values) ( `ref T` où `T` est le type d’un élément de collection), vous pouvez déclarer une variable d’itération avec le `ref` `ref readonly` modificateur ou, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bba25-111">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="bba25-112">À compter de C# 8,0, vous pouvez utiliser l' `await foreach` instruction pour consommer un flux de données asynchrone, autrement dit, le type de collection qui implémente l' <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="bba25-112">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="bba25-113">Chaque itération de la boucle peut être interrompue pendant que l’élément suivant est récupéré de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="bba25-113">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="bba25-114">L’exemple suivant montre comment utiliser l' `await foreach` instruction :</span><span class="sxs-lookup"><span data-stu-id="bba25-114">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="bba25-115">Par défaut, les éléments de flux sont traités dans le contexte capturé.</span><span class="sxs-lookup"><span data-stu-id="bba25-115">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="bba25-116">Si vous souhaitez désactiver la capture du contexte, utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="bba25-116">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="bba25-117">Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, consultez [utilisation du modèle asynchrone basé sur des tâches](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="bba25-117">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="bba25-118">Pour plus d’informations sur les flux asynchrones, consultez la section [Streams asynchrones](../../whats-new/csharp-8.md#asynchronous-streams) de l’article [nouveautés de C# 8,0](../../whats-new/csharp-8.md) .</span><span class="sxs-lookup"><span data-stu-id="bba25-118">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="bba25-119">À tout moment dans le bloc d’instructions `foreach`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="bba25-119">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="bba25-120">Vous pouvez également quitter une `foreach` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="bba25-120">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="bba25-121">Si l’instruction `foreach` est appliquée à `null`, une <xref:System.NullReferenceException> est levée.</span><span class="sxs-lookup"><span data-stu-id="bba25-121">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="bba25-122">Si la collection source de l' `foreach` instruction est vide, le corps de la `foreach` boucle n’est pas exécuté et ignoré.</span><span class="sxs-lookup"><span data-stu-id="bba25-122">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="bba25-123">Type d’une variable d’itération</span><span class="sxs-lookup"><span data-stu-id="bba25-123">Type of an iteration variable</span></span>

<span data-ttu-id="bba25-124">Vous pouvez utiliser le `var` mot clé pour permettre au compilateur de déduire le type d’une variable d’itération dans l' `foreach` instruction, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bba25-124">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="bba25-125">Vous pouvez également spécifier explicitement le type d’une variable d’itération, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bba25-125">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="bba25-126">Dans le formulaire précédent, le type `T` d’un élément de collection doit être implicitement ou explicitement convertible en type `V` d’une variable d’itération.</span><span class="sxs-lookup"><span data-stu-id="bba25-126">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="bba25-127">Si une conversion explicite de `T` en `V` échoue au moment de l’exécution, l' `foreach` instruction lève une exception <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="bba25-127">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="bba25-128">Par exemple, si `T` est un type de classe non scellé, `V` peut être n’importe quel type d’interface, même celui qui `T` n’est pas implémenté.</span><span class="sxs-lookup"><span data-stu-id="bba25-128">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="bba25-129">Au moment de l’exécution, le type d’un élément de collection peut être celui qui dérive de `T` et implémente réellement `V` .</span><span class="sxs-lookup"><span data-stu-id="bba25-129">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="bba25-130">Si ce n’est pas le cas, une <xref:System.InvalidCastException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="bba25-130">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bba25-131">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bba25-131">C# language specification</span></span>

<span data-ttu-id="bba25-132">Pour plus d’informations, voir la section [Instruction foreach](~/_csharplang/spec/statements.md#the-foreach-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="bba25-132">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="bba25-133">Pour plus d’informations sur les fonctionnalités ajoutées dans C# 8,0 et versions ultérieures, consultez les notes de proposition de fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="bba25-133">For more information about features added in C# 8.0 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="bba25-134">Flux asynchrones (C# 8,0)</span><span class="sxs-lookup"><span data-stu-id="bba25-134">Async streams (C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/async-streams.md)
- [<span data-ttu-id="bba25-135">`GetEnumerator`Prise en charge des extensions pour les `foreach` boucles (C# 9,0)</span><span class="sxs-lookup"><span data-stu-id="bba25-135">Extension `GetEnumerator` support for `foreach` loops (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/extension-getenumerator.md)

## <a name="see-also"></a><span data-ttu-id="bba25-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bba25-136">See also</span></span>

- [<span data-ttu-id="bba25-137">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="bba25-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bba25-138">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="bba25-138">C# keywords</span></span>](index.md)
- [<span data-ttu-id="bba25-139">Utilisation de foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="bba25-139">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="bba25-140">for, instruction</span><span class="sxs-lookup"><span data-stu-id="bba25-140">for statement</span></span>](for.md)
