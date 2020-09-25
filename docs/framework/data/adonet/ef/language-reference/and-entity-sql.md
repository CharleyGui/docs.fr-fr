---
title: '&amp;&amp; LES (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 86ff43f8ed20c5696d15e21284394c3cb63200e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198039"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="f69cc-102">&amp;&amp; LES (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f69cc-102">&amp;&amp; (AND) (Entity SQL)</span></span>

<span data-ttu-id="f69cc-103">Retourne `true` si les deux expressions ont pour valeur `true`; sinon, `false` ou la valeur `NULL`.</span><span class="sxs-lookup"><span data-stu-id="f69cc-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f69cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f69cc-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="f69cc-105">or</span><span class="sxs-lookup"><span data-stu-id="f69cc-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f69cc-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f69cc-106">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="f69cc-107">Toute expression valide qui retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="f69cc-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f69cc-108">Notes</span><span class="sxs-lookup"><span data-stu-id="f69cc-108">Remarks</span></span>  

 <span data-ttu-id="f69cc-109">Les doubles « et » commerciaux (&&) ont la même fonctionnalité que l'opérateur AND.</span><span class="sxs-lookup"><span data-stu-id="f69cc-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="f69cc-110">Le tableau ci-dessous indique les valeurs d'entrée et les types de retour possibles.</span><span class="sxs-lookup"><span data-stu-id="f69cc-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="f69cc-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="f69cc-111">TRUE</span></span>|<span data-ttu-id="f69cc-112">FALSE</span><span class="sxs-lookup"><span data-stu-id="f69cc-112">FALSE</span></span>|<span data-ttu-id="f69cc-113">NULL</span><span class="sxs-lookup"><span data-stu-id="f69cc-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="f69cc-114">false</span><span class="sxs-lookup"><span data-stu-id="f69cc-114">FALSE</span></span>|<span data-ttu-id="f69cc-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="f69cc-115">FALSE</span></span>|<span data-ttu-id="f69cc-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="f69cc-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="f69cc-117">NULL</span><span class="sxs-lookup"><span data-stu-id="f69cc-117">NULL</span></span>|<span data-ttu-id="f69cc-118">FALSE</span><span class="sxs-lookup"><span data-stu-id="f69cc-118">FALSE</span></span>|<span data-ttu-id="f69cc-119">NULL</span><span class="sxs-lookup"><span data-stu-id="f69cc-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f69cc-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="f69cc-120">Example</span></span>  

 <span data-ttu-id="f69cc-121">La requête Entity SQL ci-dessous montre comment utiliser l'opérateur AND.</span><span class="sxs-lookup"><span data-stu-id="f69cc-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="f69cc-122">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="f69cc-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f69cc-123">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f69cc-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f69cc-124">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f69cc-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f69cc-125">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="f69cc-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="f69cc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f69cc-126">See also</span></span>

- [<span data-ttu-id="f69cc-127">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f69cc-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
