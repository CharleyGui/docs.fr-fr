---
title: Sémantique de comparaison (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: da7b8f662d10376abd649e674701b43b7b740a6f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251182"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="454ae-102">Sémantique de comparaison (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="454ae-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="454ae-103">L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :</span><span class="sxs-lookup"><span data-stu-id="454ae-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="454ae-104">Comparaison explicite</span><span class="sxs-lookup"><span data-stu-id="454ae-104">Explicit comparison</span></span>  
 <span data-ttu-id="454ae-105">Opérations d'égalité :</span><span class="sxs-lookup"><span data-stu-id="454ae-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="454ae-106">!=</span><span class="sxs-lookup"><span data-stu-id="454ae-106">!=</span></span>  
  
 <span data-ttu-id="454ae-107">Opérations de classement :</span><span class="sxs-lookup"><span data-stu-id="454ae-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="454ae-108">Opérations relatives à la possibilité de valeurs NULL :</span><span class="sxs-lookup"><span data-stu-id="454ae-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="454ae-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="454ae-109">IS NULL</span></span>  
  
- <span data-ttu-id="454ae-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="454ae-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="454ae-111">Distinction explicite</span><span class="sxs-lookup"><span data-stu-id="454ae-111">Explicit distinction</span></span>  
 <span data-ttu-id="454ae-112">Distinction d'égalité :</span><span class="sxs-lookup"><span data-stu-id="454ae-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="454ae-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="454ae-113">DISTINCT</span></span>  
  
- <span data-ttu-id="454ae-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="454ae-114">GROUP BY</span></span>  
  
 <span data-ttu-id="454ae-115">Distinction de classement :</span><span class="sxs-lookup"><span data-stu-id="454ae-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="454ae-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="454ae-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="454ae-117">Distinction implicite</span><span class="sxs-lookup"><span data-stu-id="454ae-117">Implicit distinction</span></span>  
 <span data-ttu-id="454ae-118">Opérations et prédicats de définition (égalité) :</span><span class="sxs-lookup"><span data-stu-id="454ae-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="454ae-119">UNION</span><span class="sxs-lookup"><span data-stu-id="454ae-119">UNION</span></span>  
  
- <span data-ttu-id="454ae-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="454ae-120">INTERSECT</span></span>  
  
- <span data-ttu-id="454ae-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="454ae-121">EXCEPT</span></span>  
  
- <span data-ttu-id="454ae-122">SET</span><span class="sxs-lookup"><span data-stu-id="454ae-122">SET</span></span>  
  
- <span data-ttu-id="454ae-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="454ae-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="454ae-124">Prédicats d'élément (égalité) :</span><span class="sxs-lookup"><span data-stu-id="454ae-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="454ae-125">IN</span><span class="sxs-lookup"><span data-stu-id="454ae-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="454ae-126">Combinaisons prises en charge</span><span class="sxs-lookup"><span data-stu-id="454ae-126">Supported Combinations</span></span>  
 <span data-ttu-id="454ae-127">Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :</span><span class="sxs-lookup"><span data-stu-id="454ae-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="454ae-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="454ae-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="454ae-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="454ae-129">**!=**</span></span>|<span data-ttu-id="454ae-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="454ae-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="454ae-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="454ae-131">**DISTINCT**</span></span>|<span data-ttu-id="454ae-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="454ae-132">**UNION**</span></span><br /><br /> <span data-ttu-id="454ae-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="454ae-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="454ae-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="454ae-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="454ae-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="454ae-135">**SET**</span></span><br /><br /> <span data-ttu-id="454ae-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="454ae-136">**OVERLAPS**</span></span>|<span data-ttu-id="454ae-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="454ae-137">**IN**</span></span>|<span data-ttu-id="454ae-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="454ae-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="454ae-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="454ae-139">**>   >=**</span></span>|<span data-ttu-id="454ae-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="454ae-140">**ORDER BY**</span></span>|<span data-ttu-id="454ae-141">**EST NULL**</span><span class="sxs-lookup"><span data-stu-id="454ae-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="454ae-142">**N’EST PAS NULL**</span><span class="sxs-lookup"><span data-stu-id="454ae-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="454ae-143">Type d'entité</span><span class="sxs-lookup"><span data-stu-id="454ae-143">Entity type</span></span>|<span data-ttu-id="454ae-144">Réf.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="454ae-145">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="454ae-146">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="454ae-147">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="454ae-148">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-149">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-150">Réf.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="454ae-151">Type complexe</span><span class="sxs-lookup"><span data-stu-id="454ae-151">Complex type</span></span>|<span data-ttu-id="454ae-152">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-153">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-154">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-155">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-156">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-157">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-158">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="454ae-159">Ligne</span><span class="sxs-lookup"><span data-stu-id="454ae-159">Row</span></span>|<span data-ttu-id="454ae-160">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="454ae-161">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="454ae-162">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="454ae-163">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-164">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-165">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="454ae-166">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="454ae-167">Type primitif</span><span class="sxs-lookup"><span data-stu-id="454ae-167">Primitive type</span></span>|<span data-ttu-id="454ae-168">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="454ae-168">Provider-specific</span></span>|<span data-ttu-id="454ae-169">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="454ae-169">Provider-specific</span></span>|<span data-ttu-id="454ae-170">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="454ae-170">Provider-specific</span></span>|<span data-ttu-id="454ae-171">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="454ae-171">Provider-specific</span></span>|<span data-ttu-id="454ae-172">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="454ae-172">Provider-specific</span></span>|<span data-ttu-id="454ae-173">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="454ae-173">Provider-specific</span></span>|<span data-ttu-id="454ae-174">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="454ae-174">Provider-specific</span></span>|  
|<span data-ttu-id="454ae-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="454ae-175">Multiset</span></span>|<span data-ttu-id="454ae-176">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-177">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-178">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-179">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-180">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-181">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-182">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="454ae-183">Ref</span><span class="sxs-lookup"><span data-stu-id="454ae-183">Ref</span></span>|<span data-ttu-id="454ae-184">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="454ae-185">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="454ae-186">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="454ae-187">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="454ae-188">Throw</span><span class="sxs-lookup"><span data-stu-id="454ae-188">Throw</span></span>|<span data-ttu-id="454ae-189">Throw</span><span class="sxs-lookup"><span data-stu-id="454ae-189">Throw</span></span>|<span data-ttu-id="454ae-190">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="454ae-191">Association</span><span class="sxs-lookup"><span data-stu-id="454ae-191">Association</span></span><br /><br /> <span data-ttu-id="454ae-192">type</span><span class="sxs-lookup"><span data-stu-id="454ae-192">type</span></span>|<span data-ttu-id="454ae-193">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-194">Throw</span><span class="sxs-lookup"><span data-stu-id="454ae-194">Throw</span></span>|<span data-ttu-id="454ae-195">Throw</span><span class="sxs-lookup"><span data-stu-id="454ae-195">Throw</span></span>|<span data-ttu-id="454ae-196">Throw</span><span class="sxs-lookup"><span data-stu-id="454ae-196">Throw</span></span>|<span data-ttu-id="454ae-197">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-198">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="454ae-199">Lever<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="454ae-200"><sup>1</sup> Les références des instances de type d’entité données sont comparées implicitement, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="454ae-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="454ae-201">Une instance d'entité ne peut pas être comparée à une référence explicite.</span><span class="sxs-lookup"><span data-stu-id="454ae-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="454ae-202">Lors d'une telle tentative, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="454ae-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="454ae-203">Par exemple, la requête suivante lève une exception :</span><span class="sxs-lookup"><span data-stu-id="454ae-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="454ae-204"><sup>2</sup> Les propriétés des types complexes sont aplaties avant d’être envoyées au magasin. elles deviennent donc comparables (à condition que toutes leurs propriétés soient comparables).</span><span class="sxs-lookup"><span data-stu-id="454ae-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="454ae-205">Consultez également <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="454ae-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="454ae-206"><sup>3</sup> Le runtime Entity Framework détecte le cas non pris en charge et lève une exception significative sans engager le fournisseur/magasin.</span><span class="sxs-lookup"><span data-stu-id="454ae-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="454ae-207"><sup>4</sup> Une tentative est effectuée pour comparer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="454ae-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="454ae-208">Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.</span><span class="sxs-lookup"><span data-stu-id="454ae-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="454ae-209"><sup>5</sup> Tous les éléments individuels des références sont comparés (cela comprend le nom du jeu d’entités et toutes les propriétés de clé du type d’entité).</span><span class="sxs-lookup"><span data-stu-id="454ae-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454ae-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="454ae-210">See also</span></span>

- [<span data-ttu-id="454ae-211">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="454ae-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
