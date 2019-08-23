---
title: '\, opérateur (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 276071fef3632d1a617f177b6fe18026b290103a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917236"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="77d4d-102">\, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77d4d-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="77d4d-103">Divise deux nombres et retourne un résultat entier.</span><span class="sxs-lookup"><span data-stu-id="77d4d-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77d4d-104">Syntax</span></span>  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="77d4d-105">Composants</span><span class="sxs-lookup"><span data-stu-id="77d4d-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="77d4d-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="77d4d-106">Required.</span></span> <span data-ttu-id="77d4d-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="77d4d-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="77d4d-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="77d4d-108">Required.</span></span> <span data-ttu-id="77d4d-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="77d4d-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="77d4d-110">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="77d4d-110">Supported Types</span></span>  
 <span data-ttu-id="77d4d-111">Tous les types numériques, y compris les types `Decimal`à virgule flottante non signée et.</span><span class="sxs-lookup"><span data-stu-id="77d4d-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="77d4d-112">Résultat</span><span class="sxs-lookup"><span data-stu-id="77d4d-112">Result</span></span>  
 <span data-ttu-id="77d4d-113">Le résultat est le quotient entier de `expression1` divisé par `expression2`, qui ignore tout reste et conserve uniquement la partie entière.</span><span class="sxs-lookup"><span data-stu-id="77d4d-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="77d4d-114">C’est ce quel’on appelle la troncation.</span><span class="sxs-lookup"><span data-stu-id="77d4d-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="77d4d-115">Le type de données de résultat est un type numérique approprié pour les types `expression1` de `expression2`données de et.</span><span class="sxs-lookup"><span data-stu-id="77d4d-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="77d4d-116">Consultez les tables «arithmétiques sur les entiers» dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="77d4d-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="77d4d-117">L' [opérateur/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retourne le quotient complet, qui conserve le reste dans la partie fractionnaire.</span><span class="sxs-lookup"><span data-stu-id="77d4d-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d4d-118">Notes</span><span class="sxs-lookup"><span data-stu-id="77d4d-118">Remarks</span></span>  
 <span data-ttu-id="77d4d-119">Avant d’effectuer la Division, Visual Basic tente de convertir une expression numérique à virgule flottante en `Long`.</span><span class="sxs-lookup"><span data-stu-id="77d4d-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="77d4d-120">Si `Option Strict` est`On`, une erreur de compilateur se produit.</span><span class="sxs-lookup"><span data-stu-id="77d4d-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="77d4d-121">Si `Option Strict` est `Off`, un<xref:System.OverflowException> est possible si la valeur est en dehors de la plage du [type de données long](../../../visual-basic/language-reference/data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="77d4d-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="77d4d-122">La conversion vers `Long` est également soumise à l' *arrondi bancaire*.</span><span class="sxs-lookup"><span data-stu-id="77d4d-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="77d4d-123">Pour plus d’informations, consultez «parties fractionnaires» dans les [fonctions de conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="77d4d-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="77d4d-124">Si `expression1` ou`expression2` a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), il est traité comme zéro.</span><span class="sxs-lookup"><span data-stu-id="77d4d-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="77d4d-125">Division par zéro</span><span class="sxs-lookup"><span data-stu-id="77d4d-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="77d4d-126">Si `expression2` la valeur de est égale à `\` zéro, l’opérateur <xref:System.DivideByZeroException> lève une exception.</span><span class="sxs-lookup"><span data-stu-id="77d4d-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="77d4d-127">Cela est vrai pour tous les types de données numériques des opérandes.</span><span class="sxs-lookup"><span data-stu-id="77d4d-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77d4d-128">L' `\` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="77d4d-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="77d4d-129">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="77d4d-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="77d4d-130">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="77d4d-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77d4d-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="77d4d-131">Example</span></span>  
 <span data-ttu-id="77d4d-132">L’exemple suivant utilise l' `\` opérateur pour effectuer une division d’entier.</span><span class="sxs-lookup"><span data-stu-id="77d4d-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="77d4d-133">Le résultat est un entier qui représente le quotient entier des deux opérandes, le reste étant ignoré.</span><span class="sxs-lookup"><span data-stu-id="77d4d-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="77d4d-134">Dans l’exemple précédent, les expressions retournent respectivement les valeurs 2, 3, 33 et-22.</span><span class="sxs-lookup"><span data-stu-id="77d4d-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d4d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77d4d-135">See also</span></span>

- [<span data-ttu-id="77d4d-136">\\= (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="77d4d-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="77d4d-137">/, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77d4d-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="77d4d-138">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="77d4d-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="77d4d-139">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="77d4d-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="77d4d-140">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77d4d-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="77d4d-141">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="77d4d-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="77d4d-142">Opérateurs arithmétiques dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77d4d-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
