---
title: UNION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 9c4106d26fb73219d7b5f0c6763736aaf9163d4b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200977"
---
# <a name="union-entity-sql"></a><span data-ttu-id="7f1aa-102">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7f1aa-102">UNION (Entity SQL)</span></span>

<span data-ttu-id="7f1aa-103">Combine les résultats de deux requêtes, ou plus, en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f1aa-104">Syntax</span></span>  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f1aa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7f1aa-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="7f1aa-106">Toute expression de requête valide qui retourne une collection à combiner à la collection. Toutes les expressions doivent être du même type que la valeur `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="7f1aa-107">UNION</span><span class="sxs-lookup"><span data-stu-id="7f1aa-107">UNION</span></span>  
 <span data-ttu-id="7f1aa-108">Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="7f1aa-109">ALL</span><span class="sxs-lookup"><span data-stu-id="7f1aa-109">ALL</span></span>  
 <span data-ttu-id="7f1aa-110">Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique, y compris les doublons.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="7f1aa-111">Si cet argument n'est pas spécifié, les doublons sont supprimés de la collection des résultats.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f1aa-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="7f1aa-112">Return Value</span></span>  

 <span data-ttu-id="7f1aa-113">Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f1aa-114">Notes</span><span class="sxs-lookup"><span data-stu-id="7f1aa-114">Remarks</span></span>  

 <span data-ttu-id="7f1aa-115">UNION est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7f1aa-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="7f1aa-116">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="7f1aa-117">Pour obtenir des informations de précédence pour les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs de jeu, consultez [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7f1aa-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f1aa-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="7f1aa-118">Example</span></span>  

 <span data-ttu-id="7f1aa-119">La requête Entity SQL ci-dessous utilise l'opérateur UNION ALL pour combiner les résultats de deux requêtes en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="7f1aa-120">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="7f1aa-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7f1aa-121">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7f1aa-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7f1aa-122">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7f1aa-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7f1aa-123">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="7f1aa-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a><span data-ttu-id="7f1aa-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f1aa-124">See also</span></span>

- [<span data-ttu-id="7f1aa-125">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7f1aa-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
