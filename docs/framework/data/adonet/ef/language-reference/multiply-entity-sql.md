---
title: '* Multiplier (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 3dd77270e6765a0431dc473bbbcadeb6481a4699
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175653"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="9baae-102">\* (Multiplier) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9baae-102">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="9baae-103">Multiplie deux expressions.</span><span class="sxs-lookup"><span data-stu-id="9baae-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9baae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9baae-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9baae-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9baae-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9baae-106">Toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="9baae-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9baae-107">Types des résultats</span><span class="sxs-lookup"><span data-stu-id="9baae-107">Result Types</span></span>  

 <span data-ttu-id="9baae-108">Type de données qui résulte de la promotion de type implicite de deux arguments.</span><span class="sxs-lookup"><span data-stu-id="9baae-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9baae-109">Pour plus d’informations sur la promotion de type implicite, consultez [système de type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9baae-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9baae-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="9baae-110">Example</span></span>  

 <span data-ttu-id="9baae-111">La requête Entity SQL ci-dessous utilise l'opérateur arithmétique \* pour multiplier deux nombres.</span><span class="sxs-lookup"><span data-stu-id="9baae-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="9baae-112">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="9baae-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9baae-113">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9baae-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9baae-114">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9baae-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9baae-115">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="9baae-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="9baae-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9baae-116">See also</span></span>

- [<span data-ttu-id="9baae-117">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9baae-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
