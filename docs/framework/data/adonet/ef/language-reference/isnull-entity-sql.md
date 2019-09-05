---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250555"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="8e699-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8e699-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="8e699-103">Détermine si une expression de requête a la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="8e699-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e699-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e699-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e699-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8e699-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8e699-106">Toute expression de requête valide.</span><span class="sxs-lookup"><span data-stu-id="8e699-106">Any valid query expression.</span></span> <span data-ttu-id="8e699-107">Ne peut pas être une collection, posséder des membres de collection ou être un type d'enregistrement avec des propriétés de type collection.</span><span class="sxs-lookup"><span data-stu-id="8e699-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="8e699-108">NOT</span><span class="sxs-lookup"><span data-stu-id="8e699-108">NOT</span></span>  
 <span data-ttu-id="8e699-109">Inverse le résultat EDM.Boolean de l'opérateur IS NULL.</span><span class="sxs-lookup"><span data-stu-id="8e699-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e699-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8e699-110">Return Value</span></span>  
 <span data-ttu-id="8e699-111">`true` si `expression` retourne la valeur NULL ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="8e699-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e699-112">Notes</span><span class="sxs-lookup"><span data-stu-id="8e699-112">Remarks</span></span>  
 <span data-ttu-id="8e699-113">Utilisez `IS NULL` pour déterminer si l'élément d'une jointure externe est NULL :</span><span class="sxs-lookup"><span data-stu-id="8e699-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="8e699-114">Utilisez `IS NULL` pour déterminer si un membre a une valeur réelle :</span><span class="sxs-lookup"><span data-stu-id="8e699-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="8e699-115">Le tableau ci-dessous montre le comportement de l'opérateur `IS NULL` sur certains modèles.</span><span class="sxs-lookup"><span data-stu-id="8e699-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="8e699-116">Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :</span><span class="sxs-lookup"><span data-stu-id="8e699-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="8e699-117">Motif</span><span class="sxs-lookup"><span data-stu-id="8e699-117">Pattern</span></span>|<span data-ttu-id="8e699-118">Comportement</span><span class="sxs-lookup"><span data-stu-id="8e699-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="8e699-119">null IS NULL</span><span class="sxs-lookup"><span data-stu-id="8e699-119">null IS NULL</span></span>|<span data-ttu-id="8e699-120">Retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="8e699-120">Returns `true`.</span></span>|  
|<span data-ttu-id="8e699-121">TREAT (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="8e699-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="8e699-122">Retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="8e699-122">Returns `true`.</span></span>|  
|<span data-ttu-id="8e699-123">TREAT (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="8e699-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="8e699-124">Génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="8e699-124">Throws an error.</span></span>|  
|<span data-ttu-id="8e699-125">TREAT (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="8e699-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="8e699-126">Génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="8e699-126">Throws an error.</span></span>|  
|<span data-ttu-id="8e699-127">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="8e699-127">EntityType IS NULL</span></span>|<span data-ttu-id="8e699-128">Retourne `true` ou la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="8e699-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="8e699-129">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="8e699-129">ComplexType IS NULL</span></span>|<span data-ttu-id="8e699-130">Génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="8e699-130">Throws an error.</span></span>|  
|<span data-ttu-id="8e699-131">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="8e699-131">RowType IS NULL</span></span>|<span data-ttu-id="8e699-132">Génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="8e699-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e699-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="8e699-133">Example</span></span>  
 <span data-ttu-id="8e699-134">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise l’opérateur is not null pour déterminer si une expression de requête n’a pas la valeur null.</span><span class="sxs-lookup"><span data-stu-id="8e699-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="8e699-135">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="8e699-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8e699-136">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e699-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8e699-137">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="8e699-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8e699-138">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="8e699-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="8e699-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e699-139">See also</span></span>

- [<span data-ttu-id="8e699-140">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8e699-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
