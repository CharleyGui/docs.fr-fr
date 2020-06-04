---
title: Mod, opérateur
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: 32065567799b023556a018ae2f5ba338796e0b49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401509"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="c6924-102">Mod, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6924-102">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="c6924-103">Divise deux nombres et retourne uniquement le reste.</span><span class="sxs-lookup"><span data-stu-id="c6924-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6924-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6924-104">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="c6924-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="c6924-105">Parts</span></span>

`result` \
<span data-ttu-id="c6924-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c6924-106">Required.</span></span> <span data-ttu-id="c6924-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="c6924-107">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="c6924-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c6924-108">Required.</span></span> <span data-ttu-id="c6924-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="c6924-109">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="c6924-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c6924-110">Required.</span></span> <span data-ttu-id="c6924-111">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="c6924-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="c6924-112">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="c6924-112">Supported types</span></span>

<span data-ttu-id="c6924-113">tous les types numériques</span><span class="sxs-lookup"><span data-stu-id="c6924-113">All numeric types.</span></span> <span data-ttu-id="c6924-114">Cela comprend les types à virgule flottante non signée et `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="c6924-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="c6924-115">Résultats</span><span class="sxs-lookup"><span data-stu-id="c6924-115">Result</span></span>

<span data-ttu-id="c6924-116">Le résultat est le reste de la `number1` Division de par `number2` .</span><span class="sxs-lookup"><span data-stu-id="c6924-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="c6924-117">Par exemple, l’expression `14 Mod 4` prend la valeur 2.</span><span class="sxs-lookup"><span data-stu-id="c6924-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="c6924-118">Il existe une différence entre le *reste* et le *modulo* en mathématiques, avec des résultats différents pour les nombres négatifs.</span><span class="sxs-lookup"><span data-stu-id="c6924-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="c6924-119">L' `Mod` opérateur dans Visual Basic, l' `op_Modulus` opérateur .NET Framework, et l’instruction [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) il sous-jacente effectuent toutes une opération de reste.</span><span class="sxs-lookup"><span data-stu-id="c6924-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="c6924-120">Le résultat d’une `Mod` opération conserve le signe du dividende, `number1` et peut donc être positif ou négatif.</span><span class="sxs-lookup"><span data-stu-id="c6924-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="c6924-121">Le résultat est toujours dans la plage (- `number2` , `number2` ), exclusif.</span><span class="sxs-lookup"><span data-stu-id="c6924-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="c6924-122">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6924-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="c6924-123">Notes</span><span class="sxs-lookup"><span data-stu-id="c6924-123">Remarks</span></span>

<span data-ttu-id="c6924-124">Si `number1` ou `number2` est une valeur à virgule flottante, le reste à virgule flottante de la Division est retourné.</span><span class="sxs-lookup"><span data-stu-id="c6924-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="c6924-125">Le type de données du résultat est le plus petit type de données qui peut contenir toutes les valeurs possibles qui résultent de la division avec les types de données de `number1` et `number2` .</span><span class="sxs-lookup"><span data-stu-id="c6924-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="c6924-126">Si `number1` ou `number2` a la valeur [Nothing](../nothing.md), il est traité comme zéro.</span><span class="sxs-lookup"><span data-stu-id="c6924-126">If `number1` or `number2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="c6924-127">Les opérateurs connexes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="c6924-127">Related operators include the following:</span></span>

- <span data-ttu-id="c6924-128">L' [opérateur \ (Visual Basic)](integer-division-operator.md) retourne le quotient entier d’une division.</span><span class="sxs-lookup"><span data-stu-id="c6924-128">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="c6924-129">Par exemple, l’expression `14 \ 4` prend la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="c6924-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="c6924-130">L' [opérateur/(Visual Basic)](floating-point-division-operator.md) retourne le quotient complet, y compris le reste, sous la forme d’un nombre à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="c6924-130">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="c6924-131">Par exemple, l’expression `14 / 4` prend la valeur 3,5.</span><span class="sxs-lookup"><span data-stu-id="c6924-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="c6924-132">Division par zéro</span><span class="sxs-lookup"><span data-stu-id="c6924-132">Attempted division by zero</span></span>

<span data-ttu-id="c6924-133">Si `number2` prend la valeur zéro, le comportement de l' `Mod` opérateur dépend du type de données des opérandes :</span><span class="sxs-lookup"><span data-stu-id="c6924-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>

- <span data-ttu-id="c6924-134">Une division intégrale lève une <xref:System.DivideByZeroException> exception si `number2` ne peut pas être déterminée au moment de la compilation et génère une erreur au moment de la compilation `BC30542 Division by zero occurred while evaluating this expression` si `number2` est évalué à zéro au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c6924-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="c6924-135">Une division à virgule flottante retourne <xref:System.Double.NaN?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6924-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="c6924-136">Formule équivalente</span><span class="sxs-lookup"><span data-stu-id="c6924-136">Equivalent formula</span></span>

<span data-ttu-id="c6924-137">L’expression `a Mod b` est équivalente à l’une des formules suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6924-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="c6924-138">Imprécision à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="c6924-138">Floating-point imprecision</span></span>

<span data-ttu-id="c6924-139">Lorsque vous utilisez des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours une représentation décimale précise en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c6924-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="c6924-140">Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l' `Mod` opérateur.</span><span class="sxs-lookup"><span data-stu-id="c6924-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="c6924-141">Pour plus d’informations, consultez [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="c6924-141">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="c6924-142">Surcharge</span><span class="sxs-lookup"><span data-stu-id="c6924-142">Overloading</span></span>

<span data-ttu-id="c6924-143">L' `Mod` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement.</span><span class="sxs-lookup"><span data-stu-id="c6924-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="c6924-144">Si votre code s’applique `Mod` à une instance d’une classe ou d’une structure qui comprend une telle surcharge, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="c6924-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c6924-145">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c6924-145">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="c6924-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6924-146">Example</span></span>

<span data-ttu-id="c6924-147">L’exemple suivant utilise l' `Mod` opérateur pour diviser deux nombres et retourner uniquement le reste.</span><span class="sxs-lookup"><span data-stu-id="c6924-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="c6924-148">Si un nombre est un nombre à virgule flottante, le résultat est un nombre à virgule flottante qui représente le reste.</span><span class="sxs-lookup"><span data-stu-id="c6924-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="c6924-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6924-149">Example</span></span>

<span data-ttu-id="c6924-150">L’exemple suivant illustre le imprécision potentiel des opérandes à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="c6924-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="c6924-151">Dans la première instruction, les opérandes sont `Double` et 0,2 est une fraction binaire à répétition infinie avec une valeur stockée de 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="c6924-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="c6924-152">Dans la deuxième instruction, le caractère de type de littéral `D` force les deux opérandes à `Decimal` , et 0,2 a une représentation précise.</span><span class="sxs-lookup"><span data-stu-id="c6924-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="c6924-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6924-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="c6924-154">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="c6924-154">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c6924-155">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6924-155">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="c6924-156">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="c6924-156">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="c6924-157">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="c6924-157">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="c6924-158">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6924-158">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="c6924-159">\, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6924-159">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
