---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203590"
---
# <a name="using-entity-sql"></a><span data-ttu-id="8fc8e-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8fc8e-102">USING (Entity SQL)</span></span>

<span data-ttu-id="8fc8e-103">Spécifie les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="8fc8e-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fc8e-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="8fc8e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8fc8e-105">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="8fc8e-106">Spécifie un alias plus court avec lequel qualifier un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8fc8e-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="8fc8e-107">Tout espace de noms valide.</span><span class="sxs-lookup"><span data-stu-id="8fc8e-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc8e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="8fc8e-108">Example</span></span>  

 <span data-ttu-id="8fc8e-109">La requête Entity SQL ci-dessous utilise l'opérateur USING pour spécifier les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="8fc8e-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="8fc8e-110">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8fc8e-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8fc8e-111">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8fc8e-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="8fc8e-112">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="8fc8e-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fc8e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fc8e-113">See also</span></span>

- [<span data-ttu-id="8fc8e-114">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="8fc8e-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="8fc8e-115">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8fc8e-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
