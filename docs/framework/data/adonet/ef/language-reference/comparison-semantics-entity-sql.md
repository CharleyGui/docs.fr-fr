---
title: Sémantique de comparaison (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 9a36fcc4476c25d64fed670e857f339fb20043d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197831"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="ae8d9-102">Sémantique de comparaison (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ae8d9-102">Comparison Semantics (Entity SQL)</span></span>

<span data-ttu-id="ae8d9-103">L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="ae8d9-104">Comparaison explicite</span><span class="sxs-lookup"><span data-stu-id="ae8d9-104">Explicit comparison</span></span>  

 <span data-ttu-id="ae8d9-105">Opérations d'égalité :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="ae8d9-106">!=</span><span class="sxs-lookup"><span data-stu-id="ae8d9-106">!=</span></span>  
  
 <span data-ttu-id="ae8d9-107">Opérations de classement :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="ae8d9-108">Opérations relatives à la possibilité de valeurs NULL :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="ae8d9-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="ae8d9-109">IS NULL</span></span>  
  
- <span data-ttu-id="ae8d9-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="ae8d9-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="ae8d9-111">Distinction explicite</span><span class="sxs-lookup"><span data-stu-id="ae8d9-111">Explicit distinction</span></span>  

 <span data-ttu-id="ae8d9-112">Distinction d'égalité :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="ae8d9-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="ae8d9-113">DISTINCT</span></span>  
  
- <span data-ttu-id="ae8d9-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="ae8d9-114">GROUP BY</span></span>  
  
 <span data-ttu-id="ae8d9-115">Distinction de classement :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="ae8d9-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ae8d9-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="ae8d9-117">Distinction implicite</span><span class="sxs-lookup"><span data-stu-id="ae8d9-117">Implicit distinction</span></span>  

 <span data-ttu-id="ae8d9-118">Opérations et prédicats de définition (égalité) :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="ae8d9-119">UNION</span><span class="sxs-lookup"><span data-stu-id="ae8d9-119">UNION</span></span>  
  
- <span data-ttu-id="ae8d9-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="ae8d9-120">INTERSECT</span></span>  
  
- <span data-ttu-id="ae8d9-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="ae8d9-121">EXCEPT</span></span>  
  
- <span data-ttu-id="ae8d9-122">SET</span><span class="sxs-lookup"><span data-stu-id="ae8d9-122">SET</span></span>  
  
- <span data-ttu-id="ae8d9-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="ae8d9-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="ae8d9-124">Prédicats d'élément (égalité) :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="ae8d9-125">IN</span><span class="sxs-lookup"><span data-stu-id="ae8d9-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="ae8d9-126">Combinaisons prises en charge</span><span class="sxs-lookup"><span data-stu-id="ae8d9-126">Supported Combinations</span></span>  

 <span data-ttu-id="ae8d9-127">Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="ae8d9-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="ae8d9-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-129">**!=**</span></span>|<span data-ttu-id="ae8d9-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="ae8d9-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-131">**DISTINCT**</span></span>|<span data-ttu-id="ae8d9-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-132">**UNION**</span></span><br /><br /> <span data-ttu-id="ae8d9-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="ae8d9-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="ae8d9-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-135">**SET**</span></span><br /><br /> <span data-ttu-id="ae8d9-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-136">**OVERLAPS**</span></span>|<span data-ttu-id="ae8d9-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-137">**IN**</span></span>|<span data-ttu-id="ae8d9-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="ae8d9-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-139">**>   >=**</span></span>|<span data-ttu-id="ae8d9-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-140">**ORDER BY**</span></span>|<span data-ttu-id="ae8d9-141">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="ae8d9-142">**N’EST PAS NULL**</span><span class="sxs-lookup"><span data-stu-id="ae8d9-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="ae8d9-143">Type d'entité</span><span class="sxs-lookup"><span data-stu-id="ae8d9-143">Entity type</span></span>|<span data-ttu-id="ae8d9-144">Réf.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="ae8d9-145">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="ae8d9-146">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="ae8d9-147">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="ae8d9-148">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-149">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-150">Réf.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="ae8d9-151">Type complexe</span><span class="sxs-lookup"><span data-stu-id="ae8d9-151">Complex type</span></span>|<span data-ttu-id="ae8d9-152">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-153">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-154">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-155">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-156">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-157">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-158">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="ae8d9-159">Ligne</span><span class="sxs-lookup"><span data-stu-id="ae8d9-159">Row</span></span>|<span data-ttu-id="ae8d9-160">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="ae8d9-161">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="ae8d9-162">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="ae8d9-163">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-164">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-165">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="ae8d9-166">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="ae8d9-167">Type primitif</span><span class="sxs-lookup"><span data-stu-id="ae8d9-167">Primitive type</span></span>|<span data-ttu-id="ae8d9-168">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="ae8d9-168">Provider-specific</span></span>|<span data-ttu-id="ae8d9-169">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="ae8d9-169">Provider-specific</span></span>|<span data-ttu-id="ae8d9-170">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="ae8d9-170">Provider-specific</span></span>|<span data-ttu-id="ae8d9-171">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="ae8d9-171">Provider-specific</span></span>|<span data-ttu-id="ae8d9-172">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="ae8d9-172">Provider-specific</span></span>|<span data-ttu-id="ae8d9-173">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="ae8d9-173">Provider-specific</span></span>|<span data-ttu-id="ae8d9-174">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="ae8d9-174">Provider-specific</span></span>|  
|<span data-ttu-id="ae8d9-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="ae8d9-175">Multiset</span></span>|<span data-ttu-id="ae8d9-176">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-177">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-178">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-179">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-180">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-181">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-182">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="ae8d9-183">Ref</span><span class="sxs-lookup"><span data-stu-id="ae8d9-183">Ref</span></span>|<span data-ttu-id="ae8d9-184">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="ae8d9-185">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="ae8d9-186">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="ae8d9-187">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="ae8d9-188">Throw</span><span class="sxs-lookup"><span data-stu-id="ae8d9-188">Throw</span></span>|<span data-ttu-id="ae8d9-189">Throw</span><span class="sxs-lookup"><span data-stu-id="ae8d9-189">Throw</span></span>|<span data-ttu-id="ae8d9-190">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="ae8d9-191">Association</span><span class="sxs-lookup"><span data-stu-id="ae8d9-191">Association</span></span><br /><br /> <span data-ttu-id="ae8d9-192">type</span><span class="sxs-lookup"><span data-stu-id="ae8d9-192">type</span></span>|<span data-ttu-id="ae8d9-193">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-194">Throw</span><span class="sxs-lookup"><span data-stu-id="ae8d9-194">Throw</span></span>|<span data-ttu-id="ae8d9-195">Throw</span><span class="sxs-lookup"><span data-stu-id="ae8d9-195">Throw</span></span>|<span data-ttu-id="ae8d9-196">Throw</span><span class="sxs-lookup"><span data-stu-id="ae8d9-196">Throw</span></span>|<span data-ttu-id="ae8d9-197">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-198">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="ae8d9-199">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="ae8d9-200"><sup>1</sup> Les références des instances de type d’entité données sont comparées implicitement, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="ae8d9-201">Une instance d'entité ne peut pas être comparée à une référence explicite.</span><span class="sxs-lookup"><span data-stu-id="ae8d9-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="ae8d9-202">Lors d'une telle tentative, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="ae8d9-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="ae8d9-203">Par exemple, la requête suivante lève une exception :</span><span class="sxs-lookup"><span data-stu-id="ae8d9-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="ae8d9-204"><sup>2</sup> Les propriétés des types complexes sont aplaties avant d’être envoyées au magasin. elles deviennent donc comparables (à condition que toutes leurs propriétés soient comparables).</span><span class="sxs-lookup"><span data-stu-id="ae8d9-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="ae8d9-205">Consultez également <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="ae8d9-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="ae8d9-206"><sup>3</sup> Le runtime Entity Framework détecte le cas non pris en charge et lève une exception significative sans engager le fournisseur/magasin.</span><span class="sxs-lookup"><span data-stu-id="ae8d9-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="ae8d9-207"><sup>4</sup> Une tentative est effectuée pour comparer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="ae8d9-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="ae8d9-208">Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.</span><span class="sxs-lookup"><span data-stu-id="ae8d9-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="ae8d9-209"><sup>5</sup> Tous les éléments individuels des références sont comparés (cela comprend le nom du jeu d’entités et toutes les propriétés de clé du type d’entité).</span><span class="sxs-lookup"><span data-stu-id="ae8d9-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae8d9-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae8d9-210">See also</span></span>

- [<span data-ttu-id="ae8d9-211">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ae8d9-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
