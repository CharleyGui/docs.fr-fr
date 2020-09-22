---
title: Aggregate Clause
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: be2e401c7931b2637c14a3ea3b742a2c09917939
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869980"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="0e56f-102">Aggregate, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e56f-102">Aggregate Clause (Visual Basic)</span></span>

<span data-ttu-id="0e56f-103">Applique une ou plusieurs fonctions d’agrégation à une collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e56f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e56f-104">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="0e56f-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="0e56f-105">Parts</span></span>  
  
|<span data-ttu-id="0e56f-106">Terme</span><span class="sxs-lookup"><span data-stu-id="0e56f-106">Term</span></span>|<span data-ttu-id="0e56f-107">Définition</span><span class="sxs-lookup"><span data-stu-id="0e56f-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="0e56f-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0e56f-108">Required.</span></span> <span data-ttu-id="0e56f-109">Variable utilisée pour itérer au sein des éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="0e56f-110">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="0e56f-110">Optional.</span></span> <span data-ttu-id="0e56f-111">Type d'élément `element`.</span><span class="sxs-lookup"><span data-stu-id="0e56f-111">The type of `element`.</span></span> <span data-ttu-id="0e56f-112">Si aucun type n’est spécifié, le type de `element` est déduit à partir de `collection` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="0e56f-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0e56f-113">Required.</span></span> <span data-ttu-id="0e56f-114">Fait référence à la collection sur laquelle opérer.</span><span class="sxs-lookup"><span data-stu-id="0e56f-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="0e56f-115">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="0e56f-115">Optional.</span></span> <span data-ttu-id="0e56f-116">Une ou plusieurs clauses de requête, telles qu’une `Where` clause, pour affiner le résultat de la requête afin d’appliquer la ou les clauses d’agrégation à.</span><span class="sxs-lookup"><span data-stu-id="0e56f-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="0e56f-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0e56f-117">Required.</span></span> <span data-ttu-id="0e56f-118">Une ou plusieurs expressions délimitées par des virgules qui identifient une fonction d’agrégation à appliquer à la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="0e56f-119">Vous pouvez appliquer un alias à une fonction d’agrégation pour spécifier un nom de membre pour le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="0e56f-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="0e56f-120">Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0e56f-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="0e56f-121">Pour obtenir des exemples, consultez la section relative aux fonctions d’agrégation plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0e56f-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e56f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="0e56f-122">Remarks</span></span>  

 <span data-ttu-id="0e56f-123">La `Aggregate` clause peut être utilisée pour inclure des fonctions d’agrégation dans vos requêtes.</span><span class="sxs-lookup"><span data-stu-id="0e56f-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="0e56f-124">Les fonctions d’agrégation effectuent des vérifications et des calculs sur un ensemble de valeurs et retournent une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="0e56f-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="0e56f-125">Vous pouvez accéder à la valeur calculée à l’aide d’un membre du type de résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="0e56f-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="0e56f-126">Les fonctions d’agrégation standard que vous pouvez utiliser sont `All` les `Any` fonctions,, `Average` ,,,, `Count` `LongCount` `Max` `Min` et `Sum` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="0e56f-127">Ces fonctions sont familières aux développeurs qui sont familiarisés avec les agrégats dans SQL.</span><span class="sxs-lookup"><span data-stu-id="0e56f-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="0e56f-128">Ils sont décrits dans la section suivante de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0e56f-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="0e56f-129">Le résultat d’une fonction d’agrégation est inclus dans le résultat de la requête en tant que champ du type de résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="0e56f-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="0e56f-130">Vous pouvez fournir un alias pour le résultat de la fonction d’agrégation afin de spécifier le nom du membre du type de résultat de la requête qui contiendra la valeur d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="0e56f-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="0e56f-131">Si aucun alias n’est fourni, le nom de la fonction d’agrégation est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0e56f-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="0e56f-132">La `Aggregate` clause peut commencer une requête, ou elle peut être incluse en tant que clause supplémentaire dans une requête.</span><span class="sxs-lookup"><span data-stu-id="0e56f-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="0e56f-133">Si la `Aggregate` clause commence une requête, le résultat est une valeur unique qui est le résultat de la fonction d’agrégation spécifiée dans la `Into` clause.</span><span class="sxs-lookup"><span data-stu-id="0e56f-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="0e56f-134">Si plusieurs fonctions d’agrégation sont spécifiées dans la `Into` clause, la requête retourne un type unique avec une propriété distincte pour référencer le résultat de chaque fonction d’agrégation dans la `Into` clause.</span><span class="sxs-lookup"><span data-stu-id="0e56f-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="0e56f-135">Si la `Aggregate` clause est incluse en tant que clause supplémentaire dans une requête, le type retourné dans la collection de requêtes aura une propriété distincte pour référencer le résultat de chaque fonction d’agrégation dans la `Into` clause.</span><span class="sxs-lookup"><span data-stu-id="0e56f-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="0e56f-136">Fonctions d’agrégation</span><span class="sxs-lookup"><span data-stu-id="0e56f-136">Aggregate Functions</span></span>

