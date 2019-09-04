---
title: Fonctions d'agrégation (SqlClient pour Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: cf476192cf049f230c1956e390d215ad4abaa821
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251703"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="ac541-102">Fonctions d'agrégation (SqlClient pour Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="ac541-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="ac541-103">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) fournit des fonctions d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="ac541-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="ac541-104">Les fonctions d'agrégation effectuent des calculs sur un ensemble de valeurs d'entrée et retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="ac541-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="ac541-105">Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ac541-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="ac541-106">La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="ac541-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="ac541-107">Les fonctions d’agrégation SqlClient sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="ac541-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="ac541-108">AVG (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-108">AVG(expression)</span></span>

<span data-ttu-id="ac541-109">Retourne la moyenne des valeurs d'une collection.</span><span class="sxs-lookup"><span data-stu-id="ac541-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="ac541-110">Les valeurs NULL sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="ac541-110">Null values are ignored.</span></span>

<span data-ttu-id="ac541-111">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-111">**Arguments**</span></span>

<span data-ttu-id="ac541-112">,, Et`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="ac541-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="ac541-113">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-113">**Return Value**</span></span>

<span data-ttu-id="ac541-114">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="ac541-114">The type of `expression`.</span></span>

<span data-ttu-id="ac541-115">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="ac541-116">CHECKSUM_AGG (collection)</span><span class="sxs-lookup"><span data-stu-id="ac541-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="ac541-117">Retourne la somme de contrôle des valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="ac541-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="ac541-118">Les valeurs NULL sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="ac541-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="ac541-119">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-119">**Arguments**</span></span>
 
 <span data-ttu-id="ac541-120">Collection (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="ac541-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="ac541-121">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-121">**Return Value**</span></span>
 
 <span data-ttu-id="ac541-122">Élément `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ac541-122">An `Int32`.</span></span>
 
 <span data-ttu-id="ac541-123">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="ac541-124">COUNT (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-124">COUNT(expression)</span></span>

<span data-ttu-id="ac541-125">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ac541-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="ac541-126">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-126">**Arguments**</span></span>

<span data-ttu-id="ac541-127">Collection\<t >, où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="ac541-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="ac541-128">`Guid`(non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="ac541-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="ac541-129">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-129">**Return Value**</span></span>

<span data-ttu-id="ac541-130">Élément `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ac541-130">An `Int32`.</span></span>

<span data-ttu-id="ac541-131">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="ac541-132">[ ! code-SQL[DP EntityServices concepts # SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="ac541-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="count_bigexpression"></a><span data-ttu-id="ac541-133">COUNT_BIG (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="ac541-134">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `bigint`.</span><span class="sxs-lookup"><span data-stu-id="ac541-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="ac541-135">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-135">**Arguments**</span></span>
 
 <span data-ttu-id="ac541-136">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="ac541-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="ac541-137">`Guid`(non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="ac541-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="ac541-138">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-138">**Return Value**</span></span>

<span data-ttu-id="ac541-139">Élément `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ac541-139">An `Int64`.</span></span>

<span data-ttu-id="ac541-140">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="ac541-141">MAX (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-141">MAX(expression)</span></span>

<span data-ttu-id="ac541-142">Retourne la valeur maximale contenue dans la collection.</span><span class="sxs-lookup"><span data-stu-id="ac541-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="ac541-143">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-143">**Arguments**</span></span>

<span data-ttu-id="ac541-144">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="ac541-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="ac541-145">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-145">**Return Value**</span></span>

<span data-ttu-id="ac541-146">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="ac541-146">The type of `expression`.</span></span>

<span data-ttu-id="ac541-147">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="ac541-148">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-148">MIN(expression)</span></span>

<span data-ttu-id="ac541-149">Retourne la valeur minimale contenue dans une collection.</span><span class="sxs-lookup"><span data-stu-id="ac541-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="ac541-150">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-150">**Arguments**</span></span>

<span data-ttu-id="ac541-151">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="ac541-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="ac541-152">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-152">**Return Value**</span></span>

<span data-ttu-id="ac541-153">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="ac541-153">The type of `expression`.</span></span>

<span data-ttu-id="ac541-154">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="ac541-155">ECARTYPE (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-155">STDEV(expression)</span></span>

<span data-ttu-id="ac541-156">Retourne l'écart type statistique de toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ac541-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="ac541-157">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-157">**Arguments**</span></span>

<span data-ttu-id="ac541-158">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="ac541-158">A Collection(`Double`).</span></span>

<span data-ttu-id="ac541-159">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-159">**Return Value**</span></span>

<span data-ttu-id="ac541-160">`Double`</span><span class="sxs-lookup"><span data-stu-id="ac541-160">A `Double`.</span></span>

<span data-ttu-id="ac541-161">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="ac541-162">STDEVP (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-162">STDEVP(expression)</span></span>

<span data-ttu-id="ac541-163">Retourne l'écart type statistique du remplissage de toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ac541-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="ac541-164">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-164">**Arguments**</span></span>

<span data-ttu-id="ac541-165">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="ac541-165">A Collection(`Double`).</span></span>

<span data-ttu-id="ac541-166">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-166">**Return Value**</span></span>

<span data-ttu-id="ac541-167">`Double`</span><span class="sxs-lookup"><span data-stu-id="ac541-167">A `Double`.</span></span>

<span data-ttu-id="ac541-168">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="ac541-169">SUM (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-169">SUM(expression)</span></span>

<span data-ttu-id="ac541-170">Retourne la somme de toutes les valeurs de la collection.</span><span class="sxs-lookup"><span data-stu-id="ac541-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="ac541-171">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-171">**Arguments**</span></span>

<span data-ttu-id="ac541-172">Collection (T) où T est l’un des types suivants `Int32`:, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ac541-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="ac541-173">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-173">**Return Value**</span></span>

<span data-ttu-id="ac541-174">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="ac541-174">The type of `expression`.</span></span>

<span data-ttu-id="ac541-175">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="ac541-176">VAR (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-176">VAR(expression)</span></span>

<span data-ttu-id="ac541-177">Retourne la variance statistique de toutes les valeurs dans l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ac541-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="ac541-178">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-178">**Arguments**</span></span>

<span data-ttu-id="ac541-179">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="ac541-179">A Collection(`Double`).</span></span>

<span data-ttu-id="ac541-180">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-180">**Return Value**</span></span>

<span data-ttu-id="ac541-181">`Double`</span><span class="sxs-lookup"><span data-stu-id="ac541-181">A `Double`.</span></span>

<span data-ttu-id="ac541-182">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="ac541-183">VARP (expression)</span><span class="sxs-lookup"><span data-stu-id="ac541-183">VARP(expression)</span></span>

<span data-ttu-id="ac541-184">Retourne la variance statistique de remplissage pour toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ac541-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="ac541-185">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="ac541-185">**Arguments**</span></span>

<span data-ttu-id="ac541-186">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="ac541-186">A Collection(`Double`).</span></span>

<span data-ttu-id="ac541-187">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="ac541-187">**Return Value**</span></span>

<span data-ttu-id="ac541-188">`Double`</span><span class="sxs-lookup"><span data-stu-id="ac541-188">A `Double`.</span></span>

<span data-ttu-id="ac541-189">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="ac541-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="ac541-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac541-190">See also</span></span>

<span data-ttu-id="ac541-191">Pour plus d'informations sur les fonctions d'agrégation prises en charge par SqlClient, voir la documentation correspondant à la version de SQL Server que vous avez spécifiée dans le manifeste du fournisseur SqlClient :</span><span class="sxs-lookup"><span data-stu-id="ac541-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="ac541-192">**SQL Server 2005 :** [Fonctions d’agrégation (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="ac541-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="ac541-193">**SQL Server 2008 et versions ultérieures :** [Fonctions d’agrégation (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="ac541-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- [<span data-ttu-id="ac541-194">Langage Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ac541-194">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="ac541-195">Fonctions canoniques d’agrégation</span><span class="sxs-lookup"><span data-stu-id="ac541-195">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
