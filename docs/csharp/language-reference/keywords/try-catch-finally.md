---
title: try-catch-finally - Référence C#
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713038"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="21c88-102">try-catch-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="21c88-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="21c88-103">`catch` et `finally` sont souvent utilisés ensemble pour obtenir et utiliser des ressources dans un bloc `try`, pour traiter des circonstances exceptionnelles dans un bloc `catch` et pour libérer les ressources dans le bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="21c88-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="21c88-104">Pour plus d’informations et des exemples sur la génération répétée d’exceptions, consultez [try-catch](try-catch.md) et [Génération d’exceptions](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="21c88-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="21c88-105">Pour plus d’informations sur le bloc `finally`, consultez [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="21c88-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="21c88-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="21c88-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="21c88-107">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="21c88-107">C# language specification</span></span>

<span data-ttu-id="21c88-108">Pour plus d’informations, consultez la section [Instruction try](~/_csharplang/spec/statements.md#the-try-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="21c88-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21c88-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21c88-109">See also</span></span>

- [<span data-ttu-id="21c88-110">Référence C</span><span class="sxs-lookup"><span data-stu-id="21c88-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="21c88-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="21c88-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="21c88-112">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="21c88-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="21c88-113">Instructions try, throw et catch (C++)</span><span class="sxs-lookup"><span data-stu-id="21c88-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="21c88-114">Jeter</span><span class="sxs-lookup"><span data-stu-id="21c88-114">throw</span></span>](throw.md)
- [<span data-ttu-id="21c88-115">Comment : Jeter explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="21c88-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="21c88-116">à l’aide de l’Énoncé</span><span class="sxs-lookup"><span data-stu-id="21c88-116">using Statement</span></span>](using-statement.md)
