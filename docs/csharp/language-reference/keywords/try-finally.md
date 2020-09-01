---
description: try-finally - Référence C#
title: try-finally - Référence C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 621c5bf1607136361b72f978681607ec2aec150f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141970"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="84028-103">try-finally (référence C#)</span><span class="sxs-lookup"><span data-stu-id="84028-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="84028-104">En utilisant un bloc `finally`, vous pouvez nettoyer toutes les ressources allouées dans un bloc [try](try-catch.md) et vous pouvez exécuter du code même si une exception se produit dans le bloc `try`.</span><span class="sxs-lookup"><span data-stu-id="84028-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="84028-105">En règle générale, les instructions d’un bloc `finally` s’exécutent lorsque le contrôle quitte une instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="84028-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="84028-106">Le transfert de contrôle peut se produire suite à une exécution normale, à l’exécution d’une instruction `break`, `continue`, `goto` ou `return`, ou à la propagation d’une exception hors de l’instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="84028-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="84028-107">Dans une exception gérée, le bloc `finally` associé est assuré d’être exécuté.</span><span class="sxs-lookup"><span data-stu-id="84028-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="84028-108">Toutefois, si l’exception n’est pas gérée, l’exécution du bloc `finally` dépend de la manière dont l’opération de déroulement d’exception est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="84028-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="84028-109">Ceci, à son tour, dépend du paramétrage de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="84028-109">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="84028-110">En général, lorsqu’une exception non gérée met fin à une application, que le bloc `finally` soit exécuté ou non n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="84028-110">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="84028-111">Toutefois, si vous avez des instructions dans un bloc `finally` qui doivent être exécutées même dans cette situation, une solution consiste à ajouter un bloc `catch` à l’instruction `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="84028-111">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="84028-112">Ou bien, vous pouvez intercepter l’exception qui peut être levée dans le bloc `try` d’une instruction `try`-`finally` plus haut dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="84028-112">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="84028-113">Autrement dit, vous pouvez intercepter l’exception dans la méthode qui appelle la méthode contenant l’instruction `try`-`finally`, ou dans la méthode qui appelle cette méthode, ou dans n’importe quelle méthode figurant dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="84028-113">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="84028-114">Si l’exception n’est pas interceptée, l’exécution du bloc `finally` varie selon que le système d’exploitation choisit de déclencher une opération de déroulement d’exception.</span><span class="sxs-lookup"><span data-stu-id="84028-114">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="84028-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="84028-115">Example</span></span>

<span data-ttu-id="84028-116">Dans l’exemple suivant, une instruction de conversion non valide provoque une exception `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="84028-116">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="84028-117">L’exception n’est pas gérée.</span><span class="sxs-lookup"><span data-stu-id="84028-117">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="84028-118">Dans l’exemple suivant, une exception issue de la méthode `TryCast` est interceptée dans une méthode plus loin dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="84028-118">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="84028-119">Pour plus d’informations sur `finally`, consultez [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="84028-119">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="84028-120">C# contient également l’[instruction using](using-statement.md), qui fournit des fonctionnalités similaires pour les objets <xref:System.IDisposable> dans une syntaxe pratique.</span><span class="sxs-lookup"><span data-stu-id="84028-120">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="84028-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="84028-121">C# language specification</span></span>

<span data-ttu-id="84028-122">Pour plus d’informations, consultez la section [Instruction try](~/_csharplang/spec/statements.md#the-try-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="84028-122">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84028-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84028-123">See also</span></span>

- [<span data-ttu-id="84028-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="84028-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="84028-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="84028-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="84028-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="84028-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="84028-127">Instructions try, throw et catch (C++)</span><span class="sxs-lookup"><span data-stu-id="84028-127">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="84028-128">throw</span><span class="sxs-lookup"><span data-stu-id="84028-128">throw</span></span>](throw.md)
- [<span data-ttu-id="84028-129">try-catch</span><span class="sxs-lookup"><span data-stu-id="84028-129">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="84028-130">Comment : lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="84028-130">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
