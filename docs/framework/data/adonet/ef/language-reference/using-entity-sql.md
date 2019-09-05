---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 9495e5daf88326c5a682172d835c3349fe79e571
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248761"
---
# <a name="using-entity-sql"></a><span data-ttu-id="11469-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="11469-102">USING (Entity SQL)</span></span>
<span data-ttu-id="11469-103">Spécifie les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="11469-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11469-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11469-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="11469-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="11469-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="11469-106">Spécifie un alias plus court avec lequel qualifier un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="11469-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="11469-107">Tout espace de noms valide.</span><span class="sxs-lookup"><span data-stu-id="11469-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11469-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="11469-108">Example</span></span>  
 <span data-ttu-id="11469-109">La requête Entity SQL ci-dessous utilise l'opérateur USING pour spécifier les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="11469-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="11469-110">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="11469-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="11469-111">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md)de PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="11469-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="11469-112">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="11469-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="11469-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11469-113">See also</span></span>

- [<span data-ttu-id="11469-114">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="11469-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="11469-115">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="11469-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
