---
title: Opérateurs de comparaison
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: ea7604626ede66da818e4bc22fe4922bc752dc2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336082"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="26c66-102">Opérateurs de comparaison (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26c66-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="26c66-103">Voici les opérateurs de comparaison définis dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="26c66-103">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="26c66-104">opérateur `<`</span><span class="sxs-lookup"><span data-stu-id="26c66-104">`<` operator</span></span>

 <span data-ttu-id="26c66-105">opérateur `<=`</span><span class="sxs-lookup"><span data-stu-id="26c66-105">`<=` operator</span></span>

 <span data-ttu-id="26c66-106">opérateur `>`</span><span class="sxs-lookup"><span data-stu-id="26c66-106">`>` operator</span></span>

 <span data-ttu-id="26c66-107">opérateur `>=`</span><span class="sxs-lookup"><span data-stu-id="26c66-107">`>=` operator</span></span>

 <span data-ttu-id="26c66-108">opérateur `=`</span><span class="sxs-lookup"><span data-stu-id="26c66-108">`=` operator</span></span>

 <span data-ttu-id="26c66-109">opérateur `<>`</span><span class="sxs-lookup"><span data-stu-id="26c66-109">`<>` operator</span></span>

 [<span data-ttu-id="26c66-110">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="26c66-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)

 [<span data-ttu-id="26c66-111">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="26c66-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [<span data-ttu-id="26c66-112">Like (opérateur)</span><span class="sxs-lookup"><span data-stu-id="26c66-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)

 <span data-ttu-id="26c66-113">Ces opérateurs comparent deux expressions pour déterminer si elles sont égales, et dans le cas contraire, en quoi elles diffèrent.</span><span class="sxs-lookup"><span data-stu-id="26c66-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="26c66-114">`Is`, `IsNot`et `Like` sont abordés en détail sur des pages d’aide distinctes.</span><span class="sxs-lookup"><span data-stu-id="26c66-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="26c66-115">Les opérateurs de comparaison relationnels sont décrits en détail dans cette page.</span><span class="sxs-lookup"><span data-stu-id="26c66-115">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="26c66-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26c66-116">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="26c66-117">Composants</span><span class="sxs-lookup"><span data-stu-id="26c66-117">Parts</span></span>
 `result`  
 <span data-ttu-id="26c66-118">Requis.</span><span class="sxs-lookup"><span data-stu-id="26c66-118">Required.</span></span> <span data-ttu-id="26c66-119">Valeur `Boolean` représentant le résultat de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="26c66-119">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="26c66-120">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="26c66-120">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="26c66-121">Requis.</span><span class="sxs-lookup"><span data-stu-id="26c66-121">Required.</span></span> <span data-ttu-id="26c66-122">N'importe quelle expression.</span><span class="sxs-lookup"><span data-stu-id="26c66-122">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="26c66-123">Requis.</span><span class="sxs-lookup"><span data-stu-id="26c66-123">Required.</span></span> <span data-ttu-id="26c66-124">N’importe quel opérateur de comparaison relationnel.</span><span class="sxs-lookup"><span data-stu-id="26c66-124">Any relational comparison operator.</span></span>

 <span data-ttu-id="26c66-125">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="26c66-125">`object1`, `object2`</span></span>  
 <span data-ttu-id="26c66-126">Requis.</span><span class="sxs-lookup"><span data-stu-id="26c66-126">Required.</span></span> <span data-ttu-id="26c66-127">Noms d’objets de référence.</span><span class="sxs-lookup"><span data-stu-id="26c66-127">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="26c66-128">Requis.</span><span class="sxs-lookup"><span data-stu-id="26c66-128">Required.</span></span> <span data-ttu-id="26c66-129">Toute expression `String` .</span><span class="sxs-lookup"><span data-stu-id="26c66-129">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="26c66-130">Requis.</span><span class="sxs-lookup"><span data-stu-id="26c66-130">Required.</span></span> <span data-ttu-id="26c66-131">Toute expression `String` ou plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="26c66-131">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="26c66-132">Notes</span><span class="sxs-lookup"><span data-stu-id="26c66-132">Remarks</span></span>
 <span data-ttu-id="26c66-133">Le tableau suivant contient une liste des opérateurs de comparaison relationnelle et des conditions qui déterminent si `result` est `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="26c66-133">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="26c66-134">Opérateur</span><span class="sxs-lookup"><span data-stu-id="26c66-134">Operator</span></span>|<span data-ttu-id="26c66-135">`True` si</span><span class="sxs-lookup"><span data-stu-id="26c66-135">`True` if</span></span>|<span data-ttu-id="26c66-136">`False` si</span><span class="sxs-lookup"><span data-stu-id="26c66-136">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="26c66-137">`<` (inférieur à)</span><span class="sxs-lookup"><span data-stu-id="26c66-137">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="26c66-138">`<=` (inférieur ou égal à)</span><span class="sxs-lookup"><span data-stu-id="26c66-138">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="26c66-139">`>` (supérieur à)</span><span class="sxs-lookup"><span data-stu-id="26c66-139">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="26c66-140">`>=` (supérieur ou égal à)</span><span class="sxs-lookup"><span data-stu-id="26c66-140">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="26c66-141">`=` (égal à)</span><span class="sxs-lookup"><span data-stu-id="26c66-141">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="26c66-142">`<>` (différent de)</span><span class="sxs-lookup"><span data-stu-id="26c66-142">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="26c66-143">L' [opérateur =](../../../visual-basic/language-reference/operators/assignment-operator.md) est également utilisé comme opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="26c66-143">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="26c66-144">L’opérateur `Is`, l’opérateur `IsNot` et l’opérateur `Like` ont des fonctionnalités de comparaison spécifiques qui diffèrent des opérateurs dans le tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="26c66-144">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="26c66-145">Comparaison de nombres</span><span class="sxs-lookup"><span data-stu-id="26c66-145">Comparing Numbers</span></span>
 <span data-ttu-id="26c66-146">Lorsque vous comparez une expression de type `Single` à l’une des `Double`de type, l’expression `Single` est convertie en `Double`.</span><span class="sxs-lookup"><span data-stu-id="26c66-146">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="26c66-147">Ce comportement est opposé au comportement trouvé dans Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="26c66-147">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="26c66-148">De même, lorsque vous comparez une expression de type `Decimal` à une expression de type `Single` ou `Double`, l’expression `Decimal` est convertie en `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="26c66-148">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="26c66-149">Pour les expressions `Decimal`, toute valeur fractionnaire inférieure à 1E-28 peut être perdue.</span><span class="sxs-lookup"><span data-stu-id="26c66-149">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="26c66-150">Une telle perte de valeur fractionnaire peut entraîner une comparaison de deux valeurs égales lorsqu’elles ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="26c66-150">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="26c66-151">Pour cette raison, vous devez prendre soin de l’utilisation de l’égalité (`=`) pour comparer deux variables à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="26c66-151">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="26c66-152">Il est plus sûr de tester si la valeur absolue de la différence entre les deux nombres est inférieure à une petite tolérance acceptable.</span><span class="sxs-lookup"><span data-stu-id="26c66-152">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="26c66-153">Imprécision à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="26c66-153">Floating-point Imprecision</span></span>
 <span data-ttu-id="26c66-154">Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours une représentation précise en mémoire.</span><span class="sxs-lookup"><span data-stu-id="26c66-154">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="26c66-155">Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l' [opérateur mod](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="26c66-155">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="26c66-156">Pour plus d’informations, consultez [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="26c66-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="26c66-157">Comparaison de chaînes</span><span class="sxs-lookup"><span data-stu-id="26c66-157">Comparing Strings</span></span>
 <span data-ttu-id="26c66-158">Lorsque vous comparez des chaînes, les expressions de chaîne sont évaluées en fonction de leur ordre de tri alphabétique, qui dépend du paramètre de `Option Compare`.</span><span class="sxs-lookup"><span data-stu-id="26c66-158">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="26c66-159">`Option Compare Binary` base les comparaisons de chaînes sur un ordre de tri dérivé des représentations binaires internes des caractères.</span><span class="sxs-lookup"><span data-stu-id="26c66-159">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="26c66-160">L’ordre de tri est déterminé par la page de codes.</span><span class="sxs-lookup"><span data-stu-id="26c66-160">The sort order is determined by the code page.</span></span> <span data-ttu-id="26c66-161">L’exemple suivant montre un ordre de tri binaire standard.</span><span class="sxs-lookup"><span data-stu-id="26c66-161">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="26c66-162">`Option Compare Text` base les comparaisons de chaînes sur un ordre de tri textuel qui ne respecte pas la casse et déterminé par les paramètres régionaux de votre application.</span><span class="sxs-lookup"><span data-stu-id="26c66-162">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="26c66-163">Lorsque vous définissez `Option Compare Text` et triez les caractères dans l’exemple précédent, l’ordre de tri de texte suivant s’applique :</span><span class="sxs-lookup"><span data-stu-id="26c66-163">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="26c66-164">Dépendance des paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="26c66-164">Locale Dependence</span></span>
 <span data-ttu-id="26c66-165">Lorsque vous définissez `Option Compare Text`, le résultat d’une comparaison de chaînes peut dépendre des paramètres régionaux dans lesquels l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="26c66-165">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="26c66-166">Deux caractères peuvent être considérés comme égaux dans un paramètre régional, mais pas dans un autre.</span><span class="sxs-lookup"><span data-stu-id="26c66-166">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="26c66-167">Si vous utilisez une comparaison de chaînes pour prendre des décisions importantes, par exemple si vous souhaitez accepter une tentative de connexion, vous devez être averti de la sensibilité des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="26c66-167">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="26c66-168">Vous pouvez soit définir `Option Compare Binary`, soit appeler l' <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, qui prend en compte les paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="26c66-168">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="26c66-169">Programmation sans type avec des opérateurs de comparaison relationnels</span><span class="sxs-lookup"><span data-stu-id="26c66-169">Typeless Programming with Relational Comparison Operators</span></span>
 <span data-ttu-id="26c66-170">L’utilisation d’opérateurs de comparaison relationnelle avec des expressions `Object` n’est pas autorisée sous `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="26c66-170">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="26c66-171">Lorsque `Option Strict` est `Off`et que `expression1` ou `expression2` est une expression `Object`, les types au moment de l’exécution déterminent la façon dont ils sont comparés.</span><span class="sxs-lookup"><span data-stu-id="26c66-171">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="26c66-172">Le tableau suivant montre comment les expressions sont comparées et le résultat de la comparaison, en fonction du type de Runtime des opérandes.</span><span class="sxs-lookup"><span data-stu-id="26c66-172">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="26c66-173">Si les opérandes sont</span><span class="sxs-lookup"><span data-stu-id="26c66-173">If operands are</span></span>|<span data-ttu-id="26c66-174">La comparaison est</span><span class="sxs-lookup"><span data-stu-id="26c66-174">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="26c66-175">Les deux `String`</span><span class="sxs-lookup"><span data-stu-id="26c66-175">Both `String`</span></span>|<span data-ttu-id="26c66-176">Comparaison de tri basée sur les caractéristiques de tri des chaînes.</span><span class="sxs-lookup"><span data-stu-id="26c66-176">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="26c66-177">Valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="26c66-177">Both numeric</span></span>|<span data-ttu-id="26c66-178">Objets convertis en `Double`, comparaison numérique.</span><span class="sxs-lookup"><span data-stu-id="26c66-178">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="26c66-179">Un chiffre et un `String`</span><span class="sxs-lookup"><span data-stu-id="26c66-179">One numeric and one `String`</span></span>|<span data-ttu-id="26c66-180">La `String` est convertie en `Double` et la comparaison numérique est effectuée.</span><span class="sxs-lookup"><span data-stu-id="26c66-180">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="26c66-181">Si la `String` ne peut pas être convertie en `Double`, une <xref:System.InvalidCastException> est levée.</span><span class="sxs-lookup"><span data-stu-id="26c66-181">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="26c66-182">L’un ou l’autre ou les deux sont des types référence autres que `String`</span><span class="sxs-lookup"><span data-stu-id="26c66-182">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="26c66-183">Un objet <xref:System.InvalidCastException> est levé.</span><span class="sxs-lookup"><span data-stu-id="26c66-183">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="26c66-184">Les comparaisons numériques traitent `Nothing` comme 0.</span><span class="sxs-lookup"><span data-stu-id="26c66-184">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="26c66-185">Les comparaisons de chaînes traitent `Nothing` comme `""` (une chaîne vide).</span><span class="sxs-lookup"><span data-stu-id="26c66-185">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="26c66-186">Surcharge</span><span class="sxs-lookup"><span data-stu-id="26c66-186">Overloading</span></span>
 <span data-ttu-id="26c66-187">Les opérateurs de comparaison relationnelles (`<`.</span><span class="sxs-lookup"><span data-stu-id="26c66-187">The relational comparison operators (`<`.</span></span> <span data-ttu-id="26c66-188">`<=`, `>`, `>=`, `=`, `<>`) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="26c66-188">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="26c66-189">Si votre code utilise l’un de ces opérateurs sur ce type de classe ou de structure, assurez-vous de bien comprendre le comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="26c66-189">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="26c66-190">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="26c66-190">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="26c66-191">Notez que l' [opérateur =](../../../visual-basic/language-reference/operators/assignment-operator.md) peut être surchargé uniquement comme un opérateur de comparaison relationnel, et non comme un opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="26c66-191">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="26c66-192">Exemple</span><span class="sxs-lookup"><span data-stu-id="26c66-192">Example</span></span>
 <span data-ttu-id="26c66-193">L’exemple suivant illustre différentes utilisations des opérateurs de comparaison relationnelles, que vous utilisez pour comparer des expressions.</span><span class="sxs-lookup"><span data-stu-id="26c66-193">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="26c66-194">Les opérateurs de comparaison relationnelles retournent un résultat `Boolean` qui indique si l’expression indiquée prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="26c66-194">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="26c66-195">Lorsque vous appliquez les opérateurs `>` et `<` à des chaînes, la comparaison s’effectue à l’aide de l’ordre de tri alphabétique normal des chaînes.</span><span class="sxs-lookup"><span data-stu-id="26c66-195">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="26c66-196">Cet ordre peut dépendre de vos paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="26c66-196">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="26c66-197">Le fait que le tri respecte la casse ou non dépend du paramètre [option compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="26c66-197">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="26c66-198">Dans l’exemple précédent, la première comparaison retourne `False` et les comparaisons restantes retournent `True`.</span><span class="sxs-lookup"><span data-stu-id="26c66-198">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="26c66-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26c66-199">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="26c66-200">=, opérateur</span><span class="sxs-lookup"><span data-stu-id="26c66-200">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="26c66-201">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26c66-201">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="26c66-202">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="26c66-202">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="26c66-203">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="26c66-203">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="26c66-204">Opérateurs de comparaison dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26c66-204">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
