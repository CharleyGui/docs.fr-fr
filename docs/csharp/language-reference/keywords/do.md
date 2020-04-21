---
title: do - Référence C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 1d4323366e567dab4b27b07803d0c06e731611ce
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738906"
---
# <a name="do-c-reference"></a><span data-ttu-id="bee17-102">do (référence C#)</span><span class="sxs-lookup"><span data-stu-id="bee17-102">do (C# Reference)</span></span>

<span data-ttu-id="bee17-103">L’instruction `do` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="bee17-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="bee17-104">Dans la mesure où cette expression est évaluée après chaque exécution de la boucle, une boucle `do-while` s’exécute une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="bee17-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="bee17-105">Cela diffère de la boucle [while](while.md), qui s’exécute zéro ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="bee17-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="bee17-106">À tout moment dans le bloc d’instructions `do`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="bee17-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="bee17-107">Vous pouvez passer directement à l’évaluation de l’expression `while` à l’aide de l’instruction [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="bee17-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="bee17-108">Si l’expression correspond à `true`, l’exécution passe à la première instruction de la boucle.</span><span class="sxs-lookup"><span data-stu-id="bee17-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="bee17-109">Sinon, l’exécution passe à la première instruction après la boucle.</span><span class="sxs-lookup"><span data-stu-id="bee17-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="bee17-110">Vous pouvez également `do-while` sortir d’une boucle par le [goto](goto.md), [retour](return.md), ou [lancer des](throw.md) déclarations.</span><span class="sxs-lookup"><span data-stu-id="bee17-110">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="bee17-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="bee17-111">Example</span></span>

<span data-ttu-id="bee17-112">L’exemple suivant illustre l’utilisation de l’instruction `do`.</span><span class="sxs-lookup"><span data-stu-id="bee17-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="bee17-113">Sélectionnez **Exécuter** pour exécuter l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="bee17-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="bee17-114">Après cela, vous pouvez modifier le code et le réexécuter.</span><span class="sxs-lookup"><span data-stu-id="bee17-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="bee17-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bee17-115">C# language specification</span></span>

<span data-ttu-id="bee17-116">Pour plus d’informations, voir la section [Instruction do](~/_csharplang/spec/statements.md#the-do-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="bee17-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="bee17-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bee17-117">See also</span></span>

- [<span data-ttu-id="bee17-118">Référence C</span><span class="sxs-lookup"><span data-stu-id="bee17-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bee17-119">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="bee17-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bee17-120">Mots-clés C</span><span class="sxs-lookup"><span data-stu-id="bee17-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bee17-121">tandis que la déclaration</span><span class="sxs-lookup"><span data-stu-id="bee17-121">while statement</span></span>](while.md)
