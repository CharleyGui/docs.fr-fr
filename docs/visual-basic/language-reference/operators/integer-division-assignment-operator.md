---
title: '\=, opérateur'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 600acf9b41b63358da245fe602595fee4093b15b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330943"
---
# <a name="-operator"></a><span data-ttu-id="00d74-102">\\= Operator</span><span class="sxs-lookup"><span data-stu-id="00d74-102">\\= Operator</span></span>
<span data-ttu-id="00d74-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="00d74-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00d74-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="00d74-105">Composants</span><span class="sxs-lookup"><span data-stu-id="00d74-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="00d74-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="00d74-106">Required.</span></span> <span data-ttu-id="00d74-107">Any numeric variable or property.</span><span class="sxs-lookup"><span data-stu-id="00d74-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="00d74-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="00d74-108">Required.</span></span> <span data-ttu-id="00d74-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="00d74-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00d74-110">Notes</span><span class="sxs-lookup"><span data-stu-id="00d74-110">Remarks</span></span>  
 <span data-ttu-id="00d74-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="00d74-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="00d74-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="00d74-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="00d74-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span><span class="sxs-lookup"><span data-stu-id="00d74-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="00d74-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="00d74-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="00d74-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="00d74-115">Overloading</span></span>  
 <span data-ttu-id="00d74-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="00d74-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="00d74-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span><span class="sxs-lookup"><span data-stu-id="00d74-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="00d74-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="00d74-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="00d74-119">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="00d74-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="00d74-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="00d74-120">Example</span></span>  
 <span data-ttu-id="00d74-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span><span class="sxs-lookup"><span data-stu-id="00d74-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="00d74-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00d74-122">See also</span></span>

- [<span data-ttu-id="00d74-123">\ Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00d74-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="00d74-124">/= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00d74-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="00d74-125">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="00d74-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="00d74-126">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="00d74-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="00d74-127">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00d74-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="00d74-128">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="00d74-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="00d74-129">Instructions</span><span class="sxs-lookup"><span data-stu-id="00d74-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
