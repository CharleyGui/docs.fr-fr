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
ms.openlocfilehash: d1a46f99c21be007d33361ba095a3f0c52fe906c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701145"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="37df1-102">\, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37df1-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="37df1-103">Divise deux nombres et retourne un résultat entier.</span><span class="sxs-lookup"><span data-stu-id="37df1-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37df1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37df1-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="37df1-105">Composants</span><span class="sxs-lookup"><span data-stu-id="37df1-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="37df1-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="37df1-106">Required.</span></span> <span data-ttu-id="37df1-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="37df1-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="37df1-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="37df1-108">Required.</span></span> <span data-ttu-id="37df1-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="37df1-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="37df1-110">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="37df1-110">Supported Types</span></span>  
 <span data-ttu-id="37df1-111">Tous les types numériques, y compris les types non signés et à virgule flottante, et `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="37df1-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="37df1-112">Résultat</span><span class="sxs-lookup"><span data-stu-id="37df1-112">Result</span></span>  
 <span data-ttu-id="37df1-113">Le résultat est le quotient entier de `expression1` divisé par `expression2`, qui ignore tout reste et conserve uniquement la partie entière.</span><span class="sxs-lookup"><span data-stu-id="37df1-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="37df1-114">C’est ce que l’on appelle la *troncation*.</span><span class="sxs-lookup"><span data-stu-id="37df1-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="37df1-115">Le type de données de résultat est un type numérique approprié pour les types `expression1` de `expression2`données de et.</span><span class="sxs-lookup"><span data-stu-id="37df1-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="37df1-116">Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="37df1-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="37df1-117">L' [opérateur/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retourne le quotient complet, qui conserve le reste dans la partie fractionnaire.</span><span class="sxs-lookup"><span data-stu-id="37df1-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37df1-118">Notes</span><span class="sxs-lookup"><span data-stu-id="37df1-118">Remarks</span></span>  
 <span data-ttu-id="37df1-119">Avant d’effectuer la Division, Visual Basic tente de convertir une expression numérique à virgule flottante en `Long`.</span><span class="sxs-lookup"><span data-stu-id="37df1-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="37df1-120">Si `Option Strict` est `On`, une erreur de compilateur se produit.</span><span class="sxs-lookup"><span data-stu-id="37df1-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="37df1-121">Si `Option Strict` est `Off`, un <xref:System.OverflowException> est possible si la valeur est en dehors de la plage du [type de données long](../../../visual-basic/language-reference/data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="37df1-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="37df1-122">La conversion en `Long` est également soumise à l' *arrondi bancaire*.</span><span class="sxs-lookup"><span data-stu-id="37df1-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="37df1-123">Pour plus d’informations, consultez « parties fractionnaires » dans les [fonctions de conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="37df1-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="37df1-124">Si `expression1` ou`expression2` a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), il est traité comme zéro.</span><span class="sxs-lookup"><span data-stu-id="37df1-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="37df1-125">Division par zéro</span><span class="sxs-lookup"><span data-stu-id="37df1-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="37df1-126">Si `expression2` a la valeur zéro, l’opérateur `\` lève une exception <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="37df1-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="37df1-127">Cela est vrai pour tous les types de données numériques des opérandes.</span><span class="sxs-lookup"><span data-stu-id="37df1-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37df1-128">L’opérateur `\` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="37df1-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="37df1-129">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="37df1-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="37df1-130">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="37df1-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37df1-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="37df1-131">Example</span></span>  
 <span data-ttu-id="37df1-132">L’exemple suivant utilise l’opérateur `\` pour effectuer une division d’entier.</span><span class="sxs-lookup"><span data-stu-id="37df1-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="37df1-133">Le résultat est un entier qui représente le quotient entier des deux opérandes, le reste étant ignoré.</span><span class="sxs-lookup"><span data-stu-id="37df1-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="37df1-134">Dans l’exemple précédent, les expressions retournent respectivement les valeurs 2, 3, 33 et-22.</span><span class="sxs-lookup"><span data-stu-id="37df1-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37df1-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37df1-135">See also</span></span>

- [<span data-ttu-id="37df1-136">\\ =, opérateur</span><span class="sxs-lookup"><span data-stu-id="37df1-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="37df1-137">/, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37df1-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="37df1-138">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="37df1-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="37df1-139">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="37df1-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="37df1-140">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37df1-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="37df1-141">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="37df1-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="37df1-142">Opérateurs arithmétiques dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37df1-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
