---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 36ae2b2b1264150bc66d09366ee33723ed7b28a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166701"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="ee400-102">FLATTEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ee400-102">FLATTEN (Entity SQL)</span></span>

<span data-ttu-id="ee400-103">Convertit une collection de collections en collection plane.</span><span class="sxs-lookup"><span data-stu-id="ee400-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="ee400-104">La nouvelle collection contient les mêmes éléments que l'ancienne, mais sans structure imbriquée.</span><span class="sxs-lookup"><span data-stu-id="ee400-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee400-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee400-105">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee400-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ee400-106">Arguments</span></span>  

 `collection`  
 <span data-ttu-id="ee400-107">Expression valide qui retourne une collection de collections de valeurs à aplanir en une seule.</span><span class="sxs-lookup"><span data-stu-id="ee400-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee400-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ee400-108">Remarks</span></span>  

 <span data-ttu-id="ee400-109">`FLATTEN` est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ee400-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ee400-110">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="ee400-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ee400-111">Pour plus d’informations sur les opérateurs de jeu [, consultez except](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ee400-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee400-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee400-112">Example</span></span>  

 <span data-ttu-id="ee400-113">La requête Entity SQL ci-dessous utilise l'opérateur `FLATTEN` pour convertir une collection de collections en collection plane.</span><span class="sxs-lookup"><span data-stu-id="ee400-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="ee400-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ee400-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ee400-115">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ee400-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ee400-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="ee400-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="ee400-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee400-117">See also</span></span>

- [<span data-ttu-id="ee400-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ee400-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
