---
title: try-finally - Référence C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713012"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="44f53-102">try-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="44f53-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="44f53-103">En utilisant un bloc `finally`, vous pouvez nettoyer toutes les ressources allouées dans un bloc [try](try-catch.md) et vous pouvez exécuter du code même si une exception se produit dans le bloc `try`.</span><span class="sxs-lookup"><span data-stu-id="44f53-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="44f53-104">En règle générale, les instructions d’un bloc `finally` s’exécutent lorsque le contrôle quitte une instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="44f53-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="44f53-105">Le transfert de contrôle peut se produire suite à une exécution normale, à l’exécution d’une instruction `break`, `continue`, `goto` ou `return`, ou à la propagation d’une exception hors de l’instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="44f53-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="44f53-106">Dans une exception gérée, le bloc `finally` associé est assuré d’être exécuté.</span><span class="sxs-lookup"><span data-stu-id="44f53-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="44f53-107">Toutefois, si l’exception n’est pas gérée, l’exécution du bloc `finally` dépend de la manière dont l’opération de déroulement d’exception est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="44f53-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="44f53-108">Ceci, à son tour, dépend du paramétrage de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="44f53-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="44f53-109">En général, lorsqu’une exception non gérée met fin à une application, que le bloc `finally` soit exécuté ou non n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="44f53-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="44f53-110">Toutefois, si vous avez des instructions dans un bloc `finally` qui doivent être exécutées même dans cette situation, une solution consiste à ajouter un bloc `catch` à l’instruction `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="44f53-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="44f53-111">Ou bien, vous pouvez intercepter l’exception qui peut être levée dans le bloc `try` d’une instruction `try`-`finally` plus haut dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="44f53-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="44f53-112">Autrement dit, vous pouvez intercepter l’exception dans la méthode qui appelle la méthode contenant l’instruction `try`-`finally`, ou dans la méthode qui appelle cette méthode, ou dans n’importe quelle méthode figurant dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="44f53-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="44f53-113">Si l’exception n’est pas interceptée, l’exécution du bloc `finally` varie selon que le système d’exploitation choisit de déclencher une opération de déroulement d’exception.</span><span class="sxs-lookup"><span data-stu-id="44f53-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="44f53-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="44f53-114">Example</span></span>

<span data-ttu-id="44f53-115">Dans l’exemple suivant, une instruction de conversion non valide provoque une exception `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="44f53-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="44f53-116">L’exception n’est pas gérée.</span><span class="sxs-lookup"><span data-stu-id="44f53-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="44f53-117">Dans l’exemple suivant, une exception issue de la méthode `TryCast` est interceptée dans une méthode plus loin dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="44f53-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="44f53-118">Pour plus d’informations sur `finally`, consultez [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="44f53-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="44f53-119">C# contient également l’[instruction using](using-statement.md), qui fournit des fonctionnalités similaires pour les objets <xref:System.IDisposable> dans une syntaxe pratique.</span><span class="sxs-lookup"><span data-stu-id="44f53-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="44f53-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="44f53-120">C# language specification</span></span>

<span data-ttu-id="44f53-121">Pour plus d’informations, consultez la section [Instruction try](~/_csharplang/spec/statements.md#the-try-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="44f53-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44f53-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44f53-122">See also</span></span>

- [<span data-ttu-id="44f53-123">Référence C</span><span class="sxs-lookup"><span data-stu-id="44f53-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="44f53-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="44f53-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="44f53-125">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="44f53-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="44f53-126">Instructions try, throw et catch (C++)</span><span class="sxs-lookup"><span data-stu-id="44f53-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="44f53-127">Jeter</span><span class="sxs-lookup"><span data-stu-id="44f53-127">throw</span></span>](throw.md)
- [<span data-ttu-id="44f53-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="44f53-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="44f53-129">Comment : Jeter explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="44f53-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
