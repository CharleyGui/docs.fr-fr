---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 2ac7db5b22ad21eb152788b6c6d6a8e65c1f6a7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169633"
---
# <a name="set-entity-sql"></a><span data-ttu-id="382c0-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="382c0-102">SET (Entity SQL)</span></span>

<span data-ttu-id="382c0-103">L'expression SET est utilisée pour convertir une collection d'objets en ensemble grâce à la production d'une nouvelle collection dans laquelle toutes les éléments en double ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="382c0-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="382c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="382c0-104">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="382c0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="382c0-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="382c0-106">Toute expression de requête valide qui retourne une collection.</span><span class="sxs-lookup"><span data-stu-id="382c0-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="382c0-107">Notes</span><span class="sxs-lookup"><span data-stu-id="382c0-107">Remarks</span></span>  

 <span data-ttu-id="382c0-108">L'expression d'ensemble `SET(c)` est logiquement équivalente à l'instruction select suivante :</span><span class="sxs-lookup"><span data-stu-id="382c0-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="382c0-109">`SET` est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="382c0-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="382c0-110">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="382c0-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="382c0-111">Pour plus d’informations sur les opérateurs de jeu [, consultez except](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="382c0-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="382c0-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="382c0-112">Example</span></span>  

 <span data-ttu-id="382c0-113">La requête Entity SQL ci-dessous utilise l'expression SET pour convertir une collection d'objets en ensemble.</span><span class="sxs-lookup"><span data-stu-id="382c0-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="382c0-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="382c0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="382c0-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="382c0-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="382c0-116">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="382c0-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="382c0-117">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="382c0-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="382c0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="382c0-118">See also</span></span>

- [<span data-ttu-id="382c0-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="382c0-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
