---
title: continue, instruction - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: d5fd2f5edf85c3ac2c8f0367b85b37e76e2e856e
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422109"
---
# <a name="continue-c-reference"></a><span data-ttu-id="5654b-102">continue (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5654b-102">continue (C# Reference)</span></span>

<span data-ttu-id="5654b-103">L’instruction `continue` passe le contrôle à l’itération suivante de l’instruction [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md) ou [foreach](../../../csharp/language-reference/keywords/foreach-in.md) englobante dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="5654b-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="5654b-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="5654b-104">Example</span></span>

<span data-ttu-id="5654b-105">Dans cet exemple, un compteur est initialisé pour compter de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="5654b-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="5654b-106">Si vous utilisez l’instruction `continue` conjointement avec l’expression `(i < 9)`, les instructions entre `continue` et la fin du corps de `for` sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="5654b-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="5654b-107">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5654b-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5654b-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5654b-108">See also</span></span>

- [<span data-ttu-id="5654b-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="5654b-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="5654b-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5654b-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5654b-111">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="5654b-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="5654b-112">Instruction break</span><span class="sxs-lookup"><span data-stu-id="5654b-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
