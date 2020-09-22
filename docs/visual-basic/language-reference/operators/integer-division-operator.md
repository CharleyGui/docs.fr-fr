---
title: '\, opérateur'
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
ms.openlocfilehash: cf2dc66532925d56cea6fd141f44a245bc2dd8dd
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873395"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="6186c-102">\, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6186c-102">\ Operator (Visual Basic)</span></span>

<span data-ttu-id="6186c-103">Effectue la division entre deux nombres et retourne un résultat sous forme d'entier.</span><span class="sxs-lookup"><span data-stu-id="6186c-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6186c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6186c-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="6186c-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="6186c-105">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="6186c-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6186c-106">Required.</span></span> <span data-ttu-id="6186c-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="6186c-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="6186c-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6186c-108">Required.</span></span> <span data-ttu-id="6186c-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="6186c-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="6186c-110">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="6186c-110">Supported Types</span></span>  

 <span data-ttu-id="6186c-111">Tous les types numériques, y compris les types à virgule flottante non signée et `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="6186c-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="6186c-112">Résultats</span><span class="sxs-lookup"><span data-stu-id="6186c-112">Result</span></span>  

 <span data-ttu-id="6186c-113">Le résultat est le quotient entier de `expression1` divisé par `expression2` , qui ignore tout reste et conserve uniquement la partie entière.</span><span class="sxs-lookup"><span data-stu-id="6186c-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="6186c-114">C’est ce que l’on appelle la *troncation*.</span><span class="sxs-lookup"><span data-stu-id="6186c-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="6186c-115">Le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2` .</span><span class="sxs-lookup"><span data-stu-id="6186c-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="6186c-116">Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="6186c-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="6186c-117">L' [opérateur/(Visual Basic)](floating-point-division-operator.md) retourne le quotient complet, qui conserve le reste dans la partie fractionnaire.</span><span class="sxs-lookup"><span data-stu-id="6186c-117">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6186c-118">Notes</span><span class="sxs-lookup"><span data-stu-id="6186c-118">Remarks</span></span>  

 <span data-ttu-id="6186c-119">Avant d’effectuer la Division, Visual Basic tente de convertir une expression numérique à virgule flottante en `Long` .</span><span class="sxs-lookup"><span data-stu-id="6186c-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="6186c-120">Si `Option Strict` est `On` , une erreur de compilateur se produit.</span><span class="sxs-lookup"><span data-stu-id="6186c-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="6186c-121">Si `Option Strict` est `Off` , un <xref:System.OverflowException> est possible si la valeur est en dehors de la plage du [type de données long](../data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="6186c-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../data-types/long-data-type.md).</span></span> <span data-ttu-id="6186c-122">La conversion vers `Long` est également soumise à l' *arrondi bancaire*.</span><span class="sxs-lookup"><span data-stu-id="6186c-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="6186c-123">Pour plus d’informations, consultez « parties fractionnaires » dans les [fonctions de conversion de type](../functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6186c-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="6186c-124">Si `expression1` ou `expression2` a la valeur [Nothing](../nothing.md), il est traité comme zéro.</span><span class="sxs-lookup"><span data-stu-id="6186c-124">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="6186c-125">Division par zéro</span><span class="sxs-lookup"><span data-stu-id="6186c-125">Attempted Division by Zero</span></span>  

 <span data-ttu-id="6186c-126">Si `expression2` la valeur de est égale à zéro, l' `\` opérateur lève une <xref:System.DivideByZeroException> exception.</span><span class="sxs-lookup"><span data-stu-id="6186c-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="6186c-127">Cela est vrai pour tous les types de données numériques des opérandes.</span><span class="sxs-lookup"><span data-stu-id="6186c-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6186c-128">L' `\` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="6186c-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6186c-129">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="6186c-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6186c-130">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6186c-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6186c-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="6186c-131">Example</span></span>  

 <span data-ttu-id="6186c-132">L’exemple suivant utilise l' `\` opérateur pour effectuer une division d’entier.</span><span class="sxs-lookup"><span data-stu-id="6186c-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="6186c-133">Le résultat est un entier qui représente le quotient entier des deux opérandes, le reste étant ignoré.</span><span class="sxs-lookup"><span data-stu-id="6186c-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="6186c-134">Dans l’exemple précédent, les expressions retournent respectivement les valeurs 2, 3, 33 et-22.</span><span class="sxs-lookup"><span data-stu-id="6186c-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6186c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6186c-135">See also</span></span>

- [<span data-ttu-id="6186c-136">\\= (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="6186c-136">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="6186c-137">/, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6186c-137">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="6186c-138">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="6186c-138">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="6186c-139">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="6186c-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="6186c-140">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6186c-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="6186c-141">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="6186c-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="6186c-142">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6186c-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
