---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 6797f8038a83533b5a6bd41ad402daec7abdc7de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148050"
---
# <a name="except-entity-sql"></a><span data-ttu-id="44a17-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="44a17-102">EXCEPT (Entity SQL)</span></span>

<span data-ttu-id="44a17-103">Retourne une collection de valeurs distinctes à partir de l'expression de requête située du côté gauche de l'opérande EXCEPT, qui ne sont pas retournées à partir de l'expression de requête située à droite de l'opérande EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="44a17-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="44a17-104">Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="44a17-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a17-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44a17-105">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="44a17-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="44a17-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="44a17-107">Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête.</span><span class="sxs-lookup"><span data-stu-id="44a17-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44a17-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="44a17-108">Return Value</span></span>  

 <span data-ttu-id="44a17-109">Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="44a17-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44a17-110">Notes</span><span class="sxs-lookup"><span data-stu-id="44a17-110">Remarks</span></span>  

 <span data-ttu-id="44a17-111">EXCEPT est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="44a17-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="44a17-112">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="44a17-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="44a17-113">Le tableau ci-dessous présente la priorité des opérateurs Set [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="44a17-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="44a17-114">Priorité</span><span class="sxs-lookup"><span data-stu-id="44a17-114">Precedence</span></span>|<span data-ttu-id="44a17-115">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="44a17-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="44a17-116">Le plus élevé</span><span class="sxs-lookup"><span data-stu-id="44a17-116">Highest</span></span>|<span data-ttu-id="44a17-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="44a17-117">INTERSECT</span></span>|  
||<span data-ttu-id="44a17-118">UNION</span><span class="sxs-lookup"><span data-stu-id="44a17-118">UNION</span></span><br /><br /> <span data-ttu-id="44a17-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="44a17-119">UNION ALL</span></span>|  
||<span data-ttu-id="44a17-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="44a17-120">EXCEPT</span></span>|  
|<span data-ttu-id="44a17-121">Minimale</span><span class="sxs-lookup"><span data-stu-id="44a17-121">Lowest</span></span>|<span data-ttu-id="44a17-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="44a17-122">EXISTS</span></span><br /><br /> <span data-ttu-id="44a17-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="44a17-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="44a17-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="44a17-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="44a17-125">SET</span><span class="sxs-lookup"><span data-stu-id="44a17-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44a17-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="44a17-126">Example</span></span>  

 <span data-ttu-id="44a17-127">La requête Entity SQL ci-dessous utilise l'opérateur EXCEPT pour retourner une collection de valeurs distinctes provenant de deux expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="44a17-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="44a17-128">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="44a17-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="44a17-129">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="44a17-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="44a17-130">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="44a17-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="44a17-131">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="44a17-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="44a17-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44a17-132">See also</span></span>

- [<span data-ttu-id="44a17-133">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="44a17-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
