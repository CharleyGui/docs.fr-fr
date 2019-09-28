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
ms.openlocfilehash: ca4c519dd80c07f54dc1c3dfe70daf6948446363
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591839"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c1bd1-102">=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1bd1-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="c1bd1-103">Assigne une valeur à une variable ou à une propriété.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1bd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1bd1-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="c1bd1-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c1bd1-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c1bd1-106">Toute variable accessible en écriture ou toute propriété.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="c1bd1-107">Tout littéral, constante ou expression.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1bd1-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c1bd1-108">Remarks</span></span>  
 <span data-ttu-id="c1bd1-109">L’élément situé à gauche du signe égal (`=`) peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c1bd1-110">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c1bd1-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="c1bd1-111">L’opérateur `=` assigne la valeur à droite à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1bd1-112">L’opérateur `=` est également utilisé comme opérateur de comparaison.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="c1bd1-113">Pour plus d’informations, consultez [opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c1bd1-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c1bd1-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="c1bd1-114">Overloading</span></span>  
 <span data-ttu-id="c1bd1-115">L’opérateur `=` peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="c1bd1-116">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c1bd1-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1bd1-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1bd1-117">Example</span></span>  
 <span data-ttu-id="c1bd1-118">L’exemple suivant illustre l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="c1bd1-119">La valeur à droite est assignée à la variable située à gauche.</span><span class="sxs-lookup"><span data-stu-id="c1bd1-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c1bd1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1bd1-120">See also</span></span>

- [<span data-ttu-id="c1bd1-121">&= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="c1bd1-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="c1bd1-122">\*= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="c1bd1-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="c1bd1-123">+= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="c1bd1-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="c1bd1-124">-=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1bd1-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="c1bd1-125">/=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1bd1-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="c1bd1-126">\\ =, opérateur</span><span class="sxs-lookup"><span data-stu-id="c1bd1-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="c1bd1-127">^= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="c1bd1-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="c1bd1-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="c1bd1-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="c1bd1-129">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="c1bd1-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="c1bd1-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c1bd1-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="c1bd1-131">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="c1bd1-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
