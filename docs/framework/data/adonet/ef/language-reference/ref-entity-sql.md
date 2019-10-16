---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 08bcaad4fdc0cf5324ff9976fcf48c23b206e72f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319390"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="9d600-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9d600-102">REF (Entity SQL)</span></span>
<span data-ttu-id="9d600-103">Retourne une référence à une instance d'entité.</span><span class="sxs-lookup"><span data-stu-id="9d600-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d600-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d600-104">Syntax</span></span>  
  
```sql  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="9d600-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9d600-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9d600-106">Toute expression valide qui produit une instance d'un type d'entité.</span><span class="sxs-lookup"><span data-stu-id="9d600-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d600-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9d600-107">Return Value</span></span>  
 <span data-ttu-id="9d600-108">Référence à l'instance d'entité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9d600-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d600-109">Notes</span><span class="sxs-lookup"><span data-stu-id="9d600-109">Remarks</span></span>  
 <span data-ttu-id="9d600-110">Une référence d'entité se compose de la clé d'entité et d'un nom de jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="9d600-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="9d600-111">Des jeux d'entités différents pouvant être basés sur le même type d'entité, une clé d'entité particulière peut apparaître dans plusieurs jeux d'entités.</span><span class="sxs-lookup"><span data-stu-id="9d600-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="9d600-112">Toutefois, une référence d'entité est toujours unique.</span><span class="sxs-lookup"><span data-stu-id="9d600-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="9d600-113">Si l'expression d'entrée représente une entité rendue persistante, une référence à cette entité est retournée.</span><span class="sxs-lookup"><span data-stu-id="9d600-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="9d600-114">Si l'expression d'entrée n'est pas une entité rendue persistante, une référence Null à cette entité est retournée.</span><span class="sxs-lookup"><span data-stu-id="9d600-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="9d600-115">Si l'opérateur d'extraction de propriété (.) est utilisé pour accéder à une propriété d'une entité, la référence est automatiquement supprimée.</span><span class="sxs-lookup"><span data-stu-id="9d600-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d600-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d600-116">Example</span></span>  
 <span data-ttu-id="9d600-117">La requête Entity SQL suivante utilise l'opérateur REF pour retourner la référence d'un argument d'entité d'entrée.</span><span class="sxs-lookup"><span data-stu-id="9d600-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="9d600-118">La même requête supprime la référence car nous utilisons une opération d'extraction de propriété (.) pour accéder à une propriété de l'entité Product.</span><span class="sxs-lookup"><span data-stu-id="9d600-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="9d600-119">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="9d600-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9d600-120">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d600-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9d600-121">Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9d600-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="9d600-122">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="9d600-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="9d600-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d600-123">See also</span></span>

- [<span data-ttu-id="9d600-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="9d600-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="9d600-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="9d600-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="9d600-126">KEY</span><span class="sxs-lookup"><span data-stu-id="9d600-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="9d600-127">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9d600-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="9d600-128">Définitions de type</span><span class="sxs-lookup"><span data-stu-id="9d600-128">Type Definitions</span></span>](type-definitions-entity-sql.md)
