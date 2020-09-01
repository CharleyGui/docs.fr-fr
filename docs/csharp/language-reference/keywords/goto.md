---
description: goto, instruction - Référence C#
title: goto, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128424"
---
# <a name="goto-c-reference"></a><span data-ttu-id="7cf58-103">goto (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7cf58-103">goto (C# Reference)</span></span>

<span data-ttu-id="7cf58-104">L’instruction `goto` transfère le contrôle du programme directement à une instruction étiquetée.</span><span class="sxs-lookup"><span data-stu-id="7cf58-104">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="7cf58-105">Une utilisation courante de `goto` consiste à transférer le contrôle à une étiquette switch-case ou à l’étiquette par défaut d’une instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="7cf58-105">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="7cf58-106">L’instruction `goto` sert aussi à quitter des boucles fortement imbriquées.</span><span class="sxs-lookup"><span data-stu-id="7cf58-106">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="7cf58-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7cf58-107">Example</span></span>

<span data-ttu-id="7cf58-108">L’exemple suivant montre comment utiliser `goto` dans une instruction [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="7cf58-108">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="7cf58-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="7cf58-109">Example</span></span>

<span data-ttu-id="7cf58-110">L’exemple suivant montre comment utiliser `goto` pour quitter des boucles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="7cf58-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="7cf58-111">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7cf58-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7cf58-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cf58-112">See also</span></span>

- [<span data-ttu-id="7cf58-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7cf58-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7cf58-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7cf58-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7cf58-115">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="7cf58-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7cf58-116">goto, instruction (C++)</span><span class="sxs-lookup"><span data-stu-id="7cf58-116">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
