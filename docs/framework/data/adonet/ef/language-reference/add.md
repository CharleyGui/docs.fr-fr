---
title: + (Ajouter)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b86d273658362c3bb204d5220ff5e9db1f8de9fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198052"
---
# <a name="-add"></a><span data-ttu-id="41f48-102">+ (Ajouter)</span><span class="sxs-lookup"><span data-stu-id="41f48-102">+ (Add)</span></span>

<span data-ttu-id="41f48-103">Additionne deux nombres.</span><span class="sxs-lookup"><span data-stu-id="41f48-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41f48-104">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="41f48-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="41f48-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="41f48-106">Toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="41f48-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="41f48-107">Types des résultats</span><span class="sxs-lookup"><span data-stu-id="41f48-107">Result Types</span></span>  

 <span data-ttu-id="41f48-108">Type de données qui résulte de la promotion de type implicite de deux arguments.</span><span class="sxs-lookup"><span data-stu-id="41f48-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="41f48-109">Pour plus d’informations sur la promotion de type implicite, consultez [système de type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="41f48-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41f48-110">Notes</span><span class="sxs-lookup"><span data-stu-id="41f48-110">Remarks</span></span>  

 <span data-ttu-id="41f48-111">Pour les types EDM.String, l'addition est une concaténation.</span><span class="sxs-lookup"><span data-stu-id="41f48-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41f48-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="41f48-112">Example</span></span>  

 <span data-ttu-id="41f48-113">La requête Entity SQL ci-dessous utilise l'opérateur arithmétique + pour additionner deux nombres.</span><span class="sxs-lookup"><span data-stu-id="41f48-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="41f48-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="41f48-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="41f48-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="41f48-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="41f48-116">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="41f48-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="41f48-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="41f48-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="41f48-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41f48-118">See also</span></span>

- [<span data-ttu-id="41f48-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="41f48-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="41f48-120">Types de modèles conceptuels (CSDL)</span><span class="sxs-lookup"><span data-stu-id="41f48-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
