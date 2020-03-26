---
title: Types valeur Nullable
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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249680"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="c87fe-102">Types valeur Nullable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c87fe-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="c87fe-103">Parfois, vous travaillez avec un type de valeur qui n’a pas de valeur définie dans certaines circonstances.</span><span class="sxs-lookup"><span data-stu-id="c87fe-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="c87fe-104">Par exemple, un champ dans une base de données peut avoir à faire la distinction entre avoir une valeur assignée qui est significative et ne pas avoir une valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="c87fe-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="c87fe-105">Les types de valeur peuvent être étendus pour prendre leurs valeurs normales ou une valeur nulle.</span><span class="sxs-lookup"><span data-stu-id="c87fe-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="c87fe-106">Une telle extension est appelée un *type nul*.</span><span class="sxs-lookup"><span data-stu-id="c87fe-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="c87fe-107">Chaque type de valeur in <xref:System.Nullable%601> nullable est construit à partir de la structure générique.</span><span class="sxs-lookup"><span data-stu-id="c87fe-107">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="c87fe-108">Envisagez une base de données qui suit les activités liées au travail.</span><span class="sxs-lookup"><span data-stu-id="c87fe-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="c87fe-109">L’exemple suivant construit `Boolean` un type nul et déclare une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="c87fe-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="c87fe-110">Vous pouvez écrire la déclaration de trois façons :</span><span class="sxs-lookup"><span data-stu-id="c87fe-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="c87fe-111">La `ridesBusToWork` variable peut contenir `True`une valeur `False`de , une valeur de , ou aucune valeur du tout.</span><span class="sxs-lookup"><span data-stu-id="c87fe-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="c87fe-112">Sa valeur initiale par défaut n’a aucune valeur, ce qui, dans ce cas, pourrait signifier que l’information n’a pas encore été obtenue pour cette personne.</span><span class="sxs-lookup"><span data-stu-id="c87fe-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="c87fe-113">En revanche, `False` cela pourrait signifier que l’information a été obtenue et que la personne ne monte pas dans l’autobus pour se rendre au travail.</span><span class="sxs-lookup"><span data-stu-id="c87fe-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="c87fe-114">Vous pouvez déclarer des variables et des propriétés avec des types de valeur nul, et vous pouvez déclarer un tableau avec des éléments d’un type de valeur nul.</span><span class="sxs-lookup"><span data-stu-id="c87fe-114">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="c87fe-115">Vous pouvez déclarer les procédures avec les types de valeur nuls comme `Function` paramètres, et vous pouvez retourner un type de valeur nul d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="c87fe-115">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="c87fe-116">Vous ne pouvez pas construire un type nul sur `String`un type de référence tel qu’un tableau, un, ou une classe.</span><span class="sxs-lookup"><span data-stu-id="c87fe-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="c87fe-117">Le type sous-jacent doit être un type de valeur.</span><span class="sxs-lookup"><span data-stu-id="c87fe-117">The underlying type must be a value type.</span></span> <span data-ttu-id="c87fe-118">Pour plus d'informations, consultez [Value Types and Reference Types](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c87fe-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="c87fe-119">Utilisation d’une variable de type nul</span><span class="sxs-lookup"><span data-stu-id="c87fe-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="c87fe-120">Les membres les plus importants d’un <xref:System.Nullable%601.Value%2A> type de valeur nul sont ses propriétés et ses <xref:System.Nullable%601.HasValue%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="c87fe-120">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="c87fe-121">Pour une variable d’un <xref:System.Nullable%601.HasValue%2A> type de valeur nulle, vous indique si la variable contient une valeur définie.</span><span class="sxs-lookup"><span data-stu-id="c87fe-121">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="c87fe-122">Si <xref:System.Nullable%601.HasValue%2A> `True`est , vous pouvez <xref:System.Nullable%601.Value%2A>lire la valeur de .</span><span class="sxs-lookup"><span data-stu-id="c87fe-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="c87fe-123">Notez <xref:System.Nullable%601.HasValue%2A> que <xref:System.Nullable%601.Value%2A> `ReadOnly` les deux et sont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="c87fe-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="c87fe-124">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="c87fe-124">Default Values</span></span>

