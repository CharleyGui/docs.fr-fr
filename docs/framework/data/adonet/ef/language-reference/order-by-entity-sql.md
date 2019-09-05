---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: f3310274766ff3619604e30bfb5f5ca437cb1acd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249750"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="02b57-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="02b57-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="02b57-103">Spécifie l'ordre de classement utilisé sur les objets retournés dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="02b57-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02b57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02b57-104">Syntax</span></span>  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="02b57-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="02b57-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="02b57-106">Toute expression de requête valide qui spécifie une propriété sur laquelle doit porter le tri.</span><span class="sxs-lookup"><span data-stu-id="02b57-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="02b57-107">Vous pouvez spécifier plusieurs expressions de classement.</span><span class="sxs-lookup"><span data-stu-id="02b57-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="02b57-108">L'ordre des expressions de classement dans la clause ORDER BY détermine l'organisation de l'ensemble de résultats trié.</span><span class="sxs-lookup"><span data-stu-id="02b57-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="02b57-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="02b57-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="02b57-110">Indique que l'opération ORDER BY doit être effectuée en fonction du classement spécifié dans `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="02b57-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="02b57-111">COLLATE ne peut s'appliquer qu'aux expressions de chaîne.</span><span class="sxs-lookup"><span data-stu-id="02b57-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="02b57-112">ASC</span><span class="sxs-lookup"><span data-stu-id="02b57-112">ASC</span></span>  
 <span data-ttu-id="02b57-113">Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre croissant, de la plus petite à la plus grande.</span><span class="sxs-lookup"><span data-stu-id="02b57-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="02b57-114">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="02b57-114">This is the default.</span></span>  
  
 <span data-ttu-id="02b57-115">DESC</span><span class="sxs-lookup"><span data-stu-id="02b57-115">DESC</span></span>  
 <span data-ttu-id="02b57-116">Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre décroissant, de la plus grande à la plus petite.</span><span class="sxs-lookup"><span data-stu-id="02b57-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="02b57-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="02b57-117">LIMIT `n`</span></span>  
 <span data-ttu-id="02b57-118">Seuls les `n` premiers éléments sont sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="02b57-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="02b57-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="02b57-119">SKIP `n`</span></span>  
 <span data-ttu-id="02b57-120">Ignore les `n` premiers éléments.</span><span class="sxs-lookup"><span data-stu-id="02b57-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02b57-121">Notes</span><span class="sxs-lookup"><span data-stu-id="02b57-121">Remarks</span></span>  
 <span data-ttu-id="02b57-122">La clause ORDER BY est logiquement appliquée au résultat de la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="02b57-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="02b57-123">La clause ORDER BY peut faire référence aux éléments de la liste de sélection avec leurs alias.</span><span class="sxs-lookup"><span data-stu-id="02b57-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="02b57-124">La clause ORDER BY peut également faire référence à d'autres variables qui se trouvent actuellement dans l'étendue.</span><span class="sxs-lookup"><span data-stu-id="02b57-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="02b57-125">Toutefois, si la clause SELECT a été spécifiée avec un modificateur DISTINCT, la clause ORDER BY ne peut faire référence qu'à des alias de la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="02b57-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="02b57-126">Chaque expression contenue dans la clause ORDER BY doit correspondre à un type pouvant être comparé en inégalité (inférieur à ou supérieur à, etc.).</span><span class="sxs-lookup"><span data-stu-id="02b57-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="02b57-127">Ces types sont généralement des primitives scalaires telles que des nombres, des chaînes et des dates.</span><span class="sxs-lookup"><span data-stu-id="02b57-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="02b57-128">Les RowTypes de type comparable peuvent également être comparés sur le plan de l'ordre de classement.</span><span class="sxs-lookup"><span data-stu-id="02b57-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="02b57-129">Si votre code effectue une itération sur un ensemble ordonné autre qu'une projection de niveau supérieur, il n'est pas garanti que le résultat conservera son ordre de classement.</span><span class="sxs-lookup"><span data-stu-id="02b57-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="02b57-130">Pour une opération UNION, UNION ALL, EXCEPT ou INTERSECT triée, utilisez le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="02b57-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="02b57-131">Mots clés restreints</span><span class="sxs-lookup"><span data-stu-id="02b57-131">Restricted keywords</span></span>  
 <span data-ttu-id="02b57-132">Les mots clés suivants doivent être mis entre guillemets lorsqu'ils sont utilisés dans une clause `ORDER BY` :</span><span class="sxs-lookup"><span data-stu-id="02b57-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="02b57-133">CROSS</span><span class="sxs-lookup"><span data-stu-id="02b57-133">CROSS</span></span>  
  
- <span data-ttu-id="02b57-134">FULL</span><span class="sxs-lookup"><span data-stu-id="02b57-134">FULL</span></span>  
  
- <span data-ttu-id="02b57-135">KEY</span><span class="sxs-lookup"><span data-stu-id="02b57-135">KEY</span></span>  
  
- <span data-ttu-id="02b57-136">LEFT</span><span class="sxs-lookup"><span data-stu-id="02b57-136">LEFT</span></span>  
  
- <span data-ttu-id="02b57-137">ORDER</span><span class="sxs-lookup"><span data-stu-id="02b57-137">ORDER</span></span>  
  
- <span data-ttu-id="02b57-138">OUTER</span><span class="sxs-lookup"><span data-stu-id="02b57-138">OUTER</span></span>  
  
- <span data-ttu-id="02b57-139">RIGHT</span><span class="sxs-lookup"><span data-stu-id="02b57-139">RIGHT</span></span>  
  
- <span data-ttu-id="02b57-140">ROW</span><span class="sxs-lookup"><span data-stu-id="02b57-140">ROW</span></span>  
  
- <span data-ttu-id="02b57-141">VALUE</span><span class="sxs-lookup"><span data-stu-id="02b57-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="02b57-142">Ordre de tri des requêtes imbriquées</span><span class="sxs-lookup"><span data-stu-id="02b57-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="02b57-143">Dans Entity Framework, une expression imbriquée peut être placée n'importe où dans la requête ; l'ordre d'une requête imbriquée n'est pas conservé.</span><span class="sxs-lookup"><span data-stu-id="02b57-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="02b57-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="02b57-144">Example</span></span>  
 <span data-ttu-id="02b57-145">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur ORDER BY pour spécifier l'ordre de tri employé sur les objets retournés dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="02b57-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="02b57-146">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="02b57-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="02b57-147">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="02b57-147">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="02b57-148">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="02b57-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="02b57-149">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="02b57-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="02b57-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02b57-150">See also</span></span>

- [<span data-ttu-id="02b57-151">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="02b57-151">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="02b57-152">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="02b57-152">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="02b57-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="02b57-153">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="02b57-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="02b57-154">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="02b57-155">TOP</span><span class="sxs-lookup"><span data-stu-id="02b57-155">TOP</span></span>](top-entity-sql.md)
