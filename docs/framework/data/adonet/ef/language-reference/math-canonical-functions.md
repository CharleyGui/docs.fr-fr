---
title: Fonctions mathématiques canoniques
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250308"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="66a78-102">Fonctions mathématiques canoniques</span><span class="sxs-lookup"><span data-stu-id="66a78-102">Math Canonical Functions</span></span>

<span data-ttu-id="66a78-103">Entity SQL comprend les fonctions canoniques mathématiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="66a78-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="66a78-104">Abs(valeur)</span><span class="sxs-lookup"><span data-stu-id="66a78-104">Abs(value)</span></span>

<span data-ttu-id="66a78-105">Retourne la valeur absolue de `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="66a78-106">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="66a78-106">**Arguments**</span></span>

<span data-ttu-id="66a78-107">`Int16` ,,`Double`, ,,`Decimal`Et. `Byte` `Int32` `Int64` `Single`</span><span class="sxs-lookup"><span data-stu-id="66a78-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="66a78-108">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="66a78-108">**Return Value**</span></span>

<span data-ttu-id="66a78-109">Type d'élément `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-109">The type of `value`.</span></span>

<span data-ttu-id="66a78-110">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="66a78-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="66a78-111">Ceiling(valeur)</span><span class="sxs-lookup"><span data-stu-id="66a78-111">Ceiling(value)</span></span>

<span data-ttu-id="66a78-112">Retourne le plus petit entier qui n'est pas inférieur à `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="66a78-113">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="66a78-113">**Arguments**</span></span>

<span data-ttu-id="66a78-114">`Single` ,`Double`Et .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="66a78-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="66a78-115">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="66a78-115">**Return Value**</span></span>

<span data-ttu-id="66a78-116">Type d'élément `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-116">The type of `value`.</span></span>

<span data-ttu-id="66a78-117">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="66a78-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="66a78-118">Floor(valeur)</span><span class="sxs-lookup"><span data-stu-id="66a78-118">Floor(value)</span></span>

<span data-ttu-id="66a78-119">Retourne le plus grand entier qui n'est pas supérieur à `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="66a78-120">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="66a78-120">**Arguments**</span></span>

<span data-ttu-id="66a78-121">`Single` ,`Double`Et .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="66a78-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="66a78-122">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="66a78-122">**Return Value**</span></span>

<span data-ttu-id="66a78-123">Type d'élément `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-123">The type of `value`.</span></span>

<span data-ttu-id="66a78-124">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="66a78-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="66a78-125">Power(valeur, exposant)</span><span class="sxs-lookup"><span data-stu-id="66a78-125">Power(value, exponent)</span></span>

<span data-ttu-id="66a78-126">Retourne le résultat de `value` à l'exposant `exponent` spécifié.</span><span class="sxs-lookup"><span data-stu-id="66a78-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="66a78-127">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="66a78-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="66a78-128">`Int32, Int64, Double`, Ou`Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66a78-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="66a78-129">`Int64` ,`Double`Ou .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="66a78-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="66a78-130">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="66a78-130">**Return Value**</span></span>

<span data-ttu-id="66a78-131">Type d'élément `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-131">The type of `value`.</span></span>

<span data-ttu-id="66a78-132">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="66a78-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="66a78-133">Round(valeur)</span><span class="sxs-lookup"><span data-stu-id="66a78-133">Round(value)</span></span>

<span data-ttu-id="66a78-134">Retourne la partie entière de `value`, arrondie à l'entier le plus proche.</span><span class="sxs-lookup"><span data-stu-id="66a78-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="66a78-135">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="66a78-135">**Arguments**</span></span>

<span data-ttu-id="66a78-136">`Single` ,`Double`Et .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="66a78-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="66a78-137">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="66a78-137">**Return Value**</span></span>

<span data-ttu-id="66a78-138">Type d'élément `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-138">The type of `value`.</span></span>

<span data-ttu-id="66a78-139">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="66a78-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="66a78-140">Round(valeur, chiffres)</span><span class="sxs-lookup"><span data-stu-id="66a78-140">Round(value, digits)</span></span>

<span data-ttu-id="66a78-141">Retourne `value`, arrondi aux `digits` spécifiés les plus proches.</span><span class="sxs-lookup"><span data-stu-id="66a78-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="66a78-142">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="66a78-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="66a78-143">`Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66a78-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="66a78-144">`Int16` ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="66a78-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="66a78-145">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="66a78-145">**Return Value**</span></span>

<span data-ttu-id="66a78-146">Type d'élément `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-146">The type of `value`.</span></span>

<span data-ttu-id="66a78-147">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="66a78-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="66a78-148">Truncate(valeur, chiffres)</span><span class="sxs-lookup"><span data-stu-id="66a78-148">Truncate(value, digits)</span></span>

<span data-ttu-id="66a78-149">Retourne `value`, tronqué aux `digits` spécifiés les plus proches.</span><span class="sxs-lookup"><span data-stu-id="66a78-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="66a78-150">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="66a78-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="66a78-151">`Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66a78-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="66a78-152">`Int16` ou `Int32`.</span><span class="sxs-lookup"><span data-stu-id="66a78-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="66a78-153">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="66a78-153">**Return Value**</span></span>

<span data-ttu-id="66a78-154">Type d'élément `value`.</span><span class="sxs-lookup"><span data-stu-id="66a78-154">The type of `value`.</span></span>

<span data-ttu-id="66a78-155">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="66a78-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="66a78-156">Ces fonctions retournent `null` si une entrée de valeur `null` est fournie.</span><span class="sxs-lookup"><span data-stu-id="66a78-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="66a78-157">Des fonctionnalités équivalentes sont disponibles dans le fournisseur managé Client Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="66a78-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="66a78-158">Pour plus d’informations, consultez [SqlClient pour les fonctions de Entity Framework](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="66a78-158">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a78-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66a78-159">See also</span></span>

- [<span data-ttu-id="66a78-160">Fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="66a78-160">Canonical Functions</span></span>](canonical-functions.md)
