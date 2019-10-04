---
title: = (égal à) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 5cdfd35450514a9699a39cf78f64c0fa6b7d5f39
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833848"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="ce7c9-102">= (égal à) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce7c9-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="ce7c9-103">Compare l'égalité de deux expressions.</span><span class="sxs-lookup"><span data-stu-id="ce7c9-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce7c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce7c9-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce7c9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ce7c9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ce7c9-106">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="ce7c9-106">Any valid expression.</span></span> <span data-ttu-id="ce7c9-107">Les deux expressions doivent posséder des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="ce7c9-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ce7c9-108">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="ce7c9-108">Result Types</span></span>  
 <span data-ttu-id="ce7c9-109">`true` si l'expression de gauche est égale à l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ce7c9-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce7c9-110">Notes</span><span class="sxs-lookup"><span data-stu-id="ce7c9-110">Remarks</span></span>  
 <span data-ttu-id="ce7c9-111">L'opérateur « = = » est équivalent à « = ».</span><span class="sxs-lookup"><span data-stu-id="ce7c9-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce7c9-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce7c9-112">Example</span></span>  
 <span data-ttu-id="ce7c9-113">La requête Entity SQL ci-dessous utilise l'opérateur de comparaison « = » pour comparer l'égalité de deux expressions.</span><span class="sxs-lookup"><span data-stu-id="ce7c9-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="ce7c9-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="ce7c9-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ce7c9-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ce7c9-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ce7c9-116">Suivez la procédure indiquée dans [How pour : Exécutez une requête qui retourne les résultats StructuralType @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="ce7c9-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ce7c9-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="ce7c9-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="ce7c9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce7c9-118">See also</span></span>

- [<span data-ttu-id="ce7c9-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ce7c9-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
