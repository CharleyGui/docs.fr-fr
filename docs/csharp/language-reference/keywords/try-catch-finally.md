---
title: try-catch-finally - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 787005ec09a2c5c4f0e5033c83fd6a7ab7875b7e
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422155"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="7ad9d-102">try-catch-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7ad9d-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="7ad9d-103">`catch` et `finally` sont souvent utilisés ensemble pour obtenir et utiliser des ressources dans un bloc `try`, pour traiter des circonstances exceptionnelles dans un bloc `catch` et pour libérer les ressources dans le bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="7ad9d-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="7ad9d-104">Pour plus d’informations et des exemples sur la génération répétée d’exceptions, consultez [try-catch](try-catch.md) et [Génération d’exceptions](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ad9d-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="7ad9d-105">Pour plus d’informations sur le bloc `finally`, consultez [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="7ad9d-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="7ad9d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ad9d-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="7ad9d-107">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7ad9d-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7ad9d-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ad9d-108">See also</span></span>

- [<span data-ttu-id="7ad9d-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7ad9d-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7ad9d-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7ad9d-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7ad9d-111">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="7ad9d-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7ad9d-112">Instructions try, throw et catch (C++)</span><span class="sxs-lookup"><span data-stu-id="7ad9d-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="7ad9d-113">throw</span><span class="sxs-lookup"><span data-stu-id="7ad9d-113">throw</span></span>](throw.md)
- [<span data-ttu-id="7ad9d-114">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="7ad9d-114">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="7ad9d-115">using, instruction</span><span class="sxs-lookup"><span data-stu-id="7ad9d-115">using Statement</span></span>](using-statement.md)
