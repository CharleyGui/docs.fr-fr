---
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 281d5d2df389f0952f0552747fa12b67b14d470c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204487"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="53b20-102">GROUP BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="53b20-102">GROUP BY (Entity SQL)</span></span>

<span data-ttu-id="53b20-103">Indique les groupes dans lesquels doivent être placés les objets retournés par une expression de requête ([SELECT](select-entity-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="53b20-103">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53b20-104">Syntax</span></span>  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="53b20-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="53b20-105">Arguments</span></span>  

 `aliasedExpression`  
 <span data-ttu-id="53b20-106">Toute expression de requête valide sur laquelle le regroupement est effectué.</span><span class="sxs-lookup"><span data-stu-id="53b20-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="53b20-107">`expression` peut être une propriété ou une expression non agrégée qui référence une propriété retournée par la clause FROM.</span><span class="sxs-lookup"><span data-stu-id="53b20-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="53b20-108">Chaque expression contenue dans une clause GROUP BY doit être évaluée à un type pouvant être comparé en égalité.</span><span class="sxs-lookup"><span data-stu-id="53b20-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="53b20-109">Ces types sont généralement des primitives scalaires telles que des nombres, des chaînes et des dates.</span><span class="sxs-lookup"><span data-stu-id="53b20-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="53b20-110">Vous ne pouvez pas effectuer de regroupement sur une collection.</span><span class="sxs-lookup"><span data-stu-id="53b20-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53b20-111">Notes</span><span class="sxs-lookup"><span data-stu-id="53b20-111">Remarks</span></span>  

 <span data-ttu-id="53b20-112">Si les fonctions d’agrégation sont incluses dans la clause SELECT \<select list> , Group by calcule une valeur de synthèse pour chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="53b20-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="53b20-113">Lorsque la clause GROUP BY est spécifiée, vous devez inclure dans la liste GROUP BY chaque nom de propriété des expressions de non-agrégation figurant dans la liste de sélection, ou l'expression GROUP BY doit correspondre exactement à l'expression figurant dans la liste de sélection.</span><span class="sxs-lookup"><span data-stu-id="53b20-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53b20-114">Si la clause ORDER BY n'est pas spécifiée, les groupes retournés par la clause GROUP BY ne sont pas triés dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="53b20-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="53b20-115">Nous vous recommandons de toujours utiliser la clause ORDER BY pour définir un ordre de classement des données particulier.</span><span class="sxs-lookup"><span data-stu-id="53b20-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="53b20-116">Lorsqu'une clause GROUP BY est spécifiée, explicitement ou implicitement (par exemple, par une clause HAVING dans la requête), l'étendue actuelle est masquée, et une nouvelle étendue est introduite.</span><span class="sxs-lookup"><span data-stu-id="53b20-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="53b20-117">La clause SELECT, la clause HAVING et la clause ORDER BY ne pourront plus faire référence aux noms d'élément spécifiés dans la clause FROM.</span><span class="sxs-lookup"><span data-stu-id="53b20-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="53b20-118">Vous ne pouvez faire référence qu'aux expressions de regroupement proprement dites.</span><span class="sxs-lookup"><span data-stu-id="53b20-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="53b20-119">Pour ce faire, vous pouvez attribuer de nouveaux noms (alias) à chaque expression de regroupement.</span><span class="sxs-lookup"><span data-stu-id="53b20-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="53b20-120">Si aucun alias n'est spécifié pour une expression de regroupement, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] essaie d'en générer un en utilisant les règles de génération d'alias, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="53b20-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="53b20-121">Les expressions contenues dans la clause GROUP BY ne peuvent pas faire référence aux noms définis précédemment dans cette même clause GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="53b20-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="53b20-122">En plus de regrouper des noms, vous pouvez également spécifier des agrégats dans la clause SELECT, la clause HAVING et la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="53b20-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="53b20-123">Un agrégat contient une expression évaluée pour chaque élément du groupe.</span><span class="sxs-lookup"><span data-stu-id="53b20-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="53b20-124">L'opérateur d'agrégation réduit les valeurs de toutes ces expressions (généralement, mais pas systématiquement, à une valeur unique).</span><span class="sxs-lookup"><span data-stu-id="53b20-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="53b20-125">L'expression d'agrégation peut afficher dans l'étendue parente les références aux noms d'élément d'origine ou aux nouveaux noms introduits par la clause GROUP BY elle-même.</span><span class="sxs-lookup"><span data-stu-id="53b20-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="53b20-126">Bien que les agrégats apparaissent dans les clauses SELECT, HAVING et ORDER BY, ils sont en réalité évalués d'après la même étendue en tant qu'expressions de regroupement, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="53b20-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="53b20-127">Cette requête utilise la clause GROUP BY pour générer un rapport sur le coût de tous les produits commandés, réparti par produit.</span><span class="sxs-lookup"><span data-stu-id="53b20-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="53b20-128">Elle attribue le nom `name` au produit dans le cadre de l'expression de regroupement, puis référence ce nom dans la liste SELECT.</span><span class="sxs-lookup"><span data-stu-id="53b20-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="53b20-129">Elle spécifie également l'agrégat `sum` dans la liste SELECT qui référence en interne le prix et la quantité de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="53b20-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="53b20-130">Chaque expression clé GROUP BY doit comporter au moins une référence à l'étendue d'entrée :</span><span class="sxs-lookup"><span data-stu-id="53b20-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="53b20-131">Pour obtenir un exemple d’utilisation de GROUP BY, consultez [HAVING](having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="53b20-131">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53b20-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="53b20-132">Example</span></span>  

 <span data-ttu-id="53b20-133">La requête Entity SQL suivante utilise l'opérateur GROUP BY pour spécifier les groupes dans lesquels les objets sont retournés par une requête.</span><span class="sxs-lookup"><span data-stu-id="53b20-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="53b20-134">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="53b20-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="53b20-135">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="53b20-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="53b20-136">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="53b20-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="53b20-137">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="53b20-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="53b20-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53b20-138">See also</span></span>

- [<span data-ttu-id="53b20-139">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="53b20-139">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="53b20-140">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="53b20-140">Query Expressions</span></span>](query-expressions-entity-sql.md)
