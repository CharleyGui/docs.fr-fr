---
title: Traduction des opérateurs de requête standard
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: af22b6a895fef8037eb5c069ffb7cb23d1333531
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833683"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="dea63-102">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="dea63-102">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-103">traduit les opérateurs de requête standard en commandes SQL.</span><span class="sxs-lookup"><span data-stu-id="dea63-103">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="dea63-104">Le processeur de requêtes de la base de données détermine la sémantique d’exécution de la traduction SQL.</span><span class="sxs-lookup"><span data-stu-id="dea63-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="dea63-105">Les opérateurs de requête standard sont définis par rapport aux *séquences*.</span><span class="sxs-lookup"><span data-stu-id="dea63-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="dea63-106">Une séquence est *ordonnée* et s’appuie sur l’identité de référence pour chaque élément de la séquence.</span><span class="sxs-lookup"><span data-stu-id="dea63-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="dea63-107">Pour plus d’informations, consultez [vue d’ensemble desC#opérateurs de requête standard ()](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ou [vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dea63-107">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="dea63-108">SQL traite principalement des *ensembles de valeurs non ordonnés*.</span><span class="sxs-lookup"><span data-stu-id="dea63-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="dea63-109">Le classement est généralement une opération de post-traitement déclarée explicitement appliquée au résultat final d'une requête plutôt qu'à des résultats intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="dea63-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="dea63-110">L'identité est définie par des valeurs.</span><span class="sxs-lookup"><span data-stu-id="dea63-110">Identity is defined by values.</span></span> <span data-ttu-id="dea63-111">C’est la raison pour laquelle les requêtes SQL sont comprises pour traiter les multijeux (*sacs*) au lieu de *jeux*.</span><span class="sxs-lookup"><span data-stu-id="dea63-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="dea63-112">Les paragraphes suivants décrivent les différences entre les opérateurs de requête standard et leur traduction SQL pour le fournisseur SQL Server de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dea63-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="dea63-113">Prise en charge des opérateurs</span><span class="sxs-lookup"><span data-stu-id="dea63-113">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="dea63-114">Concat</span><span class="sxs-lookup"><span data-stu-id="dea63-114">Concat</span></span>

<span data-ttu-id="dea63-115">La méthode <xref:System.Linq.Enumerable.Concat%2A> est définie pour des multijeux ordonnés lorsque les ordres du récepteur et de l’argument sont identiques.</span><span class="sxs-lookup"><span data-stu-id="dea63-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="dea63-116"><xref:System.Linq.Enumerable.Concat%2A> fonctionne comme `UNION ALL` sur les multijeux suivis de l’ordre courant.</span><span class="sxs-lookup"><span data-stu-id="dea63-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="dea63-117">L'étape finale est le classement dans SQL avant que les résultats ne soient générés.</span><span class="sxs-lookup"><span data-stu-id="dea63-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="dea63-118"><xref:System.Linq.Enumerable.Concat%2A> ne conserve pas l’ordre de ses arguments.</span><span class="sxs-lookup"><span data-stu-id="dea63-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="dea63-119">Pour garantir un classement approprié, vous devez classer explicitement les résultats de <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="dea63-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="dea63-120">Intersect, Except, Union</span><span class="sxs-lookup"><span data-stu-id="dea63-120">Intersect, Except, Union</span></span>

<span data-ttu-id="dea63-121">Les méthodes <xref:System.Linq.Enumerable.Intersect%2A> et <xref:System.Linq.Enumerable.Except%2A> sont bien définies sur les jeux uniquement.</span><span class="sxs-lookup"><span data-stu-id="dea63-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="dea63-122">La sémantique pour les multijeux n'est pas définie.</span><span class="sxs-lookup"><span data-stu-id="dea63-122">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="dea63-123">La méthode <xref:System.Linq.Enumerable.Union%2A> est définie pour les multijeux comme la concaténation non ordonnée des multijeux (le résultat de la clause UNION ALL dans SQL).</span><span class="sxs-lookup"><span data-stu-id="dea63-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="dea63-124">Take, Skip</span><span class="sxs-lookup"><span data-stu-id="dea63-124">Take, Skip</span></span>

