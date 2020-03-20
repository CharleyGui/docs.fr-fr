---
title: Différences entre Entity SQL et Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150229"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="2f0ee-102">Différences entre Entity SQL et Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2f0ee-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="2f0ee-103">Ce sujet décrit les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] différences entre Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="2f0ee-104">Héritage et prise en charge des relations</span><span class="sxs-lookup"><span data-stu-id="2f0ee-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-105">travaille directement avec les schémas d’entités conceptuelles et prend en charge les caractéristiques conceptuelles du modèle telles que l’héritage et les relations.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="2f0ee-106">Lors de l’utilisation de l’héritage, il est souvent utile de sélectionner des instances d’un sous-type à partir d’une collection d’instances de supertype.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="2f0ee-107">[L’opérateur oftype](oftype-entity-sql.md) (semblable [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à `oftype` dans les séquences C) fournit cette capacité.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="2f0ee-108">Prise en charge des collections</span><span class="sxs-lookup"><span data-stu-id="2f0ee-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-109">traite les collections en tant qu’entités de première classe.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-109">treats collections as first-class entities.</span></span> <span data-ttu-id="2f0ee-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-110">For example:</span></span>  
  
- <span data-ttu-id="2f0ee-111">Les expressions de collection sont valides dans une clause `from`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="2f0ee-112">Les sous-requêtes `in` et `exists` ont été généralisées pour autoriser toute collection.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="2f0ee-113">Une sous-requête est un type de collection.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="2f0ee-114">`e1 in e2` et `exists(e)` sont les constructions [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui permettent d'effectuer ces opérations.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="2f0ee-115">Les opérations de définition, telles que `union`, `intersect` et `except`, s’appliquent à présent aux collections.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="2f0ee-116">Les jointures s’appliquent aux collections.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="2f0ee-117">Prise en charge des expressions</span><span class="sxs-lookup"><span data-stu-id="2f0ee-117">Support for Expressions</span></span>  
 <span data-ttu-id="2f0ee-118">Transact-SQL a des sous-ques (tables) et des expressions (lignes et colonnes).</span><span class="sxs-lookup"><span data-stu-id="2f0ee-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="2f0ee-119">Soutenir les collections et [!INCLUDE[esql](../../../../../../includes/esql-md.md)] les collections imbriquées, tout fait une expression.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-120">est plus composable que Transact-SQL, chaque expression peut être utilisée n’importe où.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="2f0ee-121">Les expressions de requête génèrent toujours des collections des types projetés et peuvent être utilisées partout où une expression de collection est autorisée.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="2f0ee-122">Pour plus d’informations sur les expressions [!INCLUDE[esql](../../../../../../includes/esql-md.md)]De Transact-SQL qui ne sont pas prises en charge, voir [Expressions non soutenues](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2f0ee-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="2f0ee-123">Les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivantes sont toutes valides :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="2f0ee-124">Traitement uniforme des sous-requêtes</span><span class="sxs-lookup"><span data-stu-id="2f0ee-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="2f0ee-125">Compte tenu de l’accent mis sur les tableaux, Transact-SQL effectue une interprétation contextuelle des sous-ques.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="2f0ee-126">Par exemple, une sous-fertilité dans la `from` clause est considérée comme un multicart (tableau).</span><span class="sxs-lookup"><span data-stu-id="2f0ee-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="2f0ee-127">En revanche, la même sous-requête utilisée dans la clause `select` est considérée comme une sous-requête scalaire.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="2f0ee-128">De même, une sous-fertilité utilisée `in` sur le côté gauche d’un opérateur est considérée comme une sous-querie scalaire, tandis que le côté droit devrait être une sous-fertilité multi-ensemble.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-129">élimine ces différences.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-129">eliminates these differences.</span></span> <span data-ttu-id="2f0ee-130">Une expression a une interprétation uniforme qui ne dépend pas du contexte dans lequel elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-131">considère toutes les sous-ques comme des sous-ques multiseques.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="2f0ee-132">Si une valeur scalaire est souhaitée [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à `anyelement` partir de la sous-querie, fournit l’opérateur qui fonctionne sur une collection (dans ce cas, la sous-querie), et extrait une valeur singleton de la collection.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="2f0ee-133">Éviter des contraintes implicites pour les sous-requêtes</span><span class="sxs-lookup"><span data-stu-id="2f0ee-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="2f0ee-134">Un effet secondaire connexe du traitement uniforme des sous-requêtes est la conversion implicite des sous-requêtes en valeurs scalaires.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="2f0ee-135">Plus précisément, dans Transact-SQL, un multi-ensemble de lignes (avec un seul champ) est implicitement converti en une valeur scalaire dont le type de données est celui du champ.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-136">ne prend pas en charge cette contrainte implicite.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-137">fournit l'opérateur ANYELEMENT pour extraire une valeur singleton d'une collection et une clause `select value` pour éviter de créer un wrapper de ligne pendant une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="2f0ee-138">Select Value : éviter le wrapper de ligne implicite</span><span class="sxs-lookup"><span data-stu-id="2f0ee-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="2f0ee-139">La clause de sélection dans une sous-fertilité Transact-SQL crée implicitement un emballage de ligne autour des éléments de la clause.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="2f0ee-140">Cela implique que nous ne pouvons pas créer de collections de scalaires ou d’objets.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="2f0ee-141">La transact-SQL permet une coercition implicite entre un tapageur avec un champ, et une valeur singleton du même type de données.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-142">fournit la clause `select value` pour ignorer la construction de ligne implicite.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="2f0ee-143">Un seul élément peut être spécifié dans une clause `select value`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="2f0ee-144">Lorsqu’une telle clause est utilisée, aucun wrapper de ligne n’est construit autour des éléments de la clause `select` et une collection de la forme souhaitée peut être générée, par exemple : `select value a`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-145">fournit également le constructeur de ligne pour construire des lignes arbitraires.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="2f0ee-146">`select` accepte un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="2f0ee-147">Corrélation gauche et utilisation d'alias</span><span class="sxs-lookup"><span data-stu-id="2f0ee-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="2f0ee-148">Dans l’article de Transact-SQL, les `select` expressions `from`d’une portée donnée (une seule clause comme ou ) ne peuvent pas faire référence à des expressions définies plus tôt dans la même portée.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="2f0ee-149">Certains dialectes de SQL (y compris Transact-SQL) `from` supportent des formes limitées de ceux-ci dans la clause.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-150">généralise les corrélations `from` laissées dans la clause et les traite uniformément.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="2f0ee-151">Les expressions dans la clause `from` peuvent référencer des définitions antérieures (définitions à gauche) dans la même clause sans nécessiter une syntaxe supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-152">impose également des restrictions supplémentaires sur les requêtes qui impliquent des clauses `group by`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="2f0ee-153">Les expressions `select` de `having` la clause et de la `group by` clause de ces requêtes ne peuvent se référer qu’aux clés via leurs pseudonymes.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="2f0ee-154">La construction suivante est valable dans Transact-SQL mais ne sont pas dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="2f0ee-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="2f0ee-155">Pour effectuer cette opération dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="2f0ee-156">Référencement de colonnes (propriétés) de tables (collections)</span><span class="sxs-lookup"><span data-stu-id="2f0ee-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="2f0ee-157">Toutes les références de colonne dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doivent être qualifiées avec l'alias de la table.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="2f0ee-158">La construction suivante `a` (en supposant `T`qu’il s’agit d’une [!INCLUDE[esql](../../../../../../includes/esql-md.md)]colonne de table valide) est valable dans Transact-SQL mais pas dans .</span><span class="sxs-lookup"><span data-stu-id="2f0ee-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="2f0ee-159">La forme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="2f0ee-160">Les alias de la table sont facultatifs dans la clause `from`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="2f0ee-161">Le nom de la table est utilisé comme alias implicite.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-162">autorise également la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-162">allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="2f0ee-163">Navigation dans les objets</span><span class="sxs-lookup"><span data-stu-id="2f0ee-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="2f0ee-164">Transact-SQL utilise la notation "." pour le référencement des colonnes de (une rangée de) une table.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-165">étend cette notation (empruntée des langages de programmation) pour prendre en charge la navigation dans les propriétés d'un objet.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="2f0ee-166">Par exemple, si `p` est une expression de type Person, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous référence la ville de l'adresse de cette personne.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="2f0ee-167">Aucune prise en charge pour \*</span><span class="sxs-lookup"><span data-stu-id="2f0ee-167">No Support for \*</span></span>  
 <span data-ttu-id="2f0ee-168">La transact-SQL prend en charge la syntaxe non qualifiée \* comme un alias\*pour l’ensemble de la rangée, et la syntaxe qualifiée (t. ) comme un raccourci pour les champs de cette table.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="2f0ee-169">De plus, Transact-SQL permet un\*compte spécial( ) agrégat, qui comprend des nuls.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-170">ne prend pas en charge la construction \*.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-170">does not support the \* construct.</span></span> <span data-ttu-id="2f0ee-171">Questions de Transact-SQL `select * from T` de `select T1.* from T1, T2...` la forme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` et `select value t1 from T1 as t1, T2 as t2...`peut être exprimée dans comme et , respectivement.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="2f0ee-172">En outre, ces constructions gèrent l'héritage (capacité des valeurs à être substituées), tandis que les variantes `select *` sont restreintes aux propriétés de niveau supérieur du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-173">ne prend pas en charge l'agrégat `count(*)`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="2f0ee-174">Utilisez `count(0)` à la place.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="2f0ee-175">Modifications apportées à Group By</span><span class="sxs-lookup"><span data-stu-id="2f0ee-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-176">prend en charge les alias des clés `group by`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="2f0ee-177">Les expressions dans la clause `select` et la clause `having` doivent faire référence aux clés `group by` par le biais de ces alias.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="2f0ee-178">Par exemple, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="2f0ee-179">... est équivalent à la Transact-SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="2f0ee-180">Agrégats basés sur des collections</span><span class="sxs-lookup"><span data-stu-id="2f0ee-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-181">prend en charge deux types d'agrégats.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="2f0ee-182">Les agrégats basés sur des collections opèrent sur des collections et produisent le résultat agrégé.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="2f0ee-183">Ils peuvent apparaître n'importe où dans la requête et ne requièrent pas de clause `group by`.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="2f0ee-184">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-185">prend également en charge les agrégats de style SQL.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="2f0ee-186">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="2f0ee-187">Utilisation des clauses ORDER BY</span><span class="sxs-lookup"><span data-stu-id="2f0ee-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="2f0ee-188">Transact-SQL `ORDER BY` permet de préciser les clauses `SELECT .. FROM .. WHERE` uniquement dans le bloc le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="2f0ee-189">En [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vous pouvez utiliser `ORDER BY` une expression imbriquée et il peut être placé n’importe où dans la requête, mais la commande dans une requête imbriquée n’est pas préservée.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="2f0ee-190">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="2f0ee-190">Identifiers</span></span>  
 <span data-ttu-id="2f0ee-191">Dans Transaction-SQL, la comparaison des identifiants est basée sur la compilation de la base de données actuelle.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="2f0ee-192">Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les identificateurs respectent toujours la casse et les accents (autrement dit, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distingue les caractères accentués et non accentués ; par exemple, « a » n'est pas égal à « à »).</span><span class="sxs-lookup"><span data-stu-id="2f0ee-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-193">traite les versions des lettres qui apparaissent identiques mais qui proviennent de pages de codes différentes comme des caractères différents.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="2f0ee-194">Pour plus d’informations, voir [Input Character Set](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2f0ee-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="2f0ee-195">Fonctionnalités Transact-SQL non disponibles dans Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2f0ee-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="2f0ee-196">La fonctionnalité Transact-SQL suivante n’est pas disponible en [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f0ee-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="2f0ee-197">DML</span><span class="sxs-lookup"><span data-stu-id="2f0ee-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-198">actuellement ne fournit aucun support pour les instructions DML (insert, mise à jour, supprimer).</span><span class="sxs-lookup"><span data-stu-id="2f0ee-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="2f0ee-199">DDL</span><span class="sxs-lookup"><span data-stu-id="2f0ee-199">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-200">ne fournit aucune prise en charge pour DDL dans la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-200">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="2f0ee-201">Programmation impérative</span><span class="sxs-lookup"><span data-stu-id="2f0ee-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-202">ne fournit aucun soutien à la programmation impérative, contrairement à Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="2f0ee-203">Utilisez un langage de programmation à la place.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="2f0ee-204">Fonctions de regroupement</span><span class="sxs-lookup"><span data-stu-id="2f0ee-204">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-205">ne fournit pas encore de prise en charge pour les fonctions de regroupement (par exemple, CUBE, ROLLUP et GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="2f0ee-205">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="2f0ee-206">Fonctions analytiques</span><span class="sxs-lookup"><span data-stu-id="2f0ee-206">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-207">ne fournit pas (encore) de prise en charge pour les fonctions analytiques.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-207">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="2f0ee-208">Fonctions et opérateurs intégrés</span><span class="sxs-lookup"><span data-stu-id="2f0ee-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-209">prend en charge un sous-ensemble de Transact-SQL construits dans des fonctions et des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="2f0ee-210">Ces opérateurs et ces fonctions seront vraisemblablement pris en charge par les principaux fournisseurs de stockage.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2f0ee-211">utilise les fonctions spécifiques au magasin déclarées dans un manifeste du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="2f0ee-212">En outre, le cadre d’entité vous permet de déclarer les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fonctions de magasin existantes intégrées et définies par l’utilisateur, pour l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="2f0ee-213">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="2f0ee-213">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-214">ne fournit pas de mécanismes pour les indicateurs de requête.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-214">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="2f0ee-215">Résultats d'une requête de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="2f0ee-215">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-216">ne prend pas en charge les résultats d'une requête de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-216">does not support batching query results.</span></span> <span data-ttu-id="2f0ee-217">Par exemple, ce qui suit est valide Transact-SQL (envoi sous forme de lot) :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="2f0ee-218">Toutefois, l'équivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas pris en charge :</span><span class="sxs-lookup"><span data-stu-id="2f0ee-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2f0ee-219">prend uniquement en charge une seule instruction de requête générant un résultat par commande.</span><span class="sxs-lookup"><span data-stu-id="2f0ee-219">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0ee-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f0ee-220">See also</span></span>

- [<span data-ttu-id="2f0ee-221">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2f0ee-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="2f0ee-222">Expressions non prises en charge</span><span class="sxs-lookup"><span data-stu-id="2f0ee-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
