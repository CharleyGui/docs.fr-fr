---
title: '&amp;&amp; (et) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: be6e7120e6c19714f151aa38a8b9a1355de29d1a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039953"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="14fb8-102">&amp;&amp; (et) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="14fb8-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="14fb8-103">Retourne `true` si les deux expressions ont pour valeur `true`; sinon, `false` ou la valeur `NULL`.</span><span class="sxs-lookup"><span data-stu-id="14fb8-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14fb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14fb8-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```
 
<span data-ttu-id="14fb8-105">or</span><span class="sxs-lookup"><span data-stu-id="14fb8-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="14fb8-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="14fb8-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="14fb8-107">Toute expression valide qui retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="14fb8-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14fb8-108">Notes</span><span class="sxs-lookup"><span data-stu-id="14fb8-108">Remarks</span></span>  
 <span data-ttu-id="14fb8-109">Les doubles « et » commerciaux (&&) ont la même fonctionnalité que l'opérateur AND.</span><span class="sxs-lookup"><span data-stu-id="14fb8-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="14fb8-110">Le tableau ci-dessous indique les valeurs d'entrée et les types de retour possibles.</span><span class="sxs-lookup"><span data-stu-id="14fb8-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="14fb8-111">true</span><span class="sxs-lookup"><span data-stu-id="14fb8-111">TRUE</span></span>|<span data-ttu-id="14fb8-112">false</span><span class="sxs-lookup"><span data-stu-id="14fb8-112">FALSE</span></span>|<span data-ttu-id="14fb8-113">NULL</span><span class="sxs-lookup"><span data-stu-id="14fb8-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="14fb8-114">false</span><span class="sxs-lookup"><span data-stu-id="14fb8-114">FALSE</span></span>|<span data-ttu-id="14fb8-115">false</span><span class="sxs-lookup"><span data-stu-id="14fb8-115">FALSE</span></span>|<span data-ttu-id="14fb8-116">false</span><span class="sxs-lookup"><span data-stu-id="14fb8-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="14fb8-117">NULL</span><span class="sxs-lookup"><span data-stu-id="14fb8-117">NULL</span></span>|<span data-ttu-id="14fb8-118">false</span><span class="sxs-lookup"><span data-stu-id="14fb8-118">FALSE</span></span>|<span data-ttu-id="14fb8-119">NULL</span><span class="sxs-lookup"><span data-stu-id="14fb8-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14fb8-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="14fb8-120">Example</span></span>  
 <span data-ttu-id="14fb8-121">La requête Entity SQL ci-dessous montre comment utiliser l'opérateur AND.</span><span class="sxs-lookup"><span data-stu-id="14fb8-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="14fb8-122">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="14fb8-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="14fb8-123">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="14fb8-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="14fb8-124">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="14fb8-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="14fb8-125">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="14fb8-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="14fb8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14fb8-126">See also</span></span>

- [<span data-ttu-id="14fb8-127">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="14fb8-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
