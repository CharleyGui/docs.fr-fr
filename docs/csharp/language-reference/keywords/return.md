---
title: return, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713129"
---
# <a name="return-c-reference"></a><span data-ttu-id="b26f4-102">return (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b26f4-102">return (C# Reference)</span></span>

<span data-ttu-id="b26f4-103">L’instruction `return` met un terme à l’exécution de la méthode dans laquelle elle apparaît et retourne le contrôle à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="b26f4-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="b26f4-104">Elle peut également retourner une valeur facultative.</span><span class="sxs-lookup"><span data-stu-id="b26f4-104">It can also return an optional value.</span></span> <span data-ttu-id="b26f4-105">Si la méthode est un type `void`, l’instruction `return` peut être omise.</span><span class="sxs-lookup"><span data-stu-id="b26f4-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="b26f4-106">Si l’instruction return est à l’intérieur d’un bloc `try`, le bloc `finally`, le cas échéant, est exécuté avant que le contrôle retourne à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="b26f4-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="b26f4-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b26f4-107">Example</span></span>

 <span data-ttu-id="b26f4-108">Dans l’exemple suivant, la méthode `CalculateArea()` retourne la variable locale `area` en tant que valeur `double`.</span><span class="sxs-lookup"><span data-stu-id="b26f4-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="b26f4-109">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b26f4-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b26f4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b26f4-110">See also</span></span>

- [<span data-ttu-id="b26f4-111">Référence C</span><span class="sxs-lookup"><span data-stu-id="b26f4-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b26f4-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b26f4-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b26f4-113">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b26f4-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b26f4-114">Déclaration de retour</span><span class="sxs-lookup"><span data-stu-id="b26f4-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
