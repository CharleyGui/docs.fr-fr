---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351477"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="bb4e7-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb4e7-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="bb4e7-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span><span class="sxs-lookup"><span data-stu-id="bb4e7-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="bb4e7-104">Converting with the Narrowing Keyword</span><span class="sxs-lookup"><span data-stu-id="bb4e7-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="bb4e7-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="bb4e7-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="bb4e7-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span><span class="sxs-lookup"><span data-stu-id="bb4e7-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="bb4e7-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span><span class="sxs-lookup"><span data-stu-id="bb4e7-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="bb4e7-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span><span class="sxs-lookup"><span data-stu-id="bb4e7-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="bb4e7-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span><span class="sxs-lookup"><span data-stu-id="bb4e7-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="bb4e7-110">The `Narrowing` keyword can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="bb4e7-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="bb4e7-111">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb4e7-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb4e7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb4e7-112">See also</span></span>

- [<span data-ttu-id="bb4e7-113">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb4e7-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="bb4e7-114">Widening</span><span class="sxs-lookup"><span data-stu-id="bb4e7-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="bb4e7-115">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="bb4e7-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="bb4e7-116">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="bb4e7-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="bb4e7-117">CType (fonction)</span><span class="sxs-lookup"><span data-stu-id="bb4e7-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="bb4e7-118">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="bb4e7-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
