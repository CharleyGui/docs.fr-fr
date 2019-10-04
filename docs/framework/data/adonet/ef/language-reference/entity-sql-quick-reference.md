---
title: Aide-mémoire Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833873"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="bb0c8-102">Aide-mémoire Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bb0c8-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="bb0c8-103">Cette rubrique fournit un aide-mémoire sur les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb0c8-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="bb0c8-104">Les requêtes de cette rubrique sont basées sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="bb0c8-105">Littéraux</span><span class="sxs-lookup"><span data-stu-id="bb0c8-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="bb0c8-106">String</span><span class="sxs-lookup"><span data-stu-id="bb0c8-106">String</span></span>  
 <span data-ttu-id="bb0c8-107">Les chaînes de caractères littérales peuvent être au format Unicode ou non-Unicode.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="bb0c8-108">Les chaînes Unicode sont précédées de N. Par exemple, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="bb0c8-109">Exemple de littéral de chaîne non-Unicode :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="bb0c8-110">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-110">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-111">`Value`</span><span class="sxs-lookup"><span data-stu-id="bb0c8-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-112">hello</span><span class="sxs-lookup"><span data-stu-id="bb0c8-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="bb0c8-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="bb0c8-113">DateTime</span></span>  
 <span data-ttu-id="bb0c8-114">Dans les littéraux DateTime, les parties date et heure sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="bb0c8-115">Il n'existe pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-115">There are no default values.</span></span>  
  
 <span data-ttu-id="bb0c8-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="bb0c8-117">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-117">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="bb0c8-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="bb0c8-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="bb0c8-120">Entier</span><span class="sxs-lookup"><span data-stu-id="bb0c8-120">Integer</span></span>  
 <span data-ttu-id="bb0c8-121">Les littéraux d'entiers peuvent être de type Int32 (123), UInt32 (123U), Int64 (123L) et UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="bb0c8-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="bb0c8-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="bb0c8-123">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-123">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-124">Valeur</span><span class="sxs-lookup"><span data-stu-id="bb0c8-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-125">1</span><span class="sxs-lookup"><span data-stu-id="bb0c8-125">1</span></span>|  
