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
ms.openlocfilehash: eccea0b43564a4980778c9d1a5b8f9a8c2a9207d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874818"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="dd944-102">=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd944-102">= Operator (Visual Basic)</span></span>

<span data-ttu-id="dd944-103">Assigne une valeur à une variable ou à une propriété.</span><span class="sxs-lookup"><span data-stu-id="dd944-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd944-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd944-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="dd944-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="dd944-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="dd944-106">Toute variable accessible en écriture ou toute propriété.</span><span class="sxs-lookup"><span data-stu-id="dd944-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="dd944-107">Tout littéral, constante ou expression.</span><span class="sxs-lookup"><span data-stu-id="dd944-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd944-108">Notes</span><span class="sxs-lookup"><span data-stu-id="dd944-108">Remarks</span></span>  

 <span data-ttu-id="dd944-109">L’élément situé à gauche du signe égal ( `=` ) peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="dd944-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="dd944-110">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="dd944-110">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="dd944-111">L' `=` opérateur assigne la valeur à droite à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="dd944-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd944-112">L' `=` opérateur est également utilisé comme un opérateur de comparaison.</span><span class="sxs-lookup"><span data-stu-id="dd944-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="dd944-113">Pour plus d’informations, consultez [opérateurs de comparaison](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="dd944-113">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="dd944-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="dd944-114">Overloading</span></span>  

 <span data-ttu-id="dd944-115">L' `=` opérateur peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="dd944-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="dd944-116">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dd944-116">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd944-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd944-117">Example</span></span>  

 <span data-ttu-id="dd944-118">L’exemple suivant illustre l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="dd944-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="dd944-119">La valeur à droite est assignée à la variable située à gauche.</span><span class="sxs-lookup"><span data-stu-id="dd944-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="dd944-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd944-120">See also</span></span>

- [<span data-ttu-id="dd944-121">&=, opérateur</span><span class="sxs-lookup"><span data-stu-id="dd944-121">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="dd944-122">\* = (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="dd944-122">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="dd944-123">Opérateur + =</span><span class="sxs-lookup"><span data-stu-id="dd944-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="dd944-124">-=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd944-124">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="dd944-125">/=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd944-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="dd944-126">\\= (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="dd944-126">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="dd944-127">^ = (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="dd944-127">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="dd944-128">Publication</span><span class="sxs-lookup"><span data-stu-id="dd944-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="dd944-129">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="dd944-129">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="dd944-130">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="dd944-130">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="dd944-131">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="dd944-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
