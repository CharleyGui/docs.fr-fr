---
title: Exemples de requêtes
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: f3f135850fb5f40b3b8882f72f5cc24512f21084
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147552"
---
# <a name="query-examples"></a><span data-ttu-id="9c0c8-102">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="9c0c8-102">Query Examples</span></span>

<span data-ttu-id="9c0c8-103">Cette section fournit des exemples Visual Basic et C# de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requêtes typiques.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="9c0c8-104">Les développeurs qui utilisent Visual Studio peuvent trouver un grand nombre d’exemples dans un exemple de solution disponible dans la section exemples.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="9c0c8-105">Pour plus d’informations, consultez [exemples](samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c0c8-105">For more information, see [Samples](samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9c0c8-106">*DB* est souvent utilisé dans des exemples de code dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] la documentation.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="9c0c8-107">*DB* est supposé être une instance d’une classe *Northwind* , qui hérite de <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="9c0c8-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c0c8-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9c0c8-108">In This Section</span></span>  

 [<span data-ttu-id="9c0c8-109">Requêtes d'agrégation</span><span class="sxs-lookup"><span data-stu-id="9c0c8-109">Aggregate Queries</span></span>](aggregate-queries.md)  
 <span data-ttu-id="9c0c8-110">Explique comment utiliser <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, etc.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="9c0c8-111">Retourner le premier élément d'une séquence</span><span class="sxs-lookup"><span data-stu-id="9c0c8-111">Return the First Element in a Sequence</span></span>](return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="9c0c8-112">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-113">Comment : retourner ou ignorer des éléments d'une séquence</span><span class="sxs-lookup"><span data-stu-id="9c0c8-113">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="9c0c8-114">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Take%2A> et de <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-115">Trier les éléments d'une séquence</span><span class="sxs-lookup"><span data-stu-id="9c0c8-115">Sort Elements in a Sequence</span></span>](sort-elements-in-a-sequence.md)  
 <span data-ttu-id="9c0c8-116">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-117">Comment : regrouper des éléments dans une séquence</span><span class="sxs-lookup"><span data-stu-id="9c0c8-117">Group Elements in a Sequence</span></span>](group-elements-in-a-sequence.md)  
 <span data-ttu-id="9c0c8-118">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-119">Comment : éliminer des éléments en double d'une séquence</span><span class="sxs-lookup"><span data-stu-id="9c0c8-119">Eliminate Duplicate Elements from a Sequence</span></span>](eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="9c0c8-120">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-121">Comment : déterminer si certains ou tous les éléments d'une séquence remplissent une condition</span><span class="sxs-lookup"><span data-stu-id="9c0c8-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="9c0c8-122">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.All%2A> et de <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-123">Concaténer deux séquences</span><span class="sxs-lookup"><span data-stu-id="9c0c8-123">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)  
 <span data-ttu-id="9c0c8-124">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-125">Comment : retourner la différence définie entre deux séquences</span><span class="sxs-lookup"><span data-stu-id="9c0c8-125">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="9c0c8-126">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-127">Retourner l'intersection définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="9c0c8-127">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="9c0c8-128">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-129">Retourner l'union définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="9c0c8-129">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="9c0c8-130">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-131">Comment : convertir une séquence en tableau</span><span class="sxs-lookup"><span data-stu-id="9c0c8-131">Convert a Sequence to an Array</span></span>](convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="9c0c8-132">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-133">Comment : convertir une séquence en liste générique</span><span class="sxs-lookup"><span data-stu-id="9c0c8-133">Convert a Sequence to a Generic List</span></span>](convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="9c0c8-134">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-135">Comment : convertir un type en IEnumerable générique</span><span class="sxs-lookup"><span data-stu-id="9c0c8-135">Convert a Type to a Generic IEnumerable</span></span>](convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="9c0c8-136">Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="9c0c8-137">Comment : formuler des jointures et des requêtes de produit croisé</span><span class="sxs-lookup"><span data-stu-id="9c0c8-137">Formulate Joins and Cross-Product Queries</span></span>](formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="9c0c8-138">Fournit des exemples d'utilisation de la navigation de clé étrangère dans les clauses `from`, `where` et `select`.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="9c0c8-139">Formuler des projections</span><span class="sxs-lookup"><span data-stu-id="9c0c8-139">Formulate Projections</span></span>](formulate-projections.md)  
 <span data-ttu-id="9c0c8-140">Fournit des exemples de combinaison `select` avec d’autres fonctionnalités (par exemple, des *types anonymes*) pour former des projections de requête.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9c0c8-141">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="9c0c8-141">Related Sections</span></span>  

 [<span data-ttu-id="9c0c8-142">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="9c0c8-142">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="9c0c8-143">Explique le concept des opérateurs de requête standard à l’aide de C#.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-143">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="9c0c8-144">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c0c8-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="9c0c8-145">Explique le concept des opérateurs de requête standard à l’aide de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-145">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="9c0c8-146">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="9c0c8-146">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="9c0c8-147">Explique comment [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise des concepts qui s'appliquent aux requêtes.</span><span class="sxs-lookup"><span data-stu-id="9c0c8-147">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="9c0c8-148">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="9c0c8-148">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="9c0c8-149">Fournit un portail vers des rubriques qui expliquent des concepts de programmation en rapport avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c0c8-149">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
