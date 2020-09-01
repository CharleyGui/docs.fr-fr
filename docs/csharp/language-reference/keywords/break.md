---
description: break, instruction - Référence C#
title: break, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134742"
---
# <a name="break-c-reference"></a><span data-ttu-id="567fe-103">break (référence C#)</span><span class="sxs-lookup"><span data-stu-id="567fe-103">break (C# Reference)</span></span>

<span data-ttu-id="567fe-104">L’instruction `break` termine la boucle englobante ou l’instruction [switch](./switch.md) la plus proche dans laquelle elle figure.</span><span class="sxs-lookup"><span data-stu-id="567fe-104">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="567fe-105">Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="567fe-105">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="567fe-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="567fe-106">Example</span></span>

<span data-ttu-id="567fe-107">Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.</span><span class="sxs-lookup"><span data-stu-id="567fe-107">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="567fe-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="567fe-108">Example</span></span>

<span data-ttu-id="567fe-109">Cet exemple illustre l’utilisation de `break` dans une instruction [switch](./switch.md).</span><span class="sxs-lookup"><span data-stu-id="567fe-109">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="567fe-110">Si vous aviez entré `4`, le résultat serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="567fe-110">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="567fe-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="567fe-111">Example</span></span>

<span data-ttu-id="567fe-112">Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe.</span><span class="sxs-lookup"><span data-stu-id="567fe-112">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="567fe-113">Le contrôle n’est retourné _qu'_ un niveau dans les boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="567fe-113">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="567fe-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="567fe-114">Example</span></span>

<span data-ttu-id="567fe-115">Dans cet exemple, l' `break` instruction est utilisée uniquement pour sortir de la branche active au cours de chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="567fe-115">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="567fe-116">La boucle elle-même n’est pas affectée par les instances de `break` qui appartiennent à l’instruction [switch](./switch.md) imbriquée.</span><span class="sxs-lookup"><span data-stu-id="567fe-116">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="567fe-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="567fe-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="567fe-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="567fe-118">See also</span></span>

- [<span data-ttu-id="567fe-119">Référence C#</span><span class="sxs-lookup"><span data-stu-id="567fe-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="567fe-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="567fe-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="567fe-121">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="567fe-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="567fe-122">switch</span><span class="sxs-lookup"><span data-stu-id="567fe-122">switch</span></span>](./switch.md)
