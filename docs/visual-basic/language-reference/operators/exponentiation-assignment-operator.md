---
title: ^=, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: a956ffdaa3456ed09443f25c3383b6aab52fb5bf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867063"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="72e69-102">^=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72e69-102">^= Operator (Visual Basic)</span></span>

<span data-ttu-id="72e69-103">Élève la valeur d’une variable ou d’une propriété à la puissance d’une expression et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="72e69-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72e69-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="72e69-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="72e69-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="72e69-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="72e69-106">Required.</span></span> <span data-ttu-id="72e69-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="72e69-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="72e69-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="72e69-108">Required.</span></span> <span data-ttu-id="72e69-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="72e69-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72e69-110">Notes</span><span class="sxs-lookup"><span data-stu-id="72e69-110">Remarks</span></span>  

 <span data-ttu-id="72e69-111">L’élément situé à gauche de l' `^=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="72e69-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="72e69-112">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="72e69-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="72e69-113">L' `^=` opérateur commence par déclencher la valeur de la variable ou de la propriété (sur le côté gauche de l’opérateur) à la puissance de la valeur de l’expression (sur le côté droit de l’opérateur).</span><span class="sxs-lookup"><span data-stu-id="72e69-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="72e69-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="72e69-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="72e69-115">Visual Basic effectue toujours une élévation à la puissance dans le [type de données double](../data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="72e69-115">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span> <span data-ttu-id="72e69-116">Les opérandes de tout type différent sont convertis en `Double` , et le résultat est toujours `Double` .</span><span class="sxs-lookup"><span data-stu-id="72e69-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="72e69-117">La valeur de `expression` peut être fractionnaire, négative ou les deux.</span><span class="sxs-lookup"><span data-stu-id="72e69-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="72e69-118">Surcharge</span><span class="sxs-lookup"><span data-stu-id="72e69-118">Overloading</span></span>  

 <span data-ttu-id="72e69-119">L' [opérateur ^](exponentiation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="72e69-119">The [^ Operator](exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="72e69-120">La surcharge de l' `^` opérateur affecte le comportement de l' `^=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="72e69-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="72e69-121">Si votre code utilise `^=` sur une classe ou une structure qui surcharge `^` , assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="72e69-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="72e69-122">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="72e69-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72e69-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="72e69-123">Example</span></span>  

 <span data-ttu-id="72e69-124">L’exemple suivant utilise l' `^=` opérateur pour élever la valeur d’une `Integer` variable à la puissance d’une deuxième variable et assigner le résultat à la première variable.</span><span class="sxs-lookup"><span data-stu-id="72e69-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="72e69-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72e69-125">See also</span></span>

- [<span data-ttu-id="72e69-126">^ (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="72e69-126">^ Operator</span></span>](exponentiation-operator.md)
- [<span data-ttu-id="72e69-127">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="72e69-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="72e69-128">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="72e69-128">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="72e69-129">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72e69-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="72e69-130">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="72e69-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="72e69-131">Publication</span><span class="sxs-lookup"><span data-stu-id="72e69-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
