---
title: goto, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715274"
---
# <a name="goto-c-reference"></a><span data-ttu-id="12bf2-102">goto (référence C#)</span><span class="sxs-lookup"><span data-stu-id="12bf2-102">goto (C# Reference)</span></span>

<span data-ttu-id="12bf2-103">L’instruction `goto` transfère le contrôle du programme directement à une instruction étiquetée.</span><span class="sxs-lookup"><span data-stu-id="12bf2-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="12bf2-104">Une utilisation courante de `goto` consiste à transférer le contrôle à une étiquette switch-case ou à l’étiquette par défaut d’une instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="12bf2-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="12bf2-105">L’instruction `goto` sert aussi à quitter des boucles fortement imbriquées.</span><span class="sxs-lookup"><span data-stu-id="12bf2-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="12bf2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="12bf2-106">Example</span></span>

<span data-ttu-id="12bf2-107">L’exemple suivant montre comment utiliser `goto` dans une instruction [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="12bf2-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="12bf2-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="12bf2-108">Example</span></span>

<span data-ttu-id="12bf2-109">L’exemple suivant montre comment utiliser `goto` pour quitter des boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="12bf2-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="12bf2-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="12bf2-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="12bf2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12bf2-111">See also</span></span>

- [<span data-ttu-id="12bf2-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="12bf2-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="12bf2-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="12bf2-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="12bf2-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="12bf2-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="12bf2-115">goto, instruction (C++)</span><span class="sxs-lookup"><span data-stu-id="12bf2-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
