---
title: '*=, opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 4b60fa44a92bff683e13f850da025d7fe753618d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349784"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="40a6d-102">\*=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40a6d-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="40a6d-103">Multiplie la valeur d’une variable ou d’une propriété par la valeur d’une expression et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="40a6d-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40a6d-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="40a6d-105">Composants</span><span class="sxs-lookup"><span data-stu-id="40a6d-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="40a6d-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="40a6d-106">Required.</span></span> <span data-ttu-id="40a6d-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="40a6d-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="40a6d-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="40a6d-108">Required.</span></span> <span data-ttu-id="40a6d-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="40a6d-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40a6d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="40a6d-110">Remarks</span></span>  
 <span data-ttu-id="40a6d-111">L’élément situé à gauche de l’opérateur `*=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="40a6d-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="40a6d-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="40a6d-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="40a6d-113">L’opérateur `*=` multiplie d’abord la valeur de l’expression (sur le côté droit de l’opérateur) par la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="40a6d-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="40a6d-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="40a6d-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="40a6d-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="40a6d-115">Overloading</span></span>  
 <span data-ttu-id="40a6d-116">L' [opérateur \*](../../../visual-basic/language-reference/operators/multiplication-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="40a6d-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="40a6d-117">La surcharge de l’opérateur `*` affecte le comportement de l’opérateur `*=`.</span><span class="sxs-lookup"><span data-stu-id="40a6d-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="40a6d-118">Si votre code utilise `*=` sur une classe ou une structure qui surcharge `*`, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="40a6d-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="40a6d-119">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="40a6d-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a6d-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="40a6d-120">Example</span></span>  
 <span data-ttu-id="40a6d-121">L’exemple suivant utilise l’opérateur `*=` pour multiplier une variable `Integer` par une seconde et assigner le résultat à la première variable.</span><span class="sxs-lookup"><span data-stu-id="40a6d-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="40a6d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40a6d-122">See also</span></span>

- [<span data-ttu-id="40a6d-123">\*, opérateur</span><span class="sxs-lookup"><span data-stu-id="40a6d-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="40a6d-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="40a6d-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="40a6d-125">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="40a6d-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="40a6d-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40a6d-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="40a6d-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="40a6d-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="40a6d-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="40a6d-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
