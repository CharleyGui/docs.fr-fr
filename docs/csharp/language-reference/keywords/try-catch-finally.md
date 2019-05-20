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
ms.openlocfilehash: 66f24994c7fcd2037887507bae65f590e4f90019
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633878"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="3c28a-102">try-catch-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3c28a-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="3c28a-103">`catch` et `finally` sont souvent utilisés ensemble pour obtenir et utiliser des ressources dans un bloc `try`, pour traiter des circonstances exceptionnelles dans un bloc `catch` et pour libérer les ressources dans le bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="3c28a-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="3c28a-104">Pour plus d’informations et des exemples sur la génération répétée d’exceptions, consultez [try-catch](try-catch.md) et [Génération d’exceptions](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="3c28a-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="3c28a-105">Pour plus d’informations sur le bloc `finally`, consultez [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="3c28a-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c28a-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c28a-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="3c28a-107">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3c28a-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3c28a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c28a-108">See also</span></span>

- [<span data-ttu-id="3c28a-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3c28a-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3c28a-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3c28a-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3c28a-111">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3c28a-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3c28a-112">Instructions try, throw et catch (C++)</span><span class="sxs-lookup"><span data-stu-id="3c28a-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="3c28a-113">Instructions de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="3c28a-113">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="3c28a-114">throw</span><span class="sxs-lookup"><span data-stu-id="3c28a-114">throw</span></span>](throw.md)
- [<span data-ttu-id="3c28a-115">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="3c28a-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="3c28a-116">using, instruction</span><span class="sxs-lookup"><span data-stu-id="3c28a-116">using Statement</span></span>](using-statement.md)
