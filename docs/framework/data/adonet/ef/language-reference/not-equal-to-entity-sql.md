---
title: '!= (différent de) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: c2ccadaa5801cac9c10241108f02ade223a8697f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249852"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="67df5-102">!= (différent de) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="67df5-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="67df5-103">Compare deux expressions pour déterminer si l'expression de gauche est différente de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="67df5-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="67df5-104">L'opérateur != (différent de) est d'un point de vue fonctionnel équivalent à l'opérateur <>.</span><span class="sxs-lookup"><span data-stu-id="67df5-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67df5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67df5-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="67df5-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="67df5-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="67df5-107">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="67df5-107">Any valid expression.</span></span> <span data-ttu-id="67df5-108">Les deux expressions doivent posséder des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="67df5-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="67df5-109">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="67df5-109">Result Types</span></span>  
 <span data-ttu-id="67df5-110">`true` si l'expression de gauche est différente de l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="67df5-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67df5-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="67df5-111">Example</span></span>  
 <span data-ttu-id="67df5-112">La requête Entity SQL ci-dessous utilise l'opérateur != pour comparer deux expressions afin de déterminer si l'expression de gauche est différente de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="67df5-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="67df5-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="67df5-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="67df5-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="67df5-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="67df5-115">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="67df5-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="67df5-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="67df5-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="67df5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67df5-117">See also</span></span>

- [<span data-ttu-id="67df5-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="67df5-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
