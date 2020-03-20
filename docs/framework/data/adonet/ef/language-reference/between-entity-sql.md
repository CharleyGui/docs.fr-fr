---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150491"
---
# <a name="between-entity-sql"></a><span data-ttu-id="e9c6f-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e9c6f-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="e9c6f-103">Détermine si une expression a pour résultat une valeur contenue dans une plage spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="e9c6f-104">L’expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN a la même fonctionnalité que l’expression Transact-SQL BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c6f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9c6f-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="e9c6f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9c6f-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e9c6f-107">Toute expression valide à tester dans la plage définie par `begin_expression` et `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="e9c6f-108">`expression` doit être du même type qu'`begin_expression` et `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="e9c6f-109">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-109">Any valid expression.</span></span> <span data-ttu-id="e9c6f-110">`begin_expression` doit être du même type qu'`expression` et `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="e9c6f-111">`begin_expression` doit être inférieur à `end_expression` ou la valeur de retour sera niée.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="e9c6f-112">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-112">Any valid expression.</span></span> <span data-ttu-id="e9c6f-113">`end_expression` doit être du même type qu'`expression` et `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="e9c6f-114">NOT</span><span class="sxs-lookup"><span data-stu-id="e9c6f-114">NOT</span></span>  
 <span data-ttu-id="e9c6f-115">Indique que le résultat de BETWEEN est inversé.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="e9c6f-116">AND</span><span class="sxs-lookup"><span data-stu-id="e9c6f-116">AND</span></span>  
 <span data-ttu-id="e9c6f-117">Espace réservé qui indique que `expression` doit se trouver dans la plage définie par `begin_expression` et `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9c6f-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e9c6f-118">Return Value</span></span>  
 <span data-ttu-id="e9c6f-119">`true` si `expression` est entre la plage indiquée par `begin_expression` et `end_expression` ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="e9c6f-120">La valeur `null` est retournée si `expression` a la valeur `null` ou si `begin_expression` ou `end_expression` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9c6f-121">Notes </span><span class="sxs-lookup"><span data-stu-id="e9c6f-121">Remarks</span></span>  
 <span data-ttu-id="e9c6f-122">Pour spécifier une gamme exclusive, utilisez les opérateurs plus grands que (>) et inférieurs à (<) au lieu de BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9c6f-123"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e9c6f-123">Example</span></span>  
 <span data-ttu-id="e9c6f-124">La requête Entity SQL ci-dessous utilise l'opérateur BETWEEN pour déterminer si une expression génère une valeur située dans une plage spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="e9c6f-125">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="e9c6f-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e9c6f-126">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e9c6f-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e9c6f-127">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e9c6f-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e9c6f-128">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="e9c6f-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="e9c6f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9c6f-129">See also</span></span>

- [<span data-ttu-id="e9c6f-130">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e9c6f-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
