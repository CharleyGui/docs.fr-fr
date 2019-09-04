---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: a943de89de37d00cc2a643b443da7ef1fd3380b9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250597"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="1197d-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1197d-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="1197d-103">Retourne une collection de valeurs distinctes qui sont retournées par les expressions de requête tant à gauche qu'à droite de l'opérande INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="1197d-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="1197d-104">Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="1197d-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1197d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1197d-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1197d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="1197d-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1197d-107">Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête.</span><span class="sxs-lookup"><span data-stu-id="1197d-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1197d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1197d-108">Return Value</span></span>  
 <span data-ttu-id="1197d-109">Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="1197d-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1197d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="1197d-110">Remarks</span></span>  
 <span data-ttu-id="1197d-111">INTERSECT est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1197d-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1197d-112">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="1197d-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1197d-113">Pour obtenir des informations de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] précédence pour les opérateurs de jeu, consultez [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1197d-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1197d-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="1197d-114">Example</span></span>  
 <span data-ttu-id="1197d-115">La requête Entity SQL ci-dessous utilise l'opérateur INTERSECT pour retourner une collection de valeurs distinctes qui sont retournées par les expressions de requête tant à gauche qu'à droite de l'opérande INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="1197d-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="1197d-116">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="1197d-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1197d-117">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1197d-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1197d-118">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="1197d-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1197d-119">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="1197d-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="1197d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1197d-120">See also</span></span>

- [<span data-ttu-id="1197d-121">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1197d-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
