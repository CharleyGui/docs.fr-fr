---
title: +=, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372205"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="15c28-102">+= (opérateur Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15c28-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="15c28-103">Ajoute la valeur d’une expression numérique à la valeur d’une variable ou d’une propriété numérique et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="15c28-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="15c28-104">Peut également être utilisé pour concaténer une `String` expression à une `String` variable ou une propriété et assigner le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="15c28-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c28-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15c28-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="15c28-106">Éléments</span><span class="sxs-lookup"><span data-stu-id="15c28-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="15c28-107">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="15c28-107">Required.</span></span> <span data-ttu-id="15c28-108">Toute variable ou `String` propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="15c28-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="15c28-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="15c28-109">Required.</span></span> <span data-ttu-id="15c28-110">Toute expression ou numérique `String` .</span><span class="sxs-lookup"><span data-stu-id="15c28-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15c28-111">Notes</span><span class="sxs-lookup"><span data-stu-id="15c28-111">Remarks</span></span>  
 <span data-ttu-id="15c28-112">L’élément situé à gauche de l' `+=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="15c28-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="15c28-113">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="15c28-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="15c28-114">L' `+=` opérateur ajoute la valeur à droite à la variable ou à la propriété à sa gauche, et assigne le résultat à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="15c28-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="15c28-115">L' `+=` opérateur peut également être utilisé pour concaténer l' `String` expression à droite à la `String` variable ou à la propriété à sa gauche, et assigner le résultat à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="15c28-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15c28-116">Lorsque vous utilisez l' `+=` opérateur, vous ne pourrez peut-être pas déterminer si l’addition ou la concaténation de chaînes aura lieu.</span><span class="sxs-lookup"><span data-stu-id="15c28-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="15c28-117">Utilisez l' `&=` opérateur pour la concaténation afin d’éliminer toute ambiguïté et de fournir du code auto-documenté.</span><span class="sxs-lookup"><span data-stu-id="15c28-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="15c28-118">Cet opérateur d’assignation effectue implicitement des conversions étendues mais non restrictives si l’environnement de compilation impose une sémantique stricte.</span><span class="sxs-lookup"><span data-stu-id="15c28-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="15c28-119">Pour plus d’informations sur ces conversions, consultez [élargissement et conversions restrictives](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="15c28-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="15c28-120">Pour plus d’informations sur la sémantique stricte et permissive, consultez [Option Strict Statement](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="15c28-120">For more information on strict and permissive semantics, see [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="15c28-121">Si la sémantique permissive est autorisée, l' `+=` opérateur effectue implicitement une variété de conversions de chaîne et numériques identiques à celles effectuées par l' `+` opérateur.</span><span class="sxs-lookup"><span data-stu-id="15c28-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="15c28-122">Pour plus d’informations sur ces conversions, consultez [opérateur +](addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="15c28-122">For details on these conversions, see [+ Operator](addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="15c28-123">Surcharge</span><span class="sxs-lookup"><span data-stu-id="15c28-123">Overloading</span></span>  
 <span data-ttu-id="15c28-124">L' `+` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="15c28-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="15c28-125">La surcharge de l' `+` opérateur affecte le comportement de l' `+=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="15c28-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="15c28-126">Si votre code utilise `+=` sur une classe ou une structure qui surcharge `+` , assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="15c28-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="15c28-127">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="15c28-127">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15c28-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="15c28-128">Example</span></span>  
 <span data-ttu-id="15c28-129">L’exemple suivant utilise l' `+=` opérateur pour combiner la valeur d’une variable à une autre.</span><span class="sxs-lookup"><span data-stu-id="15c28-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="15c28-130">La première partie utilise `+=` des variables numériques pour ajouter une valeur à une autre.</span><span class="sxs-lookup"><span data-stu-id="15c28-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="15c28-131">La deuxième partie utilise `+=` avec des `String` variables pour concaténer une valeur avec une autre.</span><span class="sxs-lookup"><span data-stu-id="15c28-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="15c28-132">Dans les deux cas, le résultat est affecté à la première variable.</span><span class="sxs-lookup"><span data-stu-id="15c28-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="15c28-133">La valeur de `num1` est maintenant 13 et la valeur de `str1` est maintenant « 103 ».</span><span class="sxs-lookup"><span data-stu-id="15c28-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c28-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15c28-134">See also</span></span>

- [<span data-ttu-id="15c28-135">Opérateur +</span><span class="sxs-lookup"><span data-stu-id="15c28-135">+ Operator</span></span>](addition-operator.md)
- [<span data-ttu-id="15c28-136">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="15c28-136">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="15c28-137">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="15c28-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="15c28-138">Opérateurs de concaténation</span><span class="sxs-lookup"><span data-stu-id="15c28-138">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="15c28-139">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15c28-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="15c28-140">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="15c28-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="15c28-141">Instructions</span><span class="sxs-lookup"><span data-stu-id="15c28-141">Statements</span></span>](../../programming-guide/language-features/statements.md)
