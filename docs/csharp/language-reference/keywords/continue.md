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
ms.openlocfilehash: 6c70934c3b861e1a1433e5c0b95bb32e9d717c53
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877650"
---
# <a name="continue-c-reference"></a><span data-ttu-id="6c975-103">continue (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6c975-103">continue (C# Reference)</span></span>

<span data-ttu-id="6c975-104">L’instruction `continue` passe le contrôle à l’itération suivante de l’instruction [while](./while.md), [do](./do.md), [for](./for.md) ou [foreach](./foreach-in.md) englobante dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="6c975-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="6c975-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c975-105">Example</span></span>

<span data-ttu-id="6c975-106">Dans cet exemple, un compteur est initialisé pour compter de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="6c975-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="6c975-107">En utilisant l' `continue` instruction conjointement avec l’expression `(i < 9)` , les instructions entre `continue` et la fin du `for` corps sont ignorées dans les itérations où `i` est inférieur à 9.</span><span class="sxs-lookup"><span data-stu-id="6c975-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped in the iterations where `i` is less than 9.</span></span> <span data-ttu-id="6c975-108">Au cours des deux dernières itérations de la `for` boucle (où i = = 9 et i = = 10), l' `continue` instruction n’est pas exécutée et la valeur de `i` est imprimée sur la console.</span><span class="sxs-lookup"><span data-stu-id="6c975-108">In the last two iterations of the `for` loop (where i == 9 and i == 10), the `continue` statement is not executed and the value of `i` is printed to the console.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="6c975-109">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6c975-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6c975-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c975-110">See also</span></span>

- [<span data-ttu-id="6c975-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6c975-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6c975-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6c975-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6c975-113">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="6c975-113">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="6c975-114">Break (instruction)</span><span class="sxs-lookup"><span data-stu-id="6c975-114">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
