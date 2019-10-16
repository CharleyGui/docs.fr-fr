---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: ba01a978c53b58f7e6c1ac9bc42a97277ac64bbc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319285"
---
# <a name="then-entity-sql"></a><span data-ttu-id="e1ba7-102">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e1ba7-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="e1ba7-103">Résultat d'une clause WHEN lorsqu'elle prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e1ba7-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ba7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1ba7-104">Syntax</span></span>  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1ba7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e1ba7-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="e1ba7-106">Toute expression booléenne valide.</span><span class="sxs-lookup"><span data-stu-id="e1ba7-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="e1ba7-107">Toute expression de requête valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="e1ba7-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1ba7-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e1ba7-108">Remarks</span></span>  
 <span data-ttu-id="e1ba7-109">Si `when_expression` prend la valeur `true`, le résultat est l'expression `then-expression`correspondante.</span><span class="sxs-lookup"><span data-stu-id="e1ba7-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="e1ba7-110">Si aucune des conditions WHEN n'est remplie, `else-expression` est évaluée.</span><span class="sxs-lookup"><span data-stu-id="e1ba7-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="e1ba7-111">Toutefois, en l'absence d'une expression `else-expression`, le résultat est Null.</span><span class="sxs-lookup"><span data-stu-id="e1ba7-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="e1ba7-112">Pour obtenir un exemple, consultez [case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e1ba7-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1ba7-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1ba7-113">Example</span></span>  
 <span data-ttu-id="e1ba7-114">La requête Entity SQL ci-dessous utilise l'expression CASE pour évaluer un ensemble d'expressions `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="e1ba7-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="e1ba7-115">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="e1ba7-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e1ba7-116">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e1ba7-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e1ba7-117">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e1ba7-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="e1ba7-118">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="e1ba7-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="e1ba7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1ba7-119">See also</span></span>

- [<span data-ttu-id="e1ba7-120">CASE</span><span class="sxs-lookup"><span data-stu-id="e1ba7-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="e1ba7-121">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e1ba7-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
