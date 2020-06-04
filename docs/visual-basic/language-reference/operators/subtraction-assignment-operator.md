---
title: -=, opérateur
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
ms.openlocfilehash: 4f403cd8a28f8d9d0ba1d24b0792a352a9c961db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406403"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="32699-102">-=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32699-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="32699-103">Soustrait la valeur d’une expression de la valeur d’une variable ou d’une propriété et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="32699-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32699-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32699-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="32699-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="32699-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="32699-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="32699-106">Required.</span></span> <span data-ttu-id="32699-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="32699-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="32699-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="32699-108">Required.</span></span> <span data-ttu-id="32699-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="32699-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32699-110">Notes</span><span class="sxs-lookup"><span data-stu-id="32699-110">Remarks</span></span>  
 <span data-ttu-id="32699-111">L’élément situé à gauche de l' `-=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="32699-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="32699-112">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="32699-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="32699-113">L' `-=` opérateur soustrait d’abord la valeur de l’expression (sur le côté droit de l’opérateur) de la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="32699-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="32699-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="32699-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="32699-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="32699-115">Overloading</span></span>  
 <span data-ttu-id="32699-116">L' [opérateur-(Visual Basic)](subtraction-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="32699-116">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="32699-117">La surcharge de l' `-` opérateur affecte le comportement de l' `-=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="32699-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="32699-118">Si votre code utilise `-=` sur une classe ou une structure qui surcharge `-` , assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="32699-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="32699-119">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="32699-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32699-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="32699-120">Example</span></span>  
 <span data-ttu-id="32699-121">L’exemple suivant utilise l' `-=` opérateur pour soustraire une `Integer` variable d’une autre et assigner le résultat à cette dernière variable.</span><span class="sxs-lookup"><span data-stu-id="32699-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="32699-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32699-122">See also</span></span>

- [<span data-ttu-id="32699-123">-, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32699-123">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="32699-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="32699-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="32699-125">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="32699-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="32699-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32699-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="32699-127">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="32699-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="32699-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="32699-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
