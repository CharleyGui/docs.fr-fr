---
title: From (clause)
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
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396179"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="d9c30-102">From, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9c30-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="d9c30-103">Spécifie une ou plusieurs variables de plage et une collection à interroger.</span><span class="sxs-lookup"><span data-stu-id="d9c30-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9c30-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d9c30-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="d9c30-105">Parts</span></span>  
  
|<span data-ttu-id="d9c30-106">Terme</span><span class="sxs-lookup"><span data-stu-id="d9c30-106">Term</span></span>|<span data-ttu-id="d9c30-107">Définition</span><span class="sxs-lookup"><span data-stu-id="d9c30-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="d9c30-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d9c30-108">Required.</span></span> <span data-ttu-id="d9c30-109">*Variable de portée* utilisée pour itérer au sein des éléments de la collection.</span><span class="sxs-lookup"><span data-stu-id="d9c30-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="d9c30-110">Une variable de portée est utilisée pour faire référence à chaque membre du au `collection` fur et à mesure que la requête itère au sein de `collection` .</span><span class="sxs-lookup"><span data-stu-id="d9c30-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="d9c30-111">Doit être un type énumérable.</span><span class="sxs-lookup"><span data-stu-id="d9c30-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="d9c30-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="d9c30-112">Optional.</span></span> <span data-ttu-id="d9c30-113">Type d'élément `element`.</span><span class="sxs-lookup"><span data-stu-id="d9c30-113">The type of `element`.</span></span> <span data-ttu-id="d9c30-114">Si aucun `type` n’est spécifié, le type de `element` est déduit à partir de `collection` .</span><span class="sxs-lookup"><span data-stu-id="d9c30-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="d9c30-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d9c30-115">Required.</span></span> <span data-ttu-id="d9c30-116">Fait référence à la collection à interroger.</span><span class="sxs-lookup"><span data-stu-id="d9c30-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="d9c30-117">Doit être un type énumérable.</span><span class="sxs-lookup"><span data-stu-id="d9c30-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9c30-118">Notes</span><span class="sxs-lookup"><span data-stu-id="d9c30-118">Remarks</span></span>  
 <span data-ttu-id="d9c30-119">La `From` clause est utilisée pour identifier les données sources d’une requête et les variables utilisées pour faire référence à un élément de la collection source.</span><span class="sxs-lookup"><span data-stu-id="d9c30-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="d9c30-120">Ces variables sont appelées *variables de portée*.</span><span class="sxs-lookup"><span data-stu-id="d9c30-120">These variables are called *range variables*.</span></span> <span data-ttu-id="d9c30-121">La `From` clause est requise pour une requête, sauf lorsque la `Aggregate` clause est utilisée pour identifier une requête qui retourne uniquement des résultats agrégés.</span><span class="sxs-lookup"><span data-stu-id="d9c30-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="d9c30-122">Pour plus d’informations, consultez [Aggregate, clause](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d9c30-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="d9c30-123">Vous pouvez spécifier plusieurs `From` clauses dans une requête pour identifier plusieurs collections à joindre.</span><span class="sxs-lookup"><span data-stu-id="d9c30-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="d9c30-124">Lorsque plusieurs regroupements sont spécifiés, ils sont itérés indépendamment ou vous pouvez les joindre s’ils sont liés.</span><span class="sxs-lookup"><span data-stu-id="d9c30-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="d9c30-125">Vous pouvez joindre implicitement des collections à l’aide de la `Select` clause, ou explicitement à l’aide des `Join` `Group Join` clauses ou.</span><span class="sxs-lookup"><span data-stu-id="d9c30-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="d9c30-126">En guise d’alternative, vous pouvez spécifier plusieurs variables de plage et collections dans une seule `From` clause, chaque variable de portée et collection étant séparée des autres par une virgule.</span><span class="sxs-lookup"><span data-stu-id="d9c30-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="d9c30-127">L’exemple de code suivant montre les deux options de syntaxe pour la `From` clause.</span><span class="sxs-lookup"><span data-stu-id="d9c30-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="d9c30-128">La `From` clause définit la portée d’une requête, qui est similaire à la portée d’une `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="d9c30-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="d9c30-129">Par conséquent, chaque variable de portée `element` dans l’étendue d’une requête doit avoir un nom unique.</span><span class="sxs-lookup"><span data-stu-id="d9c30-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="d9c30-130">Étant donné que vous pouvez spécifier plusieurs `From` clauses pour une requête, `From` les clauses suivantes peuvent faire référence à des variables de portée dans la `From` clause, ou elles peuvent faire référence à des variables de portée dans une `From` clause précédente.</span><span class="sxs-lookup"><span data-stu-id="d9c30-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="d9c30-131">Par exemple, l’exemple suivant montre une clause imbriquée dans `From` laquelle la collection de la deuxième clause est basée sur une propriété de la variable de portée dans la première clause.</span><span class="sxs-lookup"><span data-stu-id="d9c30-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="d9c30-132">Chaque `From` clause peut être suivie d’une combinaison quelconque de clauses de requête supplémentaires pour affiner la requête.</span><span class="sxs-lookup"><span data-stu-id="d9c30-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="d9c30-133">Vous pouvez affiner la requête de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="d9c30-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="d9c30-134">Combinez plusieurs collections implicitement en utilisant `From` les `Select` clauses et, ou explicitement à l’aide des `Join` `Group Join` clauses ou.</span><span class="sxs-lookup"><span data-stu-id="d9c30-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="d9c30-135">Utilisez la `Where` clause pour filtrer le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="d9c30-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="d9c30-136">Triez le résultat à l’aide de la `Order By` clause.</span><span class="sxs-lookup"><span data-stu-id="d9c30-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="d9c30-137">Regroupez les résultats similaires en utilisant la `Group By` clause.</span><span class="sxs-lookup"><span data-stu-id="d9c30-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="d9c30-138">Utilisez la `Aggregate` clause pour identifier les fonctions d’agrégation à évaluer pour l’ensemble du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="d9c30-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="d9c30-139">Utilisez la `Let` clause pour introduire une variable d’itération dont la valeur est déterminée par une expression au lieu d’une collection.</span><span class="sxs-lookup"><span data-stu-id="d9c30-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="d9c30-140">Utilisez la `Distinct` clause pour ignorer les résultats de la requête en double.</span><span class="sxs-lookup"><span data-stu-id="d9c30-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="d9c30-141">Identifiez les parties du résultat à retourner à l’aide des `Skip` `Take` `Skip While` clauses,, et `Take While` .</span><span class="sxs-lookup"><span data-stu-id="d9c30-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c30-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9c30-142">Example</span></span>  
 <span data-ttu-id="d9c30-143">L’expression de requête suivante utilise une `From` clause pour déclarer une variable `cust` de portée pour chaque `Customer` objet de la `customers` collection.</span><span class="sxs-lookup"><span data-stu-id="d9c30-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="d9c30-144">La `Where` clause utilise la variable de portée pour limiter la sortie aux clients de la région spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d9c30-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="d9c30-145">La `For Each` boucle affiche le nom de la société pour chaque client dans le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="d9c30-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="d9c30-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9c30-146">See also</span></span>

- [<span data-ttu-id="d9c30-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="d9c30-147">Queries</span></span>](index.md)
- [<span data-ttu-id="d9c30-148">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9c30-148">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d9c30-149">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="d9c30-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="d9c30-150">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="d9c30-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="d9c30-151">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="d9c30-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="d9c30-152">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="d9c30-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="d9c30-153">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="d9c30-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="d9c30-154">Distinct (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="d9c30-155">Join (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="d9c30-156">Group Join (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="d9c30-157">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="d9c30-158">Clause let</span><span class="sxs-lookup"><span data-stu-id="d9c30-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="d9c30-159">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="d9c30-160">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="d9c30-161">SkipWhile (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="d9c30-162">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="d9c30-162">Take While Clause</span></span>](take-while-clause.md)
