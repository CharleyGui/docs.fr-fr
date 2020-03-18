---
title: continue, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713659"
---
# <a name="continue-c-reference"></a><span data-ttu-id="57846-102">continue (référence C#)</span><span class="sxs-lookup"><span data-stu-id="57846-102">continue (C# Reference)</span></span>

<span data-ttu-id="57846-103">L’instruction `continue` passe le contrôle à l’itération suivante de l’instruction [while](./while.md), [do](./do.md), [for](./for.md) ou [foreach](./foreach-in.md) englobante dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="57846-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="57846-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="57846-104">Example</span></span>

<span data-ttu-id="57846-105">Dans cet exemple, un compteur est initialisé pour compter de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="57846-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="57846-106">Si vous utilisez l’instruction `continue` conjointement avec l’expression `(i < 9)`, les instructions entre `continue` et la fin du corps de `for` sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="57846-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="57846-107">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="57846-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="57846-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57846-108">See also</span></span>

- [<span data-ttu-id="57846-109">Référence C</span><span class="sxs-lookup"><span data-stu-id="57846-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="57846-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="57846-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="57846-111">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="57846-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="57846-112">Instruction break</span><span class="sxs-lookup"><span data-stu-id="57846-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
