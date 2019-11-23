---
title: Fonctions d'agrégation (SqlClient pour Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700058"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="0c9b0-102">Fonctions d'agrégation (SqlClient pour Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="0c9b0-103">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) fournit des fonctions d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="0c9b0-104">Les fonctions d'agrégation effectuent des calculs sur un ensemble de valeurs d'entrée et retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="0c9b0-105">Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="0c9b0-106">La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="0c9b0-107">Les fonctions d’agrégation SqlClient sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="0c9b0-108">AVG (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-108">AVG(expression)</span></span>

<span data-ttu-id="0c9b0-109">Retourne la moyenne des valeurs d'une collection.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="0c9b0-110">Les valeurs Null sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-110">Null values are ignored.</span></span>

<span data-ttu-id="0c9b0-111">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-111">**Arguments**</span></span>

<span data-ttu-id="0c9b0-112">`Int32`, `Int64`, `Double`et `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="0c9b0-113">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-113">**Return Value**</span></span>

<span data-ttu-id="0c9b0-114">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-114">The type of `expression`.</span></span>

<span data-ttu-id="0c9b0-115">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="0c9b0-116">CHECKSUM_AGG (collection)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="0c9b0-117">Retourne la somme de contrôle des valeurs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="0c9b0-118">Les valeurs Null sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="0c9b0-119">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-119">**Arguments**</span></span>
 
 <span data-ttu-id="0c9b0-120">Collection (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="0c9b0-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="0c9b0-121">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-121">**Return Value**</span></span>
 
 <span data-ttu-id="0c9b0-122">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-122">An `Int32`.</span></span>
 
 <span data-ttu-id="0c9b0-123">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-123">**Example**</span></span>
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="0c9b0-124">COUNT (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-124">COUNT(expression)</span></span>

<span data-ttu-id="0c9b0-125">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `Int32`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="0c9b0-126">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-126">**Arguments**</span></span>

<span data-ttu-id="0c9b0-127">Collection\<T >, où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="0c9b0-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="0c9b0-128">`Guid` (non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="0c9b0-129">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-129">**Return Value**</span></span>

<span data-ttu-id="0c9b0-130">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-130">An `Int32`.</span></span>

<span data-ttu-id="0c9b0-131">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a><span data-ttu-id="0c9b0-132">COUNT_BIG (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-132">COUNT_BIG(expression)</span></span>
 
<span data-ttu-id="0c9b0-133">Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `bigint`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-133">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="0c9b0-134">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-134">**Arguments**</span></span>
 
 <span data-ttu-id="0c9b0-135">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="0c9b0-135">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="0c9b0-136">`Guid` (non retourné dans SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="0c9b0-137">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-137">**Return Value**</span></span>

<span data-ttu-id="0c9b0-138">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-138">An `Int64`.</span></span>

<span data-ttu-id="0c9b0-139">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="0c9b0-140">MAX (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-140">MAX(expression)</span></span>

<span data-ttu-id="0c9b0-141">Retourne la valeur maximale contenue dans la collection.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="0c9b0-142">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-142">**Arguments**</span></span>

<span data-ttu-id="0c9b0-143">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="0c9b0-143">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="0c9b0-144">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-144">**Return Value**</span></span>

<span data-ttu-id="0c9b0-145">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-145">The type of `expression`.</span></span>

<span data-ttu-id="0c9b0-146">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="0c9b0-147">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-147">MIN(expression)</span></span>

<span data-ttu-id="0c9b0-148">Retourne la valeur minimale contenue dans une collection.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="0c9b0-149">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-149">**Arguments**</span></span>

<span data-ttu-id="0c9b0-150">Collection (T), où T est l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="0c9b0-150">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="0c9b0-151">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-151">**Return Value**</span></span>

<span data-ttu-id="0c9b0-152">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-152">The type of `expression`.</span></span>

<span data-ttu-id="0c9b0-153">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="0c9b0-154">ECARTYPE (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-154">STDEV(expression)</span></span>

<span data-ttu-id="0c9b0-155">Retourne l'écart type statistique de toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="0c9b0-156">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-156">**Arguments**</span></span>

<span data-ttu-id="0c9b0-157">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="0c9b0-157">A Collection(`Double`).</span></span>

<span data-ttu-id="0c9b0-158">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-158">**Return Value**</span></span>

<span data-ttu-id="0c9b0-159">`Double`</span><span class="sxs-lookup"><span data-stu-id="0c9b0-159">A `Double`.</span></span>

<span data-ttu-id="0c9b0-160">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="0c9b0-161">STDEVP (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-161">STDEVP(expression)</span></span>

<span data-ttu-id="0c9b0-162">Retourne l'écart type statistique du remplissage de toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="0c9b0-163">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-163">**Arguments**</span></span>

<span data-ttu-id="0c9b0-164">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="0c9b0-164">A Collection(`Double`).</span></span>

<span data-ttu-id="0c9b0-165">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-165">**Return Value**</span></span>

<span data-ttu-id="0c9b0-166">`Double`</span><span class="sxs-lookup"><span data-stu-id="0c9b0-166">A `Double`.</span></span>

<span data-ttu-id="0c9b0-167">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="0c9b0-168">SUM (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-168">SUM(expression)</span></span>

<span data-ttu-id="0c9b0-169">Retourne la somme de toutes les valeurs de la collection.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="0c9b0-170">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-170">**Arguments**</span></span>

<span data-ttu-id="0c9b0-171">Collection (T) où T est l’un des types suivants : `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="0c9b0-172">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-172">**Return Value**</span></span>

<span data-ttu-id="0c9b0-173">Type d'élément `expression`.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-173">The type of `expression`.</span></span>

<span data-ttu-id="0c9b0-174">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="0c9b0-175">VAR (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-175">VAR(expression)</span></span>

<span data-ttu-id="0c9b0-176">Retourne la variance statistique de toutes les valeurs dans l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="0c9b0-177">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-177">**Arguments**</span></span>

<span data-ttu-id="0c9b0-178">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="0c9b0-178">A Collection(`Double`).</span></span>

<span data-ttu-id="0c9b0-179">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-179">**Return Value**</span></span>

<span data-ttu-id="0c9b0-180">`Double`</span><span class="sxs-lookup"><span data-stu-id="0c9b0-180">A `Double`.</span></span>

<span data-ttu-id="0c9b0-181">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="0c9b0-182">VARP (expression)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-182">VARP(expression)</span></span>

<span data-ttu-id="0c9b0-183">Retourne la variance statistique de remplissage pour toutes les valeurs de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="0c9b0-184">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-184">**Arguments**</span></span>

<span data-ttu-id="0c9b0-185">Collection (`Double`).</span><span class="sxs-lookup"><span data-stu-id="0c9b0-185">A Collection(`Double`).</span></span>

<span data-ttu-id="0c9b0-186">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-186">**Return Value**</span></span>

<span data-ttu-id="0c9b0-187">`Double`</span><span class="sxs-lookup"><span data-stu-id="0c9b0-187">A `Double`.</span></span>

<span data-ttu-id="0c9b0-188">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0c9b0-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="0c9b0-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c9b0-189">See also</span></span>

- [<span data-ttu-id="0c9b0-190">Fonctions d’agrégation (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0c9b0-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="0c9b0-191">Langage Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0c9b0-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="0c9b0-192">Fonctions canoniques d’agrégation</span><span class="sxs-lookup"><span data-stu-id="0c9b0-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