<span data-ttu-id="c87fe-125">Lorsque vous déclarez une variable avec <xref:System.Nullable%601.HasValue%2A> un type de `False`valeur nul, sa propriété a une valeur par défaut de .</span><span class="sxs-lookup"><span data-stu-id="c87fe-125">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="c87fe-126">Cela signifie que par défaut la variable n’a pas de valeur définie, au lieu de la valeur par défaut de son type de valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="c87fe-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="c87fe-127">Dans l’exemple suivant, la variable `numberOfChildren` n’a initialement aucune `Integer` valeur définie, même si la valeur par défaut du type est de 0.</span><span class="sxs-lookup"><span data-stu-id="c87fe-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="c87fe-128">Une valeur nulle est utile pour indiquer une valeur indéfinie ou inconnue.</span><span class="sxs-lookup"><span data-stu-id="c87fe-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="c87fe-129">Si `numberOfChildren` elle avait `Integer`été déclarée comme, il n’y aurait aucune valeur qui pourrait indiquer que l’information n’est pas actuellement disponible.</span><span class="sxs-lookup"><span data-stu-id="c87fe-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="c87fe-130">Stockage des valeurs</span><span class="sxs-lookup"><span data-stu-id="c87fe-130">Storing Values</span></span>

<span data-ttu-id="c87fe-131">Vous stockez une valeur dans une variable ou une propriété d’un type de valeur nulle de la manière typique.</span><span class="sxs-lookup"><span data-stu-id="c87fe-131">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="c87fe-132">L’exemple suivant attribue une `numberOfChildren` valeur à la variable déclarée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="c87fe-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="c87fe-133">Si une variable ou une propriété d’un type de valeur nulle contient une valeur définie, vous pouvez la faire revenir à son état initial de ne pas avoir une valeur attribuée.</span><span class="sxs-lookup"><span data-stu-id="c87fe-133">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="c87fe-134">Vous le faites en définissant `Nothing`la variable ou la propriété à , comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c87fe-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="c87fe-135">Bien que `Nothing` vous puissiez attribuer à une variable d’un `Nothing` type de valeur nulle, vous ne pouvez pas la tester en utilisant le signe égal.</span><span class="sxs-lookup"><span data-stu-id="c87fe-135">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="c87fe-136">Comparaison qui utilise le `someVar = Nothing`signe égal, `Nothing`, évalue toujours à .</span><span class="sxs-lookup"><span data-stu-id="c87fe-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="c87fe-137">Vous pouvez tester la <xref:System.Nullable%601.HasValue%2A> propriété `False`de la variable `Is` `IsNot` pour , ou tester en utilisant le ou l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c87fe-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="c87fe-138">Récupération des valeurs</span><span class="sxs-lookup"><span data-stu-id="c87fe-138">Retrieving Values</span></span>

<span data-ttu-id="c87fe-139">Pour récupérer la valeur d’une variable d’un type <xref:System.Nullable%601.HasValue%2A> de valeur nulle, vous devez d’abord tester sa propriété pour confirmer qu’elle a une valeur.</span><span class="sxs-lookup"><span data-stu-id="c87fe-139">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="c87fe-140">Si vous essayez de <xref:System.Nullable%601.HasValue%2A> lire `False`la valeur quand <xref:System.InvalidOperationException> est, Visual Basic jette une exception.</span><span class="sxs-lookup"><span data-stu-id="c87fe-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="c87fe-141">L’exemple suivant montre la façon `numberOfChildren` recommandée de lire la variable des exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="c87fe-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="c87fe-142">Comparaison des types nuls</span><span class="sxs-lookup"><span data-stu-id="c87fe-142">Comparing Nullable Types</span></span>

