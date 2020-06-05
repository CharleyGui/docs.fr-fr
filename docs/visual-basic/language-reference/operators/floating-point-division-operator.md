---
title: /, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: e9400b50a84522f87a9a2ea4cd05b479d7a4538e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371166"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="90945-102">/, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90945-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="90945-103">Effectue la division entre deux nombres et retourne un résultat à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="90945-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90945-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90945-104">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="90945-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="90945-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="90945-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="90945-106">Required.</span></span> <span data-ttu-id="90945-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="90945-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="90945-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="90945-108">Required.</span></span> <span data-ttu-id="90945-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="90945-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="90945-110">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="90945-110">Supported Types</span></span>  
 <span data-ttu-id="90945-111">Tous les types numériques, y compris les types à virgule flottante non signée et `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="90945-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="90945-112">Résultats</span><span class="sxs-lookup"><span data-stu-id="90945-112">Result</span></span>  
 <span data-ttu-id="90945-113">Le résultat est le quotient entier de `expression1` divisé par `expression2` , y compris tout reste.</span><span class="sxs-lookup"><span data-stu-id="90945-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="90945-114">L' [opérateur \ (Visual Basic)](integer-division-operator.md) retourne le quotient entier, qui supprime le reste.</span><span class="sxs-lookup"><span data-stu-id="90945-114">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90945-115">Notes</span><span class="sxs-lookup"><span data-stu-id="90945-115">Remarks</span></span>  
 <span data-ttu-id="90945-116">Le type de données du résultat dépend des types des opérandes.</span><span class="sxs-lookup"><span data-stu-id="90945-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="90945-117">Le tableau suivant montre comment le type de données du résultat est déterminé.</span><span class="sxs-lookup"><span data-stu-id="90945-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="90945-118">Types de données des opérandes</span><span class="sxs-lookup"><span data-stu-id="90945-118">Operand data types</span></span>|<span data-ttu-id="90945-119">Type de données de résultat</span><span class="sxs-lookup"><span data-stu-id="90945-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="90945-120">Les deux expressions sont des types de données intégraux ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="90945-120">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="90945-121">Une expression est un type de données [unique](../data-types/single-data-type.md) et l’autre n’est pas un [double](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="90945-121">One expression is a [Single](../data-types/single-data-type.md) data type and the other is not a [Double](../data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="90945-122">Une expression est un type de données [décimal](../data-types/decimal-data-type.md) et l’autre n’est pas un [Single](../data-types/single-data-type.md) ou un [double](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="90945-122">One expression is a [Decimal](../data-types/decimal-data-type.md) data type and the other is not a [Single](../data-types/single-data-type.md) or a [Double](../data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="90945-123">L’une des expressions est un type de données [double](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="90945-123">Either expression is a [Double](../data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="90945-124">Avant l’exécution de la Division, toutes les expressions numériques entières sont élargies à `Double` .</span><span class="sxs-lookup"><span data-stu-id="90945-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="90945-125">Si vous assignez le résultat à un type de données intégral, Visual Basic tente de convertir le résultat de `Double` en ce type.</span><span class="sxs-lookup"><span data-stu-id="90945-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="90945-126">Cela peut lever une exception si le résultat ne tient pas dans ce type.</span><span class="sxs-lookup"><span data-stu-id="90945-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="90945-127">En particulier, consultez « tentative de division par zéro » dans cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="90945-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="90945-128">Si `expression1` ou `expression2` a la valeur [Nothing](../nothing.md), il est traité comme zéro.</span><span class="sxs-lookup"><span data-stu-id="90945-128">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="90945-129">Division par zéro</span><span class="sxs-lookup"><span data-stu-id="90945-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="90945-130">Si `expression2` la valeur de est égale à zéro, l' `/` opérateur se comporte différemment pour les différents types de données d’opérande.</span><span class="sxs-lookup"><span data-stu-id="90945-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="90945-131">Le tableau suivant présente les comportements possibles.</span><span class="sxs-lookup"><span data-stu-id="90945-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="90945-132">Types de données des opérandes</span><span class="sxs-lookup"><span data-stu-id="90945-132">Operand data types</span></span>|<span data-ttu-id="90945-133">Comportement si `expression2` est égal à zéro</span><span class="sxs-lookup"><span data-stu-id="90945-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="90945-134">Virgule flottante ( `Single` ou `Double` )</span><span class="sxs-lookup"><span data-stu-id="90945-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="90945-135">Retourne l’infini ( <xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity> ), ou <xref:System.Double.NaN> (pas un nombre) si `expression1` est également égal à zéro</span><span class="sxs-lookup"><span data-stu-id="90945-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="90945-136">Lève<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="90945-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="90945-137">Intégral (signé ou non signé)</span><span class="sxs-lookup"><span data-stu-id="90945-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="90945-138">La tentative de conversion en retour en type intégral lève une exception <xref:System.OverflowException> , car les types intégraux ne peuvent pas accepter <xref:System.Double.PositiveInfinity> , <xref:System.Double.NegativeInfinity> ou<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="90945-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="90945-139">L' `/` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="90945-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="90945-140">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="90945-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="90945-141">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="90945-141">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90945-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="90945-142">Example</span></span>  
 <span data-ttu-id="90945-143">Cet exemple utilise l' `/` opérateur pour effectuer une division à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="90945-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="90945-144">Le résultat est le quotient des deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="90945-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="90945-145">Les expressions de l’exemple précédent renvoient les valeurs 2,5 et 3,333333.</span><span class="sxs-lookup"><span data-stu-id="90945-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="90945-146">Notez que le résultat est toujours à virgule flottante ( `Double` ), même si les deux opérandes sont des constantes entières.</span><span class="sxs-lookup"><span data-stu-id="90945-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90945-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90945-147">See also</span></span>

- [<span data-ttu-id="90945-148">/=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90945-148">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="90945-149">\, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90945-149">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="90945-150">Types de données des résultats d’opérateur</span><span class="sxs-lookup"><span data-stu-id="90945-150">Data Types of Operator Results</span></span>](data-types-of-operator-results.md)
- [<span data-ttu-id="90945-151">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="90945-151">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="90945-152">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90945-152">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="90945-153">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="90945-153">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="90945-154">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90945-154">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
