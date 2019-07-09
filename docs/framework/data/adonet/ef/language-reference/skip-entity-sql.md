---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 88d4c9c987f451e9a653d5b9c213e7158670ed4b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662138"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="d1a6f-102">SKIP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d1a6f-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="d1a6f-103">Vous pouvez effectuer une pagination physique à l'aide de la sous-clause SKIP de la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="d1a6f-104">La sous-clause SKIP ne peut pas être utilisée séparément de la clause ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a6f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1a6f-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d1a6f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d1a6f-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="d1a6f-107">Nombre d'éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1a6f-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d1a6f-108">Remarks</span></span>  
 <span data-ttu-id="d1a6f-109">Si une sous-clause d'expression SKIP est présente dans une clause ORDER BY, les résultats sont triés en fonction de la spécification de classement et le jeu de résultats comprend plusieurs lignes immédiatement à la suite de l'expression SKIP.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="d1a6f-110">Par exemple, SKIP 5 ignore les cinq premières lignes et retourne la sixième ligne et les suivantes.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1a6f-111">Une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas valide si le modificateur TOP et la sous-clause SKIP figurent dans la même expression de requête.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="d1a6f-112">La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1a6f-113">Dans SQL Server 2000, l’utilisation de SKIP avec ORDER BY sur des colonnes non-clés peut retourner des résultats incorrects.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="d1a6f-114">Le nombre de lignes ignorées peut être supérieur au nombre de lignes spécifié si la colonne non-clé contient des données en double.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="d1a6f-115">Il s’agit en raison de la façon dont la sous-clause SKIP est traduite pour SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="d1a6f-116">Par exemple, dans le code suivant plus de cinq lignes pourraient être ignorées si `E.NonKeyColumn` contient des valeurs en double :</span><span class="sxs-lookup"><span data-stu-id="d1a6f-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="d1a6f-117">Le [!INCLUDE[esql](../../../../../../includes/esql-md.md)] interroger dans [Comment : Résultats de la page via requête](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) utilise l’opérateur ORDER BY avec SKIP pour spécifier l’ordre de tri utilisé sur les objets retournés dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="d1a6f-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a6f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1a6f-118">See also</span></span>

- [<span data-ttu-id="d1a6f-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="d1a6f-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="d1a6f-120">[Guide pratique pour Parcourir les résultats de la requête](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1a6f-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="d1a6f-121">Pagination</span><span class="sxs-lookup"><span data-stu-id="d1a6f-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="d1a6f-122">TOP</span><span class="sxs-lookup"><span data-stu-id="d1a6f-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
