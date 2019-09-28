---
title: /=, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592174"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ce070-102">/=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce070-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="ce070-103">Divise la valeur d’une variable ou d’une propriété par la valeur d’une expression et assigne le résultat à virgule flottante à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="ce070-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce070-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce070-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ce070-105">Composants</span><span class="sxs-lookup"><span data-stu-id="ce070-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ce070-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ce070-106">Required.</span></span> <span data-ttu-id="ce070-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="ce070-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ce070-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ce070-108">Required.</span></span> <span data-ttu-id="ce070-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="ce070-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce070-110">Notes</span><span class="sxs-lookup"><span data-stu-id="ce070-110">Remarks</span></span>  
 <span data-ttu-id="ce070-111">L’élément situé à gauche de l’opérateur `/=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="ce070-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ce070-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ce070-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ce070-113">L’opérateur `/=` divise d’abord la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur) par la valeur de l’expression (sur le côté droit de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="ce070-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="ce070-114">L’opérateur affecte ensuite le résultat à virgule flottante de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="ce070-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="ce070-115">Cette instruction affecte une valeur `Double` à la variable ou à la propriété située à gauche.</span><span class="sxs-lookup"><span data-stu-id="ce070-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="ce070-116">Si `Option Strict` est `On`, `variableorproperty` doit être un `Double`.</span><span class="sxs-lookup"><span data-stu-id="ce070-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="ce070-117">Si `Option Strict` est `Off`, Visual Basic effectue une conversion implicite et assigne la valeur résultante à `variableorproperty`, avec une erreur possible au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ce070-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="ce070-118">Pour plus d’informations, consultez [conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce070-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ce070-119">Surcharge</span><span class="sxs-lookup"><span data-stu-id="ce070-119">Overloading</span></span>  
 <span data-ttu-id="ce070-120">L' [opérateur/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="ce070-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ce070-121">La surcharge de l’opérateur `/` affecte le comportement de l’opérateur `/=`.</span><span class="sxs-lookup"><span data-stu-id="ce070-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="ce070-122">Si votre code utilise `/=` sur une classe ou une structure qui surcharge `/`, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="ce070-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ce070-123">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ce070-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce070-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce070-124">Example</span></span>  
 <span data-ttu-id="ce070-125">L’exemple suivant utilise l’opérateur `/=` pour diviser une variable `Integer` par une seconde et assigner le quotient à la première variable.</span><span class="sxs-lookup"><span data-stu-id="ce070-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="ce070-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce070-126">See also</span></span>

- [<span data-ttu-id="ce070-127">/, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce070-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="ce070-128">\\ =, opérateur</span><span class="sxs-lookup"><span data-stu-id="ce070-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="ce070-129">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="ce070-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="ce070-130">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="ce070-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="ce070-131">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce070-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ce070-132">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="ce070-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ce070-133">Instructions</span><span class="sxs-lookup"><span data-stu-id="ce070-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
