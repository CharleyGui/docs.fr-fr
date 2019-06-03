---
title: break, instruction - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 15b193d9f294c01826b6b60587678ad76248e976
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422066"
---
# <a name="break-c-reference"></a><span data-ttu-id="172b1-102">break (référence C#)</span><span class="sxs-lookup"><span data-stu-id="172b1-102">break (C# Reference)</span></span>

<span data-ttu-id="172b1-103">L’instruction `break` termine la boucle englobante ou l’instruction [switch](../../../csharp/language-reference/keywords/switch.md) la plus proche dans laquelle elle figure.</span><span class="sxs-lookup"><span data-stu-id="172b1-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="172b1-104">Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="172b1-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="172b1-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="172b1-105">Example</span></span>

<span data-ttu-id="172b1-106">Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.</span><span class="sxs-lookup"><span data-stu-id="172b1-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="172b1-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="172b1-107">Example</span></span>

<span data-ttu-id="172b1-108">Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe.</span><span class="sxs-lookup"><span data-stu-id="172b1-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="172b1-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="172b1-109">Example</span></span>

<span data-ttu-id="172b1-110">Cet exemple illustre l’utilisation de `break` dans une instruction [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="172b1-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="172b1-111">Si vous aviez entré `4`, le résultat serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="172b1-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="172b1-112">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="172b1-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="172b1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="172b1-113">See also</span></span>

- [<span data-ttu-id="172b1-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="172b1-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="172b1-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="172b1-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="172b1-116">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="172b1-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="172b1-117">switch</span><span class="sxs-lookup"><span data-stu-id="172b1-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
