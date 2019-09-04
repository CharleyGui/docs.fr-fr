---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 3d3564c37d8971d3261cb47acb774bd1b9f92192
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249216"
---
# <a name="select-entity-sql"></a><span data-ttu-id="6e194-102">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6e194-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="6e194-103">Indique les éléments retournés par une requête.</span><span class="sxs-lookup"><span data-stu-id="6e194-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e194-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e194-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e194-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e194-105">Arguments</span></span>  
 <span data-ttu-id="6e194-106">ALL</span><span class="sxs-lookup"><span data-stu-id="6e194-106">ALL</span></span>  
 <span data-ttu-id="6e194-107">Indique que les doublons peuvent apparaître dans l'ensemble de résultats.</span><span class="sxs-lookup"><span data-stu-id="6e194-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="6e194-108">ALL est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e194-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="6e194-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="6e194-109">DISTINCT</span></span>  
 <span data-ttu-id="6e194-110">Indique que seuls les résultats uniques peuvent apparaître dans l'ensemble de résultats.</span><span class="sxs-lookup"><span data-stu-id="6e194-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="6e194-111">VALUE</span><span class="sxs-lookup"><span data-stu-id="6e194-111">VALUE</span></span>  
 <span data-ttu-id="6e194-112">Autorise la spécification d'un seul élément et n'ajoute pas de wrapper de ligne.</span><span class="sxs-lookup"><span data-stu-id="6e194-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="6e194-113">Toute expression valide indiquant le nombre de premiers résultats à retourner de la requête, sous la forme `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="6e194-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="6e194-114">Le paramètre LIMIT de l’opérateur [order by](order-by-entity-sql.md) vous permet également de sélectionner les n premiers éléments dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="6e194-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="6e194-115">Expression sous la forme :</span><span class="sxs-lookup"><span data-stu-id="6e194-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="6e194-116">`expr`comme `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="6e194-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="6e194-117">Littéral ou expression.</span><span class="sxs-lookup"><span data-stu-id="6e194-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e194-118">Notes</span><span class="sxs-lookup"><span data-stu-id="6e194-118">Remarks</span></span>  
 <span data-ttu-id="6e194-119">La clause SELECT est évaluée après l’évaluation des clauses [from](from-entity-sql.md), [Group by](group-by-entity-sql.md)et [having](having-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="6e194-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="6e194-120">La clause SELECT ne peut faire référence qu'aux éléments qui se trouvent actuellement dans l'étendue (de la clause FROM ou d'étendues externes).</span><span class="sxs-lookup"><span data-stu-id="6e194-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="6e194-121">Si une clause GROUP BY a été spécifiée, la clause SELECT ne peut faire référence qu'aux alias des clés GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="6e194-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="6e194-122">Le référencement des éléments de la clause FROM n'est autorisé que dans les fonctions d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="6e194-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="6e194-123">La liste constituée d'une ou plusieurs expressions de requête figurant après le mot clé SELECT est appelée « liste de sélection » ou, de manière plus formelle, « projection ».</span><span class="sxs-lookup"><span data-stu-id="6e194-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="6e194-124">La forme de projection la plus courante est une expression de requête unique.</span><span class="sxs-lookup"><span data-stu-id="6e194-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="6e194-125">Si vous sélectionnez un membre `member1` dans une collection `collection1`, vous générez une nouvelle collection constituée de toutes les valeurs `member1` pour chaque objet de `collection1`, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6e194-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="6e194-126">Par exemple, si `customers` est une collection de type `Customer` possédant une propriété `Name` de type `string`, le fait de sélectionner `Name` dans `customers` génèrera une collection de chaînes, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6e194-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="6e194-127">Il est également possible d'utiliser la syntaxe JOIN (FULL, INNER, LEFT, OUTER, ON et RIGHT).</span><span class="sxs-lookup"><span data-stu-id="6e194-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="6e194-128">ON est requis pour les jointures internes et n'est pas autorisé pour les jointures croisées.</span><span class="sxs-lookup"><span data-stu-id="6e194-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="6e194-129">Clauses « row select » et « value select »</span><span class="sxs-lookup"><span data-stu-id="6e194-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6e194-130">prend en charge deux variantes de la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="6e194-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="6e194-131">La première variante, « row select », est identifiée par le mot clé SELECT et peut être utilisée pour spécifier une ou plusieurs valeurs devant être projetées. Étant donné qu'un wrapper de ligne est implicitement ajouté de part et d'autre des valeurs retournées, le résultat de l'expression de requête est toujours un multiensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="6e194-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="6e194-132">Chaque expression de requête figurant dans une clause « row select » doit spécifier un alias.</span><span class="sxs-lookup"><span data-stu-id="6e194-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="6e194-133">Si aucun alias n'est spécifié,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] essaie d'en générer un en utilisant les règles de génération d'alias.</span><span class="sxs-lookup"><span data-stu-id="6e194-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="6e194-134">L'autre variante de la clause SELECT, « value select », est identifiée par le mot clé SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="6e194-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="6e194-135">Elle autorise la spécification d'une seule valeur et n'ajoute pas de wrapper de ligne.</span><span class="sxs-lookup"><span data-stu-id="6e194-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="6e194-136">Une clause « row select » peut toujours être exprimée en termes de sélection de valeur (SELECT VALUE), comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6e194-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="6e194-137">Modificateurs All et Distinct</span><span class="sxs-lookup"><span data-stu-id="6e194-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="6e194-138">Les deux variantes de la clause SELECT d' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permettent de spécifier un modificateur ALL ou DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="6e194-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="6e194-139">Si le modificateur DISTINCT est spécifié, les doublons sont éliminés de la collection créée par l'expression de requête (jusqu'à la clause SELECT elle-même incluse).</span><span class="sxs-lookup"><span data-stu-id="6e194-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="6e194-140">Si le modificateur ALL est spécifié, aucune élimination de doublons n'est réalisée ; ALL est spécifié par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e194-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="6e194-141">Différences par rapport à Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e194-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="6e194-142">Contrairement à Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge l'utilisation de l'argument \* dans la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="6e194-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="6e194-143">En revanche, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] autorise les requêtes pour projeter des enregistrements entiers en faisant référence aux alias de collection de la clause FROM, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6e194-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="6e194-144">L’expression de requête Transact-SQL précédente est exprimée [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dans de la façon suivante.</span><span class="sxs-lookup"><span data-stu-id="6e194-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="6e194-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e194-145">Example</span></span>  
 <span data-ttu-id="6e194-146">La requête Entity SQL ci-dessous utilise l'opérateur SELECT pour spécifier les éléments qu'une requête doit retourner.</span><span class="sxs-lookup"><span data-stu-id="6e194-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="6e194-147">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="6e194-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6e194-148">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6e194-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6e194-149">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="6e194-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6e194-150">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="6e194-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="6e194-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e194-151">See also</span></span>

- [<span data-ttu-id="6e194-152">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="6e194-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="6e194-153">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6e194-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6e194-154">TOP</span><span class="sxs-lookup"><span data-stu-id="6e194-154">TOP</span></span>](top-entity-sql.md)