<span data-ttu-id="0e56f-137">Les fonctions d’agrégation standard qui peuvent être utilisées avec la clause sont les suivantes `Aggregate` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="0e56f-138">Tous</span><span class="sxs-lookup"><span data-stu-id="0e56f-138">All</span></span>

<span data-ttu-id="0e56f-139">Retourne `true` si tous les éléments de la collection satisfont à une condition spécifiée ; sinon, retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="0e56f-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e56f-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="0e56f-141">Quelconque</span><span class="sxs-lookup"><span data-stu-id="0e56f-141">Any</span></span>

<span data-ttu-id="0e56f-142">Retourne `true` si un élément de la collection satisfait à une condition spécifiée ; sinon, retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="0e56f-143">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e56f-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="0e56f-144">Moyenne</span><span class="sxs-lookup"><span data-stu-id="0e56f-144">Average</span></span>

<span data-ttu-id="0e56f-145">Calcule la moyenne de tous les éléments de la collection ou calcule une expression fournie pour tous les éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="0e56f-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e56f-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="0e56f-147">Nombre</span><span class="sxs-lookup"><span data-stu-id="0e56f-147">Count</span></span>

<span data-ttu-id="0e56f-148">Compte le nombre d’éléments dans la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="0e56f-149">Vous pouvez fournir une `Boolean` expression facultative pour compter uniquement le nombre d’éléments de la collection qui satisfont à une condition.</span><span class="sxs-lookup"><span data-stu-id="0e56f-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="0e56f-150">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e56f-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="0e56f-151">Group</span><span class="sxs-lookup"><span data-stu-id="0e56f-151">Group</span></span>

<span data-ttu-id="0e56f-152">Fait référence aux résultats de requête regroupés à la suite d' `Group By` une `Group Join` clause ou.</span><span class="sxs-lookup"><span data-stu-id="0e56f-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="0e56f-153">La `Group` fonction est valide uniquement dans la `Into` clause d’une `Group By` `Group Join` clause ou.</span><span class="sxs-lookup"><span data-stu-id="0e56f-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="0e56f-154">Pour plus d’informations et d’exemples, consultez [Group by](group-by-clause.md) , clause et Group [join clause](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0e56f-154">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="0e56f-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="0e56f-155">LongCount</span></span>

<span data-ttu-id="0e56f-156">Compte le nombre d’éléments dans la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="0e56f-157">Vous pouvez fournir une `Boolean` expression facultative pour compter uniquement le nombre d’éléments de la collection qui satisfont à une condition.</span><span class="sxs-lookup"><span data-stu-id="0e56f-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="0e56f-158">Retourne le résultat sous forme de `Long` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="0e56f-159">Pour obtenir un exemple, consultez la `Count` fonction Aggregate.</span><span class="sxs-lookup"><span data-stu-id="0e56f-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="0e56f-160">Max</span><span class="sxs-lookup"><span data-stu-id="0e56f-160">Max</span></span>

<span data-ttu-id="0e56f-161">Calcule la valeur maximale de la collection ou calcule une expression fournie pour tous les éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="0e56f-162">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e56f-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="0e56f-163">Min</span><span class="sxs-lookup"><span data-stu-id="0e56f-163">Min</span></span>

