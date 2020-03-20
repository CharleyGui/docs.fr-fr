---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0b69d4cb64adc1f9232631d50ec42af0d1ba47e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150127"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="9dcc3-103">!</span><span class="sxs-lookup"><span data-stu-id="9dcc3-103">!</span></span> <span data-ttu-id="9dcc3-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9dcc3-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="9dcc3-105">Inverse une expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="9dcc3-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dcc3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dcc3-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="9dcc3-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="9dcc3-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="9dcc3-108">Toute expression valide qui retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="9dcc3-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dcc3-109">Notes </span><span class="sxs-lookup"><span data-stu-id="9dcc3-109">Remarks</span></span>  
 <span data-ttu-id="9dcc3-110">Le point d'exclamation (!) a la même fonctionnalité que l'opérateur NOT.</span><span class="sxs-lookup"><span data-stu-id="9dcc3-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dcc3-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9dcc3-111">Example</span></span>  
 <span data-ttu-id="9dcc3-112">La requête Entity SQL ci-dessous utilise l'opérateur NOT pour inverser une expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="9dcc3-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="9dcc3-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="9dcc3-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9dcc3-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9dcc3-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9dcc3-115">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9dcc3-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9dcc3-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="9dcc3-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="9dcc3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dcc3-117">See also</span></span>

- [<span data-ttu-id="9dcc3-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9dcc3-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