|<span data-ttu-id="bb0c8-126">2</span><span class="sxs-lookup"><span data-stu-id="bb0c8-126">2</span></span>|  
|<span data-ttu-id="bb0c8-127">3</span><span class="sxs-lookup"><span data-stu-id="bb0c8-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="bb0c8-128">Autre</span><span class="sxs-lookup"><span data-stu-id="bb0c8-128">Other</span></span>  
 <span data-ttu-id="bb0c8-129">Les autres littéraux pris en charge par [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont Guid, Binary, Float/Double, Decimal et la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="bb0c8-130">Les littéraux NULL dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont considérés compatibles avec tous les autres types dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="bb0c8-131">Constructeurs de type</span><span class="sxs-lookup"><span data-stu-id="bb0c8-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="bb0c8-132">ROW</span><span class="sxs-lookup"><span data-stu-id="bb0c8-132">ROW</span></span>  
 <span data-ttu-id="bb0c8-133">La [ligne](row-entity-sql.md) construit une valeur anonyme, structurellement typée (enregistrement) comme dans : `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="bb0c8-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="bb0c8-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="bb0c8-135">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-135">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-136">ProductID</span></span>|<span data-ttu-id="bb0c8-137">Nom</span><span class="sxs-lookup"><span data-stu-id="bb0c8-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="bb0c8-138">1</span><span class="sxs-lookup"><span data-stu-id="bb0c8-138">1</span></span>|<span data-ttu-id="bb0c8-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="bb0c8-139">Adjustable Race</span></span>|  
|<span data-ttu-id="bb0c8-140">879</span><span class="sxs-lookup"><span data-stu-id="bb0c8-140">879</span></span>|<span data-ttu-id="bb0c8-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="bb0c8-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bb0c8-142">712</span><span class="sxs-lookup"><span data-stu-id="bb0c8-142">712</span></span>|<span data-ttu-id="bb0c8-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="bb0c8-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bb0c8-144">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-144">...</span></span>|<span data-ttu-id="bb0c8-145">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="bb0c8-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="bb0c8-146">MULTISET</span></span>  
 <span data-ttu-id="bb0c8-147">Les collections de [multiensembles](multiset-entity-sql.md), telles que :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="bb0c8-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="bb0c8-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="bb0c8-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="bb0c8-150">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-150">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-151">ProductID</span></span>|<span data-ttu-id="bb0c8-152">Nom</span><span class="sxs-lookup"><span data-stu-id="bb0c8-152">Name</span></span>|<span data-ttu-id="bb0c8-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="bb0c8-153">ProductNumber</span></span>|<span data-ttu-id="bb0c8-154">…</span><span class="sxs-lookup"><span data-stu-id="bb0c8-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="bb0c8-155">842</span><span class="sxs-lookup"><span data-stu-id="bb0c8-155">842</span></span>|<span data-ttu-id="bb0c8-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="bb0c8-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="bb0c8-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="bb0c8-157">PA-T100</span></span>|<span data-ttu-id="bb0c8-158">…</span><span class="sxs-lookup"><span data-stu-id="bb0c8-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="bb0c8-159">Object</span><span class="sxs-lookup"><span data-stu-id="bb0c8-159">Object</span></span>  
 <span data-ttu-id="bb0c8-160">Le [constructeur de type nommé](named-type-constructor-entity-sql.md) construit (nommé) des objets définis par l’utilisateur, tels que `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="bb0c8-161">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="bb0c8-162">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-162">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-163">SalesOrderDetailID</span></span>|<span data-ttu-id="bb0c8-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="bb0c8-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="bb0c8-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="bb0c8-165">OrderQty</span></span>|<span data-ttu-id="bb0c8-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-166">ProductID</span></span>|<span data-ttu-id="bb0c8-167">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="bb0c8-168">1</span><span class="sxs-lookup"><span data-stu-id="bb0c8-168">1</span></span>|<span data-ttu-id="bb0c8-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="bb0c8-169">4911-403C-98</span></span>|<span data-ttu-id="bb0c8-170">1</span><span class="sxs-lookup"><span data-stu-id="bb0c8-170">1</span></span>|<span data-ttu-id="bb0c8-171">776</span><span class="sxs-lookup"><span data-stu-id="bb0c8-171">776</span></span>|<span data-ttu-id="bb0c8-172">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-172">...</span></span>|  
|<span data-ttu-id="bb0c8-173">2</span><span class="sxs-lookup"><span data-stu-id="bb0c8-173">2</span></span>|<span data-ttu-id="bb0c8-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="bb0c8-174">4911-403C-98</span></span>|<span data-ttu-id="bb0c8-175">3</span><span class="sxs-lookup"><span data-stu-id="bb0c8-175">3</span></span>|<span data-ttu-id="bb0c8-176">777</span><span class="sxs-lookup"><span data-stu-id="bb0c8-176">777</span></span>|<span data-ttu-id="bb0c8-177">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-177">...</span></span>|  
|<span data-ttu-id="bb0c8-178">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-178">...</span></span>|<span data-ttu-id="bb0c8-179">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-179">...</span></span>|<span data-ttu-id="bb0c8-180">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-180">...</span></span>|<span data-ttu-id="bb0c8-181">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-181">...</span></span>|<span data-ttu-id="bb0c8-182">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="bb0c8-183">Références</span><span class="sxs-lookup"><span data-stu-id="bb0c8-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="bb0c8-184">REF</span><span class="sxs-lookup"><span data-stu-id="bb0c8-184">REF</span></span>  
 <span data-ttu-id="bb0c8-185">[Ref](ref-entity-sql.md) crée une référence à une instance de type d’entité.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="bb0c8-186">Par exemple, la requête suivante retourne les références à chaque entité Order dans le jeu d'entités Orders :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="bb0c8-187">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-187">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-188">Valeur</span><span class="sxs-lookup"><span data-stu-id="bb0c8-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-189">1</span><span class="sxs-lookup"><span data-stu-id="bb0c8-189">1</span></span>|  
|<span data-ttu-id="bb0c8-190">2</span><span class="sxs-lookup"><span data-stu-id="bb0c8-190">2</span></span>|  
|<span data-ttu-id="bb0c8-191">3</span><span class="sxs-lookup"><span data-stu-id="bb0c8-191">3</span></span>|  
|<span data-ttu-id="bb0c8-192">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-192">...</span></span>|  
  
 <span data-ttu-id="bb0c8-193">L'exemple suivant utilise l'opérateur d'extraction de propriété (.) pour accéder à une propriété d'entité.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="bb0c8-194">Lors de l'utilisation de l'opérateur d'extraction de propriété, la référence est automatiquement supprimée.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="bb0c8-195">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="bb0c8-196">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-196">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-197">`Value`</span><span class="sxs-lookup"><span data-stu-id="bb0c8-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="bb0c8-198">Adjustable Race</span></span>|  
|<span data-ttu-id="bb0c8-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="bb0c8-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bb0c8-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="bb0c8-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bb0c8-201">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="bb0c8-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="bb0c8-202">DEREF</span></span>  
 <span data-ttu-id="bb0c8-203">[Deref](deref-entity-sql.md) déréférence une valeur de référence et génère le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="bb0c8-204">Par exemple, la requête suivante génère les entités Order pour chaque élément Order du jeu d'entités Orders : `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="bb0c8-205">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="bb0c8-206">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-206">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-207">`Value`</span><span class="sxs-lookup"><span data-stu-id="bb0c8-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="bb0c8-208">Adjustable Race</span></span>|  
|<span data-ttu-id="bb0c8-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="bb0c8-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bb0c8-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="bb0c8-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bb0c8-211">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="bb0c8-212">CREATEREF et KEY</span><span class="sxs-lookup"><span data-stu-id="bb0c8-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="bb0c8-213">[CREATEREF](createref-entity-sql.md) crée une référence qui transmet une clé.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="bb0c8-214">La [clé](key-entity-sql.md) extrait la partie clé d’une expression avec une référence de type.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="bb0c8-215">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="bb0c8-216">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-216">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="bb0c8-218">980</span><span class="sxs-lookup"><span data-stu-id="bb0c8-218">980</span></span>|  
|<span data-ttu-id="bb0c8-219">365</span><span class="sxs-lookup"><span data-stu-id="bb0c8-219">365</span></span>|  
|<span data-ttu-id="bb0c8-220">771</span><span class="sxs-lookup"><span data-stu-id="bb0c8-220">771</span></span>|  
|<span data-ttu-id="bb0c8-221">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="bb0c8-222">Fonctions</span><span class="sxs-lookup"><span data-stu-id="bb0c8-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="bb0c8-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="bb0c8-223">Canonical</span></span>  
 <span data-ttu-id="bb0c8-224">L’espace de noms des [fonctions canoniques](canonical-functions.md) est EDM, comme dans `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="bb0c8-225">Vous n'avez pas besoin de spécifier l'espace de noms sauf si un autre espace de noms est importé et qu'il contient une fonction portant le même nom qu'une fonction canonique.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="bb0c8-226">Si deux espaces de noms partagent la même fonction, l'utilisateur doit spécifier le nom complet.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="bb0c8-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="bb0c8-228">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-228">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="bb0c8-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="bb0c8-230">6\.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-230">6</span></span>|  
|<span data-ttu-id="bb0c8-231">6\.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-231">6</span></span>|  
|<span data-ttu-id="bb0c8-232">5\.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="bb0c8-233">Spécifiques au fournisseur Microsoft</span><span class="sxs-lookup"><span data-stu-id="bb0c8-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="bb0c8-234">Les [fonctions spécifiques au fournisseur Microsoft](../sqlclient-for-ef-functions.md) se trouvent dans l’espace de noms `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="bb0c8-235">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="bb0c8-236">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-236">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="bb0c8-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="bb0c8-238">27</span><span class="sxs-lookup"><span data-stu-id="bb0c8-238">27</span></span>|  
|<span data-ttu-id="bb0c8-239">27</span><span class="sxs-lookup"><span data-stu-id="bb0c8-239">27</span></span>|  
|<span data-ttu-id="bb0c8-240">26</span><span class="sxs-lookup"><span data-stu-id="bb0c8-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="bb0c8-241">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="bb0c8-241">Namespaces</span></span>  
 <span data-ttu-id="bb0c8-242">[L’utilisation](using-entity-sql.md) de spécifie les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="bb0c8-243">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="bb0c8-244">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-244">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-245">`Value`</span><span class="sxs-lookup"><span data-stu-id="bb0c8-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-246">aa</span><span class="sxs-lookup"><span data-stu-id="bb0c8-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="bb0c8-247">Pagination</span><span class="sxs-lookup"><span data-stu-id="bb0c8-247">Paging</span></span>  
 <span data-ttu-id="bb0c8-248">La pagination peut être exprimée en déclarant une sous-clause [Skip](skip-entity-sql.md) et [Limit](limit-entity-sql.md) à la clause [order by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="bb0c8-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="bb0c8-249">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="bb0c8-250">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-250">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-251">ID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-251">ID</span></span>|<span data-ttu-id="bb0c8-252">Nom</span><span class="sxs-lookup"><span data-stu-id="bb0c8-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="bb0c8-253">10</span><span class="sxs-lookup"><span data-stu-id="bb0c8-253">10</span></span>|<span data-ttu-id="bb0c8-254">Adina</span><span class="sxs-lookup"><span data-stu-id="bb0c8-254">Adina</span></span>|  
|<span data-ttu-id="bb0c8-255">11</span><span class="sxs-lookup"><span data-stu-id="bb0c8-255">11</span></span>|<span data-ttu-id="bb0c8-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="bb0c8-256">Agcaoili</span></span>|  
|<span data-ttu-id="bb0c8-257">12</span><span class="sxs-lookup"><span data-stu-id="bb0c8-257">12</span></span>|<span data-ttu-id="bb0c8-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="bb0c8-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="bb0c8-259">Regroupement</span><span class="sxs-lookup"><span data-stu-id="bb0c8-259">Grouping</span></span>  
 <span data-ttu-id="bb0c8-260">[Regroupement par](group-by-entity-sql.md) spécifie les groupes dans lesquels les objets retournés par une expression de requête ([Select](select-entity-sql.md)) doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="bb0c8-261">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="bb0c8-262">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-262">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-263">name</span><span class="sxs-lookup"><span data-stu-id="bb0c8-263">name</span></span>|  
|----------|  
|<span data-ttu-id="bb0c8-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="bb0c8-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="bb0c8-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="bb0c8-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="bb0c8-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="bb0c8-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="bb0c8-267">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="bb0c8-268">Navigation</span><span class="sxs-lookup"><span data-stu-id="bb0c8-268">Navigation</span></span>  
 <span data-ttu-id="bb0c8-269">L'opérateur de navigation de relations vous permet de parcourir la relation entre une entité (terminaison From) et une autre entité (terminaison To).</span><span class="sxs-lookup"><span data-stu-id="bb0c8-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="bb0c8-270">[Naviguer](navigate-entity-sql.md) prend le type de relation qualifié comme \<namespace >. \<relationship nom de type >.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="bb0c8-271">Navigate retourne\<Ref T > si la cardinalité de la terminaison to est 1.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="bb0c8-272">Si la cardinalité de la terminaison to est n, la collection < Ref\<T > > sera retourné.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="bb0c8-273">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="bb0c8-274">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-274">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="bb0c8-276">1</span><span class="sxs-lookup"><span data-stu-id="bb0c8-276">1</span></span>|  
|<span data-ttu-id="bb0c8-277">2</span><span class="sxs-lookup"><span data-stu-id="bb0c8-277">2</span></span>|  
|<span data-ttu-id="bb0c8-278">3</span><span class="sxs-lookup"><span data-stu-id="bb0c8-278">3</span></span>|  
|<span data-ttu-id="bb0c8-279">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="bb0c8-280">SELECT VALUE et SELECT</span><span class="sxs-lookup"><span data-stu-id="bb0c8-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="bb0c8-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="bb0c8-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="bb0c8-282">fournit la clause SELECT VALUE pour ignorer la construction de ligne implicite.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="bb0c8-283">Un seul élément peut être spécifié dans une clause SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="bb0c8-284">Lorsqu’une telle clause est utilisée, aucun Wrapper de ligne n’est construit autour des éléments de la clause SELECT, et une collection de la forme souhaitée peut être produite, par `SELECT VALUE a`exemple :.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="bb0c8-285">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="bb0c8-286">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-286">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-287">Nom</span><span class="sxs-lookup"><span data-stu-id="bb0c8-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="bb0c8-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="bb0c8-288">Adjustable Race</span></span>|  
|<span data-ttu-id="bb0c8-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="bb0c8-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bb0c8-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="bb0c8-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bb0c8-291">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="bb0c8-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="bb0c8-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="bb0c8-293">fournit également le constructeur de ligne pour construire des lignes arbitraires.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="bb0c8-294">SELECT extrait un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, par exemple : `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="bb0c8-295">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-295">Example:</span></span>  
  
 <span data-ttu-id="bb0c8-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="bb0c8-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="bb0c8-297">Name</span><span class="sxs-lookup"><span data-stu-id="bb0c8-297">Name</span></span>|<span data-ttu-id="bb0c8-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="bb0c8-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="bb0c8-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="bb0c8-299">Adjustable Race</span></span>|<span data-ttu-id="bb0c8-300">1</span><span class="sxs-lookup"><span data-stu-id="bb0c8-300">1</span></span>|  
|<span data-ttu-id="bb0c8-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="bb0c8-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="bb0c8-302">879</span><span class="sxs-lookup"><span data-stu-id="bb0c8-302">879</span></span>|  
|<span data-ttu-id="bb0c8-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="bb0c8-303">AWC Logo Cap</span></span>|<span data-ttu-id="bb0c8-304">712</span><span class="sxs-lookup"><span data-stu-id="bb0c8-304">712</span></span>|  
|<span data-ttu-id="bb0c8-305">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-305">...</span></span>|<span data-ttu-id="bb0c8-306">...</span><span class="sxs-lookup"><span data-stu-id="bb0c8-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="bb0c8-307">Expression CASE</span><span class="sxs-lookup"><span data-stu-id="bb0c8-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="bb0c8-308">L' [expression case](case-entity-sql.md) évalue un jeu d’expressions booléennes pour déterminer le résultat.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="bb0c8-309">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="bb0c8-310">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bb0c8-310">Output:</span></span>  
  
|<span data-ttu-id="bb0c8-311">`Value`</span><span class="sxs-lookup"><span data-stu-id="bb0c8-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bb0c8-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="bb0c8-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb0c8-313">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb0c8-313">See also</span></span>

- [<span data-ttu-id="bb0c8-314">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bb0c8-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="bb0c8-315">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bb0c8-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
