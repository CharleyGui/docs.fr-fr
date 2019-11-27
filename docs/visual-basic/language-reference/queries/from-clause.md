---
title: From, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: a63fb41fc2b0ad885acf76ad5d56e446922f5b90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343776"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="91fc2-102">From, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91fc2-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="91fc2-103">Spécifie une ou plusieurs variables de plage et une collection à interroger.</span><span class="sxs-lookup"><span data-stu-id="91fc2-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91fc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91fc2-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="91fc2-105">Composants</span><span class="sxs-lookup"><span data-stu-id="91fc2-105">Parts</span></span>  
  
|<span data-ttu-id="91fc2-106">Terme</span><span class="sxs-lookup"><span data-stu-id="91fc2-106">Term</span></span>|<span data-ttu-id="91fc2-107">Définition</span><span class="sxs-lookup"><span data-stu-id="91fc2-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="91fc2-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="91fc2-108">Required.</span></span> <span data-ttu-id="91fc2-109">*Variable de portée* utilisée pour itérer au sein des éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="91fc2-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="91fc2-110">Une variable de portée est utilisée pour faire référence à chaque membre du `collection` lorsque la requête itère au sein du `collection`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="91fc2-111">Doit être un type énumérable.</span><span class="sxs-lookup"><span data-stu-id="91fc2-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="91fc2-112">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="91fc2-112">Optional.</span></span> <span data-ttu-id="91fc2-113">Type d'élément `element`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-113">The type of `element`.</span></span> <span data-ttu-id="91fc2-114">Si aucun `type` n’est spécifié, le type de `element` est déduit à partir de `collection`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="91fc2-115">Requis.</span><span class="sxs-lookup"><span data-stu-id="91fc2-115">Required.</span></span> <span data-ttu-id="91fc2-116">Fait référence à la collection à interroger.</span><span class="sxs-lookup"><span data-stu-id="91fc2-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="91fc2-117">Doit être un type énumérable.</span><span class="sxs-lookup"><span data-stu-id="91fc2-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91fc2-118">Notes</span><span class="sxs-lookup"><span data-stu-id="91fc2-118">Remarks</span></span>  
 <span data-ttu-id="91fc2-119">La clause `From` permet d’identifier les données sources d’une requête et les variables utilisées pour faire référence à un élément de la collection source.</span><span class="sxs-lookup"><span data-stu-id="91fc2-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="91fc2-120">Ces variables sont appelées *variables de portée*.</span><span class="sxs-lookup"><span data-stu-id="91fc2-120">These variables are called *range variables*.</span></span> <span data-ttu-id="91fc2-121">La clause `From` est requise pour une requête, sauf lorsque la clause `Aggregate` est utilisée pour identifier une requête qui retourne uniquement des résultats agrégés.</span><span class="sxs-lookup"><span data-stu-id="91fc2-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="91fc2-122">Pour plus d’informations, consultez [Aggregate, clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="91fc2-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="91fc2-123">Vous pouvez spécifier plusieurs clauses `From` dans une requête pour identifier plusieurs collections à joindre.</span><span class="sxs-lookup"><span data-stu-id="91fc2-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="91fc2-124">Lorsque plusieurs regroupements sont spécifiés, ils sont itérés indépendamment ou vous pouvez les joindre s’ils sont liés.</span><span class="sxs-lookup"><span data-stu-id="91fc2-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="91fc2-125">Vous pouvez joindre implicitement des collections à l’aide de la clause `Select`, ou explicitement à l’aide des clauses `Join` ou `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="91fc2-126">En guise d’alternative, vous pouvez spécifier plusieurs variables et collections de portée dans une seule clause `From`, avec chaque variable de portée associée et chaque collection, séparées par une virgule.</span><span class="sxs-lookup"><span data-stu-id="91fc2-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="91fc2-127">L’exemple de code suivant affiche les deux options de syntaxe pour la clause `From`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="91fc2-128">La clause `From` définit la portée d’une requête, qui est similaire à la portée d’une boucle `For`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="91fc2-129">Par conséquent, chaque `element` variable de portée dans l’étendue d’une requête doit avoir un nom unique.</span><span class="sxs-lookup"><span data-stu-id="91fc2-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="91fc2-130">Étant donné que vous pouvez spécifier plusieurs clauses de `From` pour une requête, les clauses de `From` suivantes peuvent faire référence à des variables de portée dans la clause `From`, ou elles peuvent faire référence à des variables de portée dans une clause `From` précédente.</span><span class="sxs-lookup"><span data-stu-id="91fc2-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="91fc2-131">Par exemple, l’exemple suivant montre une clause `From` imbriquée dans laquelle la collection de la deuxième clause est basée sur une propriété de la variable de portée dans la première clause.</span><span class="sxs-lookup"><span data-stu-id="91fc2-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="91fc2-132">Chaque clause de `From` peut être suivie d’une combinaison quelconque de clauses de requête supplémentaires pour affiner la requête.</span><span class="sxs-lookup"><span data-stu-id="91fc2-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="91fc2-133">Vous pouvez affiner la requête de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="91fc2-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="91fc2-134">Combinez plusieurs collections implicitement en utilisant les clauses `From` et `Select`, ou explicitement à l’aide des clauses `Join` ou `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="91fc2-135">Utilisez la clause `Where` pour filtrer le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="91fc2-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="91fc2-136">Triez le résultat à l’aide de la clause `Order By`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="91fc2-137">Regrouper les résultats similaires à l’aide de la clause `Group By`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="91fc2-138">Utilisez la clause `Aggregate` pour identifier les fonctions d’agrégation à évaluer pour l’ensemble du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="91fc2-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="91fc2-139">Utilisez la clause `Let` pour introduire une variable d’itération dont la valeur est déterminée par une expression au lieu d’une collection.</span><span class="sxs-lookup"><span data-stu-id="91fc2-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="91fc2-140">Utilisez la clause `Distinct` pour ignorer les résultats de la requête en double.</span><span class="sxs-lookup"><span data-stu-id="91fc2-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="91fc2-141">Identifiez les parties du résultat à retourner à l’aide des clauses `Skip`, `Take`, `Skip While`et `Take While`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91fc2-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="91fc2-142">Example</span></span>  
 <span data-ttu-id="91fc2-143">L’expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `cust` pour chaque objet `Customer` dans la collection `customers`.</span><span class="sxs-lookup"><span data-stu-id="91fc2-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="91fc2-144">La clause `Where` utilise la variable de portée pour limiter la sortie aux clients de la région spécifiée.</span><span class="sxs-lookup"><span data-stu-id="91fc2-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="91fc2-145">La boucle `For Each` affiche le nom de la société pour chaque client dans le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="91fc2-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="91fc2-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91fc2-146">See also</span></span>

- [<span data-ttu-id="91fc2-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="91fc2-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="91fc2-148">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91fc2-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="91fc2-149">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="91fc2-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="91fc2-150">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="91fc2-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="91fc2-151">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="91fc2-152">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="91fc2-153">Aggregate (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="91fc2-154">Distinct (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="91fc2-155">Join (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="91fc2-156">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="91fc2-157">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="91fc2-158">Let (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="91fc2-159">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="91fc2-160">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="91fc2-161">Skip While (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="91fc2-162">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="91fc2-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
