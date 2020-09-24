---
title: <= (inférieur ou égal à) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 09f2a7f53d00739b8542cb1149397f24d3b04f42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161800"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="44d3e-102">\<= (Inférieur ou égal à) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="44d3e-102">\<= (Less Than or Equal To) (Entity SQL)</span></span>

<span data-ttu-id="44d3e-103">Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="44d3e-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44d3e-104">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="44d3e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="44d3e-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="44d3e-106">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="44d3e-106">Any valid expression.</span></span> <span data-ttu-id="44d3e-107">Les deux expressions doivent avoir des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="44d3e-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="44d3e-108">Types des résultats</span><span class="sxs-lookup"><span data-stu-id="44d3e-108">Result Types</span></span>  

 <span data-ttu-id="44d3e-109">`true` si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="44d3e-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44d3e-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="44d3e-110">Example</span></span>  

 <span data-ttu-id="44d3e-111">La requête Entity SQL ci-dessous utilise l'opérateur de comparaison <= pour comparer deux expressions afin de déterminer si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="44d3e-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="44d3e-112">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="44d3e-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="44d3e-113">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="44d3e-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="44d3e-114">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="44d3e-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="44d3e-115">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="44d3e-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="44d3e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44d3e-116">See also</span></span>

- [<span data-ttu-id="44d3e-117">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="44d3e-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
