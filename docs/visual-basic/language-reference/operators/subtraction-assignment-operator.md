---
title: -=, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: f857c8bf2f89120e047c49674ce9e8a3bff22f7d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701314"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="34939-102">-=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34939-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="34939-103">Soustrait la valeur d’une expression de la valeur d’une variable ou d’une propriété et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="34939-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34939-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34939-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="34939-105">Composants</span><span class="sxs-lookup"><span data-stu-id="34939-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="34939-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="34939-106">Required.</span></span> <span data-ttu-id="34939-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="34939-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="34939-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="34939-108">Required.</span></span> <span data-ttu-id="34939-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="34939-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34939-110">Notes</span><span class="sxs-lookup"><span data-stu-id="34939-110">Remarks</span></span>  
 <span data-ttu-id="34939-111">L’élément situé à gauche de l’opérateur `-=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="34939-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="34939-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="34939-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="34939-113">L’opérateur `-=` soustrait d’abord la valeur de l’expression (sur le côté droit de l’opérateur) de la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="34939-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="34939-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="34939-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="34939-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="34939-115">Overloading</span></span>  
 <span data-ttu-id="34939-116">L' [opérateur-(Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="34939-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="34939-117">La surcharge de l’opérateur `-` affecte le comportement de l’opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="34939-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="34939-118">Si votre code utilise `-=` sur une classe ou une structure qui surcharge `-`, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="34939-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="34939-119">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="34939-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34939-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="34939-120">Example</span></span>  
 <span data-ttu-id="34939-121">L’exemple suivant utilise l’opérateur `-=` pour soustraire une variable `Integer` d’une autre et assigner le résultat à cette dernière variable.</span><span class="sxs-lookup"><span data-stu-id="34939-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="34939-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34939-122">See also</span></span>

- [<span data-ttu-id="34939-123">-, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34939-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="34939-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="34939-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="34939-125">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="34939-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="34939-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34939-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="34939-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="34939-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="34939-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="34939-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
