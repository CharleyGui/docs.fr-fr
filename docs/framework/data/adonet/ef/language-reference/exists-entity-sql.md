---
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: f08b3ea60a985e56e05e4686cd531f94e0bd4e18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166766"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="bd43b-102">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bd43b-102">EXISTS (Entity SQL)</span></span>

<span data-ttu-id="bd43b-103">Détermine si une collection est vide.</span><span class="sxs-lookup"><span data-stu-id="bd43b-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd43b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd43b-104">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd43b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd43b-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="bd43b-106">Toute expression valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="bd43b-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="bd43b-107">NOT</span><span class="sxs-lookup"><span data-stu-id="bd43b-107">NOT</span></span>  
 <span data-ttu-id="bd43b-108">Indique que la valeur du résultat de l'opérateur EXISTS est inversée.</span><span class="sxs-lookup"><span data-stu-id="bd43b-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd43b-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="bd43b-109">Return Value</span></span>  

 <span data-ttu-id="bd43b-110">`true` si la collection n'est pas vide ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="bd43b-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd43b-111">Notes</span><span class="sxs-lookup"><span data-stu-id="bd43b-111">Remarks</span></span>  

 <span data-ttu-id="bd43b-112">EXISTS est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd43b-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="bd43b-113">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="bd43b-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="bd43b-114">Pour obtenir des informations de précédence pour les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs de jeu, consultez [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bd43b-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd43b-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd43b-115">Example</span></span>  

 <span data-ttu-id="bd43b-116">La requête Entity SQL ci-dessous utilise l'opérateur EXISTS pour déterminer si la collection est vide.</span><span class="sxs-lookup"><span data-stu-id="bd43b-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="bd43b-117">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="bd43b-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bd43b-118">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="bd43b-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bd43b-119">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bd43b-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bd43b-120">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="bd43b-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="bd43b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd43b-121">See also</span></span>

- [<span data-ttu-id="bd43b-122">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bd43b-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
