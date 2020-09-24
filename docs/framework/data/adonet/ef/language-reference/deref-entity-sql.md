---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: c0c975ab5cf2761496db6efa1f88f409aa1b1abd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148215"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="49d46-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="49d46-102">DEREF (Entity SQL)</span></span>

<span data-ttu-id="49d46-103">Déréférence une valeur de référence et génère le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="49d46-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49d46-104">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="49d46-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="49d46-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="49d46-106">Toute expression de requête valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="49d46-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49d46-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="49d46-107">Return Value</span></span>  

 <span data-ttu-id="49d46-108">Valeur de l'entité référencée.</span><span class="sxs-lookup"><span data-stu-id="49d46-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49d46-109">Notes</span><span class="sxs-lookup"><span data-stu-id="49d46-109">Remarks</span></span>  

 <span data-ttu-id="49d46-110">L'opérateur DEREF déréférence une valeur de référence et génère le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="49d46-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="49d46-111">Par exemple, si `r` est une référence de type Ref \<T> , `Deref(r)` est une expression de type `T` qui génère l’entité référencée par `r` .</span><span class="sxs-lookup"><span data-stu-id="49d46-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="49d46-112">Si la valeur de référence est null ou non résolue (autrement dit, la cible de la référence n'existe pas), le résultat de l'opérateur DEREF est null.</span><span class="sxs-lookup"><span data-stu-id="49d46-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49d46-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="49d46-113">Example</span></span>  

 <span data-ttu-id="49d46-114">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur DEREF pour déréférencer une valeur de référence et générer le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="49d46-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="49d46-115">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="49d46-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="49d46-116">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="49d46-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="49d46-117">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="49d46-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="49d46-118">Passez à la méthode ExecutePrimitiveTypeQuery la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="49d46-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="49d46-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49d46-119">See also</span></span>

- [<span data-ttu-id="49d46-120">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="49d46-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="49d46-121">Réf</span><span class="sxs-lookup"><span data-stu-id="49d46-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="49d46-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="49d46-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="49d46-123">KEY</span><span class="sxs-lookup"><span data-stu-id="49d46-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="49d46-124">Types structurés Nullable</span><span class="sxs-lookup"><span data-stu-id="49d46-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
