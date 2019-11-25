---
title: '&amp;= Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350264"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="2c6c4-102">&amp;= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c6c4-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="2c6c4-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c6c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c6c4-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2c6c4-105">Composants</span><span class="sxs-lookup"><span data-stu-id="2c6c4-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2c6c4-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-106">Required.</span></span> <span data-ttu-id="2c6c4-107">Any `String` variable or property.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="2c6c4-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-108">Required.</span></span> <span data-ttu-id="2c6c4-109">Toute expression `String` .</span><span class="sxs-lookup"><span data-stu-id="2c6c4-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c6c4-110">Notes</span><span class="sxs-lookup"><span data-stu-id="2c6c4-110">Remarks</span></span>  
 <span data-ttu-id="2c6c4-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2c6c4-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="2c6c4-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="2c6c4-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2c6c4-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="2c6c4-114">Overloading</span></span>  
 <span data-ttu-id="2c6c4-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2c6c4-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="2c6c4-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2c6c4-118">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2c6c4-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c6c4-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="2c6c4-119">Example</span></span>  
 <span data-ttu-id="2c6c4-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span><span class="sxs-lookup"><span data-stu-id="2c6c4-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2c6c4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c6c4-121">See also</span></span>

- [<span data-ttu-id="2c6c4-122">& (opérateur)</span><span class="sxs-lookup"><span data-stu-id="2c6c4-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="2c6c4-123">+= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="2c6c4-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="2c6c4-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="2c6c4-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="2c6c4-125">opérateur de concaténation</span><span class="sxs-lookup"><span data-stu-id="2c6c4-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="2c6c4-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c6c4-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="2c6c4-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="2c6c4-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="2c6c4-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="2c6c4-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
