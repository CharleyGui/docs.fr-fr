---
description: continue, instruction - Référence C#
title: continue, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 76578b0ad7e2b969609fbf50df1f9ab7de6e5097
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128437"
---
# <a name="continue-c-reference"></a><span data-ttu-id="cf457-103">continue (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cf457-103">continue (C# Reference)</span></span>

<span data-ttu-id="cf457-104">L’instruction `continue` passe le contrôle à l’itération suivante de l’instruction [while](./while.md), [do](./do.md), [for](./for.md) ou [foreach](./foreach-in.md) englobante dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="cf457-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="cf457-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf457-105">Example</span></span>

<span data-ttu-id="cf457-106">Dans cet exemple, un compteur est initialisé pour compter de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="cf457-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="cf457-107">Si vous utilisez l’instruction `continue` conjointement avec l’expression `(i < 9)`, les instructions entre `continue` et la fin du corps de `for` sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="cf457-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="cf457-108">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="cf457-108">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cf457-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf457-109">See also</span></span>

- [<span data-ttu-id="cf457-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cf457-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cf457-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cf457-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cf457-112">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="cf457-112">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="cf457-113">Break (instruction)</span><span class="sxs-lookup"><span data-stu-id="cf457-113">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
