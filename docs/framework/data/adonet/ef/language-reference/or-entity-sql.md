---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 89c0a92030f2f067d5e5d45b58d475414a224ce4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150802"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="ccf09-102">|| (OR) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ccf09-102">|| (OR) (Entity SQL)</span></span>

<span data-ttu-id="ccf09-103">Combine deux expressions `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="ccf09-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccf09-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ccf09-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ccf09-105">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="ccf09-106">Toute expression valide qui retourne une valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ccf09-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccf09-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ccf09-107">Return Value</span></span>  

 <span data-ttu-id="ccf09-108">`true` si l'une des conditions a la valeur `true`; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ccf09-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccf09-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ccf09-109">Remarks</span></span>  

 <span data-ttu-id="ccf09-110">OR est un opérateur logique [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ccf09-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="ccf09-111">Il est utilisé pour combiner deux conditions.</span><span class="sxs-lookup"><span data-stu-id="ccf09-111">It is used to combine two conditions.</span></span> <span data-ttu-id="ccf09-112">Lorsque plusieurs opérateurs logiques sont utilisés dans une instruction, les opérateurs OR sont évalués après les opérateurs AND.</span><span class="sxs-lookup"><span data-stu-id="ccf09-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="ccf09-113">L'utilisation des parenthèses permet toutefois de modifier l'ordre de traitement.</span><span class="sxs-lookup"><span data-stu-id="ccf09-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="ccf09-114">Les barres verticales doubles (&#124;&#124;) ont les mêmes fonctionnalités que l’opérateur OR.</span><span class="sxs-lookup"><span data-stu-id="ccf09-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="ccf09-115">Le tableau ci-dessous indique les valeurs d'entrée et les types de retour possibles.</span><span class="sxs-lookup"><span data-stu-id="ccf09-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="ccf09-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="ccf09-116">TRUE</span></span>|<span data-ttu-id="ccf09-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="ccf09-117">TRUE</span></span>|<span data-ttu-id="ccf09-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="ccf09-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="ccf09-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="ccf09-119">TRUE</span></span>|<span data-ttu-id="ccf09-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="ccf09-120">FALSE</span></span>|<span data-ttu-id="ccf09-121">NULL</span><span class="sxs-lookup"><span data-stu-id="ccf09-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="ccf09-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="ccf09-122">TRUE</span></span>|<span data-ttu-id="ccf09-123">NULL</span><span class="sxs-lookup"><span data-stu-id="ccf09-123">NULL</span></span>|<span data-ttu-id="ccf09-124">NULL</span><span class="sxs-lookup"><span data-stu-id="ccf09-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ccf09-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="ccf09-125">Example</span></span>  

 <span data-ttu-id="ccf09-126">La requête Entity SQL ci-dessous utilise l'opérateur OR pour combiner deux expressions `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="ccf09-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="ccf09-127">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="ccf09-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ccf09-128">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ccf09-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ccf09-129">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ccf09-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ccf09-130">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="ccf09-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="ccf09-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccf09-131">See also</span></span>

- [<span data-ttu-id="ccf09-132">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ccf09-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
