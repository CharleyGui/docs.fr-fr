---
title: Sémantique de comparaison (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150452"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="cee59-102">Sémantique de comparaison (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cee59-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="cee59-103">L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :</span><span class="sxs-lookup"><span data-stu-id="cee59-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="cee59-104">Comparaison explicite</span><span class="sxs-lookup"><span data-stu-id="cee59-104">Explicit comparison</span></span>  
 <span data-ttu-id="cee59-105">Opérations d'égalité :</span><span class="sxs-lookup"><span data-stu-id="cee59-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="cee59-106">!=</span><span class="sxs-lookup"><span data-stu-id="cee59-106">!=</span></span>  
  
 <span data-ttu-id="cee59-107">Opérations de classement :</span><span class="sxs-lookup"><span data-stu-id="cee59-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="cee59-108">Opérations relatives à la possibilité de valeurs NULL :</span><span class="sxs-lookup"><span data-stu-id="cee59-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="cee59-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="cee59-109">IS NULL</span></span>  
  
- <span data-ttu-id="cee59-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="cee59-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="cee59-111">Distinction explicite</span><span class="sxs-lookup"><span data-stu-id="cee59-111">Explicit distinction</span></span>  
 <span data-ttu-id="cee59-112">Distinction d'égalité :</span><span class="sxs-lookup"><span data-stu-id="cee59-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="cee59-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="cee59-113">DISTINCT</span></span>  
  
- <span data-ttu-id="cee59-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="cee59-114">GROUP BY</span></span>  
  
 <span data-ttu-id="cee59-115">Distinction de classement :</span><span class="sxs-lookup"><span data-stu-id="cee59-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="cee59-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="cee59-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="cee59-117">Distinction implicite</span><span class="sxs-lookup"><span data-stu-id="cee59-117">Implicit distinction</span></span>  
 <span data-ttu-id="cee59-118">Opérations et prédicats de définition (égalité) :</span><span class="sxs-lookup"><span data-stu-id="cee59-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="cee59-119">UNION</span><span class="sxs-lookup"><span data-stu-id="cee59-119">UNION</span></span>  
  
- <span data-ttu-id="cee59-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="cee59-120">INTERSECT</span></span>  
  
- <span data-ttu-id="cee59-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="cee59-121">EXCEPT</span></span>  
  
- <span data-ttu-id="cee59-122">SET</span><span class="sxs-lookup"><span data-stu-id="cee59-122">SET</span></span>  
  
- <span data-ttu-id="cee59-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="cee59-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="cee59-124">Prédicats d'élément (égalité) :</span><span class="sxs-lookup"><span data-stu-id="cee59-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="cee59-125">IN</span><span class="sxs-lookup"><span data-stu-id="cee59-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="cee59-126">Combinaisons prises en charge</span><span class="sxs-lookup"><span data-stu-id="cee59-126">Supported Combinations</span></span>  
 <span data-ttu-id="cee59-127">Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :</span><span class="sxs-lookup"><span data-stu-id="cee59-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="cee59-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="cee59-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="cee59-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="cee59-129">**!=**</span></span>|<span data-ttu-id="cee59-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="cee59-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="cee59-131">**Distinctes**</span><span class="sxs-lookup"><span data-stu-id="cee59-131">**DISTINCT**</span></span>|<span data-ttu-id="cee59-132">**Union**</span><span class="sxs-lookup"><span data-stu-id="cee59-132">**UNION**</span></span><br /><br /> <span data-ttu-id="cee59-133">**Intersect**</span><span class="sxs-lookup"><span data-stu-id="cee59-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="cee59-134">**Sauf**</span><span class="sxs-lookup"><span data-stu-id="cee59-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="cee59-135">**Ensemble**</span><span class="sxs-lookup"><span data-stu-id="cee59-135">**SET**</span></span><br /><br /> <span data-ttu-id="cee59-136">**Chevauchements**</span><span class="sxs-lookup"><span data-stu-id="cee59-136">**OVERLAPS**</span></span>|<span data-ttu-id="cee59-137">**Dans**</span><span class="sxs-lookup"><span data-stu-id="cee59-137">**IN**</span></span>|<span data-ttu-id="cee59-138">**< <**</span><span class="sxs-lookup"><span data-stu-id="cee59-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="cee59-139">**> >**</span><span class="sxs-lookup"><span data-stu-id="cee59-139">**>   >=**</span></span>|<span data-ttu-id="cee59-140">**COMMANDE PAR**</span><span class="sxs-lookup"><span data-stu-id="cee59-140">**ORDER BY**</span></span>|<span data-ttu-id="cee59-141">**EST NUL**</span><span class="sxs-lookup"><span data-stu-id="cee59-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="cee59-142">**N’EST PAS NUL**</span><span class="sxs-lookup"><span data-stu-id="cee59-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="cee59-143">Type d'entité</span><span class="sxs-lookup"><span data-stu-id="cee59-143">Entity type</span></span>|<span data-ttu-id="cee59-144">Réf<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="cee59-145">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="cee59-146">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="cee59-147">Toutes les propriétés<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="cee59-148">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-149">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-150">Réf<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="cee59-151">Type complexe</span><span class="sxs-lookup"><span data-stu-id="cee59-151">Complex type</span></span>|<span data-ttu-id="cee59-152">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-153">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-154">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-155">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-156">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-157">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-158">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="cee59-159">Ligne</span><span class="sxs-lookup"><span data-stu-id="cee59-159">Row</span></span>|<span data-ttu-id="cee59-160">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="cee59-161">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="cee59-162">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="cee59-163">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-164">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-165">Toutes les propriétés<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="cee59-166">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="cee59-167">Type primitif</span><span class="sxs-lookup"><span data-stu-id="cee59-167">Primitive type</span></span>|<span data-ttu-id="cee59-168">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="cee59-168">Provider-specific</span></span>|<span data-ttu-id="cee59-169">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="cee59-169">Provider-specific</span></span>|<span data-ttu-id="cee59-170">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="cee59-170">Provider-specific</span></span>|<span data-ttu-id="cee59-171">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="cee59-171">Provider-specific</span></span>|<span data-ttu-id="cee59-172">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="cee59-172">Provider-specific</span></span>|<span data-ttu-id="cee59-173">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="cee59-173">Provider-specific</span></span>|<span data-ttu-id="cee59-174">Spécifique au fournisseur</span><span class="sxs-lookup"><span data-stu-id="cee59-174">Provider-specific</span></span>|  
|<span data-ttu-id="cee59-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="cee59-175">Multiset</span></span>|<span data-ttu-id="cee59-176">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-177">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-178">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-179">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-180">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-181">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-182">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="cee59-183">Ref</span><span class="sxs-lookup"><span data-stu-id="cee59-183">Ref</span></span>|<span data-ttu-id="cee59-184">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="cee59-185">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="cee59-186">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="cee59-187">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="cee59-188">Throw</span><span class="sxs-lookup"><span data-stu-id="cee59-188">Throw</span></span>|<span data-ttu-id="cee59-189">Throw</span><span class="sxs-lookup"><span data-stu-id="cee59-189">Throw</span></span>|<span data-ttu-id="cee59-190">Oui<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="cee59-191">Association</span><span class="sxs-lookup"><span data-stu-id="cee59-191">Association</span></span><br /><br /> <span data-ttu-id="cee59-192">type</span><span class="sxs-lookup"><span data-stu-id="cee59-192">type</span></span>|<span data-ttu-id="cee59-193">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-194">Throw</span><span class="sxs-lookup"><span data-stu-id="cee59-194">Throw</span></span>|<span data-ttu-id="cee59-195">Throw</span><span class="sxs-lookup"><span data-stu-id="cee59-195">Throw</span></span>|<span data-ttu-id="cee59-196">Throw</span><span class="sxs-lookup"><span data-stu-id="cee59-196">Throw</span></span>|<span data-ttu-id="cee59-197">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-198">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="cee59-199">Lancer<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="cee59-200"><sup>1</sup> Les références des instances de type entité donnée sont implicitement comparées, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cee59-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="cee59-201">Une instance d'entité ne peut pas être comparée à une référence explicite.</span><span class="sxs-lookup"><span data-stu-id="cee59-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="cee59-202">Lors d'une telle tentative, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="cee59-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="cee59-203">Par exemple, la requête suivante lève une exception :</span><span class="sxs-lookup"><span data-stu-id="cee59-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="cee59-204"><sup>2</sup> Les propriétés de types complexes sont aplaties avant d’être envoyées au magasin, de sorte qu’elles deviennent comparables (tant que toutes leurs propriétés sont comparables).</span><span class="sxs-lookup"><span data-stu-id="cee59-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="cee59-205">Voir aussi <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="cee59-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="cee59-206"><sup>3</sup> Le temps d’exécution du Cadre d’entité détecte le boîtier non pris en charge et fait une exception significative sans engager le fournisseur/magasin.</span><span class="sxs-lookup"><span data-stu-id="cee59-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="cee59-207"><sup>4</sup> Une tentative est faite pour comparer toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="cee59-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="cee59-208">Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.</span><span class="sxs-lookup"><span data-stu-id="cee59-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="cee59-209"><sup>5</sup> Tous les éléments individuels des références sont comparés (cela inclut le nom d’entité et toutes les propriétés clés du type d’entité).</span><span class="sxs-lookup"><span data-stu-id="cee59-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee59-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cee59-210">See also</span></span>

- [<span data-ttu-id="cee59-211">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cee59-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
