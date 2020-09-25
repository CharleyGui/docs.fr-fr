---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: e060956545ca924fa6fedb80b2f53ff312f307a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201198"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="2025a-102">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2025a-102">ANYELEMENT (Entity SQL)</span></span>

<span data-ttu-id="2025a-103">Extrait un élément d'une collection à valeurs multiples.</span><span class="sxs-lookup"><span data-stu-id="2025a-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2025a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2025a-104">Syntax</span></span>  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2025a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2025a-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="2025a-106">Toute expression de requête valide qui retourne une collection dont extraire un élément.</span><span class="sxs-lookup"><span data-stu-id="2025a-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2025a-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2025a-107">Return Value</span></span>  

 <span data-ttu-id="2025a-108">Élément unique de la collection ou élément arbitraire si la collection en comporte plusieurs ; si la collection est vide, retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="2025a-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="2025a-109">Si `collection` est une collection de type `Collection<T>` , `ANYELEMENT(collection)` est une expression valide qui produit une instance de type `T` .</span><span class="sxs-lookup"><span data-stu-id="2025a-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2025a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="2025a-110">Remarks</span></span>  

 <span data-ttu-id="2025a-111">ANYELEMENT extrait un élément arbitraire d'une collection à valeurs multiples.</span><span class="sxs-lookup"><span data-stu-id="2025a-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="2025a-112">L'exemple ci-dessous tente d'extraire un élément singleton du jeu `Customers`.</span><span class="sxs-lookup"><span data-stu-id="2025a-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="2025a-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="2025a-113">Example</span></span>  

 <span data-ttu-id="2025a-114">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur ANYELEMENT pour extraire un élément d'une collection à valeurs multiples.</span><span class="sxs-lookup"><span data-stu-id="2025a-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="2025a-115">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="2025a-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2025a-116">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2025a-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2025a-117">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2025a-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2025a-118">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="2025a-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="2025a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2025a-119">See also</span></span>

- [<span data-ttu-id="2025a-120">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2025a-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2025a-121">Types structurés Nullable</span><span class="sxs-lookup"><span data-stu-id="2025a-121">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
