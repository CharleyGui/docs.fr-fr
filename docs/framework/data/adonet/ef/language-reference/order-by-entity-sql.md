---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 2010ef9d6fe37e65824cac877074453db1b789db
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319445"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="d06a6-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d06a6-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="d06a6-103">Spécifie l'ordre de classement utilisé sur les objets retournés dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="d06a6-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d06a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d06a6-104">Syntax</span></span>  
  
```sql  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d06a6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d06a6-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="d06a6-106">Toute expression de requête valide qui spécifie une propriété sur laquelle doit porter le tri.</span><span class="sxs-lookup"><span data-stu-id="d06a6-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="d06a6-107">Vous pouvez spécifier plusieurs expressions de classement.</span><span class="sxs-lookup"><span data-stu-id="d06a6-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="d06a6-108">L'ordre des expressions de classement dans la clause ORDER BY détermine l'organisation de l'ensemble de résultats trié.</span><span class="sxs-lookup"><span data-stu-id="d06a6-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="d06a6-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="d06a6-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="d06a6-110">Indique que l'opération ORDER BY doit être effectuée en fonction du classement spécifié dans `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="d06a6-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="d06a6-111">COLLATE ne peut s'appliquer qu'aux expressions de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d06a6-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="d06a6-112">ASC</span><span class="sxs-lookup"><span data-stu-id="d06a6-112">ASC</span></span>  
 <span data-ttu-id="d06a6-113">Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre croissant, de la plus petite à la plus grande.</span><span class="sxs-lookup"><span data-stu-id="d06a6-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="d06a6-114">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d06a6-114">This is the default.</span></span>  
  
 <span data-ttu-id="d06a6-115">DESC</span><span class="sxs-lookup"><span data-stu-id="d06a6-115">DESC</span></span>  
 <span data-ttu-id="d06a6-116">Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre décroissant, de la plus grande à la plus petite.</span><span class="sxs-lookup"><span data-stu-id="d06a6-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="d06a6-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="d06a6-117">LIMIT `n`</span></span>  
 <span data-ttu-id="d06a6-118">Seuls les `n` premiers éléments sont sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="d06a6-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="d06a6-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="d06a6-119">SKIP `n`</span></span>  
 <span data-ttu-id="d06a6-120">Ignore les `n` premiers éléments.</span><span class="sxs-lookup"><span data-stu-id="d06a6-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d06a6-121">Notes</span><span class="sxs-lookup"><span data-stu-id="d06a6-121">Remarks</span></span>  
 <span data-ttu-id="d06a6-122">La clause ORDER BY est logiquement appliquée au résultat de la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="d06a6-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="d06a6-123">La clause ORDER BY peut faire référence aux éléments de la liste de sélection avec leurs alias.</span><span class="sxs-lookup"><span data-stu-id="d06a6-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="d06a6-124">La clause ORDER BY peut également faire référence à d'autres variables qui se trouvent actuellement dans l'étendue.</span><span class="sxs-lookup"><span data-stu-id="d06a6-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="d06a6-125">Toutefois, si la clause SELECT a été spécifiée avec un modificateur DISTINCT, la clause ORDER BY ne peut faire référence qu'à des alias de la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="d06a6-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="d06a6-126">Chaque expression contenue dans la clause ORDER BY doit correspondre à un type pouvant être comparé en inégalité (inférieur à ou supérieur à, etc.).</span><span class="sxs-lookup"><span data-stu-id="d06a6-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="d06a6-127">Ces types sont généralement des primitives scalaires telles que des nombres, des chaînes et des dates.</span><span class="sxs-lookup"><span data-stu-id="d06a6-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="d06a6-128">Les RowTypes de type comparable peuvent également être comparés sur le plan de l'ordre de classement.</span><span class="sxs-lookup"><span data-stu-id="d06a6-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="d06a6-129">Si votre code effectue une itération sur un ensemble ordonné autre qu'une projection de niveau supérieur, il n'est pas garanti que le résultat conservera son ordre de classement.</span><span class="sxs-lookup"><span data-stu-id="d06a6-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="d06a6-130">Dans l’exemple suivant, la conservation de l’ordre est garantie :</span><span class="sxs-lookup"><span data-stu-id="d06a6-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="d06a6-131">Dans la requête suivante, le classement de la requête imbriquée est ignoré :</span><span class="sxs-lookup"><span data-stu-id="d06a6-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="d06a6-132">Pour une opération UNION, UNION ALL, EXCEPT ou INTERSECT triée, utilisez le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="d06a6-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="d06a6-133">Mots clés restreints</span><span class="sxs-lookup"><span data-stu-id="d06a6-133">Restricted keywords</span></span>  
 <span data-ttu-id="d06a6-134">Les mots clés suivants doivent être mis entre guillemets lorsqu'ils sont utilisés dans une clause `ORDER BY` :</span><span class="sxs-lookup"><span data-stu-id="d06a6-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="d06a6-135">CROSS</span><span class="sxs-lookup"><span data-stu-id="d06a6-135">CROSS</span></span>  
  
