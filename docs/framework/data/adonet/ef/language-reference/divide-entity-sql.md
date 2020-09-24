---
title: '- Diviser (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d7d25d8c5b91850b21e36ba8f6f668af7a7d0045
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148159"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="c3a18-102">/ (Divide) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c3a18-102">/ (Divide) (Entity SQL)</span></span>

<span data-ttu-id="c3a18-103">Divise un nombre par un autre.</span><span class="sxs-lookup"><span data-stu-id="c3a18-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3a18-104">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="c3a18-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c3a18-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="c3a18-106">Expression numérique à diviser.</span><span class="sxs-lookup"><span data-stu-id="c3a18-106">The numeric expression to divide.</span></span> <span data-ttu-id="c3a18-107">`dividend` correspond à toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="c3a18-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="c3a18-108">Expression numérique par laquelle diviser le dividende.</span><span class="sxs-lookup"><span data-stu-id="c3a18-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="c3a18-109">`divisor` correspond à toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="c3a18-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c3a18-110">Types des résultats</span><span class="sxs-lookup"><span data-stu-id="c3a18-110">Result Types</span></span>  

 <span data-ttu-id="c3a18-111">Type de données qui résulte de la promotion de type implicite de deux arguments.</span><span class="sxs-lookup"><span data-stu-id="c3a18-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="c3a18-112">Pour plus d’informations sur la promotion de type implicite, consultez [système de type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c3a18-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3a18-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3a18-113">Example</span></span>  

 <span data-ttu-id="c3a18-114">La requête Entity SQL suivante utilise l’opérateur arithmétique/pour diviser un nombre par un autre.</span><span class="sxs-lookup"><span data-stu-id="c3a18-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="c3a18-115">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="c3a18-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c3a18-116">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3a18-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c3a18-117">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c3a18-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c3a18-118">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="c3a18-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="c3a18-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3a18-119">See also</span></span>

- [<span data-ttu-id="c3a18-120">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c3a18-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
