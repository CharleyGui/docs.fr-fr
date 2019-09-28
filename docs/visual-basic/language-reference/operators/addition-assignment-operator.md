---
title: += (opérateur Visual Basic)
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
ms.openlocfilehash: 249a19abfb08677c01ac4cc484d049a7ed1a983c
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591648"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8ca94-102">+= (opérateur Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ca94-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="8ca94-103">Ajoute la valeur d’une expression numérique à la valeur d’une variable ou d’une propriété numérique et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="8ca94-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="8ca94-104">Peut également être utilisé pour concaténer une expression `String` à une variable ou une propriété `String` et assigner le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="8ca94-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca94-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ca94-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8ca94-106">Composants</span><span class="sxs-lookup"><span data-stu-id="8ca94-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8ca94-107">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8ca94-107">Required.</span></span> <span data-ttu-id="8ca94-108">Toute variable ou propriété numérique ou `String`.</span><span class="sxs-lookup"><span data-stu-id="8ca94-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8ca94-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8ca94-109">Required.</span></span> <span data-ttu-id="8ca94-110">Toute expression numérique ou `String`.</span><span class="sxs-lookup"><span data-stu-id="8ca94-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca94-111">Notes</span><span class="sxs-lookup"><span data-stu-id="8ca94-111">Remarks</span></span>  
 <span data-ttu-id="8ca94-112">L’élément situé à gauche de l’opérateur `+=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="8ca94-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8ca94-113">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8ca94-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8ca94-114">L’opérateur `+=` ajoute la valeur à droite à la variable ou à la propriété à sa gauche, et assigne le résultat à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="8ca94-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="8ca94-115">L’opérateur `+=` peut également être utilisé pour concaténer l’expression `String` à sa droite à la variable ou à la propriété `String` à gauche, et assigner le résultat à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="8ca94-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ca94-116">Lorsque vous utilisez l’opérateur `+=`, vous ne pourrez peut-être pas déterminer si l’addition ou la concaténation de chaînes aura lieu.</span><span class="sxs-lookup"><span data-stu-id="8ca94-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="8ca94-117">Utilisez l’opérateur `&=` pour la concaténation afin d’éliminer toute ambiguïté et de fournir du code auto-documenté.</span><span class="sxs-lookup"><span data-stu-id="8ca94-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="8ca94-118">Cet opérateur d’assignation effectue implicitement des conversions étendues mais non restrictives si l’environnement de compilation impose une sémantique stricte.</span><span class="sxs-lookup"><span data-stu-id="8ca94-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="8ca94-119">Pour plus d’informations sur ces conversions, consultez [élargissement et conversions restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8ca94-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="8ca94-120">Pour plus d’informations sur la sémantique stricte et permissive, consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ca94-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="8ca94-121">Si la sémantique permissive est autorisée, l’opérateur `+=` effectue implicitement une variété de conversions de chaînes et de nombres identiques à celles effectuées par l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="8ca94-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="8ca94-122">Pour plus d’informations sur ces conversions, consultez [opérateur +](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8ca94-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8ca94-123">Surcharge</span><span class="sxs-lookup"><span data-stu-id="8ca94-123">Overloading</span></span>  
 <span data-ttu-id="8ca94-124">L’opérateur `+` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="8ca94-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8ca94-125">La surcharge de l’opérateur `+` affecte le comportement de l’opérateur `+=`.</span><span class="sxs-lookup"><span data-stu-id="8ca94-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="8ca94-126">Si votre code utilise `+=` sur une classe ou une structure qui surcharge `+`, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="8ca94-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8ca94-127">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8ca94-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca94-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ca94-128">Example</span></span>  
 <span data-ttu-id="8ca94-129">L’exemple suivant utilise l’opérateur `+=` pour combiner la valeur d’une variable à une autre.</span><span class="sxs-lookup"><span data-stu-id="8ca94-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="8ca94-130">La première partie utilise `+=` avec des variables numériques pour ajouter une valeur à une autre.</span><span class="sxs-lookup"><span data-stu-id="8ca94-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="8ca94-131">La deuxième partie utilise `+=` avec des variables de `String` pour concaténer une valeur avec une autre.</span><span class="sxs-lookup"><span data-stu-id="8ca94-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="8ca94-132">Dans les deux cas, le résultat est affecté à la première variable.</span><span class="sxs-lookup"><span data-stu-id="8ca94-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="8ca94-133">La valeur de `num1` est maintenant 13 et la valeur de `str1` est désormais « 103 ».</span><span class="sxs-lookup"><span data-stu-id="8ca94-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca94-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ca94-134">See also</span></span>

- [<span data-ttu-id="8ca94-135">+, opérateur</span><span class="sxs-lookup"><span data-stu-id="8ca94-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="8ca94-136">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="8ca94-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8ca94-137">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="8ca94-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="8ca94-138">opérateur de concaténation</span><span class="sxs-lookup"><span data-stu-id="8ca94-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="8ca94-139">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ca94-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8ca94-140">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="8ca94-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8ca94-141">Instructions</span><span class="sxs-lookup"><span data-stu-id="8ca94-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
