---
title: return, instruction - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661616"
---
# <a name="return-c-reference"></a><span data-ttu-id="16028-102">return (référence C#)</span><span class="sxs-lookup"><span data-stu-id="16028-102">return (C# Reference)</span></span>

<span data-ttu-id="16028-103">L’instruction `return` met un terme à l’exécution de la méthode dans laquelle elle apparaît et retourne le contrôle à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="16028-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="16028-104">Elle peut également retourner une valeur facultative.</span><span class="sxs-lookup"><span data-stu-id="16028-104">It can also return an optional value.</span></span> <span data-ttu-id="16028-105">Si la méthode est un type `void`, l’instruction `return` peut être omise.</span><span class="sxs-lookup"><span data-stu-id="16028-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="16028-106">Si l’instruction return est à l’intérieur d’un bloc `try`, le bloc `finally`, le cas échéant, est exécuté avant que le contrôle retourne à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="16028-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="16028-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="16028-107">Example</span></span>

 <span data-ttu-id="16028-108">Dans l’exemple suivant, la méthode `CalculateArea()` retourne la variable locale `area` en tant que valeur `double`.</span><span class="sxs-lookup"><span data-stu-id="16028-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="16028-109">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="16028-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="16028-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16028-110">See also</span></span>

- [<span data-ttu-id="16028-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="16028-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16028-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="16028-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16028-113">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="16028-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="16028-114">Instruction return</span><span class="sxs-lookup"><span data-stu-id="16028-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
