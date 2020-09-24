---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 81d135785e567d46a105adcafbf083f48cb4868e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161761"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="47d92-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="47d92-102">LIMIT (Entity SQL)</span></span>

<span data-ttu-id="47d92-103">Une pagination physique peut être effectuée par le biais de la sous-clause LIMIT de la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="47d92-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="47d92-104">La sous-clause LIMIT ne peut pas être utilisée sans la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="47d92-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d92-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47d92-105">Syntax</span></span>  
  
```sql  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="47d92-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="47d92-106">Arguments</span></span>  

 `n`  
 <span data-ttu-id="47d92-107">Nombre d'éléments qui seront sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="47d92-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="47d92-108">Si une sous-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT.</span><span class="sxs-lookup"><span data-stu-id="47d92-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="47d92-109">Par exemple, LIMIT 5 limitera le jeu de résultats à 5 instances ou lignes.</span><span class="sxs-lookup"><span data-stu-id="47d92-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="47d92-110">LIMIT est d'un point de vue fonctionnel équivalent à TOP, sauf que LIMIT a besoin de la présence de la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="47d92-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="47d92-111">SKIP et LIMIT peuvent être utilisés indépendamment avec la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="47d92-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47d92-112">Une requête Entity SQL est considérée comme non valide si le modificateur TOP et la sous-clause SKIP se trouvent dans une même expression de requête.</span><span class="sxs-lookup"><span data-stu-id="47d92-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="47d92-113">La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.</span><span class="sxs-lookup"><span data-stu-id="47d92-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47d92-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="47d92-114">Example</span></span>  

 <span data-ttu-id="47d92-115">La requête Entity SQL suivante utilise l'opérateur ORDER BY avec LIMIT pour spécifier l'ordre de classement employé sur les objets retournés dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="47d92-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="47d92-116">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="47d92-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="47d92-117">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="47d92-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="47d92-118">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="47d92-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="47d92-119">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="47d92-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="47d92-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47d92-120">See also</span></span>

- [<span data-ttu-id="47d92-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="47d92-121">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="47d92-122">[Procédure : pagination dans les résultats d’une requête](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="47d92-122">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="47d92-123">Pagination</span><span class="sxs-lookup"><span data-stu-id="47d92-123">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="47d92-124">TOP</span><span class="sxs-lookup"><span data-stu-id="47d92-124">TOP</span></span>](top-entity-sql.md)
