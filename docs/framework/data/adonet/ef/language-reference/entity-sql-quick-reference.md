---
title: Aide-mémoire Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7ec3b6fc184b4f169d6f6489bda0ec8fa4abb4f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148138"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="8d333-102">Aide-mémoire Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8d333-102">Entity SQL Quick Reference</span></span>

<span data-ttu-id="8d333-103">Cette rubrique fournit un aide-mémoire sur les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d333-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="8d333-104">Les requêtes de cette rubrique sont basées sur le modèle de vente Adventure Works Sales Model.</span><span class="sxs-lookup"><span data-stu-id="8d333-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="8d333-105">Littéraux</span><span class="sxs-lookup"><span data-stu-id="8d333-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="8d333-106">String</span><span class="sxs-lookup"><span data-stu-id="8d333-106">String</span></span>  

 <span data-ttu-id="8d333-107">Les chaînes de caractères littérales peuvent être au format Unicode ou non-Unicode.</span><span class="sxs-lookup"><span data-stu-id="8d333-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="8d333-108">Les chaînes Unicode sont précédées de N. Par exemple, `N'hello'` .</span><span class="sxs-lookup"><span data-stu-id="8d333-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="8d333-109">Exemple de littéral de chaîne non-Unicode :</span><span class="sxs-lookup"><span data-stu-id="8d333-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="8d333-110">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-110">Output:</span></span>  
  
|<span data-ttu-id="8d333-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-112">hello</span><span class="sxs-lookup"><span data-stu-id="8d333-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="8d333-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="8d333-113">DateTime</span></span>  

 <span data-ttu-id="8d333-114">Dans les littéraux DateTime, les parties date et heure sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="8d333-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="8d333-115">Il n'y a pas de valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="8d333-115">There are no default values.</span></span>  
  
 <span data-ttu-id="8d333-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="8d333-117">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-117">Output:</span></span>  
  
|<span data-ttu-id="8d333-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="8d333-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="8d333-120">Entier</span><span class="sxs-lookup"><span data-stu-id="8d333-120">Integer</span></span>  

 <span data-ttu-id="8d333-121">Les littéraux d'entiers peuvent être de type Int32 (123), UInt32 (123U), Int64 (123L) et UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="8d333-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="8d333-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="8d333-123">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-123">Output:</span></span>  
  
