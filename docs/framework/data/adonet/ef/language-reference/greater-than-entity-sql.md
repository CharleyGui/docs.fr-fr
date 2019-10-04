---
title: '> (Supérieur à) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: f2d3a0ed81cf75b7e567dbd07e119629ea47ac69
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833770"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="3f63d-102">> (Supérieur à) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3f63d-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="3f63d-103">Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="3f63d-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f63d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f63d-104">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f63d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3f63d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3f63d-106">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="3f63d-106">Any valid expression.</span></span> <span data-ttu-id="3f63d-107">Les deux expressions doivent posséder des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="3f63d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3f63d-108">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="3f63d-108">Result Types</span></span>  
 <span data-ttu-id="3f63d-109">`true` si la valeur de l'expression de gauche est supérieure à celle de l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="3f63d-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f63d-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f63d-110">Example</span></span>  
 <span data-ttu-id="3f63d-111">La requête Entity SQL ci-dessous utilise l'opérateur de comparaison > pour comparer deux expressions afin de déterminer si la valeur de l'expression de gauche est supérieure à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="3f63d-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="3f63d-112">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="3f63d-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3f63d-113">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3f63d-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3f63d-114">Suivez la procédure indiquée dans [How pour : Exécutez une requête qui retourne les résultats StructuralType @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="3f63d-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3f63d-115">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="3f63d-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="3f63d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f63d-116">See also</span></span>

- [<span data-ttu-id="3f63d-117">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3f63d-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
