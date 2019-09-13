---
title: Aide-mémoire Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7780359d981b130118cb73d4892f3dcb4b6e2e7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251025"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="84fd4-102">Aide-mémoire Entity SQL</span><span class="sxs-lookup"><span data-stu-id="84fd4-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="84fd4-103">Cette rubrique fournit un aide-mémoire sur les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84fd4-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="84fd4-104">Les requêtes de cette rubrique sont basées sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="84fd4-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="84fd4-105">Littéraux</span><span class="sxs-lookup"><span data-stu-id="84fd4-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="84fd4-106">String</span><span class="sxs-lookup"><span data-stu-id="84fd4-106">String</span></span>  
 <span data-ttu-id="84fd4-107">Les chaînes de caractères littérales peuvent être au format Unicode ou non-Unicode.</span><span class="sxs-lookup"><span data-stu-id="84fd4-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="84fd4-108">Les chaînes Unicode sont précédées de N. Par exemple, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="84fd4-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="84fd4-109">Exemple de littéral de chaîne non-Unicode :</span><span class="sxs-lookup"><span data-stu-id="84fd4-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="84fd4-110">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-110">Output:</span></span>  
  
|<span data-ttu-id="84fd4-111">`Value`</span><span class="sxs-lookup"><span data-stu-id="84fd4-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-112">hello</span><span class="sxs-lookup"><span data-stu-id="84fd4-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="84fd4-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="84fd4-113">DateTime</span></span>  
 <span data-ttu-id="84fd4-114">Dans les littéraux DateTime, les parties date et heure sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="84fd4-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="84fd4-115">Il n'existe pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="84fd4-115">There are no default values.</span></span>  
  
 <span data-ttu-id="84fd4-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="84fd4-117">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-117">Output:</span></span>  
  
|<span data-ttu-id="84fd4-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="84fd4-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="84fd4-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="84fd4-120">Entier</span><span class="sxs-lookup"><span data-stu-id="84fd4-120">Integer</span></span>  
 <span data-ttu-id="84fd4-121">Les littéraux d'entiers peuvent être de type Int32 (123), UInt32 (123U), Int64 (123L) et UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="84fd4-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="84fd4-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="84fd4-123">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-123">Output:</span></span>  
  
