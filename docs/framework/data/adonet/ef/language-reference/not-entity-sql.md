---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 7755219c5238f78e59332c508643fe2ae1f5096f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319519"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="dd453-103">!</span><span class="sxs-lookup"><span data-stu-id="dd453-103">!</span></span> <span data-ttu-id="dd453-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dd453-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="dd453-105">Inverse une expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dd453-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd453-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd453-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
``` 
  
## <a name="arguments"></a><span data-ttu-id="dd453-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="dd453-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="dd453-108">Toute expression valide qui retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="dd453-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd453-109">Notes</span><span class="sxs-lookup"><span data-stu-id="dd453-109">Remarks</span></span>  
 <span data-ttu-id="dd453-110">Le point d'exclamation (!) a la même fonctionnalité que l'opérateur NOT.</span><span class="sxs-lookup"><span data-stu-id="dd453-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd453-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd453-111">Example</span></span>  
 <span data-ttu-id="dd453-112">La requête Entity SQL ci-dessous utilise l'opérateur NOT pour inverser une expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dd453-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="dd453-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="dd453-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dd453-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="dd453-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dd453-115">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="dd453-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="dd453-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="dd453-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="dd453-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd453-117">See also</span></span>

- [<span data-ttu-id="dd453-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="dd453-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
