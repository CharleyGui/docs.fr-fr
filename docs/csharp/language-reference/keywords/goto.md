---
title: goto, instruction - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 675893f02a0022b403d2afc018d24d6f826b8f75
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421808"
---
# <a name="goto-c-reference"></a><span data-ttu-id="e5d4c-102">goto (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e5d4c-102">goto (C# Reference)</span></span>

<span data-ttu-id="e5d4c-103">L’instruction `goto` transfère le contrôle du programme directement à une instruction étiquetée.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="e5d4c-104">Une utilisation courante de `goto` consiste à transférer le contrôle à une étiquette switch-case ou à l’étiquette par défaut d’une instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="e5d4c-105">L’instruction `goto` sert aussi à quitter des boucles fortement imbriquées.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="e5d4c-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5d4c-106">Example</span></span>

<span data-ttu-id="e5d4c-107">L’exemple suivant montre comment utiliser `goto` dans une instruction [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="e5d4c-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="e5d4c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5d4c-108">Example</span></span>

<span data-ttu-id="e5d4c-109">L’exemple suivant montre comment utiliser `goto` pour quitter des boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="e5d4c-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e5d4c-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e5d4c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5d4c-111">See also</span></span>

- [<span data-ttu-id="e5d4c-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="e5d4c-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e5d4c-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e5d4c-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e5d4c-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="e5d4c-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e5d4c-115">goto, instruction (C++)</span><span class="sxs-lookup"><span data-stu-id="e5d4c-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
