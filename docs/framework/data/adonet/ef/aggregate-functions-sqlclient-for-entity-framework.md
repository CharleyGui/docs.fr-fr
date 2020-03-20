---
title: Fonctions d'agrégation (SqlClient pour Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150647"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="b666d-102">Fonctions d'agrégation (SqlClient pour Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="b666d-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="b666d-103">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) fournit des fonctions d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="b666d-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="b666d-104">Les fonctions d'agrégation effectuent des calculs sur un ensemble de valeurs d'entrée et retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="b666d-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="b666d-105">Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient.</span><span class="sxs-lookup"><span data-stu-id="b666d-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="b666d-106">La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="b666d-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="b666d-107">Voici les fonctions d’agrégats SqlClient.</span><span class="sxs-lookup"><span data-stu-id="b666d-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="b666d-108">AVG (expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-108">AVG(expression)</span></span>

<span data-ttu-id="b666d-109">Retourne la moyenne des valeurs d'une collection.</span><span class="sxs-lookup"><span data-stu-id="b666d-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="b666d-110">Les valeurs NULL sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="b666d-110">Null values are ignored.</span></span>

<span data-ttu-id="b666d-111">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-111">**Arguments**</span></span>

<span data-ttu-id="b666d-112">Un `Int32` `Int64`, `Double`, `Decimal`, et .</span><span class="sxs-lookup"><span data-stu-id="b666d-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="b666d-113">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-113">**Return Value**</span></span>

<span data-ttu-id="b666d-114">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b666d-114">The type of `expression`.</span></span>

<span data-ttu-id="b666d-115">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="b666d-116">CHECKSUM_AGG (collection)</span><span class="sxs-lookup"><span data-stu-id="b666d-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="b666d-117">Retourne la somme de contrôle des valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="b666d-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="b666d-118">Les valeurs NULL sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="b666d-118">Null values are ignored.</span></span>

 <span data-ttu-id="b666d-119">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-119">**Arguments**</span></span>

 <span data-ttu-id="b666d-120">Une collection`Int32`( ).</span><span class="sxs-lookup"><span data-stu-id="b666d-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="b666d-121">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-121">**Return Value**</span></span>

 <span data-ttu-id="b666d-122">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="b666d-122">An `Int32`.</span></span>

 <span data-ttu-id="b666d-123">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="b666d-124">COUNT (expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-124">COUNT(expression)</span></span>

<span data-ttu-id="b666d-125">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `Int32`.</span><span class="sxs-lookup"><span data-stu-id="b666d-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="b666d-126">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-126">**Arguments**</span></span>

<span data-ttu-id="b666d-127">Une\<collection T>, où T est l’un des types suivants:</span><span class="sxs-lookup"><span data-stu-id="b666d-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="b666d-128">`Guid`(non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="b666d-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="b666d-129">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-129">**Return Value**</span></span>

<span data-ttu-id="b666d-130">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="b666d-130">An `Int32`.</span></span>

<span data-ttu-id="b666d-131">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="b666d-132">COUNT_BIG(expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="b666d-133">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `bigint`.</span><span class="sxs-lookup"><span data-stu-id="b666d-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="b666d-134">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-134">**Arguments**</span></span>

 <span data-ttu-id="b666d-135">Une collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b666d-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="b666d-136">`Guid`(non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="b666d-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="b666d-137">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-137">**Return Value**</span></span>

<span data-ttu-id="b666d-138">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="b666d-138">An `Int64`.</span></span>

<span data-ttu-id="b666d-139">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="b666d-140">MAX(expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-140">MAX(expression)</span></span>

<span data-ttu-id="b666d-141">Retourne la valeur maximale contenue dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b666d-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="b666d-142">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-142">**Arguments**</span></span>

<span data-ttu-id="b666d-143">Une collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b666d-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="b666d-144">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-144">**Return Value**</span></span>

<span data-ttu-id="b666d-145">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b666d-145">The type of `expression`.</span></span>

<span data-ttu-id="b666d-146">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="b666d-147">MIN (expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-147">MIN(expression)</span></span>

<span data-ttu-id="b666d-148">Retourne la valeur minimale contenue dans une collection.</span><span class="sxs-lookup"><span data-stu-id="b666d-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="b666d-149">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-149">**Arguments**</span></span>

<span data-ttu-id="b666d-150">Une collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b666d-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="b666d-151">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-151">**Return Value**</span></span>

<span data-ttu-id="b666d-152">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b666d-152">The type of `expression`.</span></span>

<span data-ttu-id="b666d-153">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="b666d-154">STDEV(expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-154">STDEV(expression)</span></span>

<span data-ttu-id="b666d-155">Renvoie l'écart type statistique de toutes les valeurs dans l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b666d-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="b666d-156">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-156">**Arguments**</span></span>

<span data-ttu-id="b666d-157">Une collection`Double`( ).</span><span class="sxs-lookup"><span data-stu-id="b666d-157">A Collection(`Double`).</span></span>

<span data-ttu-id="b666d-158">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-158">**Return Value**</span></span>

<span data-ttu-id="b666d-159">`Double`.</span><span class="sxs-lookup"><span data-stu-id="b666d-159">A `Double`.</span></span>

<span data-ttu-id="b666d-160">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="b666d-161">STDEVP (expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-161">STDEVP(expression)</span></span>

<span data-ttu-id="b666d-162">Renvoie l'écart type de remplissage pour toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b666d-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="b666d-163">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-163">**Arguments**</span></span>

<span data-ttu-id="b666d-164">Une collection`Double`( ).</span><span class="sxs-lookup"><span data-stu-id="b666d-164">A Collection(`Double`).</span></span>

<span data-ttu-id="b666d-165">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-165">**Return Value**</span></span>

<span data-ttu-id="b666d-166">`Double`.</span><span class="sxs-lookup"><span data-stu-id="b666d-166">A `Double`.</span></span>

<span data-ttu-id="b666d-167">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="b666d-168">SUM(expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-168">SUM(expression)</span></span>

<span data-ttu-id="b666d-169">Retourne la somme de toutes les valeurs de la collection.</span><span class="sxs-lookup"><span data-stu-id="b666d-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="b666d-170">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-170">**Arguments**</span></span>

<span data-ttu-id="b666d-171">Une collection (T) où T est `Int32` `Int64`l’un des types suivants: , , `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="b666d-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="b666d-172">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-172">**Return Value**</span></span>

<span data-ttu-id="b666d-173">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b666d-173">The type of `expression`.</span></span>

<span data-ttu-id="b666d-174">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="b666d-175">VAR (expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-175">VAR(expression)</span></span>

<span data-ttu-id="b666d-176">Renvoie la variance statistique de toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b666d-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="b666d-177">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-177">**Arguments**</span></span>

<span data-ttu-id="b666d-178">Une collection`Double`( ).</span><span class="sxs-lookup"><span data-stu-id="b666d-178">A Collection(`Double`).</span></span>

<span data-ttu-id="b666d-179">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-179">**Return Value**</span></span>

<span data-ttu-id="b666d-180">`Double`.</span><span class="sxs-lookup"><span data-stu-id="b666d-180">A `Double`.</span></span>

<span data-ttu-id="b666d-181">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="b666d-182">VARP (expression)</span><span class="sxs-lookup"><span data-stu-id="b666d-182">VARP(expression)</span></span>

<span data-ttu-id="b666d-183">Renvoie la variance statistique de remplissage pour toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b666d-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="b666d-184">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b666d-184">**Arguments**</span></span>

<span data-ttu-id="b666d-185">Une collection`Double`( ).</span><span class="sxs-lookup"><span data-stu-id="b666d-185">A Collection(`Double`).</span></span>

<span data-ttu-id="b666d-186">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="b666d-186">**Return Value**</span></span>

<span data-ttu-id="b666d-187">`Double`.</span><span class="sxs-lookup"><span data-stu-id="b666d-187">A `Double`.</span></span>

<span data-ttu-id="b666d-188">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b666d-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="b666d-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b666d-189">See also</span></span>

- [<span data-ttu-id="b666d-190">Fonctions d'agrégation (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b666d-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="b666d-191">Langage d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b666d-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="b666d-192">Fonctions d'agrégation canoniques</span><span class="sxs-lookup"><span data-stu-id="b666d-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
