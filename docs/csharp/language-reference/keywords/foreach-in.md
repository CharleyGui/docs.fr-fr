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
ms.openlocfilehash: 3fbaacb96be2714aaff49679836e5d2d4a3783da
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422472"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="6071f-102">foreach, instruction (C#)</span><span class="sxs-lookup"><span data-stu-id="6071f-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="6071f-103">L’instruction `foreach` exécute une instruction ou un bloc d’instructions pour chaque élément d’une instance du type qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6071f-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="6071f-104">L’instruction `foreach` n’est pas limitée à ces types et peut être appliquée à une instance de n’importe quel type répondant aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="6071f-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="6071f-105">comporte la méthode `GetEnumerator` sans paramètre publique dont le retour est de type classe, struct ou interface,</span><span class="sxs-lookup"><span data-stu-id="6071f-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="6071f-106">le type de retour de la méthode `GetEnumerator` contient la propriété publique `Current` et la méthode sans paramètre publique `MoveNext`, dont le type de retour est <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="6071f-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="6071f-107">À partir de C# 7.3, si la propriété `Current` de l’énumérateur retourne une [valeur de retour de référence](ref.md#reference-return-values) (`ref T` où `T` est le type de l’élément de collection), vous pouvez déclarer la variable d’itération avec le modificateur `ref` ou `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="6071f-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="6071f-108">À tout moment dans le bloc d’instructions `foreach`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="6071f-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="6071f-109">Vous pouvez également quitter une boucle `foreach` en utilisant les instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="6071f-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="6071f-110">Si l’instruction `foreach` est appliquée à `null`, une <xref:System.NullReferenceException> est levée.</span><span class="sxs-lookup"><span data-stu-id="6071f-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="6071f-111">Si la collection source de l’instruction `foreach` est vide, le corps de la boucle `foreach` n’est pas exécuté et est ignoré.</span><span class="sxs-lookup"><span data-stu-id="6071f-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="6071f-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="6071f-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="6071f-113">L’exemple suivant montre l’utilisation de l’instruction `foreach` avec une instance de type <xref:System.Collections.Generic.List%601> qui implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="6071f-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="6071f-114">L’exemple suivant utilise l’instruction `foreach` avec une instance de type <xref:System.Span%601?displayProperty=nameWithType> qui n’implémente aucune interface :</span><span class="sxs-lookup"><span data-stu-id="6071f-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="6071f-115">L’exemple suivant utilise une variable d’itération `ref` pour définir la valeur de chaque élément dans un tableau stackalloc.</span><span class="sxs-lookup"><span data-stu-id="6071f-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="6071f-116">La version `ref readonly` effectue une itération de la collection pour imprimer toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="6071f-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="6071f-117">La déclaration `readonly` utilise une déclaration de variable locale implicite.</span><span class="sxs-lookup"><span data-stu-id="6071f-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="6071f-118">Les déclarations de variable implicite peuvent être utilisées avec les déclarations `ref` ou `ref readonly`, tout comme les déclarations de variable explicitement typée.</span><span class="sxs-lookup"><span data-stu-id="6071f-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="6071f-119">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6071f-119">C# language specification</span></span>

<span data-ttu-id="6071f-120">Pour plus d’informations, voir la section [Instruction foreach](~/_csharplang/spec/statements.md#the-foreach-statement) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6071f-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6071f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6071f-121">See also</span></span>

- [<span data-ttu-id="6071f-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6071f-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6071f-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6071f-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6071f-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="6071f-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6071f-125">Utiliser foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="6071f-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="6071f-126">instruction for</span><span class="sxs-lookup"><span data-stu-id="6071f-126">for statement</span></span>](for.md)
