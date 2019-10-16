---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319207"
---
# <a name="using-entity-sql"></a><span data-ttu-id="da514-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="da514-102">USING (Entity SQL)</span></span>
<span data-ttu-id="da514-103">Spécifie les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="da514-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da514-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da514-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="da514-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="da514-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="da514-106">Spécifie un alias plus court avec lequel qualifier un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="da514-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="da514-107">Tout espace de noms valide.</span><span class="sxs-lookup"><span data-stu-id="da514-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da514-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="da514-108">Example</span></span>  
 <span data-ttu-id="da514-109">La requête Entity SQL ci-dessous utilise l'opérateur USING pour spécifier les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="da514-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="da514-110">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="da514-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="da514-111">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="da514-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="da514-112">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="da514-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="da514-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da514-113">See also</span></span>

- [<span data-ttu-id="da514-114">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="da514-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="da514-115">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="da514-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
