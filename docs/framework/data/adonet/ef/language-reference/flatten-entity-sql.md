---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833803"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="fa58a-102">FLATTEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fa58a-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="fa58a-103">Convertit une collection de collections en collection plane.</span><span class="sxs-lookup"><span data-stu-id="fa58a-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="fa58a-104">La nouvelle collection contient les mêmes éléments que l'ancienne, mais sans structure imbriquée.</span><span class="sxs-lookup"><span data-stu-id="fa58a-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa58a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa58a-105">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa58a-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="fa58a-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="fa58a-107">Expression valide qui retourne une collection de collections de valeurs à aplanir en une seule.</span><span class="sxs-lookup"><span data-stu-id="fa58a-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa58a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="fa58a-108">Remarks</span></span>  
 <span data-ttu-id="fa58a-109">`FLATTEN` est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fa58a-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="fa58a-110">Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="fa58a-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="fa58a-111">Pour plus d’informations sur les opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] définis, consultez [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fa58a-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa58a-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="fa58a-112">Example</span></span>  
 <span data-ttu-id="fa58a-113">La requête Entity SQL ci-dessous utilise l'opérateur `FLATTEN` pour convertir une collection de collections en collection plane.</span><span class="sxs-lookup"><span data-stu-id="fa58a-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="fa58a-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fa58a-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fa58a-115">Suivez la procédure indiquée dans [How pour : Exécutez une requête qui retourne les résultats StructuralType @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="fa58a-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="fa58a-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="fa58a-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="fa58a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa58a-117">See also</span></span>

- [<span data-ttu-id="fa58a-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fa58a-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
