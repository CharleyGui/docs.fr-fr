---
title: =, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 516cb21e02d9fb2cd4b8d72282bb74163e1fb14b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371763"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="28a23-102">=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28a23-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="28a23-103">Assigne une valeur à une variable ou à une propriété.</span><span class="sxs-lookup"><span data-stu-id="28a23-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28a23-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="28a23-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="28a23-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="28a23-106">Toute variable accessible en écriture ou toute propriété.</span><span class="sxs-lookup"><span data-stu-id="28a23-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="28a23-107">Tout littéral, constante ou expression.</span><span class="sxs-lookup"><span data-stu-id="28a23-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28a23-108">Notes</span><span class="sxs-lookup"><span data-stu-id="28a23-108">Remarks</span></span>  
 <span data-ttu-id="28a23-109">L’élément situé à gauche du signe égal ( `=` ) peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="28a23-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="28a23-110">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="28a23-110">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="28a23-111">L' `=` opérateur assigne la valeur à droite à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="28a23-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28a23-112">L' `=` opérateur est également utilisé comme un opérateur de comparaison.</span><span class="sxs-lookup"><span data-stu-id="28a23-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="28a23-113">Pour plus d’informations, consultez [opérateurs de comparaison](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="28a23-113">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="28a23-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="28a23-114">Overloading</span></span>  
 <span data-ttu-id="28a23-115">L' `=` opérateur peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="28a23-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="28a23-116">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="28a23-116">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28a23-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="28a23-117">Example</span></span>  
 <span data-ttu-id="28a23-118">L’exemple suivant illustre l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="28a23-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="28a23-119">La valeur à droite est assignée à la variable située à gauche.</span><span class="sxs-lookup"><span data-stu-id="28a23-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="28a23-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28a23-120">See also</span></span>

- [<span data-ttu-id="28a23-121">&=, opérateur</span><span class="sxs-lookup"><span data-stu-id="28a23-121">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="28a23-122">\* = (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="28a23-122">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="28a23-123">Opérateur + =</span><span class="sxs-lookup"><span data-stu-id="28a23-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="28a23-124">-=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28a23-124">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="28a23-125">/=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28a23-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="28a23-126">\\= (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="28a23-126">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="28a23-127">^ = (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="28a23-127">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="28a23-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="28a23-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="28a23-129">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="28a23-129">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="28a23-130">Seulement</span><span class="sxs-lookup"><span data-stu-id="28a23-130">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="28a23-131">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="28a23-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
