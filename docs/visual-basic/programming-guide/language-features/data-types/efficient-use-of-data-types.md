---
title: Utilisation efficace des types de données
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 621dec7537e9c993024e271b96ab8706baf89885
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350111"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="82379-102">Utilisation efficace des types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82379-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="82379-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span><span class="sxs-lookup"><span data-stu-id="82379-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="82379-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span><span class="sxs-lookup"><span data-stu-id="82379-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="82379-105">Strong Typing</span><span class="sxs-lookup"><span data-stu-id="82379-105">Strong Typing</span></span>
 <span data-ttu-id="82379-106">Specifying data types for all your variables is known as *strong typing*.</span><span class="sxs-lookup"><span data-stu-id="82379-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="82379-107">Using strong typing has several advantages:</span><span class="sxs-lookup"><span data-stu-id="82379-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="82379-108">It enables IntelliSense support for your variables.</span><span class="sxs-lookup"><span data-stu-id="82379-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="82379-109">This allows you to see their properties and other members as you type in the code.</span><span class="sxs-lookup"><span data-stu-id="82379-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="82379-110">It takes advantage of compiler type checking.</span><span class="sxs-lookup"><span data-stu-id="82379-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="82379-111">This catches statements that can fail at run time due to errors such as overflow.</span><span class="sxs-lookup"><span data-stu-id="82379-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="82379-112">It also catches calls to methods on objects that do not support them.</span><span class="sxs-lookup"><span data-stu-id="82379-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="82379-113">It results in faster execution of your code.</span><span class="sxs-lookup"><span data-stu-id="82379-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="82379-114">Most Efficient Data Types</span><span class="sxs-lookup"><span data-stu-id="82379-114">Most Efficient Data Types</span></span>
 <span data-ttu-id="82379-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span><span class="sxs-lookup"><span data-stu-id="82379-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="82379-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span><span class="sxs-lookup"><span data-stu-id="82379-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="82379-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span><span class="sxs-lookup"><span data-stu-id="82379-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="82379-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span><span class="sxs-lookup"><span data-stu-id="82379-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="82379-119">Specifying Data Type</span><span class="sxs-lookup"><span data-stu-id="82379-119">Specifying Data Type</span></span>
 <span data-ttu-id="82379-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span><span class="sxs-lookup"><span data-stu-id="82379-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="82379-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span><span class="sxs-lookup"><span data-stu-id="82379-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="82379-122">Character Conversion</span><span class="sxs-lookup"><span data-stu-id="82379-122">Character Conversion</span></span>
 <span data-ttu-id="82379-123">The `AscW` and `ChrW` functions operate in Unicode.</span><span class="sxs-lookup"><span data-stu-id="82379-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="82379-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span><span class="sxs-lookup"><span data-stu-id="82379-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="82379-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82379-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="82379-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="82379-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="82379-127">Types de données numériques</span><span class="sxs-lookup"><span data-stu-id="82379-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="82379-128">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="82379-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="82379-129">Utilisation de la fonctionnalité IntelliSense</span><span class="sxs-lookup"><span data-stu-id="82379-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
