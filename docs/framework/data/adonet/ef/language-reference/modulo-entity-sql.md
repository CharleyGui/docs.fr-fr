---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 25bd34db3a627fa708e1ab9a3f0e237426487bcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175705"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="3df33-102">(Modulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3df33-102">(Modulo) (Entity SQL)</span></span>

<span data-ttu-id="3df33-103">Retourne le reste d'une expression divisée par une autre.</span><span class="sxs-lookup"><span data-stu-id="3df33-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3df33-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="3df33-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3df33-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="3df33-106">Expression numérique à diviser.</span><span class="sxs-lookup"><span data-stu-id="3df33-106">The numeric expression to divide.</span></span> <span data-ttu-id="3df33-107">`dividend` correspond à toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="3df33-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="3df33-108">Expression numérique par laquelle diviser le dividende.</span><span class="sxs-lookup"><span data-stu-id="3df33-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="3df33-109">`divisor` correspond à toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="3df33-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3df33-110">Types des résultats</span><span class="sxs-lookup"><span data-stu-id="3df33-110">Result Types</span></span>  

 <span data-ttu-id="3df33-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="3df33-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="3df33-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3df33-112">Example</span></span>  

 <span data-ttu-id="3df33-113">La requête Entity SQL ci-dessous utilise l'opérateur arithmétique % pour retourner le reste d'une expression divisée par une autre.</span><span class="sxs-lookup"><span data-stu-id="3df33-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="3df33-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="3df33-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3df33-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3df33-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3df33-116">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3df33-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3df33-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="3df33-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="3df33-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3df33-118">See also</span></span>

- [<span data-ttu-id="3df33-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3df33-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
