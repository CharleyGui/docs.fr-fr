---
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 65efedd36401db402a32748afaebff0f2af9f2a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185221"
---
# <a name="case-entity-sql"></a><span data-ttu-id="72aa2-102">CASE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="72aa2-102">CASE (Entity SQL)</span></span>

<span data-ttu-id="72aa2-103">Évalue un ensemble d'expressions `Boolean` pour déterminer le résultat.</span><span class="sxs-lookup"><span data-stu-id="72aa2-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72aa2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72aa2-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="72aa2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="72aa2-105">Arguments</span></span>  

 `n`  
 <span data-ttu-id="72aa2-106">Est un espace réservé indiquant que plusieurs clauses WHEN `Boolean_expression` THEN `result_expression` peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="72aa2-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="72aa2-107">THEN `result_expression`</span><span class="sxs-lookup"><span data-stu-id="72aa2-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="72aa2-108">Expression retournée lorsque `Boolean_expression` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="72aa2-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="72aa2-109">`result expression` peut être une expression valide quelconque.</span><span class="sxs-lookup"><span data-stu-id="72aa2-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="72aa2-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="72aa2-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="72aa2-111">Expression retournée si aucune opération de comparaison ne donne `true`.</span><span class="sxs-lookup"><span data-stu-id="72aa2-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="72aa2-112">Si cet argument est omis et qu'aucune opération de comparaison n'a la valeur `true`, CASE retourne la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="72aa2-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="72aa2-113">`else_result_expression` peut être une expression valide quelconque.</span><span class="sxs-lookup"><span data-stu-id="72aa2-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="72aa2-114">Les types de données de `else_result_expression` et celui de tout argument `result_expression` doivent être identiques ou permettre une conversion implicite.</span><span class="sxs-lookup"><span data-stu-id="72aa2-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="72aa2-115">WHEN `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="72aa2-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="72aa2-116">Expression `Boolean` évaluée lorsque le format CASE recherché est utilisé.</span><span class="sxs-lookup"><span data-stu-id="72aa2-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="72aa2-117">`Boolean_expression` peut être une expression `Boolean` valide quelconque.</span><span class="sxs-lookup"><span data-stu-id="72aa2-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72aa2-118">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="72aa2-118">Return Value</span></span>  

 <span data-ttu-id="72aa2-119">Retourne le type de priorité le plus élevé de l'ensemble des types dans `result_expression` ainsi que la valeur facultative `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="72aa2-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72aa2-120">Notes</span><span class="sxs-lookup"><span data-stu-id="72aa2-120">Remarks</span></span>  

 <span data-ttu-id="72aa2-121">L' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression case ressemble à l’expression case Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="72aa2-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="72aa2-122">Vous pouvez utiliser l'expression case pour effectuer une série de tests conditionnels visant à identifier l'expression qui produira le résultat approprié.</span><span class="sxs-lookup"><span data-stu-id="72aa2-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="72aa2-123">Cette forme de l'expression case s'applique à une série d'une ou de plusieurs expressions `Boolean` pour déterminer l'expression résultante correcte.</span><span class="sxs-lookup"><span data-stu-id="72aa2-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="72aa2-124">La fonction CASE évalue `Boolean_expression` pour chaque clause WHEN dans l'ordre spécifié et retourne l'expression `result_expression` de la première expression `Boolean_expression` qui prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="72aa2-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="72aa2-125">Les expressions restantes ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="72aa2-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="72aa2-126">Si aucune expression `Boolean_expression` ne prend la valeur `true`, le moteur de base de données retourne l'expression `else_result_expression` si une clause ELSE est spécifiée ou la valeur Null dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="72aa2-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="72aa2-127">Une instruction CASE ne peut pas retourner de multiset.</span><span class="sxs-lookup"><span data-stu-id="72aa2-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72aa2-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="72aa2-128">Example</span></span>  

 <span data-ttu-id="72aa2-129">La requête Entity SQL ci-dessous utilise l'expression CASE pour évaluer un ensemble d'expressions `Boolean` afin de déterminer le résultat.</span><span class="sxs-lookup"><span data-stu-id="72aa2-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="72aa2-130">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="72aa2-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="72aa2-131">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="72aa2-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="72aa2-132">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="72aa2-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="72aa2-133">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="72aa2-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="72aa2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72aa2-134">See also</span></span>

- [<span data-ttu-id="72aa2-135">THEN</span><span class="sxs-lookup"><span data-stu-id="72aa2-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="72aa2-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="72aa2-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="72aa2-137">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="72aa2-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
