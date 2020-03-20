---
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150465"
---
# <a name="case-entity-sql"></a><span data-ttu-id="76d76-102">CASE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="76d76-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="76d76-103">Évalue un ensemble d'expressions `Boolean` pour déterminer le résultat.</span><span class="sxs-lookup"><span data-stu-id="76d76-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76d76-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="76d76-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="76d76-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="76d76-106">Est un espace réservé indiquant que plusieurs clauses WHEN `Boolean_expression` THEN `result_expression` peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="76d76-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="76d76-107">THEN `result_expression`</span><span class="sxs-lookup"><span data-stu-id="76d76-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="76d76-108">Expression retournée lorsque `Boolean_expression` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="76d76-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="76d76-109">`result expression` peut être une expression valide quelconque.</span><span class="sxs-lookup"><span data-stu-id="76d76-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="76d76-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="76d76-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="76d76-111">Expression retournée si aucune opération de comparaison ne donne `true`.</span><span class="sxs-lookup"><span data-stu-id="76d76-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="76d76-112">Si cet argument est omis et qu'aucune opération de comparaison n'a la valeur `true`, CASE retourne la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="76d76-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="76d76-113">`else_result_expression` peut être une expression valide quelconque.</span><span class="sxs-lookup"><span data-stu-id="76d76-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="76d76-114">Les types de données de `else_result_expression` et celui de tout argument `result_expression` doivent être identiques ou permettre une conversion implicite.</span><span class="sxs-lookup"><span data-stu-id="76d76-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="76d76-115">WHEN `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="76d76-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="76d76-116">Expression `Boolean` évaluée lorsque le format CASE recherché est utilisé.</span><span class="sxs-lookup"><span data-stu-id="76d76-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="76d76-117">`Boolean_expression` peut être une expression `Boolean` valide quelconque.</span><span class="sxs-lookup"><span data-stu-id="76d76-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76d76-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="76d76-118">Return Value</span></span>  
 <span data-ttu-id="76d76-119">Retourne le type de priorité le plus élevé de l'ensemble des types dans `result_expression` ainsi que la valeur facultative `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="76d76-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76d76-120">Notes </span><span class="sxs-lookup"><span data-stu-id="76d76-120">Remarks</span></span>  
 <span data-ttu-id="76d76-121">L’expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de cas ressemble à l’expression de cas de Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="76d76-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="76d76-122">Vous pouvez utiliser l'expression case pour effectuer une série de tests conditionnels visant à identifier l'expression qui produira le résultat approprié.</span><span class="sxs-lookup"><span data-stu-id="76d76-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="76d76-123">Cette forme de l'expression case s'applique à une série d'une ou de plusieurs expressions `Boolean` pour déterminer l'expression résultante correcte.</span><span class="sxs-lookup"><span data-stu-id="76d76-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="76d76-124">La fonction CASE évalue `Boolean_expression` pour chaque clause WHEN dans l'ordre spécifié et retourne l'expression `result_expression` de la première expression `Boolean_expression` qui prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="76d76-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="76d76-125">Les expressions restantes ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="76d76-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="76d76-126">Si aucune expression `Boolean_expression` ne prend la valeur `true`, le moteur de base de données retourne l'expression `else_result_expression` si une clause ELSE est spécifiée ou la valeur Null dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="76d76-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="76d76-127">Une instruction CASE ne peut pas retourner de multiset.</span><span class="sxs-lookup"><span data-stu-id="76d76-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76d76-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="76d76-128">Example</span></span>  
 <span data-ttu-id="76d76-129">La requête Entity SQL ci-dessous utilise l'expression CASE pour évaluer un ensemble d'expressions `Boolean` afin de déterminer le résultat.</span><span class="sxs-lookup"><span data-stu-id="76d76-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="76d76-130">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="76d76-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="76d76-131">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="76d76-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="76d76-132">Suivez la procédure dans [Comment: Exécuter une requête qui retourne primitiveType Résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="76d76-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="76d76-133">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="76d76-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="76d76-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76d76-134">See also</span></span>

- [<span data-ttu-id="76d76-135">Puis</span><span class="sxs-lookup"><span data-stu-id="76d76-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="76d76-136">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="76d76-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="76d76-137">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="76d76-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
