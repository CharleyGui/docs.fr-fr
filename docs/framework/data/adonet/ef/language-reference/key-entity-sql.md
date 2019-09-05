---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 44ab5352c3b2a94cb210c3de775d2347d2df7fe7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250481"
---
# <a name="key-entity-sql"></a><span data-ttu-id="658a7-102">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="658a7-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="658a7-103">Extrait la clé d'une référence ou d'une expression d'entité.</span><span class="sxs-lookup"><span data-stu-id="658a7-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="658a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="658a7-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="658a7-105">Notes</span><span class="sxs-lookup"><span data-stu-id="658a7-105">Remarks</span></span>  
 <span data-ttu-id="658a7-106">Une clé d'entité contient les valeurs de clés dans l'ordre correct de l'entité ou de la référence d'entité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="658a7-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="658a7-107">Plusieurs jeux d'entités pouvant être basés sur le même type d'entité, la même clé peut apparaître dans chaque jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="658a7-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="658a7-108">Pour obtenir une référence unique, utilisez `REF`.</span><span class="sxs-lookup"><span data-stu-id="658a7-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="658a7-109">Le type de retour de l'opérateur KEY est un type de ligne qui inclut un champ pour chaque clé de l'entité, dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="658a7-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="658a7-110">Dans l'exemple suivant, une référence à l'entité BadOrder est passée à l'opérateur Key, lequel retourne la partie clé de cette référence.</span><span class="sxs-lookup"><span data-stu-id="658a7-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="658a7-111">Dans le cas présent, un type d'enregistrement ayant exactement un champ correspondant à la propriété `Id` .</span><span class="sxs-lookup"><span data-stu-id="658a7-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="658a7-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="658a7-112">Example</span></span>  
 <span data-ttu-id="658a7-113">La requête Entity SQL suivante utilise l'opérateur KEY pour extraire la partie clé d'une expression avec référence de type.</span><span class="sxs-lookup"><span data-stu-id="658a7-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="658a7-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="658a7-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="658a7-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="658a7-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="658a7-116">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="658a7-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="658a7-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="658a7-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="658a7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="658a7-118">See also</span></span>

- [<span data-ttu-id="658a7-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="658a7-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="658a7-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="658a7-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="658a7-121">REF</span><span class="sxs-lookup"><span data-stu-id="658a7-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="658a7-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="658a7-122">DEREF</span></span>](deref-entity-sql.md)