<span data-ttu-id="c87fe-143">Lorsque des `Boolean` variables où les variables sont `True`utilisées `False`dans `Nothing`les expressions Boolean, le résultat peut être , , ou .</span><span class="sxs-lookup"><span data-stu-id="c87fe-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="c87fe-144">Ce qui suit est `And` `Or`le tableau de vérité pour et .</span><span class="sxs-lookup"><span data-stu-id="c87fe-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="c87fe-145">Parce `b1` `b2` qu’et ont maintenant trois valeurs possibles, il ya neuf combinaisons à évaluer.</span><span class="sxs-lookup"><span data-stu-id="c87fe-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="c87fe-146">b1</span><span class="sxs-lookup"><span data-stu-id="c87fe-146">b1</span></span>|<span data-ttu-id="c87fe-147">B2</span><span class="sxs-lookup"><span data-stu-id="c87fe-147">b2</span></span>|<span data-ttu-id="c87fe-148">b1 Et b2</span><span class="sxs-lookup"><span data-stu-id="c87fe-148">b1 And b2</span></span>|<span data-ttu-id="c87fe-149">b1 Ou b2</span><span class="sxs-lookup"><span data-stu-id="c87fe-149">b1 Or b2</span></span>|
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

<span data-ttu-id="c87fe-150">Lorsque la valeur d’une variable `Nothing`boolean `true` ou `false`d’expression est , il n’est ni ni .</span><span class="sxs-lookup"><span data-stu-id="c87fe-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="c87fe-151">Considérez l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c87fe-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="c87fe-152">Dans cet `b1 And b2` exemple, `Nothing`évalue à .</span><span class="sxs-lookup"><span data-stu-id="c87fe-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="c87fe-153">Par conséquent, `Else` la clause est `If` exécutée dans chaque énoncé, et la sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c87fe-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="c87fe-154">`AndAlso`et `OrElse`, qui utilisent l’évaluation en court-circuit, doivent évaluer `Nothing`leurs deuxièmes opérands lorsque le premier évalue à .</span><span class="sxs-lookup"><span data-stu-id="c87fe-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="c87fe-155">Propagation</span><span class="sxs-lookup"><span data-stu-id="c87fe-155">Propagation</span></span>

<span data-ttu-id="c87fe-156">Si l’un ou les deux opérands d’une opération arithmétique, comparaison, décalage ou type est un type de valeur nulable, le résultat de l’opération est également un type de valeur nul.</span><span class="sxs-lookup"><span data-stu-id="c87fe-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="c87fe-157">Si les deux opérandes `Nothing`ont des valeurs qui ne le sont pas, l’opération est exécutée sur les valeurs sous-jacentes des opérandes, comme si ni l’un ni l’autre n’étaient un type de valeur nul.</span><span class="sxs-lookup"><span data-stu-id="c87fe-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="c87fe-158">Dans l’exemple `compare1` suivant, les variables et `sum1` sont implicitement tapées.</span><span class="sxs-lookup"><span data-stu-id="c87fe-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="c87fe-159">Si vous reposez le pointeur de souris au-dessus d’eux, vous verrez que le compilateur infère les types de valeur nul pour les deux d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="c87fe-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="c87fe-160">Si l’un ou les deux `Nothing`opérands `Nothing`ont une valeur de , le résultat sera .</span><span class="sxs-lookup"><span data-stu-id="c87fe-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="c87fe-161">Utilisation de types nuls avec des données</span><span class="sxs-lookup"><span data-stu-id="c87fe-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="c87fe-162">Une base de données est l’un des endroits les plus importants pour utiliser des types de valeur nul.</span><span class="sxs-lookup"><span data-stu-id="c87fe-162">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="c87fe-163">Tous les objets de base de données ne prennent pas actuellement en charge les types de valeur nuls, mais les adaptateurs de table générés par le concepteur le font.</span><span class="sxs-lookup"><span data-stu-id="c87fe-163">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="c87fe-164">Voir [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="c87fe-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="c87fe-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c87fe-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="c87fe-166">Types de données</span><span class="sxs-lookup"><span data-stu-id="c87fe-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="c87fe-167">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="c87fe-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="c87fe-168">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="c87fe-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="c87fe-169">Remplir des datasets à l’aide de TableAdapters</span><span class="sxs-lookup"><span data-stu-id="c87fe-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="c87fe-170">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="c87fe-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="c87fe-171">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="c87fe-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="c87fe-172">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="c87fe-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="c87fe-173">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="c87fe-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="c87fe-174">Types de valeur nuls (C)</span><span class="sxs-lookup"><span data-stu-id="c87fe-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