|<span data-ttu-id="84fd4-124">Valeur</span><span class="sxs-lookup"><span data-stu-id="84fd4-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-125">1</span><span class="sxs-lookup"><span data-stu-id="84fd4-125">1</span></span>|  
|<span data-ttu-id="84fd4-126">2</span><span class="sxs-lookup"><span data-stu-id="84fd4-126">2</span></span>|  
|<span data-ttu-id="84fd4-127">3</span><span class="sxs-lookup"><span data-stu-id="84fd4-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="84fd4-128">Autre</span><span class="sxs-lookup"><span data-stu-id="84fd4-128">Other</span></span>  
 <span data-ttu-id="84fd4-129">Les autres littéraux pris en charge par [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont Guid, Binary, Float/Double, Decimal et la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="84fd4-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="84fd4-130">Les littéraux NULL dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont considérés compatibles avec tous les autres types dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="84fd4-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="84fd4-131">Constructeurs de type</span><span class="sxs-lookup"><span data-stu-id="84fd4-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="84fd4-132">ROW</span><span class="sxs-lookup"><span data-stu-id="84fd4-132">ROW</span></span>  
 <span data-ttu-id="84fd4-133">La fonction [Row](row-entity-sql.md) construit une valeur anonyme, structurellement typée (enregistrement) comme dans :`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="84fd4-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="84fd4-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="84fd4-135">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-135">Output:</span></span>  
  
|<span data-ttu-id="84fd4-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="84fd4-136">ProductID</span></span>|<span data-ttu-id="84fd4-137">Nom</span><span class="sxs-lookup"><span data-stu-id="84fd4-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="84fd4-138">1</span><span class="sxs-lookup"><span data-stu-id="84fd4-138">1</span></span>|<span data-ttu-id="84fd4-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="84fd4-139">Adjustable Race</span></span>|  
|<span data-ttu-id="84fd4-140">879</span><span class="sxs-lookup"><span data-stu-id="84fd4-140">879</span></span>|<span data-ttu-id="84fd4-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="84fd4-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="84fd4-142">712</span><span class="sxs-lookup"><span data-stu-id="84fd4-142">712</span></span>|<span data-ttu-id="84fd4-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="84fd4-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="84fd4-144">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-144">...</span></span>|<span data-ttu-id="84fd4-145">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="84fd4-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="84fd4-146">MULTISET</span></span>  
 <span data-ttu-id="84fd4-147">Les collections de [multiensembles](multiset-entity-sql.md), telles que :</span><span class="sxs-lookup"><span data-stu-id="84fd4-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="84fd4-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="84fd4-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="84fd4-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="84fd4-150">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-150">Output:</span></span>  
  
|<span data-ttu-id="84fd4-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="84fd4-151">ProductID</span></span>|<span data-ttu-id="84fd4-152">Nom</span><span class="sxs-lookup"><span data-stu-id="84fd4-152">Name</span></span>|<span data-ttu-id="84fd4-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="84fd4-153">ProductNumber</span></span>|<span data-ttu-id="84fd4-154">…</span><span class="sxs-lookup"><span data-stu-id="84fd4-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="84fd4-155">842</span><span class="sxs-lookup"><span data-stu-id="84fd4-155">842</span></span>|<span data-ttu-id="84fd4-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="84fd4-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="84fd4-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="84fd4-157">PA-T100</span></span>|<span data-ttu-id="84fd4-158">…</span><span class="sxs-lookup"><span data-stu-id="84fd4-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="84fd4-159">Object</span><span class="sxs-lookup"><span data-stu-id="84fd4-159">Object</span></span>  
 <span data-ttu-id="84fd4-160">Le [constructeur de type nommé](named-type-constructor-entity-sql.md) construit (nommé) des objets définis par l’utilisateur `person("abc", 12)`, tels que.</span><span class="sxs-lookup"><span data-stu-id="84fd4-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="84fd4-161">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="84fd4-162">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-162">Output:</span></span>  
  
|<span data-ttu-id="84fd4-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="84fd4-163">SalesOrderDetailID</span></span>|<span data-ttu-id="84fd4-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="84fd4-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="84fd4-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="84fd4-165">OrderQty</span></span>|<span data-ttu-id="84fd4-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="84fd4-166">ProductID</span></span>|<span data-ttu-id="84fd4-167">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="84fd4-168">1</span><span class="sxs-lookup"><span data-stu-id="84fd4-168">1</span></span>|<span data-ttu-id="84fd4-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="84fd4-169">4911-403C-98</span></span>|<span data-ttu-id="84fd4-170">1</span><span class="sxs-lookup"><span data-stu-id="84fd4-170">1</span></span>|<span data-ttu-id="84fd4-171">776</span><span class="sxs-lookup"><span data-stu-id="84fd4-171">776</span></span>|<span data-ttu-id="84fd4-172">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-172">...</span></span>|  
|<span data-ttu-id="84fd4-173">2</span><span class="sxs-lookup"><span data-stu-id="84fd4-173">2</span></span>|<span data-ttu-id="84fd4-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="84fd4-174">4911-403C-98</span></span>|<span data-ttu-id="84fd4-175">3</span><span class="sxs-lookup"><span data-stu-id="84fd4-175">3</span></span>|<span data-ttu-id="84fd4-176">777</span><span class="sxs-lookup"><span data-stu-id="84fd4-176">777</span></span>|<span data-ttu-id="84fd4-177">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-177">...</span></span>|  
|<span data-ttu-id="84fd4-178">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-178">...</span></span>|<span data-ttu-id="84fd4-179">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-179">...</span></span>|<span data-ttu-id="84fd4-180">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-180">...</span></span>|<span data-ttu-id="84fd4-181">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-181">...</span></span>|<span data-ttu-id="84fd4-182">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="84fd4-183">Références</span><span class="sxs-lookup"><span data-stu-id="84fd4-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="84fd4-184">REF</span><span class="sxs-lookup"><span data-stu-id="84fd4-184">REF</span></span>  
 <span data-ttu-id="84fd4-185">[Ref](ref-entity-sql.md) crée une référence à une instance de type d’entité.</span><span class="sxs-lookup"><span data-stu-id="84fd4-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="84fd4-186">Par exemple, la requête suivante retourne les références à chaque entité Order dans le jeu d'entités Orders :</span><span class="sxs-lookup"><span data-stu-id="84fd4-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="84fd4-187">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-187">Output:</span></span>  
  
|<span data-ttu-id="84fd4-188">Valeur</span><span class="sxs-lookup"><span data-stu-id="84fd4-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-189">1</span><span class="sxs-lookup"><span data-stu-id="84fd4-189">1</span></span>|  
|<span data-ttu-id="84fd4-190">2</span><span class="sxs-lookup"><span data-stu-id="84fd4-190">2</span></span>|  
|<span data-ttu-id="84fd4-191">3</span><span class="sxs-lookup"><span data-stu-id="84fd4-191">3</span></span>|  
|<span data-ttu-id="84fd4-192">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-192">...</span></span>|  
  
 <span data-ttu-id="84fd4-193">L'exemple suivant utilise l'opérateur d'extraction de propriété (.) pour accéder à une propriété d'entité.</span><span class="sxs-lookup"><span data-stu-id="84fd4-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="84fd4-194">Lors de l'utilisation de l'opérateur d'extraction de propriété, la référence est automatiquement supprimée.</span><span class="sxs-lookup"><span data-stu-id="84fd4-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="84fd4-195">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="84fd4-196">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-196">Output:</span></span>  
  
|<span data-ttu-id="84fd4-197">Valeur</span><span class="sxs-lookup"><span data-stu-id="84fd4-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="84fd4-198">Adjustable Race</span></span>|  
|<span data-ttu-id="84fd4-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="84fd4-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="84fd4-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="84fd4-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="84fd4-201">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="84fd4-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="84fd4-202">DEREF</span></span>  
 <span data-ttu-id="84fd4-203">[Deref](deref-entity-sql.md) déréférence une valeur de référence et génère le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="84fd4-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="84fd4-204">Par exemple, la requête suivante génère les entités Order pour chaque élément Order du jeu d'entités Orders : `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="84fd4-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="84fd4-205">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="84fd4-206">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-206">Output:</span></span>  
  
|<span data-ttu-id="84fd4-207">`Value`</span><span class="sxs-lookup"><span data-stu-id="84fd4-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="84fd4-208">Adjustable Race</span></span>|  
|<span data-ttu-id="84fd4-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="84fd4-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="84fd4-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="84fd4-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="84fd4-211">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="84fd4-212">CREATEREF et KEY</span><span class="sxs-lookup"><span data-stu-id="84fd4-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="84fd4-213">[CREATEREF](createref-entity-sql.md) crée une référence qui transmet une clé.</span><span class="sxs-lookup"><span data-stu-id="84fd4-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="84fd4-214">La [clé](key-entity-sql.md) extrait la partie clé d’une expression avec une référence de type.</span><span class="sxs-lookup"><span data-stu-id="84fd4-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="84fd4-215">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="84fd4-216">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-216">Output:</span></span>  
  
|<span data-ttu-id="84fd4-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="84fd4-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="84fd4-218">980</span><span class="sxs-lookup"><span data-stu-id="84fd4-218">980</span></span>|  
|<span data-ttu-id="84fd4-219">365</span><span class="sxs-lookup"><span data-stu-id="84fd4-219">365</span></span>|  
|<span data-ttu-id="84fd4-220">771</span><span class="sxs-lookup"><span data-stu-id="84fd4-220">771</span></span>|  
|<span data-ttu-id="84fd4-221">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="84fd4-222">Fonctions</span><span class="sxs-lookup"><span data-stu-id="84fd4-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="84fd4-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="84fd4-223">Canonical</span></span>  
 <span data-ttu-id="84fd4-224">L’espace de noms des [fonctions canoniques](canonical-functions.md) est EDM `Edm.Length("string")`, comme dans.</span><span class="sxs-lookup"><span data-stu-id="84fd4-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="84fd4-225">Vous n'avez pas besoin de spécifier l'espace de noms sauf si un autre espace de noms est importé et qu'il contient une fonction portant le même nom qu'une fonction canonique.</span><span class="sxs-lookup"><span data-stu-id="84fd4-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="84fd4-226">Si deux espaces de noms partagent la même fonction, l'utilisateur doit spécifier le nom complet.</span><span class="sxs-lookup"><span data-stu-id="84fd4-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="84fd4-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="84fd4-228">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-228">Output:</span></span>  
  
|<span data-ttu-id="84fd4-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="84fd4-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="84fd4-230">6\.</span><span class="sxs-lookup"><span data-stu-id="84fd4-230">6</span></span>|  
|<span data-ttu-id="84fd4-231">6\.</span><span class="sxs-lookup"><span data-stu-id="84fd4-231">6</span></span>|  
|<span data-ttu-id="84fd4-232">5\.</span><span class="sxs-lookup"><span data-stu-id="84fd4-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="84fd4-233">Spécifiques au fournisseur Microsoft</span><span class="sxs-lookup"><span data-stu-id="84fd4-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="84fd4-234">Les [fonctions spécifiques au fournisseur Microsoft](../sqlclient-for-ef-functions.md) se trouvent `SqlServer` dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="84fd4-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="84fd4-235">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="84fd4-236">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-236">Output:</span></span>  
  
|<span data-ttu-id="84fd4-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="84fd4-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="84fd4-238">27</span><span class="sxs-lookup"><span data-stu-id="84fd4-238">27</span></span>|  
|<span data-ttu-id="84fd4-239">27</span><span class="sxs-lookup"><span data-stu-id="84fd4-239">27</span></span>|  
|<span data-ttu-id="84fd4-240">26</span><span class="sxs-lookup"><span data-stu-id="84fd4-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="84fd4-241">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="84fd4-241">Namespaces</span></span>  
 <span data-ttu-id="84fd4-242">[L’utilisation](using-entity-sql.md) de spécifie les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="84fd4-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="84fd4-243">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="84fd4-244">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-244">Output:</span></span>  
  
|<span data-ttu-id="84fd4-245">`Value`</span><span class="sxs-lookup"><span data-stu-id="84fd4-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-246">aa</span><span class="sxs-lookup"><span data-stu-id="84fd4-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="84fd4-247">Pagination</span><span class="sxs-lookup"><span data-stu-id="84fd4-247">Paging</span></span>  
 <span data-ttu-id="84fd4-248">La pagination peut être exprimée en déclarant une sous-clause [Skip](skip-entity-sql.md) et [Limit](limit-entity-sql.md) à la clause [order by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="84fd4-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="84fd4-249">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="84fd4-250">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-250">Output:</span></span>  
  
|<span data-ttu-id="84fd4-251">ID</span><span class="sxs-lookup"><span data-stu-id="84fd4-251">ID</span></span>|<span data-ttu-id="84fd4-252">Nom</span><span class="sxs-lookup"><span data-stu-id="84fd4-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="84fd4-253">10</span><span class="sxs-lookup"><span data-stu-id="84fd4-253">10</span></span>|<span data-ttu-id="84fd4-254">Adina</span><span class="sxs-lookup"><span data-stu-id="84fd4-254">Adina</span></span>|  
|<span data-ttu-id="84fd4-255">11</span><span class="sxs-lookup"><span data-stu-id="84fd4-255">11</span></span>|<span data-ttu-id="84fd4-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="84fd4-256">Agcaoili</span></span>|  
|<span data-ttu-id="84fd4-257">12</span><span class="sxs-lookup"><span data-stu-id="84fd4-257">12</span></span>|<span data-ttu-id="84fd4-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="84fd4-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="84fd4-259">Regroupement</span><span class="sxs-lookup"><span data-stu-id="84fd4-259">Grouping</span></span>  
 <span data-ttu-id="84fd4-260">[Regroupement par](group-by-entity-sql.md) spécifie les groupes dans lesquels les objets retournés par une expression de requête ([Select](select-entity-sql.md)) doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="84fd4-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="84fd4-261">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="84fd4-262">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-262">Output:</span></span>  
  
|<span data-ttu-id="84fd4-263">name</span><span class="sxs-lookup"><span data-stu-id="84fd4-263">name</span></span>|  
|----------|  
|<span data-ttu-id="84fd4-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="84fd4-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="84fd4-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="84fd4-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="84fd4-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="84fd4-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="84fd4-267">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="84fd4-268">Navigation</span><span class="sxs-lookup"><span data-stu-id="84fd4-268">Navigation</span></span>  
 <span data-ttu-id="84fd4-269">L'opérateur de navigation de relations vous permet de parcourir la relation entre une entité (terminaison From) et une autre entité (terminaison To).</span><span class="sxs-lookup"><span data-stu-id="84fd4-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="84fd4-270">[Naviguer](navigate-entity-sql.md) prend le type de relation qualifié \<en tant qu'\< espace de noms >. nom du type de relation >.</span><span class="sxs-lookup"><span data-stu-id="84fd4-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="84fd4-271">Navigate retourne\<Ref T > si la cardinalité de la terminaison to est 1.</span><span class="sxs-lookup"><span data-stu-id="84fd4-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="84fd4-272">Si la cardinalité de la terminaison to est n, la collection < Ref\<T > > sera retourné.</span><span class="sxs-lookup"><span data-stu-id="84fd4-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="84fd4-273">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="84fd4-274">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-274">Output:</span></span>  
  
|<span data-ttu-id="84fd4-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="84fd4-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="84fd4-276">1</span><span class="sxs-lookup"><span data-stu-id="84fd4-276">1</span></span>|  
|<span data-ttu-id="84fd4-277">2</span><span class="sxs-lookup"><span data-stu-id="84fd4-277">2</span></span>|  
|<span data-ttu-id="84fd4-278">3</span><span class="sxs-lookup"><span data-stu-id="84fd4-278">3</span></span>|  
|<span data-ttu-id="84fd4-279">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="84fd4-280">SELECT VALUE et SELECT</span><span class="sxs-lookup"><span data-stu-id="84fd4-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="84fd4-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="84fd4-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="84fd4-282">fournit la clause SELECT VALUE pour ignorer la construction de ligne implicite.</span><span class="sxs-lookup"><span data-stu-id="84fd4-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="84fd4-283">Un seul élément peut être spécifié dans une clause SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="84fd4-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="84fd4-284">Lorsqu’une telle clause est utilisée, aucun Wrapper de ligne n’est construit autour des éléments de la clause SELECT, et une collection de la forme souhaitée peut être produite, par `SELECT VALUE a`exemple :.</span><span class="sxs-lookup"><span data-stu-id="84fd4-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="84fd4-285">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="84fd4-286">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-286">Output:</span></span>  
  
|<span data-ttu-id="84fd4-287">Nom</span><span class="sxs-lookup"><span data-stu-id="84fd4-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="84fd4-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="84fd4-288">Adjustable Race</span></span>|  
|<span data-ttu-id="84fd4-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="84fd4-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="84fd4-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="84fd4-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="84fd4-291">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="84fd4-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="84fd4-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="84fd4-293">fournit également le constructeur de ligne pour construire des lignes arbitraires.</span><span class="sxs-lookup"><span data-stu-id="84fd4-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="84fd4-294">SELECT extrait un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, par exemple : `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="84fd4-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="84fd4-295">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-295">Example:</span></span>  
  
 <span data-ttu-id="84fd4-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="84fd4-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="84fd4-297">Name</span><span class="sxs-lookup"><span data-stu-id="84fd4-297">Name</span></span>|<span data-ttu-id="84fd4-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="84fd4-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="84fd4-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="84fd4-299">Adjustable Race</span></span>|<span data-ttu-id="84fd4-300">1</span><span class="sxs-lookup"><span data-stu-id="84fd4-300">1</span></span>|  
|<span data-ttu-id="84fd4-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="84fd4-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="84fd4-302">879</span><span class="sxs-lookup"><span data-stu-id="84fd4-302">879</span></span>|  
|<span data-ttu-id="84fd4-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="84fd4-303">AWC Logo Cap</span></span>|<span data-ttu-id="84fd4-304">712</span><span class="sxs-lookup"><span data-stu-id="84fd4-304">712</span></span>|  
|<span data-ttu-id="84fd4-305">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-305">...</span></span>|<span data-ttu-id="84fd4-306">...</span><span class="sxs-lookup"><span data-stu-id="84fd4-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="84fd4-307">Expression CASE</span><span class="sxs-lookup"><span data-stu-id="84fd4-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="84fd4-308">L' [expression case](case-entity-sql.md) évalue un jeu d’expressions booléennes pour déterminer le résultat.</span><span class="sxs-lookup"><span data-stu-id="84fd4-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="84fd4-309">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84fd4-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="84fd4-310">Sortie :</span><span class="sxs-lookup"><span data-stu-id="84fd4-310">Output:</span></span>  
  
|<span data-ttu-id="84fd4-311">`Value`</span><span class="sxs-lookup"><span data-stu-id="84fd4-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="84fd4-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="84fd4-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84fd4-313">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84fd4-313">See also</span></span>

- [<span data-ttu-id="84fd4-314">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="84fd4-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="84fd4-315">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="84fd4-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