<span data-ttu-id="0e56f-164">Calcule la valeur minimale de la collection ou calcule une expression fournie pour tous les éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="0e56f-165">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e56f-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="0e56f-166">SUM</span><span class="sxs-lookup"><span data-stu-id="0e56f-166">Sum</span></span>

<span data-ttu-id="0e56f-167">Calcule la somme de tous les éléments de la collection ou calcule une expression fournie pour tous les éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="0e56f-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="0e56f-168">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e56f-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="0e56f-169">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e56f-169">Example</span></span>  

<span data-ttu-id="0e56f-170">L’exemple suivant montre comment utiliser la `Aggregate` clause pour appliquer des fonctions d’agrégation à un résultat de requête.</span><span class="sxs-lookup"><span data-stu-id="0e56f-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="0e56f-171">Création de fonctions d’agrégation définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="0e56f-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="0e56f-172">Vous pouvez inclure vos propres fonctions d’agrégation personnalisées dans une expression de requête en ajoutant des méthodes d’extension au <xref:System.Collections.Generic.IEnumerable%601> type.</span><span class="sxs-lookup"><span data-stu-id="0e56f-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="0e56f-173">Votre méthode personnalisée peut ensuite effectuer un calcul ou une opération sur la collection énumérable qui a référencé votre fonction d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="0e56f-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="0e56f-174">Pour plus d’informations sur les méthodes d’extension, consultez [Méthodes d’extension](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0e56f-174">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="0e56f-175">Par exemple, l’exemple suivant montre une fonction d’agrégation personnalisée qui calcule la valeur médiane d’une collection de nombres.</span><span class="sxs-lookup"><span data-stu-id="0e56f-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="0e56f-176">Il existe deux surcharges de la `Median` méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="0e56f-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="0e56f-177">La première surcharge accepte, en entrée, une collection de type `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="0e56f-178">Si la `Median` fonction d’agrégation est appelée pour un champ de requête de type `Double` , cette méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="0e56f-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="0e56f-179">La deuxième surcharge de la `Median` méthode peut être passée à n’importe quel type générique.</span><span class="sxs-lookup"><span data-stu-id="0e56f-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="0e56f-180">La surcharge générique de la `Median` méthode prend un deuxième paramètre qui fait référence `Func(Of T, Double)` à l’expression lambda pour projeter une valeur pour un type (à partir d’une collection) comme valeur correspondante de type `Double` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="0e56f-181">Il délègue ensuite le calcul de la valeur médiane à l’autre surcharge de la `Median` méthode.</span><span class="sxs-lookup"><span data-stu-id="0e56f-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="0e56f-182">Pour plus d’informations sur les expressions lambda, consultez [expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0e56f-182">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="0e56f-183">L’exemple suivant montre des exemples de requêtes qui appellent la `Median` fonction d’agrégation sur une collection de type `Integer` , et une collection de type `Double` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="0e56f-184">La requête qui appelle la `Median` fonction d’agrégation sur la collection de type `Double` appelle la surcharge de la `Median` méthode qui accepte, en entrée, une collection de type `Double` .</span><span class="sxs-lookup"><span data-stu-id="0e56f-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="0e56f-185">La requête qui appelle la `Median` fonction d’agrégation sur la collection de type `Integer` appelle la surcharge générique de la `Median` méthode.</span><span class="sxs-lookup"><span data-stu-id="0e56f-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="0e56f-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e56f-186">See also</span></span>

- [<span data-ttu-id="0e56f-187">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e56f-187">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0e56f-188">Requêtes</span><span class="sxs-lookup"><span data-stu-id="0e56f-188">Queries</span></span>](index.md)
- [<span data-ttu-id="0e56f-189">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="0e56f-189">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="0e56f-190">From, clause</span><span class="sxs-lookup"><span data-stu-id="0e56f-190">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="0e56f-191">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="0e56f-191">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="0e56f-192">Group By (clause)</span><span class="sxs-lookup"><span data-stu-id="0e56f-192">Group By Clause</span></span>](group-by-clause.md)
