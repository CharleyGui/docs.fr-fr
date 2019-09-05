---
title: Fonctions d'agrégation canoniques
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 3f4bb84c45e503fc0018e7869f3b41ddab4581a6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251352"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="f8b24-102">Fonctions d'agrégation canoniques</span><span class="sxs-lookup"><span data-stu-id="f8b24-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="f8b24-103">Les agrégats sont des expressions qui réduisent une série de valeurs d'entrée en, par exemple, une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="f8b24-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="f8b24-104">Ils sont normalement utilisés avec la clause GROUP BY de l'expression SELECT et leur utilisation est sujette à certaines contraintes.</span><span class="sxs-lookup"><span data-stu-id="f8b24-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="f8b24-105">Fonctions canoniques d’agrégation Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8b24-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="f8b24-106">Voici les fonctions d’agrégation Entity SQL canoniques.</span><span class="sxs-lookup"><span data-stu-id="f8b24-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="f8b24-107">Avg(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-107">Avg(expression)</span></span>

<span data-ttu-id="f8b24-108">Retourne la moyenne des valeurs non Null.</span><span class="sxs-lookup"><span data-stu-id="f8b24-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="f8b24-109">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-109">**Arguments**</span></span>

<span data-ttu-id="f8b24-110">,, Et`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="f8b24-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="f8b24-111">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-111">**Return Value**</span></span>

<span data-ttu-id="f8b24-112">Type de `expression`ou `null` si toutes les valeurs d’entrée sont `null` des valeurs.</span><span class="sxs-lookup"><span data-stu-id="f8b24-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-113">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="f8b24-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-114">BigCount(expression)</span></span>

<span data-ttu-id="f8b24-115">Retourne la taille de l'agrégat, y compris les valeurs Null et dupliquées.</span><span class="sxs-lookup"><span data-stu-id="f8b24-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="f8b24-116">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-116">**Arguments**</span></span>

<span data-ttu-id="f8b24-117">N'importe quel type.</span><span class="sxs-lookup"><span data-stu-id="f8b24-117">Any type.</span></span>

<span data-ttu-id="f8b24-118">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-118">**Return Value**</span></span>

<span data-ttu-id="f8b24-119">Élément `Int64`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-119">An `Int64`.</span></span>

<span data-ttu-id="f8b24-120">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="f8b24-121">Count(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-121">Count(expression)</span></span>

<span data-ttu-id="f8b24-122">Retourne la taille de l'agrégat, y compris les valeurs Null et dupliquées.</span><span class="sxs-lookup"><span data-stu-id="f8b24-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="f8b24-123">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-123">**Arguments**</span></span>

<span data-ttu-id="f8b24-124">N'importe quel type.</span><span class="sxs-lookup"><span data-stu-id="f8b24-124">Any type.</span></span>

<span data-ttu-id="f8b24-125">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-125">**Return Value**</span></span>

<span data-ttu-id="f8b24-126">Élément `Int32`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-126">An `Int32`.</span></span>

<span data-ttu-id="f8b24-127">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="f8b24-128">Max(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-128">Max(expression)</span></span>

<span data-ttu-id="f8b24-129">Retourne la valeur maximale des valeurs non-Null.</span><span class="sxs-lookup"><span data-stu-id="f8b24-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="f8b24-130">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-130">**Arguments**</span></span>

<span data-ttu-id="f8b24-131">`Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="f8b24-132">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-132">**Return Value**</span></span>

<span data-ttu-id="f8b24-133">Type de `expression`ou `null` si toutes les valeurs d’entrée sont `null` des valeurs.</span><span class="sxs-lookup"><span data-stu-id="f8b24-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-134">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="f8b24-135">Min(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-135">Min(expression)</span></span>

<span data-ttu-id="f8b24-136">Retourne la valeur minimale des valeurs non Null.</span><span class="sxs-lookup"><span data-stu-id="f8b24-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="f8b24-137">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-137">**Arguments**</span></span>

<span data-ttu-id="f8b24-138">`Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="f8b24-139">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-139">**Return Value**</span></span>

<span data-ttu-id="f8b24-140">Type de `expression`ou `null` si toutes les valeurs d’entrée sont `null` des valeurs.</span><span class="sxs-lookup"><span data-stu-id="f8b24-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-141">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="f8b24-142">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-142">StDev(expression)</span></span>

<span data-ttu-id="f8b24-143">Retourne l'écart type des valeurs non Null.</span><span class="sxs-lookup"><span data-stu-id="f8b24-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="f8b24-144">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-144">**Arguments**</span></span>

<span data-ttu-id="f8b24-145">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="f8b24-146">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-146">**Return Value**</span></span>

<span data-ttu-id="f8b24-147">`Double`</span><span class="sxs-lookup"><span data-stu-id="f8b24-147">A `Double`.</span></span> <span data-ttu-id="f8b24-148">`Null` si toutes les valeurs d'entrée sont `null`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-149">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="f8b24-150">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-150">StDevP(expression)</span></span>

<span data-ttu-id="f8b24-151">Retourne l'écart type pour le remplissage de toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="f8b24-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="f8b24-152">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-152">**Arguments**</span></span>

<span data-ttu-id="f8b24-153">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="f8b24-154">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-154">**Return Value**</span></span>

<span data-ttu-id="f8b24-155">Ou si toutes les valeurs d’entrée sont `null` des valeurs. `null` `Double`</span><span class="sxs-lookup"><span data-stu-id="f8b24-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-156">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="f8b24-157">Sum(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-157">Sum(expression)</span></span>

<span data-ttu-id="f8b24-158">Retourne la somme des valeurs non-Null.</span><span class="sxs-lookup"><span data-stu-id="f8b24-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="f8b24-159">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-159">**Arguments**</span></span>

<span data-ttu-id="f8b24-160">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="f8b24-161">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-161">**Return Value**</span></span>

<span data-ttu-id="f8b24-162">Ou si toutes les valeurs d’entrée sont `null` des valeurs. `null` `Double`</span><span class="sxs-lookup"><span data-stu-id="f8b24-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-163">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="f8b24-164">Var(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-164">Var(expression)</span></span>

<span data-ttu-id="f8b24-165">Retourne la variance de toutes les valeurs non-Null.</span><span class="sxs-lookup"><span data-stu-id="f8b24-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="f8b24-166">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-166">**Arguments**</span></span>

<span data-ttu-id="f8b24-167">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="f8b24-168">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-168">**Return Value**</span></span>

<span data-ttu-id="f8b24-169">Ou si toutes les valeurs d’entrée sont `null` des valeurs. `null` `Double`</span><span class="sxs-lookup"><span data-stu-id="f8b24-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-170">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="f8b24-171">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="f8b24-171">VarP(expression)</span></span>

<span data-ttu-id="f8b24-172">Retourne la variance pour le remplissage de toutes les valeurs non-Null.</span><span class="sxs-lookup"><span data-stu-id="f8b24-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="f8b24-173">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="f8b24-173">**Arguments**</span></span>

<span data-ttu-id="f8b24-174">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f8b24-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="f8b24-175">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="f8b24-175">**Return Value**</span></span>

<span data-ttu-id="f8b24-176">Ou si toutes les valeurs d’entrée sont `null` des valeurs. `null` `Double`</span><span class="sxs-lookup"><span data-stu-id="f8b24-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="f8b24-177">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="f8b24-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="f8b24-178">Des fonctionnalités équivalentes sont disponibles dans le fournisseur managé Client Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="f8b24-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="f8b24-179">Pour plus d’informations, consultez [SqlClient pour les fonctions de Entity Framework](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f8b24-179">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="f8b24-180">Agrégats basés sur des collections</span><span class="sxs-lookup"><span data-stu-id="f8b24-180">Collection-based aggregates</span></span>

<span data-ttu-id="f8b24-181">Les agrégats basés sur des collections (fonctions de collection) opèrent sur des collections et retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="f8b24-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="f8b24-182">Par exemple, si ORDERs est une collection de toutes les commandes, vous pouvez calculer la première date d’expédition à l’aide de l’expression suivante :</span><span class="sxs-lookup"><span data-stu-id="f8b24-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="f8b24-183">Les expressions figurant dans des agrégats basés sur des collections sont évalués dans la résolution de noms de portée ambiante actuelle.</span><span class="sxs-lookup"><span data-stu-id="f8b24-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="f8b24-184">Agrégats basés sur des groupes</span><span class="sxs-lookup"><span data-stu-id="f8b24-184">Group-based aggregates</span></span>

<span data-ttu-id="f8b24-185">Les agrégats basés sur des groupes sont calculés sur un groupe défini par la clause GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="f8b24-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="f8b24-186">Pour chaque groupe du résultat, un agrégat distinct est calculé en utilisant les éléments de chaque groupe fourni en entrée pour le calcul.</span><span class="sxs-lookup"><span data-stu-id="f8b24-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="f8b24-187">Lorsqu'une clause group-by est utilisée dans une expression select, seuls des noms d'expressions de regroupement, des agrégats ou des expressions constantes peuvent figurer dans la projection ou la clause order-by.</span><span class="sxs-lookup"><span data-stu-id="f8b24-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="f8b24-188">L'exemple suivant calcule la quantité moyenne commandée pour chaque produit :</span><span class="sxs-lookup"><span data-stu-id="f8b24-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="f8b24-189">Il est possible d’avoir un agrégat basé sur des groupes sans clause GROUP-BY explicite dans l’expression SELECT.</span><span class="sxs-lookup"><span data-stu-id="f8b24-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="f8b24-190">Dans ce cas, tous les éléments sont traités comme un seul groupe.</span><span class="sxs-lookup"><span data-stu-id="f8b24-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="f8b24-191">Cela équivaut à spécifier un regroupement basé sur une constante.</span><span class="sxs-lookup"><span data-stu-id="f8b24-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="f8b24-192">L'expression suivante, par exemple :</span><span class="sxs-lookup"><span data-stu-id="f8b24-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="f8b24-193">est équivalente à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="f8b24-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="f8b24-194">Les expressions figurant dans des agrégats basés sur des groupes sont évalués dans la résolution de noms de portée qui serait visible pour l’expression de la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="f8b24-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="f8b24-195">Comme dans Transact-SQL, les agrégats basés sur des groupes peuvent également spécifier un modificateur ALL ou DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="f8b24-195">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="f8b24-196">Si le modificateur DISTINCT est spécifié, les doublons sont éliminés de la collection d’entrée de l’agrégat, avant que celui-ci ne soit calculé.</span><span class="sxs-lookup"><span data-stu-id="f8b24-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="f8b24-197">Si le modificateur ALL est spécifié (ou si aucun modificateur ne l'est), les doublons ne sont pas éliminés.</span><span class="sxs-lookup"><span data-stu-id="f8b24-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8b24-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8b24-198">See also</span></span>

- [<span data-ttu-id="f8b24-199">Fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="f8b24-199">Canonical Functions</span></span>](canonical-functions.md)
