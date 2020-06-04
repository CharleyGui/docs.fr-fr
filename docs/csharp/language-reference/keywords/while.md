---
title: while - Référence C#
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: af616c2381b993f86296cbfa43a01ba2f9e000c2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401860"
---
# <a name="while-c-reference"></a><span data-ttu-id="ea7cf-102">while (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ea7cf-102">while (C# Reference)</span></span>

<span data-ttu-id="ea7cf-103">L’instruction `while` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="ea7cf-104">Dans la mesure où cette expression est évaluée avant chaque exécution de la boucle, une boucle `while` s’exécute plusieurs fois ou pas du tout.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="ea7cf-105">Cela diffère de la boucle [do](do.md), qui s’exécute une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="ea7cf-106">À tout moment dans le bloc d’instructions `while`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="ea7cf-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="ea7cf-107">Vous pouvez passer directement à l’évaluation de l’expression `while` à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="ea7cf-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="ea7cf-108">Si l’expression correspond à `true`, l’exécution passe à la première instruction de la boucle.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="ea7cf-109">Sinon, l’exécution passe à la première instruction après la boucle.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="ea7cf-110">Vous pouvez également quitter une `while` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="ea7cf-110">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="ea7cf-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea7cf-111">Example</span></span>

<span data-ttu-id="ea7cf-112">L’exemple suivant illustre l’utilisation de l’instruction `while`.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="ea7cf-113">Sélectionnez **Exécuter** pour exécuter l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="ea7cf-114">Après cela, vous pouvez modifier le code et le réexécuter.</span><span class="sxs-lookup"><span data-stu-id="ea7cf-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](snippets/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="ea7cf-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ea7cf-115">C# language specification</span></span>

<span data-ttu-id="ea7cf-116">Pour plus d’informations, voir la section [Instruction while](~/_csharplang/spec/statements.md#the-while-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="ea7cf-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea7cf-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea7cf-117">See also</span></span>

- [<span data-ttu-id="ea7cf-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ea7cf-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ea7cf-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ea7cf-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ea7cf-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="ea7cf-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ea7cf-121">instruction do</span><span class="sxs-lookup"><span data-stu-id="ea7cf-121">do statement</span></span>](do.md)
