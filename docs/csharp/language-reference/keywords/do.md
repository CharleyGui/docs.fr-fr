---
title: do - Référence C#
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 5612cfb2462117ac431de9c702cd8137f495e5dc
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551808"
---
# <a name="do-c-reference"></a><span data-ttu-id="1b7f9-102">do (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1b7f9-102">do (C# Reference)</span></span>

<span data-ttu-id="1b7f9-103">L’instruction `do` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="1b7f9-104">Dans la mesure où cette expression est évaluée après chaque exécution de la boucle, une boucle `do-while` s’exécute une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="1b7f9-105">Cela diffère de la boucle [while](while.md), qui s’exécute zéro ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="1b7f9-106">À tout moment dans le bloc d’instructions `do`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="1b7f9-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="1b7f9-107">Vous pouvez passer directement à l’évaluation de l’expression `while` à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="1b7f9-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="1b7f9-108">Si l’expression correspond à `true`, l’exécution passe à la première instruction de la boucle.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="1b7f9-109">Sinon, l’exécution passe à la première instruction après la boucle.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="1b7f9-110">Vous pouvez également quitter une boucle `do-while` en utilisant les instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="1b7f9-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="1b7f9-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b7f9-111">Example</span></span>

<span data-ttu-id="1b7f9-112">L’exemple suivant illustre l’utilisation de l’instruction `do`.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="1b7f9-113">Sélectionnez **Exécuter** pour exécuter l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="1b7f9-114">Après cela, vous pouvez modifier le code et le réexécuter.</span><span class="sxs-lookup"><span data-stu-id="1b7f9-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="1b7f9-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1b7f9-115">C# language specification</span></span>

<span data-ttu-id="1b7f9-116">Pour plus d’informations, voir la section [Instruction do](~/_csharplang/spec/statements.md#the-do-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="1b7f9-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b7f9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b7f9-117">See also</span></span>

- [<span data-ttu-id="1b7f9-118">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="1b7f9-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1b7f9-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1b7f9-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1b7f9-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="1b7f9-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1b7f9-121">instruction while</span><span class="sxs-lookup"><span data-stu-id="1b7f9-121">while statement</span></span>](while.md)
