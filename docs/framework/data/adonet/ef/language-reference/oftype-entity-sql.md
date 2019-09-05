---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 36701a5e75e804ea541d242aaff243de0b24cec3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249793"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="20b33-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="20b33-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="20b33-103">Retourne une collection d'objets à partir d'une expression de requête d'un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="20b33-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20b33-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="20b33-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="20b33-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="20b33-106">Toute expression de requête valide qui retourne une collection d'objets.</span><span class="sxs-lookup"><span data-stu-id="20b33-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="20b33-107">Type en fonction duquel tester chaque objet retourné par `expression` .</span><span class="sxs-lookup"><span data-stu-id="20b33-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="20b33-108">Le type doit être qualifié par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="20b33-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20b33-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="20b33-109">Return Value</span></span>  
 <span data-ttu-id="20b33-110">Collection d'objets du type `test_type`ou d'un type de base ou dérivé de `test_type`.</span><span class="sxs-lookup"><span data-stu-id="20b33-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="20b33-111">Si ONLY est spécifié, seules les instances de `test_type` ou une collection vide seront retournées.</span><span class="sxs-lookup"><span data-stu-id="20b33-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20b33-112">Notes</span><span class="sxs-lookup"><span data-stu-id="20b33-112">Remarks</span></span>  
 <span data-ttu-id="20b33-113">Une expression `OFTYPE` spécifie une expression de type émise pour effectuer un test de type sur chaque élément d'une collection.</span><span class="sxs-lookup"><span data-stu-id="20b33-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="20b33-114">L'expression `OFTYPE` produit une nouvelle collection du type spécifié ne contenant que les éléments qui étaient équivalents à ce type ou à l'un de ses sous-types.</span><span class="sxs-lookup"><span data-stu-id="20b33-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="20b33-115">Une expression `OFTYPE` est l'abréviation de l'expression de requête suivante :</span><span class="sxs-lookup"><span data-stu-id="20b33-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="20b33-116">Un Manager étant un sous-type d'Employee, l'expression suivante produit à partir d'une collection d'employés (employee) une collection composée uniquement de responsables (manager) :</span><span class="sxs-lookup"><span data-stu-id="20b33-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="20b33-117">Il est également possible d'effectuer un upcast sur une collection à l'aide du filtre de type :</span><span class="sxs-lookup"><span data-stu-id="20b33-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="20b33-118">Puisque tous les cadres (executives) sont des responsables, la collection obtenue contient toujours tous les cadres d'origine, même si elle est désormais typée en tant que collection de responsables.</span><span class="sxs-lookup"><span data-stu-id="20b33-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="20b33-119">Le tableau suivant montre le comportement de l'opérateur `OFTYPE` sur certains modèles.</span><span class="sxs-lookup"><span data-stu-id="20b33-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="20b33-120">Toutes les exceptions sont levées du côté client avant que le fournisseur ne soit appelé :</span><span class="sxs-lookup"><span data-stu-id="20b33-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="20b33-121">Motif</span><span class="sxs-lookup"><span data-stu-id="20b33-121">Pattern</span></span>|<span data-ttu-id="20b33-122">Comportement</span><span class="sxs-lookup"><span data-stu-id="20b33-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="20b33-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="20b33-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="20b33-124">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="20b33-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="20b33-125">OFTYPE(Collection(ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="20b33-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="20b33-126">Exception</span><span class="sxs-lookup"><span data-stu-id="20b33-126">Throws</span></span>|  
|<span data-ttu-id="20b33-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="20b33-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="20b33-128">Exception</span><span class="sxs-lookup"><span data-stu-id="20b33-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20b33-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="20b33-129">Example</span></span>  
 <span data-ttu-id="20b33-130">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise l'opérateur OFTYPE pour retourner une collection d'objets OnsiteCourse à partir d'une collection d'objets Course.</span><span class="sxs-lookup"><span data-stu-id="20b33-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="20b33-131">Cette requête est basée sur le modèle [School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="20b33-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="20b33-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20b33-132">See also</span></span>

- [<span data-ttu-id="20b33-133">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="20b33-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
