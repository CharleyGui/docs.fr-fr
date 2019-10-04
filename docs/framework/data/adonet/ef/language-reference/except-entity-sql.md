---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833864"
---
# <a name="except-entity-sql"></a><span data-ttu-id="73e3d-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73e3d-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="73e3d-103">Retourne une collection de valeurs distinctes à partir de l'expression de requête située du côté gauche de l'opérande EXCEPT, qui ne sont pas retournées à partir de l'expression de requête située à droite de l'opérande EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="73e3d-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="73e3d-104">Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="73e3d-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e3d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73e3d-105">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="73e3d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="73e3d-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="73e3d-107">Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête.</span><span class="sxs-lookup"><span data-stu-id="73e3d-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73e3d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="73e3d-108">Return Value</span></span>  
 <span data-ttu-id="73e3d-109">Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="73e3d-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73e3d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="73e3d-110">Remarks</span></span>  
 <span data-ttu-id="73e3d-111">EXCEPT est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="73e3d-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="73e3d-112">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="73e3d-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="73e3d-113">Le tableau ci-dessous présente la priorité des opérateurs Set [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="73e3d-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="73e3d-114">Priorité</span><span class="sxs-lookup"><span data-stu-id="73e3d-114">Precedence</span></span>|<span data-ttu-id="73e3d-115">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="73e3d-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="73e3d-116">Maximale</span><span class="sxs-lookup"><span data-stu-id="73e3d-116">Highest</span></span>|<span data-ttu-id="73e3d-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="73e3d-117">INTERSECT</span></span>|  
||<span data-ttu-id="73e3d-118">UNION</span><span class="sxs-lookup"><span data-stu-id="73e3d-118">UNION</span></span><br /><br /> <span data-ttu-id="73e3d-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="73e3d-119">UNION ALL</span></span>|  
||<span data-ttu-id="73e3d-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="73e3d-120">EXCEPT</span></span>|  
|<span data-ttu-id="73e3d-121">Minimale</span><span class="sxs-lookup"><span data-stu-id="73e3d-121">Lowest</span></span>|<span data-ttu-id="73e3d-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="73e3d-122">EXISTS</span></span><br /><br /> <span data-ttu-id="73e3d-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="73e3d-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="73e3d-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="73e3d-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="73e3d-125">SET</span><span class="sxs-lookup"><span data-stu-id="73e3d-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="73e3d-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="73e3d-126">Example</span></span>  
 <span data-ttu-id="73e3d-127">La requête Entity SQL ci-dessous utilise l'opérateur EXCEPT pour retourner une collection de valeurs distinctes provenant de deux expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="73e3d-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="73e3d-128">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="73e3d-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73e3d-129">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="73e3d-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="73e3d-130">Suivez la procédure indiquée dans [How pour : Exécutez une requête qui retourne les résultats StructuralType @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="73e3d-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="73e3d-131">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="73e3d-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="73e3d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73e3d-132">See also</span></span>

- [<span data-ttu-id="73e3d-133">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="73e3d-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
