---
title: UNION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 34eac0dfd28d39ec68f084ea10dd46693f44eea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248798"
---
# <a name="union-entity-sql"></a><span data-ttu-id="c628e-102">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c628e-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="c628e-103">Combine les résultats de deux requêtes, ou plus, en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="c628e-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c628e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c628e-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c628e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c628e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c628e-106">Toute expression de requête valide qui retourne une collection à combiner à la collection. Toutes les expressions doivent être du même type que la valeur `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c628e-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="c628e-107">UNION</span><span class="sxs-lookup"><span data-stu-id="c628e-107">UNION</span></span>  
 <span data-ttu-id="c628e-108">Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique.</span><span class="sxs-lookup"><span data-stu-id="c628e-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="c628e-109">ALL</span><span class="sxs-lookup"><span data-stu-id="c628e-109">ALL</span></span>  
 <span data-ttu-id="c628e-110">Spécifie que plusieurs collections doivent être combinées et retournées sous la forme d'une collection unique, y compris les doublons.</span><span class="sxs-lookup"><span data-stu-id="c628e-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="c628e-111">Si cet argument n'est pas spécifié, les doublons sont supprimés de la collection des résultats.</span><span class="sxs-lookup"><span data-stu-id="c628e-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c628e-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c628e-112">Return Value</span></span>  
 <span data-ttu-id="c628e-113">Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c628e-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c628e-114">Notes</span><span class="sxs-lookup"><span data-stu-id="c628e-114">Remarks</span></span>  
 <span data-ttu-id="c628e-115">UNION est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c628e-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="c628e-116">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="c628e-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="c628e-117">Pour obtenir des informations de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] précédence pour les opérateurs de jeu, consultez [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c628e-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c628e-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="c628e-118">Example</span></span>  
 <span data-ttu-id="c628e-119">La requête Entity SQL ci-dessous utilise l'opérateur UNION ALL pour combiner les résultats de deux requêtes en une collection unique.</span><span class="sxs-lookup"><span data-stu-id="c628e-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="c628e-120">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="c628e-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c628e-121">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c628e-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c628e-122">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="c628e-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c628e-123">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="c628e-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="c628e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c628e-124">See also</span></span>

- [<span data-ttu-id="c628e-125">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c628e-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
