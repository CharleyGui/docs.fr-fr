---
title: Constantes et types de données littérales
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 8ebecddfab0724023c269e92c1fc5534f096bf1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333732"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="c87ad-102">Constantes et types de données littérales (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c87ad-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="c87ad-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span><span class="sxs-lookup"><span data-stu-id="c87ad-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="c87ad-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span><span class="sxs-lookup"><span data-stu-id="c87ad-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="c87ad-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span><span class="sxs-lookup"><span data-stu-id="c87ad-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="c87ad-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span><span class="sxs-lookup"><span data-stu-id="c87ad-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="c87ad-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span><span class="sxs-lookup"><span data-stu-id="c87ad-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="c87ad-108">The compiler determines the type of the constant from the type of the expression.</span><span class="sxs-lookup"><span data-stu-id="c87ad-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="c87ad-109">A numeric integer literal is cast by default to the `Integer` data type.</span><span class="sxs-lookup"><span data-stu-id="c87ad-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="c87ad-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span><span class="sxs-lookup"><span data-stu-id="c87ad-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="c87ad-111">Literals and Type Coercion</span><span class="sxs-lookup"><span data-stu-id="c87ad-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="c87ad-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c87ad-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="c87ad-113">The following example produces an error:</span><span class="sxs-lookup"><span data-stu-id="c87ad-113">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="c87ad-114">The error results from the representation of the literal.</span><span class="sxs-lookup"><span data-stu-id="c87ad-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="c87ad-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span><span class="sxs-lookup"><span data-stu-id="c87ad-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="c87ad-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span><span class="sxs-lookup"><span data-stu-id="c87ad-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="c87ad-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span><span class="sxs-lookup"><span data-stu-id="c87ad-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="c87ad-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="c87ad-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c87ad-119">The following example demonstrates correct usage of type characters and enclosing characters:</span><span class="sxs-lookup"><span data-stu-id="c87ad-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c87ad-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c87ad-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="c87ad-121">Type de données</span><span class="sxs-lookup"><span data-stu-id="c87ad-121">Data type</span></span>|<span data-ttu-id="c87ad-122">Enclosing character</span><span class="sxs-lookup"><span data-stu-id="c87ad-122">Enclosing character</span></span>|<span data-ttu-id="c87ad-123">Appended type character</span><span class="sxs-lookup"><span data-stu-id="c87ad-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="c87ad-124">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-124">(none)</span></span>|<span data-ttu-id="c87ad-125">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="c87ad-126">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-126">(none)</span></span>|<span data-ttu-id="c87ad-127">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="c87ad-128">"</span><span class="sxs-lookup"><span data-stu-id="c87ad-128">"</span></span>|<span data-ttu-id="c87ad-129">C</span><span class="sxs-lookup"><span data-stu-id="c87ad-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="c87ad-130">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="c87ad-131">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-131">(none)</span></span>|<span data-ttu-id="c87ad-132">D or @</span><span class="sxs-lookup"><span data-stu-id="c87ad-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="c87ad-133">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-133">(none)</span></span>|<span data-ttu-id="c87ad-134">R or #</span><span class="sxs-lookup"><span data-stu-id="c87ad-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="c87ad-135">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-135">(none)</span></span>|<span data-ttu-id="c87ad-136">I or %</span><span class="sxs-lookup"><span data-stu-id="c87ad-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="c87ad-137">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-137">(none)</span></span>|<span data-ttu-id="c87ad-138">L or &</span><span class="sxs-lookup"><span data-stu-id="c87ad-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="c87ad-139">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-139">(none)</span></span>|<span data-ttu-id="c87ad-140">S</span><span class="sxs-lookup"><span data-stu-id="c87ad-140">S</span></span>|  
|`Single`|<span data-ttu-id="c87ad-141">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-141">(none)</span></span>|<span data-ttu-id="c87ad-142">F or !</span><span class="sxs-lookup"><span data-stu-id="c87ad-142">F or !</span></span>|  
|`String`|<span data-ttu-id="c87ad-143">"</span><span class="sxs-lookup"><span data-stu-id="c87ad-143">"</span></span>|<span data-ttu-id="c87ad-144">(aucune)</span><span class="sxs-lookup"><span data-stu-id="c87ad-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c87ad-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c87ad-145">See also</span></span>

- [<span data-ttu-id="c87ad-146">Constantes définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c87ad-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [<span data-ttu-id="c87ad-147">Guide pratique : déclarer une constante</span><span class="sxs-lookup"><span data-stu-id="c87ad-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [<span data-ttu-id="c87ad-148">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="c87ad-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="c87ad-149">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="c87ad-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c87ad-150">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="c87ad-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="c87ad-151">Vue d’ensemble des énumérations</span><span class="sxs-lookup"><span data-stu-id="c87ad-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="c87ad-152">How to: Declare an Enumeration</span><span class="sxs-lookup"><span data-stu-id="c87ad-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="c87ad-153">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="c87ad-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="c87ad-154">Types de données</span><span class="sxs-lookup"><span data-stu-id="c87ad-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c87ad-155">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="c87ad-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
