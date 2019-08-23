---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 76a63140668fb1f41cf9e6f901d9a43240a1d098
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936083"
---
# <a name="having-entity-sql"></a><span data-ttu-id="bf2d9-102">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bf2d9-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="bf2d9-103">Spécifie une condition de recherche pour un groupe ou un agrégat.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf2d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf2d9-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf2d9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bf2d9-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="bf2d9-106">Indique les critères de recherche à réunir pour le groupe ou l'agrégat.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="bf2d9-107">Lorsque HAVING est utilisé avec GROUP BY ALL, la clause HAVING remplace ALL.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf2d9-108">Notes</span><span class="sxs-lookup"><span data-stu-id="bf2d9-108">Remarks</span></span>  
 <span data-ttu-id="bf2d9-109">La clause HAVING est utilisée pour spécifier une condition de filtrage supplémentaire sur le résultat d'un regroupement.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="bf2d9-110">Si aucune clause GROUP BY n'est spécifiée dans l'expression de requête, un groupe implicite constitué d'un seul ensemble est supposé exister.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf2d9-111">HAVING ne peut être utilisé qu’avec l’instruction [Select](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="bf2d9-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="bf2d9-112">Lorsque [Group by](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) n’est pas utilisé, having se comporte comme une clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="bf2d9-113">La clause HAVING fonctionne comme la clause WHERE, à la différence près que son application intervient après l'opération GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="bf2d9-114">Cela signifie que la clause HAVING ne peut faire référence qu'à des agrégats et des alias de regroupement, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="bf2d9-115">La clause précédente limite les groupes à ceux qui comportent plusieurs produits.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf2d9-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf2d9-116">Example</span></span>  
 <span data-ttu-id="bf2d9-117">La requête Entity SQL ci-dessous utilise les opérateurs HAVING et GROUP BY pour spécifier un critère de recherche pour un groupe ou un agrégat.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="bf2d9-118">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bf2d9-119">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="bf2d9-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bf2d9-120">Suivez la procédure décrite [dans la rubrique Procédure: Exécutez une requête qui retourne les résultats](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)de PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="bf2d9-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="bf2d9-121">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="bf2d9-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="bf2d9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf2d9-122">See also</span></span>

- [<span data-ttu-id="bf2d9-123">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bf2d9-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="bf2d9-124">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="bf2d9-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
