---
title: Types valeur Nullable-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: 072496a560775a8f79274f1d44dd389d6ed5b40d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351763"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="a01e3-102">Types valeur Nullable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a01e3-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="a01e3-103">Parfois, vous utilisez un type valeur qui n’a pas de valeur définie dans certaines circonstances.</span><span class="sxs-lookup"><span data-stu-id="a01e3-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="a01e3-104">Par exemple, un champ dans une base de données peut être obligé de faire la distinction entre avoir une valeur assignée explicite et ne pas avoir de valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="a01e3-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="a01e3-105">Les types valeur peuvent être étendus pour prendre leurs valeurs normales ou une valeur null.</span><span class="sxs-lookup"><span data-stu-id="a01e3-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="a01e3-106">Une telle extension est appelée un *type Nullable*.</span><span class="sxs-lookup"><span data-stu-id="a01e3-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="a01e3-107">Chaque type Nullable est construit à partir de la structure <xref:System.Nullable%601> générique.</span><span class="sxs-lookup"><span data-stu-id="a01e3-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="a01e3-108">Prenons l’exemple d’une base de données qui effectue le suivi des activités liées au travail.</span><span class="sxs-lookup"><span data-stu-id="a01e3-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="a01e3-109">L’exemple suivant construit un type Nullable `Boolean` et déclare une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="a01e3-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="a01e3-110">Vous pouvez écrire la déclaration de trois manières :</span><span class="sxs-lookup"><span data-stu-id="a01e3-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="a01e3-111">La variable `ridesBusToWork` peut contenir une valeur de `True`, une valeur de `False`, ou aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="a01e3-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="a01e3-112">Sa valeur par défaut initiale est aucune valeur, ce qui, dans ce cas, signifie que les informations n’ont pas encore été obtenues pour cette personne.</span><span class="sxs-lookup"><span data-stu-id="a01e3-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="a01e3-113">En revanche, `False` peut signifier que les informations ont été obtenues et que la personne n’a pas la possibilité d’ignorer le bus pour fonctionner.</span><span class="sxs-lookup"><span data-stu-id="a01e3-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="a01e3-114">Vous pouvez déclarer des variables et des propriétés avec des types Nullable, et vous pouvez déclarer un tableau avec des éléments d’un type Nullable.</span><span class="sxs-lookup"><span data-stu-id="a01e3-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="a01e3-115">Vous pouvez déclarer des procédures avec des types Nullable comme paramètres, et vous pouvez retourner un type Nullable à partir d’une procédure `Function`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="a01e3-116">Vous ne pouvez pas construire un type Nullable sur un type référence, tel qu’un tableau, un `String` ou une classe.</span><span class="sxs-lookup"><span data-stu-id="a01e3-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="a01e3-117">Le type sous-jacent doit être un type valeur.</span><span class="sxs-lookup"><span data-stu-id="a01e3-117">The underlying type must be a value type.</span></span> <span data-ttu-id="a01e3-118">Pour plus d'informations, consultez [Value Types and Reference Types](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a01e3-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="a01e3-119">Utilisation d’une variable de type Nullable</span><span class="sxs-lookup"><span data-stu-id="a01e3-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="a01e3-120">Les membres les plus importants d’un type Nullable sont ses propriétés <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="a01e3-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="a01e3-121">Pour une variable de type Nullable, <xref:System.Nullable%601.HasValue%2A> vous indique si la variable contient une valeur définie.</span><span class="sxs-lookup"><span data-stu-id="a01e3-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="a01e3-122">Si <xref:System.Nullable%601.HasValue%2A> est `True`, vous pouvez lire la valeur à partir de <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="a01e3-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="a01e3-123">Notez que les <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A> sont des propriétés `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="a01e3-124">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="a01e3-124">Default Values</span></span>

<span data-ttu-id="a01e3-125">Quand vous déclarez une variable avec un type Nullable, sa propriété <xref:System.Nullable%601.HasValue%2A> a une valeur par défaut de `False`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="a01e3-126">Cela signifie que, par défaut, la variable n’a pas de valeur définie, et non la valeur par défaut de son type de valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="a01e3-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="a01e3-127">Dans l’exemple suivant, la variable `numberOfChildren` n’a initialement aucune valeur définie, même si la valeur par défaut du type `Integer` est 0.</span><span class="sxs-lookup"><span data-stu-id="a01e3-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="a01e3-128">Une valeur null est utile pour indiquer une valeur non définie ou inconnue.</span><span class="sxs-lookup"><span data-stu-id="a01e3-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="a01e3-129">Si `numberOfChildren` avait été déclaré comme `Integer`, aucune valeur ne peut indiquer que les informations ne sont pas disponibles actuellement.</span><span class="sxs-lookup"><span data-stu-id="a01e3-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="a01e3-130">Stocker des valeurs</span><span class="sxs-lookup"><span data-stu-id="a01e3-130">Storing Values</span></span>

<span data-ttu-id="a01e3-131">Vous stockez une valeur dans une variable ou une propriété d’un type Nullable de la façon habituelle.</span><span class="sxs-lookup"><span data-stu-id="a01e3-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="a01e3-132">L’exemple suivant affecte une valeur à la variable `numberOfChildren` déclarée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="a01e3-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="a01e3-133">Si une variable ou une propriété d’un type Nullable contient une valeur définie, vous pouvez la forcer à revenir à son état initial qui n’a pas de valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="a01e3-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="a01e3-134">Pour ce faire, affectez à la variable ou à la propriété la valeur `Nothing`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a01e3-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="a01e3-135">Bien que vous puissiez assigner `Nothing` à une variable d’un type Nullable, vous ne pouvez pas le tester pour `Nothing` à l’aide du signe égal.</span><span class="sxs-lookup"><span data-stu-id="a01e3-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="a01e3-136">La comparaison qui utilise le signe égal, `someVar = Nothing`, correspond toujours à `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="a01e3-137">Vous pouvez tester la propriété <xref:System.Nullable%601.HasValue%2A> de la variable pour `False`, ou pour un test à l’aide de l’opérateur `Is` ou `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="a01e3-138">Récupération de valeurs</span><span class="sxs-lookup"><span data-stu-id="a01e3-138">Retrieving Values</span></span>

