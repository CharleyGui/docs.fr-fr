---
description: try-catch-finally - Référence C#
title: try-catch-finally - Référence C#
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 6e85330e12c53e0728ef671530709748090ebe02
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142009"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="91024-103">try-catch-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="91024-103">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="91024-104">`catch` et `finally` sont souvent utilisés ensemble pour obtenir et utiliser des ressources dans un bloc `try`, pour traiter des circonstances exceptionnelles dans un bloc `catch` et pour libérer les ressources dans le bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="91024-104">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="91024-105">Pour plus d’informations et des exemples sur la génération répétée d’exceptions, consultez [try-catch](try-catch.md) et [Génération d’exceptions](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="91024-105">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="91024-106">Pour plus d’informations sur le bloc `finally`, consultez [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="91024-106">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="91024-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="91024-107">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="91024-108">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="91024-108">C# language specification</span></span>

<span data-ttu-id="91024-109">Pour plus d’informations, consultez la section [Instruction try](~/_csharplang/spec/statements.md#the-try-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="91024-109">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91024-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91024-110">See also</span></span>

- [<span data-ttu-id="91024-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="91024-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="91024-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="91024-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="91024-113">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="91024-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="91024-114">Instructions try, throw et catch (C++)</span><span class="sxs-lookup"><span data-stu-id="91024-114">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="91024-115">throw</span><span class="sxs-lookup"><span data-stu-id="91024-115">throw</span></span>](throw.md)
- [<span data-ttu-id="91024-116">Comment : lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="91024-116">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="91024-117">using, instruction</span><span class="sxs-lookup"><span data-stu-id="91024-117">using Statement</span></span>](using-statement.md)
