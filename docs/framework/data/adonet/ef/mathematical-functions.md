---
title: Fonctions mathématiques
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182486"
---
# <a name="mathematical-functions"></a><span data-ttu-id="8db7a-102">Fonctions mathématiques</span><span class="sxs-lookup"><span data-stu-id="8db7a-102">Mathematical Functions</span></span>

<span data-ttu-id="8db7a-103">Le fournisseur de données .NET Framework pour SQL Server (SqlClient) propose des fonctions mathématiques qui effectuent des calculs sur des valeurs d’entrée qui sont fournies comme arguments, et retournent une valeur numérique comme résultat.</span><span class="sxs-lookup"><span data-stu-id="8db7a-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="8db7a-104">Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient.</span><span class="sxs-lookup"><span data-stu-id="8db7a-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="8db7a-105">La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="8db7a-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="8db7a-106">Le tableau suivant décrit les fonctions mathématiques SqlClient.</span><span class="sxs-lookup"><span data-stu-id="8db7a-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="8db7a-107">ABS (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-107">ABS(expression)</span></span>

<span data-ttu-id="8db7a-108">Effectue la fonction de valeur absolue.</span><span class="sxs-lookup"><span data-stu-id="8db7a-108">Performs the absolute value function.</span></span>

<span data-ttu-id="8db7a-109">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-109">**Arguments**</span></span>

<span data-ttu-id="8db7a-110">`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="8db7a-111">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-111">**Return Value**</span></span>

<span data-ttu-id="8db7a-112">Valeur absolue de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="8db7a-113">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="8db7a-114">ACOS (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-114">ACOS(expression)</span></span>

<span data-ttu-id="8db7a-115">Retourne la valeur d'arc cosinus de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="8db7a-116">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-116">**Arguments**</span></span>

<span data-ttu-id="8db7a-117">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="8db7a-118">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-118">**Return Value**</span></span>

<span data-ttu-id="8db7a-119">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-119">A `Double`.</span></span>

<span data-ttu-id="8db7a-120">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="8db7a-121">ASIN (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-121">ASIN(expression)</span></span>

<span data-ttu-id="8db7a-122">Retourne la valeur d'arcsinus de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="8db7a-123">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-123">**Arguments**</span></span>

<span data-ttu-id="8db7a-124">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="8db7a-125">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-125">**Return Value**</span></span>

<span data-ttu-id="8db7a-126">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-126">A `Double`.</span></span>

<span data-ttu-id="8db7a-127">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="8db7a-128">ATAN (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-128">ATAN(expression)</span></span>

<span data-ttu-id="8db7a-129">Retourne la valeur d'arctangente de l'expression numérique spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="8db7a-130">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-130">**Arguments**</span></span>

<span data-ttu-id="8db7a-131">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="8db7a-132">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-132">**Return Value**</span></span>

<span data-ttu-id="8db7a-133">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-133">A `Double`.</span></span>

<span data-ttu-id="8db7a-134">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="8db7a-135">ATN2 (expression, expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="8db7a-136">Retourne l'angle, en radians, dont la tangente est comprise entre les deux expressions numériques spécifiées.</span><span class="sxs-lookup"><span data-stu-id="8db7a-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="8db7a-137">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-137">**Arguments**</span></span>

<span data-ttu-id="8db7a-138">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="8db7a-139">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-139">**Return Value**</span></span>

<span data-ttu-id="8db7a-140">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-140">A `Double`.</span></span>

<span data-ttu-id="8db7a-141">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="8db7a-142">CEILING (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-142">CEILING(expression)</span></span>

<span data-ttu-id="8db7a-143">Convertit l'expression spécifiée en plus petit entier supérieur ou égal à cette expression.</span><span class="sxs-lookup"><span data-stu-id="8db7a-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="8db7a-144">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-144">**Arguments**</span></span>

<span data-ttu-id="8db7a-145">`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="8db7a-146">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-146">**Return Value**</span></span>

<span data-ttu-id="8db7a-147">,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="8db7a-148">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="8db7a-149">COS(expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-149">COS(expression)</span></span>

<span data-ttu-id="8db7a-150">Calcule le cosinus trigonométrique de l'angle spécifié, en radians.</span><span class="sxs-lookup"><span data-stu-id="8db7a-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="8db7a-151">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-151">**Arguments**</span></span> 

<span data-ttu-id="8db7a-152">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-153">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-153">**Return Value**</span></span> 

<span data-ttu-id="8db7a-154">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-154">A `Double`.</span></span> 

<span data-ttu-id="8db7a-155">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="8db7a-156">COT (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-156">COT(expression)</span></span>

<span data-ttu-id="8db7a-157">Calcule la cotangente trigonométrique de l'angle spécifié, en radians.</span><span class="sxs-lookup"><span data-stu-id="8db7a-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="8db7a-158">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-158">**Arguments**</span></span> 

<span data-ttu-id="8db7a-159">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-160">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-160">**Return Value**</span></span> 

<span data-ttu-id="8db7a-161">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-161">A `Double`.</span></span> 

<span data-ttu-id="8db7a-162">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="8db7a-163">DEGRÉS (radians)</span><span class="sxs-lookup"><span data-stu-id="8db7a-163">DEGREES(radians)</span></span>

<span data-ttu-id="8db7a-164">Retourne l'angle correspondant, en degrés.</span><span class="sxs-lookup"><span data-stu-id="8db7a-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="8db7a-165">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-165">**Arguments**</span></span> 

<span data-ttu-id="8db7a-166">`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="8db7a-167">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-167">**Return Value**</span></span> 

<span data-ttu-id="8db7a-168">,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="8db7a-169">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="8db7a-170">EXP (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-170">EXP(expression)</span></span>

<span data-ttu-id="8db7a-171">Calcule la valeur exponentielle d'une expression numérique spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="8db7a-172">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-172">**Arguments**</span></span> 

<span data-ttu-id="8db7a-173">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-174">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-174">**Return Value**</span></span> 

<span data-ttu-id="8db7a-175">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-175">A `Double`.</span></span> 

<span data-ttu-id="8db7a-176">**Exemple**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="8db7a-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="8db7a-177">FLOOR (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-177">FLOOR(expression)</span></span>

<span data-ttu-id="8db7a-178">Convertit l'expression spécifiée en plus grand entier inférieur ou égal à cette expression.</span><span class="sxs-lookup"><span data-stu-id="8db7a-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="8db7a-179">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-179">**Arguments**</span></span> 

<span data-ttu-id="8db7a-180">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-181">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-181">**Return Value**</span></span> 

<span data-ttu-id="8db7a-182">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-182">A `Double`.</span></span> 

<span data-ttu-id="8db7a-183">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="8db7a-184">LOG (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-184">LOG(expression)</span></span>

<span data-ttu-id="8db7a-185">Calcule le logarithme népérien de l'expression `float` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="8db7a-186">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-186">**Arguments**</span></span> 

<span data-ttu-id="8db7a-187">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-188">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-188">**Return Value**</span></span> 

<span data-ttu-id="8db7a-189">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-189">A `Double`.</span></span> 

<span data-ttu-id="8db7a-190">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="8db7a-191">LOG10 (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-191">LOG10(expression)</span></span>

<span data-ttu-id="8db7a-192">Retourne le logarithme en base 10 de l'expression `Double` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="8db7a-193">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-193">**Arguments**</span></span> 

<span data-ttu-id="8db7a-194">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-195">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-195">**Return Value**</span></span> 

<span data-ttu-id="8db7a-196">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-196">A `Double`.</span></span> 

<span data-ttu-id="8db7a-197">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="8db7a-198">PI()</span><span class="sxs-lookup"><span data-stu-id="8db7a-198">PI()</span></span>

<span data-ttu-id="8db7a-199">Retourne la valeur constante de pi sous la forme d'une valeur `Double`.</span><span class="sxs-lookup"><span data-stu-id="8db7a-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="8db7a-200">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-200">**Return Value**</span></span> 

<span data-ttu-id="8db7a-201">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-201">A `Double`.</span></span> 

<span data-ttu-id="8db7a-202">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="8db7a-203">PUISSANCE (expression_numérique, power_expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="8db7a-204">Calcule la valeur d'une expression donnée élevée à une puissance spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="8db7a-205">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="8db7a-206">,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="8db7a-207">Qui représente la puissance à laquelle le `numeric_expression`doit être déclenché. `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="8db7a-208">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-208">**Return Value**</span></span> 

<span data-ttu-id="8db7a-209">Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="8db7a-210">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="8db7a-211">RADIANs (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-211">RADIANS(expression)</span></span>

<span data-ttu-id="8db7a-212">Convertit les degrés en radians.</span><span class="sxs-lookup"><span data-stu-id="8db7a-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="8db7a-213">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-213">**Arguments**</span></span> 

<span data-ttu-id="8db7a-214">`expression`: ,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="8db7a-215">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-215">**Return Value**</span></span> 

<span data-ttu-id="8db7a-216">,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="8db7a-217">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="8db7a-218">RAND ([Seed])</span><span class="sxs-lookup"><span data-stu-id="8db7a-218">RAND([seed])</span></span>

<span data-ttu-id="8db7a-219">Retourne une valeur aléatoire comprise entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="8db7a-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="8db7a-220">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-220">**Arguments**</span></span> 

<span data-ttu-id="8db7a-221">Valeur de départ en tant `Int32`que.</span><span class="sxs-lookup"><span data-stu-id="8db7a-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="8db7a-222">Si la valeur initiale n'est pas spécifiée, le moteur de base de données SQL Server affecte une valeur initiale aléatoire.</span><span class="sxs-lookup"><span data-stu-id="8db7a-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="8db7a-223">Pour une valeur initiale spécifiée, le résultat retourné est toujours le même.</span><span class="sxs-lookup"><span data-stu-id="8db7a-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="8db7a-224">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-224">**Return Value**</span></span> 

<span data-ttu-id="8db7a-225">Valeur `Double` aléatoire comprise entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="8db7a-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="8db7a-226">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="8db7a-227">ROUND (expression_numérique, longueur [, fonction])</span><span class="sxs-lookup"><span data-stu-id="8db7a-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="8db7a-228">Retourne une expression numérique, arrondie à la longueur ou à la précision spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="8db7a-229">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="8db7a-230">,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="8db7a-231">`Int32` qui représente la précision selon laquelle arrondir `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="8db7a-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="8db7a-232">Lorsque `length` est un nombre positif, `numeric_expression` est arrondi au nombre de décimales indiqué par `length`.</span><span class="sxs-lookup"><span data-stu-id="8db7a-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="8db7a-233">Lorsque `length` est un nombre négatif, `numeric_expression` est arrondi à gauche de la virgule décimale, selon l'indication fournie par `length`.</span><span class="sxs-lookup"><span data-stu-id="8db7a-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="8db7a-234">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="8db7a-234">Optional.</span></span> <span data-ttu-id="8db7a-235">`Int32` Qui représente le type d’opération à effectuer.</span><span class="sxs-lookup"><span data-stu-id="8db7a-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="8db7a-236">Quand la fonction est omise ou a la valeur 0 (valeur par défaut `numeric_expression` ), est arrondie.</span><span class="sxs-lookup"><span data-stu-id="8db7a-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="8db7a-237">Lorsqu’une valeur autre que 0 est spécifiée, `numeric_expression` est tronqué.</span><span class="sxs-lookup"><span data-stu-id="8db7a-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="8db7a-238">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-238">**Return Value**</span></span> 

<span data-ttu-id="8db7a-239">Valeur du paramètre `numeric_expression` donné élevé à la puissance `power_expression` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="8db7a-240">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="8db7a-241">SIGN (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-241">SIGN(expression)</span></span> 

<span data-ttu-id="8db7a-242">Retourne le signe positif (+1), nul (0) ou négatif (-1) de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="8db7a-243">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-243">**Arguments**</span></span> 

<span data-ttu-id="8db7a-244">`expression` : `Int32`, `Int64`, `Double` ou `Decimal`</span><span class="sxs-lookup"><span data-stu-id="8db7a-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="8db7a-245">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-245">**Return Value**</span></span> 

<span data-ttu-id="8db7a-246">,, Ou`Decimal`. `Int32` `Int64` `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="8db7a-247">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="8db7a-248">SIN(expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-248">SIN(expression)</span></span>

<span data-ttu-id="8db7a-249">Calcule le sinus trigonométrique de l'angle spécifié, en radians, et retourne une expression `Double`.</span><span class="sxs-lookup"><span data-stu-id="8db7a-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="8db7a-250">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-250">**Arguments**</span></span> 

<span data-ttu-id="8db7a-251">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-252">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-252">**Return Value**</span></span> 

<span data-ttu-id="8db7a-253">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-253">A `Double`.</span></span> 

<span data-ttu-id="8db7a-254">**Exemple**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="8db7a-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="8db7a-255">SQRT (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-255">SQRT(expression)</span></span>

<span data-ttu-id="8db7a-256">Retourne la racine carrée de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="8db7a-257">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-257">**Arguments**</span></span> 

<span data-ttu-id="8db7a-258">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-259">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-259">**Return Value**</span></span> 

<span data-ttu-id="8db7a-260">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-260">A `Double`.</span></span> 

<span data-ttu-id="8db7a-261">**Exemple**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="8db7a-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="8db7a-262">SQUARE (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-262">SQUARE(expression)</span></span>

<span data-ttu-id="8db7a-263">Retourne le carré de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="8db7a-264">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-264">**Arguments**</span></span> 

<span data-ttu-id="8db7a-265">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="8db7a-266">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-266">**Return Value**</span></span> 

<span data-ttu-id="8db7a-267">`Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-267">A `Double`.</span></span> 

<span data-ttu-id="8db7a-268">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="8db7a-269">TAN (expression)</span><span class="sxs-lookup"><span data-stu-id="8db7a-269">TAN(expression)</span></span>

<span data-ttu-id="8db7a-270">Calcule la tangente d'une expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8db7a-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="8db7a-271">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="8db7a-271">**Arguments**</span></span> 

<span data-ttu-id="8db7a-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="8db7a-272">`expression`: `Double`</span></span> 

<span data-ttu-id="8db7a-273">**Valeur de retour**</span><span class="sxs-lookup"><span data-stu-id="8db7a-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="8db7a-274">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="8db7a-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="8db7a-275">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8db7a-275">See also</span></span>

<span data-ttu-id="8db7a-276">Pour plus d'informations sur les fonctions mathématiques prises en charge par SqlClient, consultez la documentation correspondant à la version de SQL Server que vous avez spécifiée dans le manifeste du fournisseur SqlClient :</span><span class="sxs-lookup"><span data-stu-id="8db7a-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="8db7a-277">**SQL Server 2005 :** [Fonctions mathématiques (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="8db7a-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="8db7a-278">**SQL Server 2008 :** [Fonctions mathématiques (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="8db7a-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="8db7a-279">**SQL Server 2012 et versions ultérieures :** [Fonctions mathématiques (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="8db7a-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span></span>

- [<span data-ttu-id="8db7a-280">Fonctions SqlClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8db7a-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
