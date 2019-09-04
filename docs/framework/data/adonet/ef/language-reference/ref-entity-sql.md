---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 9d35306d1299e91ecaa55a7d2818ee1e2982793f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249199"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="fabec-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fabec-102">REF (Entity SQL)</span></span>
<span data-ttu-id="fabec-103">Retourne une référence à une instance d'entité.</span><span class="sxs-lookup"><span data-stu-id="fabec-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fabec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fabec-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="fabec-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fabec-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fabec-106">Toute expression valide qui produit une instance d'un type d'entité.</span><span class="sxs-lookup"><span data-stu-id="fabec-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fabec-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fabec-107">Return Value</span></span>  
 <span data-ttu-id="fabec-108">Référence à l'instance d'entité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fabec-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fabec-109">Notes</span><span class="sxs-lookup"><span data-stu-id="fabec-109">Remarks</span></span>  
 <span data-ttu-id="fabec-110">Une référence d'entité se compose de la clé d'entité et d'un nom de jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="fabec-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="fabec-111">Des jeux d'entités différents pouvant être basés sur le même type d'entité, une clé d'entité particulière peut apparaître dans plusieurs jeux d'entités.</span><span class="sxs-lookup"><span data-stu-id="fabec-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="fabec-112">Toutefois, une référence d'entité est toujours unique.</span><span class="sxs-lookup"><span data-stu-id="fabec-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="fabec-113">Si l'expression d'entrée représente une entité rendue persistante, une référence à cette entité est retournée.</span><span class="sxs-lookup"><span data-stu-id="fabec-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="fabec-114">Si l'expression d'entrée n'est pas une entité rendue persistante, une référence Null à cette entité est retournée.</span><span class="sxs-lookup"><span data-stu-id="fabec-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="fabec-115">Si l'opérateur d'extraction de propriété (.) est utilisé pour accéder à une propriété d'une entité, la référence est automatiquement supprimée.</span><span class="sxs-lookup"><span data-stu-id="fabec-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fabec-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="fabec-116">Example</span></span>  
 <span data-ttu-id="fabec-117">La requête Entity SQL suivante utilise l'opérateur REF pour retourner la référence d'un argument d'entité d'entrée.</span><span class="sxs-lookup"><span data-stu-id="fabec-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="fabec-118">La même requête supprime la référence car nous utilisons une opération d'extraction de propriété (.) pour accéder à une propriété de l'entité Product.</span><span class="sxs-lookup"><span data-stu-id="fabec-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="fabec-119">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="fabec-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fabec-120">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fabec-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fabec-121">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md)de PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="fabec-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="fabec-122">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="fabec-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="fabec-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fabec-123">See also</span></span>

- [<span data-ttu-id="fabec-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="fabec-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="fabec-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="fabec-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="fabec-126">KEY</span><span class="sxs-lookup"><span data-stu-id="fabec-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="fabec-127">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fabec-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fabec-128">Définitions de type</span><span class="sxs-lookup"><span data-stu-id="fabec-128">Type Definitions</span></span>](type-definitions-entity-sql.md)
