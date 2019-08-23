---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: e637218bb3db69d4b09fd734b939fd30f50ed806
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961889"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="babe9-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="babe9-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="babe9-103">Une pagination physique peut être effectuée par le biais de la sous-clause LIMIT de la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="babe9-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="babe9-104">La sous-clause LIMIT ne peut pas être utilisée sans la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="babe9-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babe9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="babe9-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="babe9-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="babe9-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="babe9-107">Nombre d'éléments qui seront sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="babe9-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="babe9-108">Si une sous-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT.</span><span class="sxs-lookup"><span data-stu-id="babe9-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="babe9-109">Par exemple, LIMIT 5 limitera le jeu de résultats à 5 instances ou lignes.</span><span class="sxs-lookup"><span data-stu-id="babe9-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="babe9-110">LIMIT est d'un point de vue fonctionnel équivalent à TOP, sauf que LIMIT a besoin de la présence de la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="babe9-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="babe9-111">SKIP et LIMIT peuvent être utilisés indépendamment avec la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="babe9-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="babe9-112">Une requête Entity SQL est considérée comme non valide si le modificateur TOP et la sous-clause SKIP se trouvent dans une même expression de requête.</span><span class="sxs-lookup"><span data-stu-id="babe9-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="babe9-113">La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.</span><span class="sxs-lookup"><span data-stu-id="babe9-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="babe9-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="babe9-114">Example</span></span>  
 <span data-ttu-id="babe9-115">La requête Entity SQL suivante utilise l'opérateur ORDER BY avec LIMIT pour spécifier l'ordre de classement employé sur les objets retournés dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="babe9-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="babe9-116">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="babe9-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="babe9-117">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="babe9-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="babe9-118">Suivez la procédure décrite [dans la rubrique Procédure: Exécutez une requête qui retourne les résultats](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="babe9-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="babe9-119">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="babe9-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="babe9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="babe9-120">See also</span></span>

- [<span data-ttu-id="babe9-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="babe9-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="babe9-122">[Guide pratique : Page des résultats de la requête](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="babe9-122">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="babe9-123">Pagination</span><span class="sxs-lookup"><span data-stu-id="babe9-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="babe9-124">TOP</span><span class="sxs-lookup"><span data-stu-id="babe9-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
