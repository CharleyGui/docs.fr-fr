---
description: return, instruction - Référence C#
title: return, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136996"
---
# <a name="return-c-reference"></a><span data-ttu-id="efe32-103">return (référence C#)</span><span class="sxs-lookup"><span data-stu-id="efe32-103">return (C# Reference)</span></span>

<span data-ttu-id="efe32-104">L’instruction `return` met un terme à l’exécution de la méthode dans laquelle elle apparaît et retourne le contrôle à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="efe32-104">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="efe32-105">Elle peut également retourner une valeur facultative.</span><span class="sxs-lookup"><span data-stu-id="efe32-105">It can also return an optional value.</span></span> <span data-ttu-id="efe32-106">Si la méthode est un type `void`, l’instruction `return` peut être omise.</span><span class="sxs-lookup"><span data-stu-id="efe32-106">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="efe32-107">Si l’instruction return est à l’intérieur d’un bloc `try`, le bloc `finally`, le cas échéant, est exécuté avant que le contrôle retourne à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="efe32-107">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="efe32-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="efe32-108">Example</span></span>

 <span data-ttu-id="efe32-109">Dans l’exemple suivant, la méthode `CalculateArea()` retourne la variable locale `area` en tant que valeur `double`.</span><span class="sxs-lookup"><span data-stu-id="efe32-109">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="efe32-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="efe32-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="efe32-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efe32-111">See also</span></span>

- [<span data-ttu-id="efe32-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="efe32-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="efe32-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="efe32-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="efe32-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="efe32-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="efe32-115">Instruction return</span><span class="sxs-lookup"><span data-stu-id="efe32-115">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
