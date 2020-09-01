---
description: do - Référence C#
title: do - Référence C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 601231f23a58e8af8339a733677f0bbd92bb4ffc
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126955"
---
# <a name="do-c-reference"></a><span data-ttu-id="e6c33-103">do (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e6c33-103">do (C# Reference)</span></span>

<span data-ttu-id="e6c33-104">L’instruction `do` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e6c33-104">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="e6c33-105">Dans la mesure où cette expression est évaluée après chaque exécution de la boucle, une boucle `do-while` s’exécute une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e6c33-105">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="e6c33-106">Cela diffère de la boucle [while](while.md), qui s’exécute zéro ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e6c33-106">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="e6c33-107">À tout moment dans le bloc d’instructions `do`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="e6c33-107">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="e6c33-108">Vous pouvez passer directement à l’évaluation de l’expression `while` à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="e6c33-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="e6c33-109">Si l’expression correspond à `true`, l’exécution passe à la première instruction de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e6c33-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="e6c33-110">Sinon, l’exécution passe à la première instruction après la boucle.</span><span class="sxs-lookup"><span data-stu-id="e6c33-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="e6c33-111">Vous pouvez également quitter une `do-while` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="e6c33-111">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="e6c33-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="e6c33-112">Example</span></span>

<span data-ttu-id="e6c33-113">L’exemple suivant illustre l’utilisation de l’instruction `do`.</span><span class="sxs-lookup"><span data-stu-id="e6c33-113">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="e6c33-114">Sélectionnez **Exécuter** pour exécuter l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="e6c33-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="e6c33-115">Après cela, vous pouvez modifier le code et le réexécuter.</span><span class="sxs-lookup"><span data-stu-id="e6c33-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="e6c33-116">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e6c33-116">C# language specification</span></span>

<span data-ttu-id="e6c33-117">Pour plus d’informations, voir la section [Instruction do](~/_csharplang/spec/statements.md#the-do-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="e6c33-117">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6c33-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6c33-118">See also</span></span>

- [<span data-ttu-id="e6c33-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="e6c33-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e6c33-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e6c33-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e6c33-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="e6c33-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e6c33-122">while, instruction</span><span class="sxs-lookup"><span data-stu-id="e6c33-122">while statement</span></span>](while.md)