<span data-ttu-id="dea63-125">les méthodes <xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A> sont bien définies uniquement par rapport aux *jeux ordonnés*.</span><span class="sxs-lookup"><span data-stu-id="dea63-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="dea63-126">La sémantique des jeux non ordonnés ou des multijeux n'est pas définie.</span><span class="sxs-lookup"><span data-stu-id="dea63-126">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="dea63-127"><xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A> présentent certaines limitations lorsqu’elles sont utilisées dans des requêtes sur SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="dea63-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="dea63-128">Pour plus d’informations, consultez l’entrée « ignorer et prendre des exceptions dans SQL Server 2000 » dans [résolution des problèmes](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="dea63-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

<span data-ttu-id="dea63-129">En raison des limitations de classement dans SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tente de déplacer le classement de l’argument de ces méthodes vers le résultat de la méthode.</span><span class="sxs-lookup"><span data-stu-id="dea63-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="dea63-130">Prenons l'exemple de la requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suivante :</span><span class="sxs-lookup"><span data-stu-id="dea63-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="dea63-131">Le SQL généré pour ce code déplace le classement à la fin, comme suit :</span><span class="sxs-lookup"><span data-stu-id="dea63-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="dea63-132">Il devient évident que le classement spécifié doit être cohérent lorsque <xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A> sont enchaînés.</span><span class="sxs-lookup"><span data-stu-id="dea63-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="dea63-133">Si ce n'est pas le cas, les résultats ne sont pas définis.</span><span class="sxs-lookup"><span data-stu-id="dea63-133">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="dea63-134"><xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A> sont bien définis pour des arguments intégraux constants non négatifs basés sur la spécification de l’opérateur de requête standard.</span><span class="sxs-lookup"><span data-stu-id="dea63-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="dea63-135">Opérateurs sans traduction</span><span class="sxs-lookup"><span data-stu-id="dea63-135">Operators with No Translation</span></span>

<span data-ttu-id="dea63-136">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne traduit pas les méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="dea63-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="dea63-137">La raison la plus courante est la différence entre les multijeux non ordonnés et les séquences.</span><span class="sxs-lookup"><span data-stu-id="dea63-137">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="dea63-138">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="dea63-138">Operators</span></span>|<span data-ttu-id="dea63-139">Raisonnement</span><span class="sxs-lookup"><span data-stu-id="dea63-139">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="dea63-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="dea63-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="dea63-141">Les requêtes SQL fonctionnent sur des multijeux et non sur des séquences.</span><span class="sxs-lookup"><span data-stu-id="dea63-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="dea63-142">`ORDER BY` doit être la dernière clause appliquée aux résultats.</span><span class="sxs-lookup"><span data-stu-id="dea63-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="dea63-143">Il n'existe donc aucune traduction à caractère général pour ces deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="dea63-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="dea63-144">La traduction de cette méthode est possible pour un jeu ordonné mais n'est pas fournie actuellement par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dea63-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="dea63-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="dea63-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="dea63-146">La traduction de ces méthodes est possible pour un jeu ordonné mais n'est pas fournie actuellement par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dea63-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="dea63-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="dea63-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="dea63-148">Les requêtes SQL fonctionnent sur des multijeux et non sur des séquences indexables.</span><span class="sxs-lookup"><span data-stu-id="dea63-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="dea63-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (surcharge avec ARG par défaut)</span><span class="sxs-lookup"><span data-stu-id="dea63-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="dea63-150">En général, il est impossible de spécifier une valeur par défaut pour un tuple arbitraire.</span><span class="sxs-lookup"><span data-stu-id="dea63-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="dea63-151">Les valeurs null pour les tuples sont possibles dans certains cas par le biais de jointures externes.</span><span class="sxs-lookup"><span data-stu-id="dea63-151">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="dea63-152">Traduction d'expression</span><span class="sxs-lookup"><span data-stu-id="dea63-152">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="dea63-153">Sémantique Null</span><span class="sxs-lookup"><span data-stu-id="dea63-153">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-154">n’impose pas la sémantique de comparaison null sur SQL.</span><span class="sxs-lookup"><span data-stu-id="dea63-154">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="dea63-155">Les opérateurs de comparaison sont traduits syntaxiquement dans leurs équivalents SQL.</span><span class="sxs-lookup"><span data-stu-id="dea63-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="dea63-156">Pour cette raison, la sémantique reflète la sémantique SQL définie par le serveur ou les paramètres de connexion.</span><span class="sxs-lookup"><span data-stu-id="dea63-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="dea63-157">Par exemple, deux valeurs NULL sont considérées comme non égales sous les paramètres par défaut SQL Server, mais vous pouvez modifier les paramètres pour changer la sémantique.</span><span class="sxs-lookup"><span data-stu-id="dea63-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-158">ne tient pas compte des paramètres du serveur lorsqu’il traduit des requêtes.</span><span class="sxs-lookup"><span data-stu-id="dea63-158">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="dea63-159">Une comparaison avec le littéral null est traduite dans la version SQL appropriée (`is null` ou `is not null`).</span><span class="sxs-lookup"><span data-stu-id="dea63-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="dea63-160">La valeur `null` dans le classement est définie par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dea63-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-161">ne modifie pas le classement.</span><span class="sxs-lookup"><span data-stu-id="dea63-161">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="dea63-162">Agrégats</span><span class="sxs-lookup"><span data-stu-id="dea63-162">Aggregates</span></span>

<span data-ttu-id="dea63-163">La méthode d'agrégation (opérateur de requête standard) <xref:System.Linq.Enumerable.Sum%2A> prend la valeur zéro pour une séquence vide ou contenant uniquement des valeurs null.</span><span class="sxs-lookup"><span data-stu-id="dea63-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="dea63-164">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la sémantique de SQL reste inchangée et <xref:System.Linq.Enumerable.Sum%2A> prend la valeur `null` au lieu de zéro pour une séquence vide ou pour une séquence qui contient uniquement des valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="dea63-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="dea63-165">Les limitations SQL sur les résultats intermédiaires s'appliquent aux agrégats dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dea63-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="dea63-166">Le <xref:System.Linq.Enumerable.Sum%2A> de quantités d'entiers 32 bits n'est pas calculé à partir des résultats 64 bits.</span><span class="sxs-lookup"><span data-stu-id="dea63-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="dea63-167">Un dépassement de capacité peut se produire pour une traduction [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de <xref:System.Linq.Enumerable.Sum%2A>, même si l'implémentation de l'opérateur de requête standard n'entraîne pas de dépassement de capacité pour la séquence en mémoire correspondante.</span><span class="sxs-lookup"><span data-stu-id="dea63-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="dea63-168">De même, la traduction [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de <xref:System.Linq.Enumerable.Average%2A> pour des valeurs entières est calculée comme un `integer` et non comme un `double`.</span><span class="sxs-lookup"><span data-stu-id="dea63-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="dea63-169">Arguments d’entité</span><span class="sxs-lookup"><span data-stu-id="dea63-169">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-170">permet d’utiliser les types d’entités dans les méthodes de <xref:System.Linq.Enumerable.GroupBy%2A> et de <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="dea63-170">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="dea63-171">Dans la traduction de ces opérateurs, l’utilisation d’un argument d’un type est considérée comme équivalente à la spécification de tous les membres de ce type.</span><span class="sxs-lookup"><span data-stu-id="dea63-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="dea63-172">Par exemple, le code suivant est équivalent :</span><span class="sxs-lookup"><span data-stu-id="dea63-172">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="dea63-173">Arguments égaux/comparables</span><span class="sxs-lookup"><span data-stu-id="dea63-173">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="dea63-174">L’implémentation des méthodes suivantes nécessite l’égalité des arguments :</span><span class="sxs-lookup"><span data-stu-id="dea63-174">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-175">prend en charge l’égalité et la comparaison des arguments *plats* , mais pas pour les arguments qui contiennent ou contiennent des séquences.</span><span class="sxs-lookup"><span data-stu-id="dea63-175">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="dea63-176">Un argument plat est un type qui peut être mappé à une ligne SQL.</span><span class="sxs-lookup"><span data-stu-id="dea63-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="dea63-177">Une projection d'un ou de plusieurs types d'entité qui peuvent être déterminés statiquement comme ne contenant pas de séquence est considérée comme un argument plat.</span><span class="sxs-lookup"><span data-stu-id="dea63-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="dea63-178">Voici quelques exemples d’arguments plats :</span><span class="sxs-lookup"><span data-stu-id="dea63-178">The following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="dea63-179">Voici des exemples d’arguments non plats (hiérarchiques) :</span><span class="sxs-lookup"><span data-stu-id="dea63-179">The following are examples of non-flat (hierarchical) arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="dea63-180">Traduction de fonctions Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dea63-180">Visual Basic Function Translation</span></span>

<span data-ttu-id="dea63-181">Les fonctions d'assistance suivantes utilisées par le compilateur Visual Basic sont traduites en opérateurs et en fonctions SQL correspondants :</span><span class="sxs-lookup"><span data-stu-id="dea63-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="dea63-182">Méthodes de conversion :</span><span class="sxs-lookup"><span data-stu-id="dea63-182">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="dea63-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="dea63-183">ToBoolean</span></span>|<span data-ttu-id="dea63-184">ToSByte</span><span class="sxs-lookup"><span data-stu-id="dea63-184">ToSByte</span></span>|<span data-ttu-id="dea63-185">ToByte</span><span class="sxs-lookup"><span data-stu-id="dea63-185">ToByte</span></span>|<span data-ttu-id="dea63-186">ToChar</span><span class="sxs-lookup"><span data-stu-id="dea63-186">ToChar</span></span>|
|<span data-ttu-id="dea63-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="dea63-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="dea63-188">ToDate</span><span class="sxs-lookup"><span data-stu-id="dea63-188">ToDate</span></span>|<span data-ttu-id="dea63-189">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="dea63-189">ToDecimal</span></span>|<span data-ttu-id="dea63-190">ToDouble</span><span class="sxs-lookup"><span data-stu-id="dea63-190">ToDouble</span></span>|
|<span data-ttu-id="dea63-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="dea63-191">ToInteger</span></span>|<span data-ttu-id="dea63-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="dea63-192">ToUInteger</span></span>|<span data-ttu-id="dea63-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="dea63-193">ToLong</span></span>|<span data-ttu-id="dea63-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="dea63-194">ToULong</span></span>|
|<span data-ttu-id="dea63-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="dea63-195">ToShort</span></span>|<span data-ttu-id="dea63-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="dea63-196">ToUShort</span></span>|<span data-ttu-id="dea63-197">ToSingle</span><span class="sxs-lookup"><span data-stu-id="dea63-197">ToSingle</span></span>|<span data-ttu-id="dea63-198">ToString</span><span class="sxs-lookup"><span data-stu-id="dea63-198">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="dea63-199">Prise en charge de l'héritage</span><span class="sxs-lookup"><span data-stu-id="dea63-199">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="dea63-200">Restrictions du mappage d'héritage</span><span class="sxs-lookup"><span data-stu-id="dea63-200">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="dea63-201">Pour plus d’informations, consultez [Comment : mapper des hiérarchies d’héritage](how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="dea63-201">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="dea63-202">Héritage dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="dea63-202">Inheritance in Queries</span></span>

<span data-ttu-id="dea63-203">Les casts C# sont pris en charge uniquement dans la projection.</span><span class="sxs-lookup"><span data-stu-id="dea63-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="dea63-204">Les casts utilisés ailleurs ne sont pas traduits et sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="dea63-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="dea63-205">Hormis les noms de fonction SQL, SQL effectue uniquement l'équivalent du <xref:System.Convert> CLR.</span><span class="sxs-lookup"><span data-stu-id="dea63-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="dea63-206">Autrement dit, SQL peut modifier la valeur d'un type en un autre.</span><span class="sxs-lookup"><span data-stu-id="dea63-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="dea63-207">Le cast CLR n'a pas d'équivalent car il n'existe pas de concept de réinterprétation des mêmes bits que ceux d'un autre type.</span><span class="sxs-lookup"><span data-stu-id="dea63-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="dea63-208">C'est pourquoi un cast C# fonctionne uniquement en local.</span><span class="sxs-lookup"><span data-stu-id="dea63-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="dea63-209">Il n'est pas mis à distance.</span><span class="sxs-lookup"><span data-stu-id="dea63-209">It is not remoted.</span></span>

<span data-ttu-id="dea63-210">Les opérateurs `is` et `as` et la méthode `GetType` ne sont pas restreints à l'opérateur `Select`.</span><span class="sxs-lookup"><span data-stu-id="dea63-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="dea63-211">Ils peuvent également être utilisés dans d'autres opérateurs de requête.</span><span class="sxs-lookup"><span data-stu-id="dea63-211">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="dea63-212">Prise en charge de SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="dea63-212">SQL Server 2008 Support</span></span>

<span data-ttu-id="dea63-213">À partir du .NET Framework version 3.5 SP1, LINQ to SQL prend en charge le mappage aux nouveaux types de date et d'heure introduits avec SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="dea63-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="dea63-214">Cependant, il existe certaines limites concernant les opérateurs de requête LINQ to SQL pris en charge pour les valeurs mappées à ces nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="dea63-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="dea63-215">Opérateurs de requête non pris en charge</span><span class="sxs-lookup"><span data-stu-id="dea63-215">Unsupported Query Operators</span></span>

<span data-ttu-id="dea63-216">Les opérateurs de requête suivants ne sont pas pris en charge pour les valeurs mappées aux nouveaux types de date et d'heure SQL Server : `DATETIME2`, `DATE`, `TIME` et `DATETIMEOFFSET`.</span><span class="sxs-lookup"><span data-stu-id="dea63-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="dea63-217">Pour plus d’informations sur le mappage à ces SQL Server types de date et d’heure, consultez [mappage de type SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="dea63-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="dea63-218">Prise en charge de SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="dea63-218">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-219">ne prend pas en charge les fonctionnalités SQL Server 2005 suivantes :</span><span class="sxs-lookup"><span data-stu-id="dea63-219">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="dea63-220">Procédures stockées écrites pour le CLR SQL.</span><span class="sxs-lookup"><span data-stu-id="dea63-220">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="dea63-221">Type défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dea63-221">User-defined type.</span></span>

- <span data-ttu-id="dea63-222">Fonctionnalités de requête XML.</span><span class="sxs-lookup"><span data-stu-id="dea63-222">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="dea63-223">Prise en charge de SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="dea63-223">SQL Server 2000 Support</span></span>

<span data-ttu-id="dea63-224">Les limitations suivantes de l’SQL Server 2000 (par rapport à Microsoft SQL Server 2005) affectent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prise en charge.</span><span class="sxs-lookup"><span data-stu-id="dea63-224">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="dea63-225">Opérateurs Cross Apply et Outer Apply</span><span class="sxs-lookup"><span data-stu-id="dea63-225">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="dea63-226">Ces opérateurs ne sont pas disponibles dans SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="dea63-226">These operators are not available in SQL Server 2000.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dea63-227">tente une série de réécritures pour les remplacer par des jointures appropriées.</span><span class="sxs-lookup"><span data-stu-id="dea63-227">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="dea63-228">`Cross Apply` et `Outer Apply` sont générés pour les navigations de relation.</span><span class="sxs-lookup"><span data-stu-id="dea63-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="dea63-229">Le jeu des requêtes pour lequel ces réécritures sont possibles n'est pas bien défini.</span><span class="sxs-lookup"><span data-stu-id="dea63-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="dea63-230">Pour cette raison, l’ensemble minimal de requêtes prises en charge pour SQL Server 2000 est l’ensemble qui n’implique pas de navigation entre les relations.</span><span class="sxs-lookup"><span data-stu-id="dea63-230">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="dea63-231">text / ntext</span><span class="sxs-lookup"><span data-stu-id="dea63-231">text / ntext</span></span>

<span data-ttu-id="dea63-232">Les types de données `text` / `ntext` ne peuvent pas être utilisés dans certaines opérations de requête sur `varchar(max)` / `nvarchar(max)`, qui sont pris en charge par Microsoft SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="dea63-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="dea63-233">Aucune résolution n’est disponible pour cette limitation.</span><span class="sxs-lookup"><span data-stu-id="dea63-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="dea63-234">Précisément, vous ne pouvez pas utiliser `Distinct()` sur des résultats contenant des membres mappés à des colonnes `text` ou `ntext`.</span><span class="sxs-lookup"><span data-stu-id="dea63-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="dea63-235">Comportement déclenché par les sous-requêtes</span><span class="sxs-lookup"><span data-stu-id="dea63-235">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="dea63-236">Le classeur SQL Server 2000 (via SP4) a certaines particularités qui sont déclenchées par des requêtes imbriquées.</span><span class="sxs-lookup"><span data-stu-id="dea63-236">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="dea63-237">Le jeu de requêtes SQL qui déclenche ces spécificités n'est pas bien défini.</span><span class="sxs-lookup"><span data-stu-id="dea63-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="dea63-238">Pour cette raison, vous ne pouvez pas définir le jeu de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requêtes qui peuvent provoquer des exceptions de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dea63-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="dea63-239">Opérateurs Skip et Take</span><span class="sxs-lookup"><span data-stu-id="dea63-239">Skip and Take Operators</span></span>

<span data-ttu-id="dea63-240"><xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A> présentent certaines limitations lorsqu’elles sont utilisées dans des requêtes sur SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="dea63-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="dea63-241">Pour plus d’informations, consultez l’entrée « ignorer et prendre des exceptions dans SQL Server 2000 » dans [résolution des problèmes](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="dea63-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="dea63-242">Matérialisation d'objet</span><span class="sxs-lookup"><span data-stu-id="dea63-242">Object Materialization</span></span>

<span data-ttu-id="dea63-243">La matérialisation crée des objets CLR à partir de lignes retournées par une ou plusieurs requêtes SQL.</span><span class="sxs-lookup"><span data-stu-id="dea63-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="dea63-244">Les appels suivants sont *exécutés localement* dans le cadre de la matérialisation :</span><span class="sxs-lookup"><span data-stu-id="dea63-244">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="dea63-245">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="dea63-245">Constructors</span></span>

  - <span data-ttu-id="dea63-246">`ToString` méthodes dans les projections</span><span class="sxs-lookup"><span data-stu-id="dea63-246">`ToString` methods in projections</span></span>

  - <span data-ttu-id="dea63-247">Casts de type dans les projections</span><span class="sxs-lookup"><span data-stu-id="dea63-247">Type casts in projections</span></span>

- <span data-ttu-id="dea63-248">Les méthodes qui suivent la méthode <xref:System.Linq.Enumerable.AsEnumerable%2A> sont *exécutées localement*.</span><span class="sxs-lookup"><span data-stu-id="dea63-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="dea63-249">Cette méthode ne provoque pas d'exécution immédiate.</span><span class="sxs-lookup"><span data-stu-id="dea63-249">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="dea63-250">Vous pouvez utiliser un `struct` comme type de retour d'un résultat de requête ou comme membre du type de résultat.</span><span class="sxs-lookup"><span data-stu-id="dea63-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="dea63-251">Les entités doivent être des classes.</span><span class="sxs-lookup"><span data-stu-id="dea63-251">Entities are required to be classes.</span></span> <span data-ttu-id="dea63-252">Les types anonymes sont matérialisés en instances de classe, mais les structs nommés (non entités) peuvent être utilisés dans la projection.</span><span class="sxs-lookup"><span data-stu-id="dea63-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="dea63-253">Un membre du type de retour d’un résultat de requête peut être de type <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="dea63-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="dea63-254">Il est matérialisé en collection locale.</span><span class="sxs-lookup"><span data-stu-id="dea63-254">It is materialized as a local collection.</span></span>

- <span data-ttu-id="dea63-255">Les méthodes suivantes provoquent la *matérialisation immédiate* de la séquence à laquelle les méthodes sont appliquées :</span><span class="sxs-lookup"><span data-stu-id="dea63-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="dea63-256">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dea63-256">See also</span></span>

- [<span data-ttu-id="dea63-257">Référence</span><span class="sxs-lookup"><span data-stu-id="dea63-257">Reference</span></span>](reference.md)
- [<span data-ttu-id="dea63-258">Retourner ou ignorer des éléments d’une séquence</span><span class="sxs-lookup"><span data-stu-id="dea63-258">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="dea63-259">Concaténer deux séquences</span><span class="sxs-lookup"><span data-stu-id="dea63-259">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)
- [<span data-ttu-id="dea63-260">Retourner la différence définie entre deux séquences</span><span class="sxs-lookup"><span data-stu-id="dea63-260">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="dea63-261">Retourner l’intersection définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="dea63-261">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="dea63-262">Retourner l’union définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="dea63-262">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)