<span data-ttu-id="a01e3-139">Pour récupérer la valeur d’une variable d’un type Nullable, vous devez d’abord tester sa propriété <xref:System.Nullable%601.HasValue%2A> pour confirmer qu’elle a une valeur.</span><span class="sxs-lookup"><span data-stu-id="a01e3-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="a01e3-140">Si vous essayez de lire la valeur lorsque <xref:System.Nullable%601.HasValue%2A> est `False`, Visual Basic lève une exception <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="a01e3-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="a01e3-141">L’exemple suivant illustre la méthode recommandée pour lire la variable `numberOfChildren` des exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="a01e3-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="a01e3-142">Comparaison des types Nullable</span><span class="sxs-lookup"><span data-stu-id="a01e3-142">Comparing Nullable Types</span></span>

<span data-ttu-id="a01e3-143">Quand des variables null `Boolean` sont utilisées dans des expressions booléennes, le résultat peut être `True`, `False` ou `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="a01e3-144">Voici la table de vérité pour `And` et `Or`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="a01e3-145">Étant donné que `b1` et `b2` ont désormais trois valeurs possibles, il existe neuf combinaisons à évaluer.</span><span class="sxs-lookup"><span data-stu-id="a01e3-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="a01e3-146">b1</span><span class="sxs-lookup"><span data-stu-id="a01e3-146">b1</span></span>|<span data-ttu-id="a01e3-147">b2</span><span class="sxs-lookup"><span data-stu-id="a01e3-147">b2</span></span>|<span data-ttu-id="a01e3-148">B1 et B2</span><span class="sxs-lookup"><span data-stu-id="a01e3-148">b1 And b2</span></span>|<span data-ttu-id="a01e3-149">B1 ou B2</span><span class="sxs-lookup"><span data-stu-id="a01e3-149">b1 Or b2</span></span>|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

<span data-ttu-id="a01e3-150">Quand la valeur d’une variable ou d’une expression booléenne est `Nothing`, elle n’est ni `true`, ni `false`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="a01e3-151">Prenons l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a01e3-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="a01e3-152">Dans cet exemple, `b1 And b2` correspond à `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="a01e3-153">Par conséquent, la clause `Else` est exécutée dans chaque instruction `If`, et la sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a01e3-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="a01e3-154">`AndAlso` et `OrElse`, qui utilisent l’évaluation de court-circuit, doivent évaluer leurs deux opérandes lorsque le premier est évalué à `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="a01e3-155">Propagation</span><span class="sxs-lookup"><span data-stu-id="a01e3-155">Propagation</span></span>

<span data-ttu-id="a01e3-156">Si l’un des opérandes d’une opération arithmétique, de comparaison, de décalage ou de type est Nullable, le résultat de l’opération est également Nullable.</span><span class="sxs-lookup"><span data-stu-id="a01e3-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="a01e3-157">Si les deux opérandes ont des valeurs qui ne sont pas `Nothing`, l’opération est effectuée sur les valeurs sous-jacentes des opérandes, comme si aucun n’était un type Nullable.</span><span class="sxs-lookup"><span data-stu-id="a01e3-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="a01e3-158">Dans l’exemple suivant, les variables `compare1` et `sum1` sont implicitement typées.</span><span class="sxs-lookup"><span data-stu-id="a01e3-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="a01e3-159">Si vous placez le pointeur de la souris dessus, vous verrez que le compilateur déduit les types Nullable pour les deux.</span><span class="sxs-lookup"><span data-stu-id="a01e3-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="a01e3-160">Si l’un des opérandes ou les deux ont la valeur `Nothing`, le résultat sera `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a01e3-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="a01e3-161">Utilisation de types Nullable avec des données</span><span class="sxs-lookup"><span data-stu-id="a01e3-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="a01e3-162">Une base de données est l’un des emplacements les plus importants pour l’utilisation de types Nullable.</span><span class="sxs-lookup"><span data-stu-id="a01e3-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="a01e3-163">Tous les objets de base de données ne prennent pas actuellement en charge les types Nullable, contrairement aux adaptateurs de table générés par le concepteur.</span><span class="sxs-lookup"><span data-stu-id="a01e3-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="a01e3-164">Consultez [prise en charge de TableAdapter pour les types Nullable](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="a01e3-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="a01e3-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a01e3-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="a01e3-166">Types de données</span><span class="sxs-lookup"><span data-stu-id="a01e3-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="a01e3-167">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="a01e3-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="a01e3-168">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="a01e3-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="a01e3-169">Remplir des datasets à l’aide de TableAdapters</span><span class="sxs-lookup"><span data-stu-id="a01e3-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="a01e3-170">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="a01e3-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="a01e3-171">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="a01e3-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="a01e3-172">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="a01e3-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="a01e3-173">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="a01e3-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="a01e3-174">Utilisation des types valeur NullableC#()</span><span class="sxs-lookup"><span data-stu-id="a01e3-174">Using Nullable Value Types (C#)</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
