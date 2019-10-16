---
title: < = (inférieur ou égal à) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: b3c8fef47b06b9fdd0a1619a9e56d3d916d9dd2d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319636"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="325e4-102">\<= (Inférieur ou égal à) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="325e4-102">\<= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="325e4-103">Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="325e4-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="325e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="325e4-104">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="325e4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="325e4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="325e4-106">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="325e4-106">Any valid expression.</span></span> <span data-ttu-id="325e4-107">Les deux expressions doivent posséder des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="325e4-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="325e4-108">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="325e4-108">Result Types</span></span>  
 <span data-ttu-id="325e4-109">`true` si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="325e4-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="325e4-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="325e4-110">Example</span></span>  
 <span data-ttu-id="325e4-111">La requête Entity SQL ci-dessous utilise l'opérateur de comparaison <= pour comparer deux expressions afin de déterminer si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="325e4-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="325e4-112">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="325e4-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="325e4-113">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="325e4-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="325e4-114">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="325e4-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="325e4-115">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="325e4-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="325e4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="325e4-116">See also</span></span>

- [<span data-ttu-id="325e4-117">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="325e4-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
