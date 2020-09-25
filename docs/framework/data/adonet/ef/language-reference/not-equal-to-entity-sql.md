---
title: '!= (différent de) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: bebe85072f5a2cf6a133b88c6d3f5c97299aa63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191773"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="a5ec7-102">!= (différent de) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a5ec7-102">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="a5ec7-103">Compare deux expressions pour déterminer si l'expression de gauche est différente de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="a5ec7-104">L'opérateur != (différent de) est d'un point de vue fonctionnel équivalent à l'opérateur <>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ec7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5ec7-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5ec7-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5ec7-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="a5ec7-107">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-107">Any valid expression.</span></span> <span data-ttu-id="a5ec7-108">Les deux expressions doivent avoir des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a5ec7-109">Types des résultats</span><span class="sxs-lookup"><span data-stu-id="a5ec7-109">Result Types</span></span>  

 <span data-ttu-id="a5ec7-110">`true` si l'expression de gauche est différente de l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ec7-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5ec7-111">Example</span></span>  

 <span data-ttu-id="a5ec7-112">La requête Entity SQL ci-dessous utilise l'opérateur != pour comparer deux expressions afin de déterminer si l'expression de gauche est différente de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="a5ec7-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a5ec7-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5ec7-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a5ec7-115">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a5ec7-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a5ec7-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="a5ec7-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="a5ec7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5ec7-117">See also</span></span>

- [<span data-ttu-id="a5ec7-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a5ec7-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
