---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: fe8a177b83932c1c7607f8444c05292c0ee29684
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250845"
---
# <a name="having-entity-sql"></a><span data-ttu-id="e764c-102">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e764c-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="e764c-103">Spécifie une condition de recherche pour un groupe ou un agrégat.</span><span class="sxs-lookup"><span data-stu-id="e764c-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e764c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e764c-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e764c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e764c-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="e764c-106">Indique les critères de recherche à réunir pour le groupe ou l'agrégat.</span><span class="sxs-lookup"><span data-stu-id="e764c-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="e764c-107">Lorsque HAVING est utilisé avec GROUP BY ALL, la clause HAVING remplace ALL.</span><span class="sxs-lookup"><span data-stu-id="e764c-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e764c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e764c-108">Remarks</span></span>  
 <span data-ttu-id="e764c-109">La clause HAVING est utilisée pour spécifier une condition de filtrage supplémentaire sur le résultat d'un regroupement.</span><span class="sxs-lookup"><span data-stu-id="e764c-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="e764c-110">Si aucune clause GROUP BY n'est spécifiée dans l'expression de requête, un groupe implicite constitué d'un seul ensemble est supposé exister.</span><span class="sxs-lookup"><span data-stu-id="e764c-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e764c-111">HAVING ne peut être utilisé qu’avec l’instruction [Select](select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="e764c-111">HAVING can be used only with the [SELECT](select-entity-sql.md) statement.</span></span> <span data-ttu-id="e764c-112">Lorsque [Group by](group-by-entity-sql.md) n’est pas utilisé, having se comporte comme une clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="e764c-112">When [GROUP BY](group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="e764c-113">La clause HAVING fonctionne comme la clause WHERE, à la différence près que son application intervient après l'opération GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="e764c-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="e764c-114">Cela signifie que la clause HAVING ne peut faire référence qu'à des agrégats et des alias de regroupement, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e764c-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="e764c-115">La clause précédente limite les groupes à ceux qui comportent plusieurs produits.</span><span class="sxs-lookup"><span data-stu-id="e764c-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e764c-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="e764c-116">Example</span></span>  
 <span data-ttu-id="e764c-117">La requête Entity SQL ci-dessous utilise les opérateurs HAVING et GROUP BY pour spécifier un critère de recherche pour un groupe ou un agrégat.</span><span class="sxs-lookup"><span data-stu-id="e764c-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="e764c-118">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="e764c-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e764c-119">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e764c-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e764c-120">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md)de PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="e764c-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="e764c-121">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="e764c-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="e764c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e764c-122">See also</span></span>

- [<span data-ttu-id="e764c-123">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e764c-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e764c-124">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="e764c-124">Query Expressions</span></span>](query-expressions-entity-sql.md)
