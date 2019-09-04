---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: c64e440e8cd8f86706db69d923ba7085d0cb3b3a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248994"
---
# <a name="then-entity-sql"></a><span data-ttu-id="0a427-102">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0a427-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="0a427-103">Résultat d'une clause WHEN lorsqu'elle prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0a427-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a427-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a427-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0a427-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0a427-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="0a427-106">Toute expression booléenne valide.</span><span class="sxs-lookup"><span data-stu-id="0a427-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="0a427-107">Toute expression de requête valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="0a427-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a427-108">Notes</span><span class="sxs-lookup"><span data-stu-id="0a427-108">Remarks</span></span>  
 <span data-ttu-id="0a427-109">Si `when_expression` prend la valeur `true`, le résultat est l'expression `then-expression`correspondante.</span><span class="sxs-lookup"><span data-stu-id="0a427-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="0a427-110">Si aucune des conditions WHEN n'est remplie, `else-expression` est évaluée.</span><span class="sxs-lookup"><span data-stu-id="0a427-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="0a427-111">Toutefois, en l'absence d'une expression `else-expression`, le résultat est Null.</span><span class="sxs-lookup"><span data-stu-id="0a427-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="0a427-112">Pour obtenir un exemple, consultez [case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0a427-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a427-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a427-113">Example</span></span>  
 <span data-ttu-id="0a427-114">La requête Entity SQL ci-dessous utilise l'expression CASE pour évaluer un ensemble d'expressions `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0a427-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="0a427-115">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="0a427-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0a427-116">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0a427-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0a427-117">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md)de PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="0a427-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="0a427-118">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="0a427-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="0a427-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a427-119">See also</span></span>

- [<span data-ttu-id="0a427-120">CASE</span><span class="sxs-lookup"><span data-stu-id="0a427-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="0a427-121">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0a427-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
