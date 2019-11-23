---
title: Passage des arguments par position et par nom
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352617"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="74d1d-102">Passage des arguments par position et par nom (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74d1d-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="74d1d-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span><span class="sxs-lookup"><span data-stu-id="74d1d-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="74d1d-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span><span class="sxs-lookup"><span data-stu-id="74d1d-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="74d1d-105">You can supply named arguments in any order.</span><span class="sxs-lookup"><span data-stu-id="74d1d-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="74d1d-106">For example, the following `Sub` procedure takes three arguments:</span><span class="sxs-lookup"><span data-stu-id="74d1d-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="74d1d-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span><span class="sxs-lookup"><span data-stu-id="74d1d-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="74d1d-108">Passing Arguments by Position</span><span class="sxs-lookup"><span data-stu-id="74d1d-108">Passing Arguments by Position</span></span>

<span data-ttu-id="74d1d-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span><span class="sxs-lookup"><span data-stu-id="74d1d-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="74d1d-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span><span class="sxs-lookup"><span data-stu-id="74d1d-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="74d1d-111">The following example calls the `Display` method without the `age` argument:</span><span class="sxs-lookup"><span data-stu-id="74d1d-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="74d1d-112">Passing Arguments by Name</span><span class="sxs-lookup"><span data-stu-id="74d1d-112">Passing Arguments by Name</span></span>

<span data-ttu-id="74d1d-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span><span class="sxs-lookup"><span data-stu-id="74d1d-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="74d1d-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span><span class="sxs-lookup"><span data-stu-id="74d1d-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="74d1d-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span><span class="sxs-lookup"><span data-stu-id="74d1d-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="74d1d-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span><span class="sxs-lookup"><span data-stu-id="74d1d-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="74d1d-117">Mixing Arguments by Position and by Name</span><span class="sxs-lookup"><span data-stu-id="74d1d-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="74d1d-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span><span class="sxs-lookup"><span data-stu-id="74d1d-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="74d1d-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span><span class="sxs-lookup"><span data-stu-id="74d1d-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="74d1d-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span><span class="sxs-lookup"><span data-stu-id="74d1d-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="74d1d-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span><span class="sxs-lookup"><span data-stu-id="74d1d-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="74d1d-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="74d1d-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="74d1d-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span><span class="sxs-lookup"><span data-stu-id="74d1d-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="74d1d-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="74d1d-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="74d1d-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span><span class="sxs-lookup"><span data-stu-id="74d1d-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="74d1d-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="74d1d-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="74d1d-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="74d1d-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="74d1d-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span><span class="sxs-lookup"><span data-stu-id="74d1d-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="74d1d-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="74d1d-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="74d1d-130">Restrictions on Supplying Arguments by Name</span><span class="sxs-lookup"><span data-stu-id="74d1d-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="74d1d-131">You cannot pass arguments by name to avoid entering required arguments.</span><span class="sxs-lookup"><span data-stu-id="74d1d-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="74d1d-132">You can omit only the optional arguments.</span><span class="sxs-lookup"><span data-stu-id="74d1d-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="74d1d-133">You cannot pass a parameter array by name.</span><span class="sxs-lookup"><span data-stu-id="74d1d-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="74d1d-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span><span class="sxs-lookup"><span data-stu-id="74d1d-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="74d1d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74d1d-135">See also</span></span>

- [<span data-ttu-id="74d1d-136">Procédures</span><span class="sxs-lookup"><span data-stu-id="74d1d-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="74d1d-137">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="74d1d-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="74d1d-138">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="74d1d-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="74d1d-139">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="74d1d-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="74d1d-140">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="74d1d-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="74d1d-141">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="74d1d-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="74d1d-142">Optional</span><span class="sxs-lookup"><span data-stu-id="74d1d-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="74d1d-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="74d1d-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
