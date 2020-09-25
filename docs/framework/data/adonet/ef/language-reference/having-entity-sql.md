---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: a117f377b3f03b6a1a12e39426a24f3141aa40ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204461"
---
# <a name="having-entity-sql"></a><span data-ttu-id="c2a57-102">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c2a57-102">HAVING (Entity SQL)</span></span>

<span data-ttu-id="c2a57-103">Indique un critère de recherche pour un groupe ou une fonction d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="c2a57-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2a57-104">Syntax</span></span>  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c2a57-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c2a57-105">Arguments</span></span>  

 `search_condition`  
 <span data-ttu-id="c2a57-106">Indique les critères de recherche à réunir pour le groupe ou l'agrégat.</span><span class="sxs-lookup"><span data-stu-id="c2a57-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="c2a57-107">Lorsque HAVING est utilisé avec GROUP BY ALL, la clause HAVING remplace ALL.</span><span class="sxs-lookup"><span data-stu-id="c2a57-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2a57-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c2a57-108">Remarks</span></span>  

 <span data-ttu-id="c2a57-109">La clause HAVING est utilisée pour spécifier une condition de filtrage supplémentaire sur le résultat d'un regroupement.</span><span class="sxs-lookup"><span data-stu-id="c2a57-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="c2a57-110">Si aucune clause GROUP BY n'est spécifiée dans l'expression de requête, un groupe implicite constitué d'un seul ensemble est supposé exister.</span><span class="sxs-lookup"><span data-stu-id="c2a57-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2a57-111">HAVING ne peut être utilisé qu’avec l’instruction [Select](select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="c2a57-111">HAVING can be used only with the [SELECT](select-entity-sql.md) statement.</span></span> <span data-ttu-id="c2a57-112">Lorsque [Group by](group-by-entity-sql.md) n’est pas utilisé, having se comporte comme une clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="c2a57-112">When [GROUP BY](group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
<span data-ttu-id="c2a57-113">La clause HAVING fonctionne comme la clause WHERE, à la différence près que son application intervient après l'opération GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="c2a57-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="c2a57-114">Cela signifie que la clause HAVING ne peut faire référence qu’à des agrégats et des alias de regroupement, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c2a57-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example:</span></span>
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="c2a57-115">La clause précédente limite les groupes à ceux qui comportent plusieurs produits.</span><span class="sxs-lookup"><span data-stu-id="c2a57-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2a57-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2a57-116">Example</span></span>  

 <span data-ttu-id="c2a57-117">La requête Entity SQL ci-dessous utilise les opérateurs HAVING et GROUP BY pour spécifier un critère de recherche pour un groupe ou un agrégat.</span><span class="sxs-lookup"><span data-stu-id="c2a57-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="c2a57-118">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="c2a57-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c2a57-119">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c2a57-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c2a57-120">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c2a57-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="c2a57-121">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="c2a57-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a><span data-ttu-id="c2a57-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2a57-122">See also</span></span>

- [<span data-ttu-id="c2a57-123">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c2a57-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c2a57-124">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="c2a57-124">Query Expressions</span></span>](query-expressions-entity-sql.md)
