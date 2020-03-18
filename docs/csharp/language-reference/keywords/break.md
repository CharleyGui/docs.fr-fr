---
title: break, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713751"
---
# <a name="break-c-reference"></a><span data-ttu-id="9e995-102">break (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9e995-102">break (C# Reference)</span></span>

<span data-ttu-id="9e995-103">L’instruction `break` termine la boucle englobante ou l’instruction [switch](./switch.md) la plus proche dans laquelle elle figure.</span><span class="sxs-lookup"><span data-stu-id="9e995-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="9e995-104">Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="9e995-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="9e995-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9e995-105">Example</span></span>

<span data-ttu-id="9e995-106">Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.</span><span class="sxs-lookup"><span data-stu-id="9e995-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="9e995-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9e995-107">Example</span></span>

<span data-ttu-id="9e995-108">Cet exemple illustre l’utilisation de `break` dans une instruction [switch](./switch.md).</span><span class="sxs-lookup"><span data-stu-id="9e995-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="9e995-109">Si vous aviez entré `4`, le résultat serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="9e995-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="9e995-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9e995-110">Example</span></span>

<span data-ttu-id="9e995-111">Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe.</span><span class="sxs-lookup"><span data-stu-id="9e995-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="9e995-112">Le contrôle n’est retourné _qu’un_ niveau dans les boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="9e995-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="9e995-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9e995-113">Example</span></span>

<span data-ttu-id="9e995-114">Dans cet exemple, l’instruction `break` n’est utilisée que pour sortir de la branche actuelle lors de chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="9e995-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="9e995-115">La boucle elle-même n’est `break` pas affectée par les cas qui appartiennent à l’énoncé [d’interrupteur](./switch.md) imbriqué.</span><span class="sxs-lookup"><span data-stu-id="9e995-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="9e995-116">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9e995-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9e995-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e995-117">See also</span></span>

- [<span data-ttu-id="9e995-118">Référence C</span><span class="sxs-lookup"><span data-stu-id="9e995-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9e995-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9e995-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9e995-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="9e995-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9e995-121">Interrupteur</span><span class="sxs-lookup"><span data-stu-id="9e995-121">switch</span></span>](./switch.md)
