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
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602249"
---
# <a name="break-c-reference"></a><span data-ttu-id="1da1b-102">break (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1da1b-102">break (C# Reference)</span></span>

<span data-ttu-id="1da1b-103">L’instruction `break` termine la boucle englobante ou l’instruction [switch](./switch.md) la plus proche dans laquelle elle figure.</span><span class="sxs-lookup"><span data-stu-id="1da1b-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="1da1b-104">Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="1da1b-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="1da1b-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="1da1b-105">Example</span></span>

<span data-ttu-id="1da1b-106">Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.</span><span class="sxs-lookup"><span data-stu-id="1da1b-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="1da1b-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="1da1b-107">Example</span></span>

<span data-ttu-id="1da1b-108">Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe.</span><span class="sxs-lookup"><span data-stu-id="1da1b-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="1da1b-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="1da1b-109">Example</span></span>

<span data-ttu-id="1da1b-110">Cet exemple illustre l’utilisation de `break` dans une instruction [switch](./switch.md).</span><span class="sxs-lookup"><span data-stu-id="1da1b-110">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="1da1b-111">Si vous aviez entré `4`, le résultat serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="1da1b-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="1da1b-112">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1da1b-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1da1b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1da1b-113">See also</span></span>

- [<span data-ttu-id="1da1b-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1da1b-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1da1b-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1da1b-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1da1b-116">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="1da1b-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="1da1b-117">switch</span><span class="sxs-lookup"><span data-stu-id="1da1b-117">switch</span></span>](./switch.md)
