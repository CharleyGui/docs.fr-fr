---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: bdee9281fd406a3d029d3a10536cbdd48d2f7a58
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319412"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="560fc-102">OVERLAPS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="560fc-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="560fc-103">Détermine si deux collections ont des éléments en commun.</span><span class="sxs-lookup"><span data-stu-id="560fc-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="560fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="560fc-104">Syntax</span></span>  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="560fc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="560fc-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="560fc-106">Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête.</span><span class="sxs-lookup"><span data-stu-id="560fc-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="560fc-107">Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="560fc-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="560fc-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="560fc-108">Return Value</span></span>  
 <span data-ttu-id="560fc-109">`true` si les deux collections ont des éléments en commun ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="560fc-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="560fc-110">Notes</span><span class="sxs-lookup"><span data-stu-id="560fc-110">Remarks</span></span>  
 <span data-ttu-id="560fc-111">Les chevauchements offrent des fonctionnalités équivalentes à celles-ci :</span><span class="sxs-lookup"><span data-stu-id="560fc-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="560fc-112">OVERLAPS est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="560fc-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="560fc-113">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="560fc-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="560fc-114">Pour obtenir des informations de précédence pour les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultez [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="560fc-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="560fc-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="560fc-115">Example</span></span>  
 <span data-ttu-id="560fc-116">La requête Entity SQL ci-dessous utilise l'opérateur OVERLAPS pour déterminer si deux collections ont une valeur commune.</span><span class="sxs-lookup"><span data-stu-id="560fc-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="560fc-117">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="560fc-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="560fc-118">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="560fc-118">To compile and run this, follow these steps:</span></span>  
  
1. <span data-ttu-id="560fc-119">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="560fc-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="560fc-120">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="560fc-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="560fc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="560fc-121">See also</span></span>

- [<span data-ttu-id="560fc-122">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="560fc-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