|<span data-ttu-id="8d333-124">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-125">1</span><span class="sxs-lookup"><span data-stu-id="8d333-125">1</span></span>|  
|<span data-ttu-id="8d333-126">2</span><span class="sxs-lookup"><span data-stu-id="8d333-126">2</span></span>|  
|<span data-ttu-id="8d333-127">3</span><span class="sxs-lookup"><span data-stu-id="8d333-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="8d333-128">Autres</span><span class="sxs-lookup"><span data-stu-id="8d333-128">Other</span></span>  

 <span data-ttu-id="8d333-129">Les autres littéraux pris en charge par [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont Guid, Binary, Float/Double, Decimal et la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="8d333-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="8d333-130">Les littéraux NULL dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont considérés compatibles avec tous les autres types dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="8d333-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="8d333-131">Constructeurs de type</span><span class="sxs-lookup"><span data-stu-id="8d333-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="8d333-132">ROW</span><span class="sxs-lookup"><span data-stu-id="8d333-132">ROW</span></span>  

 <span data-ttu-id="8d333-133">La fonction [Row](row-entity-sql.md) construit une valeur anonyme, structurellement typée (enregistrement) comme dans :`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="8d333-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="8d333-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="8d333-135">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-135">Output:</span></span>  
  
|<span data-ttu-id="8d333-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="8d333-136">ProductID</span></span>|<span data-ttu-id="8d333-137">Nom</span><span class="sxs-lookup"><span data-stu-id="8d333-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="8d333-138">1</span><span class="sxs-lookup"><span data-stu-id="8d333-138">1</span></span>|<span data-ttu-id="8d333-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="8d333-139">Adjustable Race</span></span>|  
|<span data-ttu-id="8d333-140">879</span><span class="sxs-lookup"><span data-stu-id="8d333-140">879</span></span>|<span data-ttu-id="8d333-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="8d333-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="8d333-142">712</span><span class="sxs-lookup"><span data-stu-id="8d333-142">712</span></span>|<span data-ttu-id="8d333-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="8d333-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="8d333-144">...</span><span class="sxs-lookup"><span data-stu-id="8d333-144">...</span></span>|<span data-ttu-id="8d333-145">...</span><span class="sxs-lookup"><span data-stu-id="8d333-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="8d333-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="8d333-146">MULTISET</span></span>  

 <span data-ttu-id="8d333-147">[MULTISET](multiset-entity-sql.md) Les collections de multiensembles, telles que :</span><span class="sxs-lookup"><span data-stu-id="8d333-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="8d333-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="8d333-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="8d333-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="8d333-150">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-150">Output:</span></span>  
  
|<span data-ttu-id="8d333-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="8d333-151">ProductID</span></span>|<span data-ttu-id="8d333-152">Nom</span><span class="sxs-lookup"><span data-stu-id="8d333-152">Name</span></span>|<span data-ttu-id="8d333-153">RéférenceProduit</span><span class="sxs-lookup"><span data-stu-id="8d333-153">ProductNumber</span></span>|<span data-ttu-id="8d333-154">…</span><span class="sxs-lookup"><span data-stu-id="8d333-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="8d333-155">842</span><span class="sxs-lookup"><span data-stu-id="8d333-155">842</span></span>|<span data-ttu-id="8d333-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="8d333-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="8d333-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="8d333-157">PA-T100</span></span>|<span data-ttu-id="8d333-158">…</span><span class="sxs-lookup"><span data-stu-id="8d333-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="8d333-159">Object</span><span class="sxs-lookup"><span data-stu-id="8d333-159">Object</span></span>  

 <span data-ttu-id="8d333-160">Le [constructeur de type nommé](named-type-constructor-entity-sql.md) construit (nommé) des objets définis par l’utilisateur, tels que `person("abc", 12)` .</span><span class="sxs-lookup"><span data-stu-id="8d333-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="8d333-161">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="8d333-162">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-162">Output:</span></span>  
  
|<span data-ttu-id="8d333-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="8d333-163">SalesOrderDetailID</span></span>|<span data-ttu-id="8d333-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="8d333-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="8d333-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="8d333-165">OrderQty</span></span>|<span data-ttu-id="8d333-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="8d333-166">ProductID</span></span>|<span data-ttu-id="8d333-167">...</span><span class="sxs-lookup"><span data-stu-id="8d333-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="8d333-168">1</span><span class="sxs-lookup"><span data-stu-id="8d333-168">1</span></span>|<span data-ttu-id="8d333-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="8d333-169">4911-403C-98</span></span>|<span data-ttu-id="8d333-170">1</span><span class="sxs-lookup"><span data-stu-id="8d333-170">1</span></span>|<span data-ttu-id="8d333-171">776</span><span class="sxs-lookup"><span data-stu-id="8d333-171">776</span></span>|<span data-ttu-id="8d333-172">...</span><span class="sxs-lookup"><span data-stu-id="8d333-172">...</span></span>|  
|<span data-ttu-id="8d333-173">2</span><span class="sxs-lookup"><span data-stu-id="8d333-173">2</span></span>|<span data-ttu-id="8d333-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="8d333-174">4911-403C-98</span></span>|<span data-ttu-id="8d333-175">3</span><span class="sxs-lookup"><span data-stu-id="8d333-175">3</span></span>|<span data-ttu-id="8d333-176">777</span><span class="sxs-lookup"><span data-stu-id="8d333-176">777</span></span>|<span data-ttu-id="8d333-177">...</span><span class="sxs-lookup"><span data-stu-id="8d333-177">...</span></span>|  
|<span data-ttu-id="8d333-178">...</span><span class="sxs-lookup"><span data-stu-id="8d333-178">...</span></span>|<span data-ttu-id="8d333-179">...</span><span class="sxs-lookup"><span data-stu-id="8d333-179">...</span></span>|<span data-ttu-id="8d333-180">...</span><span class="sxs-lookup"><span data-stu-id="8d333-180">...</span></span>|<span data-ttu-id="8d333-181">...</span><span class="sxs-lookup"><span data-stu-id="8d333-181">...</span></span>|<span data-ttu-id="8d333-182">...</span><span class="sxs-lookup"><span data-stu-id="8d333-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="8d333-183">Références</span><span class="sxs-lookup"><span data-stu-id="8d333-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="8d333-184">REF</span><span class="sxs-lookup"><span data-stu-id="8d333-184">REF</span></span>  

 <span data-ttu-id="8d333-185">[Ref](ref-entity-sql.md) crée une référence à une instance de type d’entité.</span><span class="sxs-lookup"><span data-stu-id="8d333-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="8d333-186">Par exemple, la requête suivante retourne les références à chaque entité Order dans le jeu d'entités Orders :</span><span class="sxs-lookup"><span data-stu-id="8d333-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="8d333-187">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-187">Output:</span></span>  
  
|<span data-ttu-id="8d333-188">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-189">1</span><span class="sxs-lookup"><span data-stu-id="8d333-189">1</span></span>|  
|<span data-ttu-id="8d333-190">2</span><span class="sxs-lookup"><span data-stu-id="8d333-190">2</span></span>|  
|<span data-ttu-id="8d333-191">3</span><span class="sxs-lookup"><span data-stu-id="8d333-191">3</span></span>|  
|<span data-ttu-id="8d333-192">...</span><span class="sxs-lookup"><span data-stu-id="8d333-192">...</span></span>|  
  
 <span data-ttu-id="8d333-193">L'exemple suivant utilise l'opérateur d'extraction de propriété (.) pour accéder à une propriété d'entité.</span><span class="sxs-lookup"><span data-stu-id="8d333-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="8d333-194">Lors de l'utilisation de l'opérateur d'extraction de propriété, la référence est automatiquement supprimée.</span><span class="sxs-lookup"><span data-stu-id="8d333-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="8d333-195">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="8d333-196">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-196">Output:</span></span>  
  
|<span data-ttu-id="8d333-197">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="8d333-198">Adjustable Race</span></span>|  
|<span data-ttu-id="8d333-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="8d333-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="8d333-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="8d333-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="8d333-201">...</span><span class="sxs-lookup"><span data-stu-id="8d333-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="8d333-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="8d333-202">DEREF</span></span>  

 <span data-ttu-id="8d333-203">[Deref](deref-entity-sql.md) déréférence une valeur de référence et génère le résultat de ce déréférencement.</span><span class="sxs-lookup"><span data-stu-id="8d333-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="8d333-204">Par exemple, la requête suivante génère les entités Order pour chaque élément Order du jeu d'entités Orders : `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="8d333-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="8d333-205">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="8d333-206">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-206">Output:</span></span>  
  
|<span data-ttu-id="8d333-207">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="8d333-208">Adjustable Race</span></span>|  
|<span data-ttu-id="8d333-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="8d333-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="8d333-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="8d333-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="8d333-211">...</span><span class="sxs-lookup"><span data-stu-id="8d333-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="8d333-212">CREATEREF et KEY</span><span class="sxs-lookup"><span data-stu-id="8d333-212">CREATEREF AND KEY</span></span>  

 <span data-ttu-id="8d333-213">[CREATEREF](createref-entity-sql.md) crée une référence qui transmet une clé.</span><span class="sxs-lookup"><span data-stu-id="8d333-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="8d333-214">La [clé](key-entity-sql.md) extrait la partie clé d’une expression avec une référence de type.</span><span class="sxs-lookup"><span data-stu-id="8d333-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="8d333-215">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="8d333-216">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-216">Output:</span></span>  
  
|<span data-ttu-id="8d333-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="8d333-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="8d333-218">980</span><span class="sxs-lookup"><span data-stu-id="8d333-218">980</span></span>|  
|<span data-ttu-id="8d333-219">365</span><span class="sxs-lookup"><span data-stu-id="8d333-219">365</span></span>|  
|<span data-ttu-id="8d333-220">771</span><span class="sxs-lookup"><span data-stu-id="8d333-220">771</span></span>|  
|<span data-ttu-id="8d333-221">...</span><span class="sxs-lookup"><span data-stu-id="8d333-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="8d333-222">Fonctions</span><span class="sxs-lookup"><span data-stu-id="8d333-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="8d333-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="8d333-223">Canonical</span></span>  

 <span data-ttu-id="8d333-224">L’espace de noms des [fonctions canoniques](canonical-functions.md) est EDM, comme dans `Edm.Length("string")` .</span><span class="sxs-lookup"><span data-stu-id="8d333-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="8d333-225">Vous n'avez pas besoin de spécifier l'espace de noms sauf si un autre espace de noms est importé et qu'il contient une fonction portant le même nom qu'une fonction canonique.</span><span class="sxs-lookup"><span data-stu-id="8d333-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="8d333-226">Si deux espaces de noms partagent la même fonction, l'utilisateur doit spécifier le nom complet.</span><span class="sxs-lookup"><span data-stu-id="8d333-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="8d333-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="8d333-228">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-228">Output:</span></span>  
  
|<span data-ttu-id="8d333-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="8d333-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="8d333-230">6</span><span class="sxs-lookup"><span data-stu-id="8d333-230">6</span></span>|  
|<span data-ttu-id="8d333-231">6</span><span class="sxs-lookup"><span data-stu-id="8d333-231">6</span></span>|  
|<span data-ttu-id="8d333-232">5</span><span class="sxs-lookup"><span data-stu-id="8d333-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="8d333-233">Spécifiques au fournisseur Microsoft</span><span class="sxs-lookup"><span data-stu-id="8d333-233">Microsoft Provider-Specific</span></span>  

 <span data-ttu-id="8d333-234">Les [fonctions spécifiques au fournisseur Microsoft](../sqlclient-for-ef-functions.md) se trouvent dans l' `SqlServer` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8d333-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="8d333-235">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="8d333-236">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-236">Output:</span></span>  
  
|<span data-ttu-id="8d333-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="8d333-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="8d333-238">27</span><span class="sxs-lookup"><span data-stu-id="8d333-238">27</span></span>|  
|<span data-ttu-id="8d333-239">27</span><span class="sxs-lookup"><span data-stu-id="8d333-239">27</span></span>|  
|<span data-ttu-id="8d333-240">26</span><span class="sxs-lookup"><span data-stu-id="8d333-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="8d333-241">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="8d333-241">Namespaces</span></span>  

 <span data-ttu-id="8d333-242">[L’utilisation](using-entity-sql.md) de spécifie les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="8d333-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="8d333-243">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="8d333-244">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-244">Output:</span></span>  
  
|<span data-ttu-id="8d333-245">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-246">aa</span><span class="sxs-lookup"><span data-stu-id="8d333-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="8d333-247">Pagination</span><span class="sxs-lookup"><span data-stu-id="8d333-247">Paging</span></span>  

 <span data-ttu-id="8d333-248">La pagination peut être exprimée en déclarant une sous-clause [Skip](skip-entity-sql.md) et [Limit](limit-entity-sql.md) à la clause [order by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="8d333-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="8d333-249">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="8d333-250">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-250">Output:</span></span>  
  
|<span data-ttu-id="8d333-251">id</span><span class="sxs-lookup"><span data-stu-id="8d333-251">ID</span></span>|<span data-ttu-id="8d333-252">Nom</span><span class="sxs-lookup"><span data-stu-id="8d333-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="8d333-253">10</span><span class="sxs-lookup"><span data-stu-id="8d333-253">10</span></span>|<span data-ttu-id="8d333-254">Adina</span><span class="sxs-lookup"><span data-stu-id="8d333-254">Adina</span></span>|  
|<span data-ttu-id="8d333-255">11</span><span class="sxs-lookup"><span data-stu-id="8d333-255">11</span></span>|<span data-ttu-id="8d333-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="8d333-256">Agcaoili</span></span>|  
|<span data-ttu-id="8d333-257">12</span><span class="sxs-lookup"><span data-stu-id="8d333-257">12</span></span>|<span data-ttu-id="8d333-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="8d333-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="8d333-259">Regroupement</span><span class="sxs-lookup"><span data-stu-id="8d333-259">Grouping</span></span>  

 <span data-ttu-id="8d333-260">[Regroupement par](group-by-entity-sql.md) spécifie les groupes dans lesquels les objets retournés par une expression de requête ([Select](select-entity-sql.md)) doivent être placés.</span><span class="sxs-lookup"><span data-stu-id="8d333-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="8d333-261">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="8d333-262">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-262">Output:</span></span>  
  
|<span data-ttu-id="8d333-263">name</span><span class="sxs-lookup"><span data-stu-id="8d333-263">name</span></span>|  
|----------|  
|<span data-ttu-id="8d333-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="8d333-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="8d333-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="8d333-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="8d333-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="8d333-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="8d333-267">...</span><span class="sxs-lookup"><span data-stu-id="8d333-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="8d333-268">Navigation</span><span class="sxs-lookup"><span data-stu-id="8d333-268">Navigation</span></span>  

 <span data-ttu-id="8d333-269">L'opérateur de navigation de relations vous permet de parcourir la relation entre une entité (terminaison From) et une autre entité (terminaison To).</span><span class="sxs-lookup"><span data-stu-id="8d333-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="8d333-270">[Naviguer](navigate-entity-sql.md) prend le type de relation qualifié comme \<namespace> . \<relationship type name> .</span><span class="sxs-lookup"><span data-stu-id="8d333-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="8d333-271">Navigate retourne Ref \<T> si la cardinalité de la terminaison to est 1.</span><span class="sxs-lookup"><span data-stu-id="8d333-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="8d333-272">Si la cardinalité de la terminaison to est n, la collection<Ref \<T>> sera retournée.</span><span class="sxs-lookup"><span data-stu-id="8d333-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="8d333-273">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="8d333-274">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-274">Output:</span></span>  
  
|<span data-ttu-id="8d333-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="8d333-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="8d333-276">1</span><span class="sxs-lookup"><span data-stu-id="8d333-276">1</span></span>|  
|<span data-ttu-id="8d333-277">2</span><span class="sxs-lookup"><span data-stu-id="8d333-277">2</span></span>|  
|<span data-ttu-id="8d333-278">3</span><span class="sxs-lookup"><span data-stu-id="8d333-278">3</span></span>|  
|<span data-ttu-id="8d333-279">...</span><span class="sxs-lookup"><span data-stu-id="8d333-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="8d333-280">SELECT VALUE et SELECT</span><span class="sxs-lookup"><span data-stu-id="8d333-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="8d333-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="8d333-281">SELECT VALUE</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8d333-282">fournit la clause SELECT VALUE pour ignorer la construction de ligne implicite.</span><span class="sxs-lookup"><span data-stu-id="8d333-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="8d333-283">Un seul élément peut être spécifié dans une clause SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="8d333-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="8d333-284">Lorsqu’une telle clause est utilisée, aucun Wrapper de ligne n’est construit autour des éléments de la clause SELECT, et une collection de la forme souhaitée peut être produite, par exemple : `SELECT VALUE a` .</span><span class="sxs-lookup"><span data-stu-id="8d333-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="8d333-285">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="8d333-286">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-286">Output:</span></span>  
  
|<span data-ttu-id="8d333-287">Nom</span><span class="sxs-lookup"><span data-stu-id="8d333-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="8d333-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="8d333-288">Adjustable Race</span></span>|  
|<span data-ttu-id="8d333-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="8d333-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="8d333-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="8d333-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="8d333-291">...</span><span class="sxs-lookup"><span data-stu-id="8d333-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="8d333-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="8d333-292">SELECT</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8d333-293">fournit également le constructeur de ligne pour construire des lignes arbitraires.</span><span class="sxs-lookup"><span data-stu-id="8d333-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="8d333-294">SELECT extrait un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, par exemple : `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="8d333-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="8d333-295">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-295">Example:</span></span>  
  
 <span data-ttu-id="8d333-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="8d333-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="8d333-297">Nom</span><span class="sxs-lookup"><span data-stu-id="8d333-297">Name</span></span>|<span data-ttu-id="8d333-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="8d333-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="8d333-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="8d333-299">Adjustable Race</span></span>|<span data-ttu-id="8d333-300">1</span><span class="sxs-lookup"><span data-stu-id="8d333-300">1</span></span>|  
|<span data-ttu-id="8d333-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="8d333-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="8d333-302">879</span><span class="sxs-lookup"><span data-stu-id="8d333-302">879</span></span>|  
|<span data-ttu-id="8d333-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="8d333-303">AWC Logo Cap</span></span>|<span data-ttu-id="8d333-304">712</span><span class="sxs-lookup"><span data-stu-id="8d333-304">712</span></span>|  
|<span data-ttu-id="8d333-305">...</span><span class="sxs-lookup"><span data-stu-id="8d333-305">...</span></span>|<span data-ttu-id="8d333-306">...</span><span class="sxs-lookup"><span data-stu-id="8d333-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="8d333-307">Expression CASE</span><span class="sxs-lookup"><span data-stu-id="8d333-307">CASE EXPRESSION</span></span>  

 <span data-ttu-id="8d333-308">L' [expression case](case-entity-sql.md) évalue un jeu d’expressions booléennes pour déterminer le résultat.</span><span class="sxs-lookup"><span data-stu-id="8d333-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="8d333-309">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8d333-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="8d333-310">Sortie :</span><span class="sxs-lookup"><span data-stu-id="8d333-310">Output:</span></span>  
  
|<span data-ttu-id="8d333-311">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d333-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="8d333-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="8d333-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d333-313">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d333-313">See also</span></span>

- [<span data-ttu-id="8d333-314">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8d333-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8d333-315">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8d333-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