- <span data-ttu-id="d06a6-136">FULL</span><span class="sxs-lookup"><span data-stu-id="d06a6-136">FULL</span></span>  
  
- <span data-ttu-id="d06a6-137">KEY</span><span class="sxs-lookup"><span data-stu-id="d06a6-137">KEY</span></span>  
  
- <span data-ttu-id="d06a6-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="d06a6-138">LEFT</span></span>  
  
- <span data-ttu-id="d06a6-139">ORDER</span><span class="sxs-lookup"><span data-stu-id="d06a6-139">ORDER</span></span>  
  
- <span data-ttu-id="d06a6-140">OUTER</span><span class="sxs-lookup"><span data-stu-id="d06a6-140">OUTER</span></span>  
  
- <span data-ttu-id="d06a6-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="d06a6-141">RIGHT</span></span>  
  
- <span data-ttu-id="d06a6-142">ROW</span><span class="sxs-lookup"><span data-stu-id="d06a6-142">ROW</span></span>  
  
- <span data-ttu-id="d06a6-143">VALUE</span><span class="sxs-lookup"><span data-stu-id="d06a6-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="d06a6-144">Ordre de tri des requêtes imbriquées</span><span class="sxs-lookup"><span data-stu-id="d06a6-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="d06a6-145">Dans Entity Framework, une expression imbriquée peut être placée n'importe où dans la requête ; l'ordre d'une requête imbriquée n'est pas conservé.</span><span class="sxs-lookup"><span data-stu-id="d06a6-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="d06a6-146">La requête suivante classe les résultats par nom de famille :</span><span class="sxs-lookup"><span data-stu-id="d06a6-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="d06a6-147">Dans la requête suivante, le classement de la requête imbriquée est ignoré :</span><span class="sxs-lookup"><span data-stu-id="d06a6-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="d06a6-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="d06a6-148">Example</span></span>  
 <span data-ttu-id="d06a6-149">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur ORDER BY pour spécifier l'ordre de tri employé sur les objets retournés dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="d06a6-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="d06a6-150">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="d06a6-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d06a6-151">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d06a6-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d06a6-152">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d06a6-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d06a6-153">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="d06a6-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="d06a6-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d06a6-154">See also</span></span>

- [<span data-ttu-id="d06a6-155">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="d06a6-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="d06a6-156">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d06a6-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="d06a6-157">SKIP</span><span class="sxs-lookup"><span data-stu-id="d06a6-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="d06a6-158">LIMIT</span><span class="sxs-lookup"><span data-stu-id="d06a6-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="d06a6-159">TOP</span><span class="sxs-lookup"><span data-stu-id="d06a6-159">TOP</span></span>](top-entity-sql.md)
