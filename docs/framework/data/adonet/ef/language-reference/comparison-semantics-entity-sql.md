---
title: Sémantique de comparaison (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 2ca91861d4830321168e96fb200c4889dc33b04b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631720"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="347f8-102">Sémantique de comparaison (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="347f8-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="347f8-103">L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :</span><span class="sxs-lookup"><span data-stu-id="347f8-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="347f8-104">Comparaison explicite</span><span class="sxs-lookup"><span data-stu-id="347f8-104">Explicit comparison</span></span>  
 <span data-ttu-id="347f8-105">Opérations d'égalité :</span><span class="sxs-lookup"><span data-stu-id="347f8-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="347f8-106">!=</span><span class="sxs-lookup"><span data-stu-id="347f8-106">!=</span></span>  
  
 <span data-ttu-id="347f8-107">Opérations de classement :</span><span class="sxs-lookup"><span data-stu-id="347f8-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="347f8-108">Opérations relatives à la possibilité de valeurs NULL :</span><span class="sxs-lookup"><span data-stu-id="347f8-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="347f8-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="347f8-109">IS NULL</span></span>  
  
- <span data-ttu-id="347f8-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="347f8-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="347f8-111">Distinction explicite</span><span class="sxs-lookup"><span data-stu-id="347f8-111">Explicit distinction</span></span>  
 <span data-ttu-id="347f8-112">Distinction d'égalité :</span><span class="sxs-lookup"><span data-stu-id="347f8-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="347f8-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="347f8-113">DISTINCT</span></span>  
  
- <span data-ttu-id="347f8-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="347f8-114">GROUP BY</span></span>  
  
 <span data-ttu-id="347f8-115">Distinction de classement :</span><span class="sxs-lookup"><span data-stu-id="347f8-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="347f8-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="347f8-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="347f8-117">Distinction implicite</span><span class="sxs-lookup"><span data-stu-id="347f8-117">Implicit distinction</span></span>  
 <span data-ttu-id="347f8-118">Opérations et prédicats de définition (égalité) :</span><span class="sxs-lookup"><span data-stu-id="347f8-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="347f8-119">UNION</span><span class="sxs-lookup"><span data-stu-id="347f8-119">UNION</span></span>  
  
- <span data-ttu-id="347f8-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="347f8-120">INTERSECT</span></span>  
  
- <span data-ttu-id="347f8-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="347f8-121">EXCEPT</span></span>  
  
- <span data-ttu-id="347f8-122">SET</span><span class="sxs-lookup"><span data-stu-id="347f8-122">SET</span></span>  
  
- <span data-ttu-id="347f8-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="347f8-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="347f8-124">Prédicats d'élément (égalité) :</span><span class="sxs-lookup"><span data-stu-id="347f8-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="347f8-125">IN</span><span class="sxs-lookup"><span data-stu-id="347f8-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="347f8-126">Combinaisons prises en charge</span><span class="sxs-lookup"><span data-stu-id="347f8-126">Supported Combinations</span></span>  
 <span data-ttu-id="347f8-127">Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :</span><span class="sxs-lookup"><span data-stu-id="347f8-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="347f8-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="347f8-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="347f8-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="347f8-129">**!=**</span></span>|<span data-ttu-id="347f8-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="347f8-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="347f8-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="347f8-131">**DISTINCT**</span></span>|<span data-ttu-id="347f8-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="347f8-132">**UNION**</span></span><br /><br /> <span data-ttu-id="347f8-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="347f8-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="347f8-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="347f8-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="347f8-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="347f8-135">**SET**</span></span><br /><br /> <span data-ttu-id="347f8-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="347f8-136">**OVERLAPS**</span></span>|<span data-ttu-id="347f8-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="347f8-137">**IN**</span></span>|<span data-ttu-id="347f8-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="347f8-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="347f8-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="347f8-139">**>   >=**</span></span>|<span data-ttu-id="347f8-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="347f8-140">**ORDER BY**</span></span>|<span data-ttu-id="347f8-141">**A LA VALEUR NULL**</span><span class="sxs-lookup"><span data-stu-id="347f8-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="347f8-142">**N’EST PAS NULL**</span><span class="sxs-lookup"><span data-stu-id="347f8-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="347f8-143">Type d'entité</span><span class="sxs-lookup"><span data-stu-id="347f8-143">Entity type</span></span>|<span data-ttu-id="347f8-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="347f8-145">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="347f8-146">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="347f8-147">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="347f8-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="347f8-151">Type complexe</span><span class="sxs-lookup"><span data-stu-id="347f8-151">Complex type</span></span>|<span data-ttu-id="347f8-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="347f8-159">Ligne</span><span class="sxs-lookup"><span data-stu-id="347f8-159">Row</span></span>|<span data-ttu-id="347f8-160">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="347f8-161">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="347f8-162">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="347f8-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-165">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="347f8-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="347f8-167">Type primitif</span><span class="sxs-lookup"><span data-stu-id="347f8-167">Primitive type</span></span>|<span data-ttu-id="347f8-168">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="347f8-168">Provider-specific</span></span>|<span data-ttu-id="347f8-169">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="347f8-169">Provider-specific</span></span>|<span data-ttu-id="347f8-170">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="347f8-170">Provider-specific</span></span>|<span data-ttu-id="347f8-171">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="347f8-171">Provider-specific</span></span>|<span data-ttu-id="347f8-172">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="347f8-172">Provider-specific</span></span>|<span data-ttu-id="347f8-173">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="347f8-173">Provider-specific</span></span>|<span data-ttu-id="347f8-174">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="347f8-174">Provider-specific</span></span>|  
|<span data-ttu-id="347f8-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="347f8-175">Multiset</span></span>|<span data-ttu-id="347f8-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="347f8-183">Ref</span><span class="sxs-lookup"><span data-stu-id="347f8-183">Ref</span></span>|<span data-ttu-id="347f8-184">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="347f8-185">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="347f8-186">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="347f8-187">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="347f8-188">Throw</span><span class="sxs-lookup"><span data-stu-id="347f8-188">Throw</span></span>|<span data-ttu-id="347f8-189">Throw</span><span class="sxs-lookup"><span data-stu-id="347f8-189">Throw</span></span>|<span data-ttu-id="347f8-190">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="347f8-191">Association</span><span class="sxs-lookup"><span data-stu-id="347f8-191">Association</span></span><br /><br /> <span data-ttu-id="347f8-192">type</span><span class="sxs-lookup"><span data-stu-id="347f8-192">type</span></span>|<span data-ttu-id="347f8-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-194">Throw</span><span class="sxs-lookup"><span data-stu-id="347f8-194">Throw</span></span>|<span data-ttu-id="347f8-195">Throw</span><span class="sxs-lookup"><span data-stu-id="347f8-195">Throw</span></span>|<span data-ttu-id="347f8-196">Throw</span><span class="sxs-lookup"><span data-stu-id="347f8-196">Throw</span></span>|<span data-ttu-id="347f8-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="347f8-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="347f8-200"><sup>1</sup>les références des instances du type d’entité donnée sont comparées implicitement, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="347f8-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="347f8-201">Une instance d'entité ne peut pas être comparée à une référence explicite.</span><span class="sxs-lookup"><span data-stu-id="347f8-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="347f8-202">Lors d'une telle tentative, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="347f8-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="347f8-203">Par exemple, la requête suivante lève une exception :</span><span class="sxs-lookup"><span data-stu-id="347f8-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="347f8-204"><sup>2</sup>propriétés de types complexes sont aplanies avant d’être envoyés au magasin, afin de pouvoir être comparées (tant que toutes leurs propriétés peuvent être comparées).</span><span class="sxs-lookup"><span data-stu-id="347f8-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="347f8-205">Consultez également <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="347f8-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="347f8-206"><sup>3</sup>runtime de l’Entity Framework détecte le cas non pris en charge et lève une exception explicite sans engager le fournisseur/magasin.</span><span class="sxs-lookup"><span data-stu-id="347f8-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="347f8-207"><sup>4</sup>une tentative est faite pour comparer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="347f8-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="347f8-208">Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.</span><span class="sxs-lookup"><span data-stu-id="347f8-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="347f8-209"><sup>5</sup>tous les éléments individuels des références sont comparés (Cela inclut le nom de jeu d’entités et de toutes les propriétés de clé du type d’entité).</span><span class="sxs-lookup"><span data-stu-id="347f8-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347f8-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="347f8-210">See also</span></span>

- [<span data-ttu-id="347f8-211">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="347f8-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
