---
title: Fonctions d'agrégation (SqlClient pour Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1c32ccfe18c67c9baeb7df0f981c9129b3bbc8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204513"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="b242c-102">Fonctions d'agrégation (SqlClient pour Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="b242c-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="b242c-103">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) fournit des fonctions d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="b242c-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="b242c-104">Les fonctions d'agrégation effectuent des calculs sur un ensemble de valeurs d'entrée et retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="b242c-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="b242c-105">Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient.</span><span class="sxs-lookup"><span data-stu-id="b242c-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="b242c-106">La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="b242c-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="b242c-107">Les fonctions d’agrégation SqlClient sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="b242c-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="b242c-108">AVG (expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-108">AVG(expression)</span></span>

<span data-ttu-id="b242c-109">Retourne la moyenne des valeurs d'une collection.</span><span class="sxs-lookup"><span data-stu-id="b242c-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="b242c-110">Les valeurs NULL sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="b242c-110">Null values are ignored.</span></span>

<span data-ttu-id="b242c-111">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-111">**Arguments**</span></span>

<span data-ttu-id="b242c-112">, `Int32` , `Int64` `Double` Et `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="b242c-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="b242c-113">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-113">**Return Value**</span></span>

<span data-ttu-id="b242c-114">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b242c-114">The type of `expression`.</span></span>

<span data-ttu-id="b242c-115">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="b242c-116">CHECKSUM_AGG (collection)</span><span class="sxs-lookup"><span data-stu-id="b242c-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="b242c-117">Retourne la somme de contrôle des valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="b242c-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="b242c-118">Les valeurs NULL sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="b242c-118">Null values are ignored.</span></span>

 <span data-ttu-id="b242c-119">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-119">**Arguments**</span></span>

 <span data-ttu-id="b242c-120">Collection ( `Int32` ).</span><span class="sxs-lookup"><span data-stu-id="b242c-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="b242c-121">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-121">**Return Value**</span></span>

 <span data-ttu-id="b242c-122">Élément `Int32`.</span><span class="sxs-lookup"><span data-stu-id="b242c-122">An `Int32`.</span></span>

 <span data-ttu-id="b242c-123">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="b242c-124">COUNT(expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-124">COUNT(expression)</span></span>

<span data-ttu-id="b242c-125">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `Int32`.</span><span class="sxs-lookup"><span data-stu-id="b242c-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="b242c-126">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-126">**Arguments**</span></span>

<span data-ttu-id="b242c-127">Collection \<T> , où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b242c-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="b242c-128">`Guid` (non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="b242c-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="b242c-129">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-129">**Return Value**</span></span>

<span data-ttu-id="b242c-130">Élément `Int32`.</span><span class="sxs-lookup"><span data-stu-id="b242c-130">An `Int32`.</span></span>

<span data-ttu-id="b242c-131">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="b242c-132">COUNT_BIG (expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="b242c-133">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `bigint`.</span><span class="sxs-lookup"><span data-stu-id="b242c-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="b242c-134">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-134">**Arguments**</span></span>

 <span data-ttu-id="b242c-135">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b242c-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="b242c-136">`Guid` (non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="b242c-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="b242c-137">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-137">**Return Value**</span></span>

<span data-ttu-id="b242c-138">Élément `Int64`.</span><span class="sxs-lookup"><span data-stu-id="b242c-138">An `Int64`.</span></span>

<span data-ttu-id="b242c-139">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="b242c-140">MAX(expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-140">MAX(expression)</span></span>

<span data-ttu-id="b242c-141">Retourne la valeur maximale contenue dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b242c-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="b242c-142">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-142">**Arguments**</span></span>

<span data-ttu-id="b242c-143">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b242c-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="b242c-144">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-144">**Return Value**</span></span>

<span data-ttu-id="b242c-145">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b242c-145">The type of `expression`.</span></span>

<span data-ttu-id="b242c-146">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="b242c-147">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-147">MIN(expression)</span></span>

<span data-ttu-id="b242c-148">Retourne la valeur minimale contenue dans une collection.</span><span class="sxs-lookup"><span data-stu-id="b242c-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="b242c-149">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-149">**Arguments**</span></span>

<span data-ttu-id="b242c-150">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b242c-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="b242c-151">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-151">**Return Value**</span></span>

<span data-ttu-id="b242c-152">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b242c-152">The type of `expression`.</span></span>

<span data-ttu-id="b242c-153">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="b242c-154">ECARTYPE (expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-154">STDEV(expression)</span></span>

<span data-ttu-id="b242c-155">Renvoie l'écart type statistique de toutes les valeurs dans l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b242c-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="b242c-156">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-156">**Arguments**</span></span>

<span data-ttu-id="b242c-157">Collection ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="b242c-157">A Collection(`Double`).</span></span>

<span data-ttu-id="b242c-158">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-158">**Return Value**</span></span>

<span data-ttu-id="b242c-159">`Double`</span><span class="sxs-lookup"><span data-stu-id="b242c-159">A `Double`.</span></span>

<span data-ttu-id="b242c-160">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="b242c-161">STDEVP (expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-161">STDEVP(expression)</span></span>

<span data-ttu-id="b242c-162">Renvoie l'écart type de remplissage pour toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b242c-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="b242c-163">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-163">**Arguments**</span></span>

<span data-ttu-id="b242c-164">Collection ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="b242c-164">A Collection(`Double`).</span></span>

<span data-ttu-id="b242c-165">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-165">**Return Value**</span></span>

<span data-ttu-id="b242c-166">`Double`</span><span class="sxs-lookup"><span data-stu-id="b242c-166">A `Double`.</span></span>

<span data-ttu-id="b242c-167">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="b242c-168">SUM(expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-168">SUM(expression)</span></span>

<span data-ttu-id="b242c-169">Retourne la somme de toutes les valeurs de la collection.</span><span class="sxs-lookup"><span data-stu-id="b242c-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="b242c-170">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-170">**Arguments**</span></span>

<span data-ttu-id="b242c-171">Collection (T) où T est l’un des types suivants : `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="b242c-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="b242c-172">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-172">**Return Value**</span></span>

<span data-ttu-id="b242c-173">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="b242c-173">The type of `expression`.</span></span>

<span data-ttu-id="b242c-174">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="b242c-175">VAR (expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-175">VAR(expression)</span></span>

<span data-ttu-id="b242c-176">Renvoie la variance statistique de toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b242c-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="b242c-177">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-177">**Arguments**</span></span>

<span data-ttu-id="b242c-178">Collection ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="b242c-178">A Collection(`Double`).</span></span>

<span data-ttu-id="b242c-179">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-179">**Return Value**</span></span>

<span data-ttu-id="b242c-180">`Double`</span><span class="sxs-lookup"><span data-stu-id="b242c-180">A `Double`.</span></span>

<span data-ttu-id="b242c-181">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="b242c-182">VARP (expression)</span><span class="sxs-lookup"><span data-stu-id="b242c-182">VARP(expression)</span></span>

<span data-ttu-id="b242c-183">Renvoie la variance statistique de remplissage pour toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b242c-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="b242c-184">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="b242c-184">**Arguments**</span></span>

<span data-ttu-id="b242c-185">Collection ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="b242c-185">A Collection(`Double`).</span></span>

<span data-ttu-id="b242c-186">**Valeur renvoyée**</span><span class="sxs-lookup"><span data-stu-id="b242c-186">**Return Value**</span></span>

<span data-ttu-id="b242c-187">`Double`</span><span class="sxs-lookup"><span data-stu-id="b242c-187">A `Double`.</span></span>

<span data-ttu-id="b242c-188">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="b242c-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="b242c-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b242c-189">See also</span></span>

- [<span data-ttu-id="b242c-190">Fonctions d'agrégation (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b242c-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="b242c-191">Langage d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b242c-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="b242c-192">Fonctions d'agrégation canoniques</span><span class="sxs-lookup"><span data-stu-id="b242c-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
