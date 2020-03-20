---
title: Fonctions mathématiques
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149763"
---
# <a name="mathematical-functions"></a><span data-ttu-id="26dd3-102">Fonctions mathématiques</span><span class="sxs-lookup"><span data-stu-id="26dd3-102">Mathematical Functions</span></span>

<span data-ttu-id="26dd3-103">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) propose des fonctions mathématiques qui effectuent des calculs sur des valeurs d’entrée qui sont fournies comme arguments, et retournent une valeur numérique comme résultat.</span><span class="sxs-lookup"><span data-stu-id="26dd3-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="26dd3-104">Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient.</span><span class="sxs-lookup"><span data-stu-id="26dd3-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="26dd3-105">La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="26dd3-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="26dd3-106">Le tableau suivant décrit les fonctions mathématiques SqlClient.</span><span class="sxs-lookup"><span data-stu-id="26dd3-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="26dd3-107">ABS (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-107">ABS(expression)</span></span>

<span data-ttu-id="26dd3-108">Effectue la fonction de valeur absolue.</span><span class="sxs-lookup"><span data-stu-id="26dd3-108">Performs the absolute value function.</span></span>

<span data-ttu-id="26dd3-109">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-109">**Arguments**</span></span>

<span data-ttu-id="26dd3-110">`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-111">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-111">**Return Value**</span></span>

<span data-ttu-id="26dd3-112">Valeur absolue de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="26dd3-113">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="26dd3-114">ACOS (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-114">ACOS(expression)</span></span>

<span data-ttu-id="26dd3-115">Retourne la valeur d'arc cosinus de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="26dd3-116">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-116">**Arguments**</span></span>

<span data-ttu-id="26dd3-117">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-118">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-118">**Return Value**</span></span>

<span data-ttu-id="26dd3-119">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-119">A `Double`.</span></span>

<span data-ttu-id="26dd3-120">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="26dd3-121">ASIN (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-121">ASIN(expression)</span></span>

<span data-ttu-id="26dd3-122">Retourne la valeur d'arcsinus de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="26dd3-123">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-123">**Arguments**</span></span>

<span data-ttu-id="26dd3-124">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-125">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-125">**Return Value**</span></span>

<span data-ttu-id="26dd3-126">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-126">A `Double`.</span></span>

<span data-ttu-id="26dd3-127">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="26dd3-128">ATAN(expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-128">ATAN(expression)</span></span>

<span data-ttu-id="26dd3-129">Retourne la valeur d'arctangente de l'expression numérique spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="26dd3-130">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-130">**Arguments**</span></span>

<span data-ttu-id="26dd3-131">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-132">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-132">**Return Value**</span></span>

<span data-ttu-id="26dd3-133">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-133">A `Double`.</span></span>

<span data-ttu-id="26dd3-134">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="26dd3-135">ATN2 (expression, expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="26dd3-136">Retourne l'angle, en radians, dont la tangente est comprise entre les deux expressions numériques spécifiées.</span><span class="sxs-lookup"><span data-stu-id="26dd3-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="26dd3-137">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-137">**Arguments**</span></span>

<span data-ttu-id="26dd3-138">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-139">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-139">**Return Value**</span></span>

<span data-ttu-id="26dd3-140">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-140">A `Double`.</span></span>

<span data-ttu-id="26dd3-141">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="26dd3-142">CEILING(expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-142">CEILING(expression)</span></span>

<span data-ttu-id="26dd3-143">Convertit l'expression spécifiée en plus petit entier supérieur ou égal à cette expression.</span><span class="sxs-lookup"><span data-stu-id="26dd3-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="26dd3-144">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-144">**Arguments**</span></span>

<span data-ttu-id="26dd3-145">`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-146">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-146">**Return Value**</span></span>

<span data-ttu-id="26dd3-147">Un `Int32` `Int64`, `Double`, `Decimal`, ou .</span><span class="sxs-lookup"><span data-stu-id="26dd3-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-148">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-148">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="26dd3-149">COS (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-149">COS(expression)</span></span>

<span data-ttu-id="26dd3-150">Calcule le cosinus trigonométrique de l'angle spécifié, en radians.</span><span class="sxs-lookup"><span data-stu-id="26dd3-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="26dd3-151">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-151">**Arguments**</span></span>

<span data-ttu-id="26dd3-152">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-152">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-153">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-153">**Return Value**</span></span>

<span data-ttu-id="26dd3-154">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-154">A `Double`.</span></span>

<span data-ttu-id="26dd3-155">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-155">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="26dd3-156">COT (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-156">COT(expression)</span></span>

<span data-ttu-id="26dd3-157">Calcule la cotangente trigonométrique de l'angle spécifié, en radians.</span><span class="sxs-lookup"><span data-stu-id="26dd3-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="26dd3-158">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-158">**Arguments**</span></span>

<span data-ttu-id="26dd3-159">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-159">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-160">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-160">**Return Value**</span></span>

<span data-ttu-id="26dd3-161">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-161">A `Double`.</span></span>

<span data-ttu-id="26dd3-162">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-162">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="26dd3-163">DEGREES (radians)</span><span class="sxs-lookup"><span data-stu-id="26dd3-163">DEGREES(radians)</span></span>

<span data-ttu-id="26dd3-164">Retourne l'angle correspondant, en degrés.</span><span class="sxs-lookup"><span data-stu-id="26dd3-164">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="26dd3-165">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-165">**Arguments**</span></span>

<span data-ttu-id="26dd3-166">`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-167">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-167">**Return Value**</span></span>

<span data-ttu-id="26dd3-168">Un `Int32` `Int64`, `Double`, `Decimal`, ou .</span><span class="sxs-lookup"><span data-stu-id="26dd3-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-169">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-169">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="26dd3-170">EXP (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-170">EXP(expression)</span></span>

<span data-ttu-id="26dd3-171">Calcule la valeur exponentielle d'une expression numérique spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-171">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="26dd3-172">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-172">**Arguments**</span></span>

<span data-ttu-id="26dd3-173">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-173">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-174">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-174">**Return Value**</span></span>

<span data-ttu-id="26dd3-175">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-175">A `Double`.</span></span>

<span data-ttu-id="26dd3-176">**Exemple**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="26dd3-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="26dd3-177">FLOOR (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-177">FLOOR(expression)</span></span>

<span data-ttu-id="26dd3-178">Convertit l'expression spécifiée en plus grand entier inférieur ou égal à cette expression.</span><span class="sxs-lookup"><span data-stu-id="26dd3-178">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="26dd3-179">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-179">**Arguments**</span></span>

<span data-ttu-id="26dd3-180">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-180">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-181">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-181">**Return Value**</span></span>

<span data-ttu-id="26dd3-182">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-182">A `Double`.</span></span>

<span data-ttu-id="26dd3-183">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-183">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="26dd3-184">LOG(expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-184">LOG(expression)</span></span>

<span data-ttu-id="26dd3-185">Calcule le logarithme népérien de l'expression `float` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-185">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="26dd3-186">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-186">**Arguments**</span></span>

<span data-ttu-id="26dd3-187">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-187">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-188">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-188">**Return Value**</span></span>

<span data-ttu-id="26dd3-189">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-189">A `Double`.</span></span>

<span data-ttu-id="26dd3-190">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-190">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="26dd3-191">LOG10 (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-191">LOG10(expression)</span></span>

<span data-ttu-id="26dd3-192">Retourne le logarithme en base 10 de l'expression `Double` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="26dd3-193">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-193">**Arguments**</span></span>

<span data-ttu-id="26dd3-194">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-194">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-195">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-195">**Return Value**</span></span>

<span data-ttu-id="26dd3-196">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-196">A `Double`.</span></span>

<span data-ttu-id="26dd3-197">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-197">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="26dd3-198">PI()</span><span class="sxs-lookup"><span data-stu-id="26dd3-198">PI()</span></span>

<span data-ttu-id="26dd3-199">Retourne la valeur constante de pi sous la forme d'une valeur `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-199">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="26dd3-200">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-200">**Return Value**</span></span>

<span data-ttu-id="26dd3-201">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-201">A `Double`.</span></span>

<span data-ttu-id="26dd3-202">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-202">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="26dd3-203">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="26dd3-204">Calcule la valeur d'une expression donnée élevée à une puissance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="26dd3-205">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-205">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="26dd3-206">Un `Int32` `Int64`, `Double`, `Decimal`, ou .</span><span class="sxs-lookup"><span data-stu-id="26dd3-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="26dd3-207">Un `Double` qui représente le pouvoir `numeric_expression`auquel élever le .</span><span class="sxs-lookup"><span data-stu-id="26dd3-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="26dd3-208">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-208">**Return Value**</span></span>

<span data-ttu-id="26dd3-209">Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="26dd3-210">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-210">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="26dd3-211">RADIANS(expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-211">RADIANS(expression)</span></span>

<span data-ttu-id="26dd3-212">Convertit les degrés en radians.</span><span class="sxs-lookup"><span data-stu-id="26dd3-212">Converts degrees to radians.</span></span>

<span data-ttu-id="26dd3-213">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-213">**Arguments**</span></span>

<span data-ttu-id="26dd3-214">`expression` :`Int32`,`Int64`, `Double` ou `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-215">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-215">**Return Value**</span></span>

<span data-ttu-id="26dd3-216">Un `Int32` `Int64`, `Double`, `Decimal`, ou .</span><span class="sxs-lookup"><span data-stu-id="26dd3-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-217">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-217">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="26dd3-218">RAND ([semences])</span><span class="sxs-lookup"><span data-stu-id="26dd3-218">RAND([seed])</span></span>

<span data-ttu-id="26dd3-219">Retourne une valeur aléatoire comprise entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="26dd3-219">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="26dd3-220">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-220">**Arguments**</span></span>

<span data-ttu-id="26dd3-221">La valeur de `Int32`graine comme un .</span><span class="sxs-lookup"><span data-stu-id="26dd3-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="26dd3-222">Si la valeur initiale n'est pas spécifiée, le moteur de base de données SQL Server affecte une valeur initiale aléatoire.</span><span class="sxs-lookup"><span data-stu-id="26dd3-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="26dd3-223">Pour une valeur de départ spécifiée, le résultat retourné est toujours le même.</span><span class="sxs-lookup"><span data-stu-id="26dd3-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="26dd3-224">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-224">**Return Value**</span></span>

<span data-ttu-id="26dd3-225">Valeur `Double` aléatoire comprise entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="26dd3-225">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="26dd3-226">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-226">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="26dd3-227">ROUND (numeric_expression, longueur[,fonction])</span><span class="sxs-lookup"><span data-stu-id="26dd3-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="26dd3-228">Retourne une expression numérique, arrondie à la longueur ou à la précision spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-228">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="26dd3-229">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-229">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="26dd3-230">Un `Int32` `Int64`, `Double`, `Decimal`, ou .</span><span class="sxs-lookup"><span data-stu-id="26dd3-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="26dd3-231">`Int32` qui représente la précision selon laquelle arrondir `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="26dd3-232">Lorsque `length` est un nombre positif, `numeric_expression` est arrondi au nombre de décimales indiqué par `length`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="26dd3-233">Lorsque `length` est un nombre négatif, `numeric_expression` est arrondi à gauche de la virgule décimale, selon l'indication fournie par `length`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="26dd3-234">facultatif.</span><span class="sxs-lookup"><span data-stu-id="26dd3-234">Optional.</span></span> <span data-ttu-id="26dd3-235">Un `Int32` qui représente le type d’opération à effectuer.</span><span class="sxs-lookup"><span data-stu-id="26dd3-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="26dd3-236">Lorsque la fonction est omise ou a `numeric_expression` une valeur de 0 (par défaut), est arrondie.</span><span class="sxs-lookup"><span data-stu-id="26dd3-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="26dd3-237">Lorsqu’une valeur autre que `numeric_expression` 0 est spécifiée, est tronquée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="26dd3-238">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-238">**Return Value**</span></span>

<span data-ttu-id="26dd3-239">Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="26dd3-240">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-240">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="26dd3-241">SIGN(expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-241">SIGN(expression)</span></span>

<span data-ttu-id="26dd3-242">Renvoie le chiffre positif (+1), zéro (0) ou négatif (-1) de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="26dd3-243">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-243">**Arguments**</span></span>

<span data-ttu-id="26dd3-244">`expression` : `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="26dd3-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="26dd3-245">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-245">**Return Value**</span></span>

<span data-ttu-id="26dd3-246">Un `Int32` `Int64`, `Double`, `Decimal`, ou .</span><span class="sxs-lookup"><span data-stu-id="26dd3-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="26dd3-247">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-247">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="26dd3-248">SIN(expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-248">SIN(expression)</span></span>

<span data-ttu-id="26dd3-249">Calcule le sinus trigonométrique de l'angle spécifié, en radians, et retourne une expression `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="26dd3-250">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-250">**Arguments**</span></span>

<span data-ttu-id="26dd3-251">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-251">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-252">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-252">**Return Value**</span></span>

<span data-ttu-id="26dd3-253">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-253">A `Double`.</span></span>

<span data-ttu-id="26dd3-254">**Exemple**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="26dd3-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="26dd3-255">SQRT(expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-255">SQRT(expression)</span></span>

<span data-ttu-id="26dd3-256">Retourne la racine carrée de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-256">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="26dd3-257">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-257">**Arguments**</span></span>

<span data-ttu-id="26dd3-258">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-258">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-259">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-259">**Return Value**</span></span>

<span data-ttu-id="26dd3-260">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-260">A `Double`.</span></span>

<span data-ttu-id="26dd3-261">**Exemple**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="26dd3-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="26dd3-262">SQUARE (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-262">SQUARE(expression)</span></span>

<span data-ttu-id="26dd3-263">Retourne le carré de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-263">Returns the square of the specified expression.</span></span>

<span data-ttu-id="26dd3-264">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-264">**Arguments**</span></span>

<span data-ttu-id="26dd3-265">`expression` : une `Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-265">`expression`: A `Double`.</span></span>

<span data-ttu-id="26dd3-266">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-266">**Return Value**</span></span>

<span data-ttu-id="26dd3-267">`Double`.</span><span class="sxs-lookup"><span data-stu-id="26dd3-267">A `Double`.</span></span>

<span data-ttu-id="26dd3-268">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-268">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="26dd3-269">TAN (expression)</span><span class="sxs-lookup"><span data-stu-id="26dd3-269">TAN(expression)</span></span>

<span data-ttu-id="26dd3-270">Calcule la tangente d'une expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26dd3-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="26dd3-271">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="26dd3-271">**Arguments**</span></span>

<span data-ttu-id="26dd3-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="26dd3-272">`expression`: `Double`</span></span>

<span data-ttu-id="26dd3-273">**Valeur de rendement**</span><span class="sxs-lookup"><span data-stu-id="26dd3-273">**Return Value**</span></span>

`Double`

<span data-ttu-id="26dd3-274">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="26dd3-274">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="26dd3-275">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26dd3-275">See also</span></span>

- [<span data-ttu-id="26dd3-276">Fonctions mathématiques (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="26dd3-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="26dd3-277">Fonctions SqlClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="26dd3-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
