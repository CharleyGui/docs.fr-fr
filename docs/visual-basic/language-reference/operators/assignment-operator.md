---
title: =, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: d260dffb7175e9dddcbf9acb75415f5f973727e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962017"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="4c6c6-102">=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="4c6c6-103">Assigne une valeur à une variable ou à une propriété.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c6c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c6c6-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="4c6c6-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4c6c6-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="4c6c6-106">Toute variable accessible en écriture ou toute propriété.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="4c6c6-107">Tout littéral, constante ou expression.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c6c6-108">Notes</span><span class="sxs-lookup"><span data-stu-id="4c6c6-108">Remarks</span></span>  
 <span data-ttu-id="4c6c6-109">L’élément situé à gauche du signe égal (`=`) peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="4c6c6-110">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="4c6c6-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="4c6c6-111">L' `=` opérateur assigne la valeur à droite à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c6c6-112">L' `=` opérateur est également utilisé comme un opérateur de comparaison.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="4c6c6-113">Pour plus d’informations, consultez [opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4c6c6-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4c6c6-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="4c6c6-114">Overloading</span></span>  
 <span data-ttu-id="4c6c6-115">L' `=` opérateur peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="4c6c6-116">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4c6c6-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c6c6-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="4c6c6-117">Example</span></span>  
 <span data-ttu-id="4c6c6-118">L’exemple suivant illustre l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="4c6c6-119">La valeur à droite est assignée à la variable située à gauche.</span><span class="sxs-lookup"><span data-stu-id="4c6c6-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="4c6c6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c6c6-120">See also</span></span>

- [<span data-ttu-id="4c6c6-121">&= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="4c6c6-122">\*= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="4c6c6-123">+= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="4c6c6-124">-=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="4c6c6-125">/=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="4c6c6-126">\\= (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="4c6c6-127">^= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4c6c6-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="4c6c6-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="4c6c6-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="4c6c6-129">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="4c6c6-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="4c6c6-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="4c6c6-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="4c6c6-131">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="4c6c6-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
