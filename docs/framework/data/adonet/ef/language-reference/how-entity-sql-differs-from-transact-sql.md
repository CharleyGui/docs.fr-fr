---
title: Différences entre Entity SQL et Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 96e2283074b6c69e51bb7fee4d4f257cdb58d615
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615629"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="b0e66-102">Différences entre Entity SQL et Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0e66-102">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="b0e66-103">Cet article décrit les différences entre Entity SQL et Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b0e66-103">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="b0e66-104">Héritage et prise en charge des relations</span><span class="sxs-lookup"><span data-stu-id="b0e66-104">Inheritance and Relationships Support</span></span>  
 <span data-ttu-id="b0e66-105">Entity SQL fonctionne directement avec les schémas d’entité conceptuels et prend en charge des fonctionnalités de modèle conceptuel telles que l’héritage et les relations.</span><span class="sxs-lookup"><span data-stu-id="b0e66-105">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="b0e66-106">Lors de l’utilisation de l’héritage, il est souvent utile de sélectionner des instances d’un sous-type à partir d’une collection d’instances de supertype.</span><span class="sxs-lookup"><span data-stu-id="b0e66-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="b0e66-107">L’opérateur [OfType](oftype-entity-sql.md) dans Entity SQL (semblable à `oftype` dans les séquences C#) fournit cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b0e66-107">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="b0e66-108">Prise en charge des collections</span><span class="sxs-lookup"><span data-stu-id="b0e66-108">Support for Collections</span></span>  
 <span data-ttu-id="b0e66-109">Entity SQL traite les collections comme des entités de première classe.</span><span class="sxs-lookup"><span data-stu-id="b0e66-109">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="b0e66-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b0e66-110">For example:</span></span>  
  
- <span data-ttu-id="b0e66-111">Les expressions de collection sont valides dans une clause `from`.</span><span class="sxs-lookup"><span data-stu-id="b0e66-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="b0e66-112">Les sous-requêtes `in` et `exists` ont été généralisées pour autoriser toute collection.</span><span class="sxs-lookup"><span data-stu-id="b0e66-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="b0e66-113">Une sous-requête est un type de collection.</span><span class="sxs-lookup"><span data-stu-id="b0e66-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="b0e66-114">`e1 in e2`et `exists(e)` sont les constructions de Entity SQL pour effectuer ces opérations.</span><span class="sxs-lookup"><span data-stu-id="b0e66-114">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="b0e66-115">Les opérations de définition, telles que `union`, `intersect` et `except`, s’appliquent à présent aux collections.</span><span class="sxs-lookup"><span data-stu-id="b0e66-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="b0e66-116">Les jointures s’appliquent aux collections.</span><span class="sxs-lookup"><span data-stu-id="b0e66-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="b0e66-117">Prise en charge des expressions</span><span class="sxs-lookup"><span data-stu-id="b0e66-117">Support for Expressions</span></span>  
 <span data-ttu-id="b0e66-118">Transact-SQL contient des sous-requêtes (tables) et des expressions (lignes et colonnes).</span><span class="sxs-lookup"><span data-stu-id="b0e66-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="b0e66-119">Pour prendre en charge les collections et les collections imbriquées, Entity SQL transforme tout en une expression.</span><span class="sxs-lookup"><span data-stu-id="b0e66-119">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="b0e66-120">Entity SQL est plus composable que Transact-SQL, chaque expression peut être utilisée n’importe où.</span><span class="sxs-lookup"><span data-stu-id="b0e66-120">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="b0e66-121">Les expressions de requête génèrent toujours des collections des types projetés et peuvent être utilisées partout où une expression de collection est autorisée.</span><span class="sxs-lookup"><span data-stu-id="b0e66-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="b0e66-122">Pour plus d’informations sur les expressions Transact-SQL qui ne sont pas prises en charge dans Entity SQL, consultez [expressions non prises en charge](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b0e66-122">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="b0e66-123">Les requêtes Entity SQL valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0e66-123">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="b0e66-124">Traitement uniforme des sous-requêtes</span><span class="sxs-lookup"><span data-stu-id="b0e66-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="b0e66-125">En raison de son importance sur les tables, Transact-SQL effectue une interprétation contextuelle des sous-requêtes.</span><span class="sxs-lookup"><span data-stu-id="b0e66-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="b0e66-126">Par exemple, une sous-requête dans la `from` clause est considérée comme un multiensemble (table).</span><span class="sxs-lookup"><span data-stu-id="b0e66-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="b0e66-127">En revanche, la même sous-requête utilisée dans la clause `select` est considérée comme une sous-requête scalaire.</span><span class="sxs-lookup"><span data-stu-id="b0e66-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="b0e66-128">De même, une sous-requête utilisée sur le côté gauche d’un `in` opérateur est considérée comme une sous-requête scalaire, tandis que le côté droit est supposé être une sous-requête de multiensemble.</span><span class="sxs-lookup"><span data-stu-id="b0e66-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="b0e66-129">Entity SQL élimine ces différences.</span><span class="sxs-lookup"><span data-stu-id="b0e66-129">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="b0e66-130">Une expression a une interprétation uniforme qui ne dépend pas du contexte dans lequel elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b0e66-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="b0e66-131">Entity SQL considère toutes les sous-requêtes comme des sous-requêtes de multiensemble.</span><span class="sxs-lookup"><span data-stu-id="b0e66-131">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="b0e66-132">Si une valeur scalaire est souhaitée à partir de la sous-requête, Entity SQL fournit l' `anyelement` opérateur qui opère sur une collection (dans ce cas, la sous-requête) et extrait une valeur singleton de la collection.</span><span class="sxs-lookup"><span data-stu-id="b0e66-132">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="b0e66-133">Éviter des contraintes implicites pour les sous-requêtes</span><span class="sxs-lookup"><span data-stu-id="b0e66-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="b0e66-134">Un effet secondaire connexe du traitement uniforme des sous-requêtes est la conversion implicite des sous-requêtes en valeurs scalaires.</span><span class="sxs-lookup"><span data-stu-id="b0e66-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="b0e66-135">En particulier, dans Transact-SQL, un multiensemble de lignes (avec un champ unique) est converti implicitement en une valeur scalaire dont le type de données est celui du champ.</span><span class="sxs-lookup"><span data-stu-id="b0e66-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="b0e66-136">Entity SQL ne prend pas en charge cette contrainte implicite.</span><span class="sxs-lookup"><span data-stu-id="b0e66-136">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="b0e66-137">Entity SQL fournit l' `ANYELEMENT` opérateur pour extraire une valeur Singleton d’une collection et une `select value` clause pour éviter de créer un wrapper de ligne pendant une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="b0e66-137">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="b0e66-138">Select Value : éviter le wrapper de ligne implicite</span><span class="sxs-lookup"><span data-stu-id="b0e66-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="b0e66-139">La clause SELECT dans une sous-requête Transact-SQL crée implicitement un wrapper de ligne autour des éléments de la clause.</span><span class="sxs-lookup"><span data-stu-id="b0e66-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="b0e66-140">Cela implique que nous ne pouvons pas créer de collections de scalaires ou d’objets.</span><span class="sxs-lookup"><span data-stu-id="b0e66-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="b0e66-141">Transact-SQL autorise une contrainte implicite entre une `rowtype` avec un champ et une valeur singleton du même type de données.</span><span class="sxs-lookup"><span data-stu-id="b0e66-141">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="b0e66-142">Entity SQL fournit la `select value` clause pour ignorer la construction de ligne implicite.</span><span class="sxs-lookup"><span data-stu-id="b0e66-142">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="b0e66-143">Un seul élément peut être spécifié dans une clause `select value`.</span><span class="sxs-lookup"><span data-stu-id="b0e66-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="b0e66-144">Lorsqu’une telle clause est utilisée, aucun Wrapper de ligne n’est construit autour des éléments de la `select` clause, et une collection de la forme souhaitée peut être produite, par exemple, `select value a` .</span><span class="sxs-lookup"><span data-stu-id="b0e66-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="b0e66-145">Entity SQL fournit également le constructeur de ligne pour construire des lignes arbitraires.</span><span class="sxs-lookup"><span data-stu-id="b0e66-145">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="b0e66-146">`select`prend un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs :</span><span class="sxs-lookup"><span data-stu-id="b0e66-146">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="b0e66-147">Corrélation gauche et utilisation d'alias</span><span class="sxs-lookup"><span data-stu-id="b0e66-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="b0e66-148">Dans Transact-SQL, les expressions d’une étendue donnée (une clause unique comme `select` ou `from` ) ne peuvent pas faire référence à des expressions définies précédemment dans la même portée.</span><span class="sxs-lookup"><span data-stu-id="b0e66-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="b0e66-149">Certains dialectes de SQL (y compris Transact-SQL) prennent en charge des formes limitées de celles-ci dans la `from` clause.</span><span class="sxs-lookup"><span data-stu-id="b0e66-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="b0e66-150">Entity SQL généralise les corrélations gauches dans la `from` clause et les traite uniformément.</span><span class="sxs-lookup"><span data-stu-id="b0e66-150">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="b0e66-151">Les expressions dans la clause `from` peuvent référencer des définitions antérieures (définitions à gauche) dans la même clause sans nécessiter une syntaxe supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b0e66-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="b0e66-152">Entity SQL impose également des restrictions supplémentaires sur les requêtes qui impliquent des `group by` clauses.</span><span class="sxs-lookup"><span data-stu-id="b0e66-152">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="b0e66-153">Les expressions dans la `select` clause et la `having` clause de ces requêtes peuvent uniquement faire référence aux `group by` clés par le biais de leurs alias.</span><span class="sxs-lookup"><span data-stu-id="b0e66-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="b0e66-154">La construction suivante est valide dans Transact-SQL, mais n’est pas dans Entity SQL :</span><span class="sxs-lookup"><span data-stu-id="b0e66-154">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="b0e66-155">Pour effectuer cette opération dans Entity SQL :</span><span class="sxs-lookup"><span data-stu-id="b0e66-155">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="b0e66-156">Référencement de colonnes (propriétés) de tables (collections)</span><span class="sxs-lookup"><span data-stu-id="b0e66-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="b0e66-157">Toutes les références de colonnes dans Entity SQL doivent être qualifiées avec l’alias de table.</span><span class="sxs-lookup"><span data-stu-id="b0e66-157">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="b0e66-158">La construction suivante (en supposant que `a` est une colonne valide de la table `T` ) est valide dans Transact-SQL, mais pas dans Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="b0e66-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="b0e66-159">Le formulaire Entity SQL est</span><span class="sxs-lookup"><span data-stu-id="b0e66-159">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="b0e66-160">Les alias de la table sont facultatifs dans la clause `from`.</span><span class="sxs-lookup"><span data-stu-id="b0e66-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="b0e66-161">Le nom de la table est utilisé comme alias implicite.</span><span class="sxs-lookup"><span data-stu-id="b0e66-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="b0e66-162">Entity SQL autorise également le formulaire suivant :</span><span class="sxs-lookup"><span data-stu-id="b0e66-162">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="b0e66-163">Navigation dans les objets</span><span class="sxs-lookup"><span data-stu-id="b0e66-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="b0e66-164">Transact-SQL utilise la notation « . » pour référencer les colonnes d’une table (une ligne).</span><span class="sxs-lookup"><span data-stu-id="b0e66-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="b0e66-165">Entity SQL étend cette notation (empruntée des langages de programmation) pour prendre en charge la navigation dans les propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="b0e66-165">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="b0e66-166">Par exemple, si `p` est une expression de type Person, voici la syntaxe Entity SQL pour référencer la ville de l’adresse de cette personne.</span><span class="sxs-lookup"><span data-stu-id="b0e66-166">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="b0e66-167">Aucune prise en charge de\*</span><span class="sxs-lookup"><span data-stu-id="b0e66-167">No Support for \*</span></span>  
 <span data-ttu-id="b0e66-168">Transact-SQL prend en charge la \* syntaxe non qualifiée en tant qu’alias pour la ligne entière, et la syntaxe qualifiée \* (t. \* ) comme raccourci pour les champs de cette table.</span><span class="sxs-lookup"><span data-stu-id="b0e66-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="b0e66-169">En outre, Transact-SQL autorise un agrégat count ( \* ) spécial, qui comprend des valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="b0e66-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="b0e66-170">Entity SQL ne prend pas en charge la construction \*.</span><span class="sxs-lookup"><span data-stu-id="b0e66-170">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="b0e66-171">Les requêtes Transact-SQL de la forme `select * from T` et `select T1.* from T1, T2...` peuvent être exprimées en Entity SQL sous la forme `select value t from T as t` et `select value t1 from T1 as t1, T2 as t2...` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="b0e66-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="b0e66-172">En outre, ces constructions gèrent l'héritage (capacité des valeurs à être substituées), tandis que les variantes `select *` sont restreintes aux propriétés de niveau supérieur du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="b0e66-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="b0e66-173">Entity SQL ne prend pas en charge l' `count(*)` agrégat.</span><span class="sxs-lookup"><span data-stu-id="b0e66-173">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="b0e66-174">Utilisez `count(0)` à la place.</span><span class="sxs-lookup"><span data-stu-id="b0e66-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="b0e66-175">Modifications apportées à Group By</span><span class="sxs-lookup"><span data-stu-id="b0e66-175">Changes to Group By</span></span>  
 <span data-ttu-id="b0e66-176">Entity SQL prend en charge l’alias des `group by` clés.</span><span class="sxs-lookup"><span data-stu-id="b0e66-176">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="b0e66-177">Les expressions dans la clause `select` et la clause `having` doivent faire référence aux clés `group by` par le biais de ces alias.</span><span class="sxs-lookup"><span data-stu-id="b0e66-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="b0e66-178">Par exemple, cette syntaxe de Entity SQL :</span><span class="sxs-lookup"><span data-stu-id="b0e66-178">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="b0e66-179">... équivaut à l’instruction Transact-SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="b0e66-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="b0e66-180">Agrégats basés sur des collections</span><span class="sxs-lookup"><span data-stu-id="b0e66-180">Collection-Based Aggregates</span></span>  
 <span data-ttu-id="b0e66-181">Entity SQL prend en charge deux types d’agrégats.</span><span class="sxs-lookup"><span data-stu-id="b0e66-181">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="b0e66-182">Les agrégats basés sur des collections opèrent sur des collections et produisent le résultat agrégé.</span><span class="sxs-lookup"><span data-stu-id="b0e66-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="b0e66-183">Ils peuvent apparaître n'importe où dans la requête et ne requièrent pas de clause `group by`.</span><span class="sxs-lookup"><span data-stu-id="b0e66-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="b0e66-184">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b0e66-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="b0e66-185">Entity SQL prend également en charge les agrégats de style SQL.</span><span class="sxs-lookup"><span data-stu-id="b0e66-185">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="b0e66-186">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b0e66-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="b0e66-187">Utilisation des clauses ORDER BY</span><span class="sxs-lookup"><span data-stu-id="b0e66-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="b0e66-188">Transact-SQL autorise `ORDER BY` la spécification de clauses uniquement dans le bloc le plus haut `SELECT .. FROM .. WHERE` .</span><span class="sxs-lookup"><span data-stu-id="b0e66-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="b0e66-189">Dans Entity SQL, vous pouvez utiliser une expression imbriquée `ORDER BY` et elle peut être placée n’importe où dans la requête, mais l’ordre dans une requête imbriquée n’est pas conservé.</span><span class="sxs-lookup"><span data-stu-id="b0e66-189">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="b0e66-190">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="b0e66-190">Identifiers</span></span>  
 <span data-ttu-id="b0e66-191">Dans Transact-SQL, la comparaison des identificateurs est basée sur le classement de la base de données active.</span><span class="sxs-lookup"><span data-stu-id="b0e66-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="b0e66-192">Dans Entity SQL, les identificateurs respectent toujours la casse et respectent les accents (autrement dit, Entity SQL fait la distinction entre les caractères accentués et non accentués ; par exemple, « a » n’est pas égal à « à »).</span><span class="sxs-lookup"><span data-stu-id="b0e66-192">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="b0e66-193">Entity SQL traite les versions des lettres qui s’affichent de la même façon, mais qui proviennent de différentes pages de codes comme des caractères différents.</span><span class="sxs-lookup"><span data-stu-id="b0e66-193">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="b0e66-194">Pour plus d’informations, consultez [jeu de caractères d’entrée](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b0e66-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="b0e66-195">Fonctionnalités Transact-SQL non disponibles dans Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0e66-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="b0e66-196">La fonctionnalité Transact-SQL suivante n’est pas disponible dans Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="b0e66-196">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="b0e66-197">DML</span><span class="sxs-lookup"><span data-stu-id="b0e66-197">DML</span></span>  
 <span data-ttu-id="b0e66-198">Entity SQL ne fournit actuellement aucune prise en charge des instructions DML (insertion, mise à jour, suppression).</span><span class="sxs-lookup"><span data-stu-id="b0e66-198">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="b0e66-199">DDL</span><span class="sxs-lookup"><span data-stu-id="b0e66-199">DDL</span></span>  
 <span data-ttu-id="b0e66-200">Entity SQL n’offre aucune prise en charge de DDL dans la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="b0e66-200">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="b0e66-201">Programmation impérative</span><span class="sxs-lookup"><span data-stu-id="b0e66-201">Imperative Programming</span></span>  
 <span data-ttu-id="b0e66-202">Entity SQL n’offre aucune prise en charge de la programmation impérative, contrairement à Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b0e66-202">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="b0e66-203">Utilisez un langage de programmation à la place.</span><span class="sxs-lookup"><span data-stu-id="b0e66-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="b0e66-204">Fonctions de regroupement</span><span class="sxs-lookup"><span data-stu-id="b0e66-204">Grouping Functions</span></span>  
 <span data-ttu-id="b0e66-205">Entity SQL ne fournit pas encore de prise en charge pour les fonctions de regroupement (par exemple CUBE, ROLLUP et GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="b0e66-205">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="b0e66-206">Fonctions analytiques</span><span class="sxs-lookup"><span data-stu-id="b0e66-206">Analytic Functions</span></span>  
 <span data-ttu-id="b0e66-207">Entity SQL ne permet pas (encore) de prendre en charge les fonctions analytiques.</span><span class="sxs-lookup"><span data-stu-id="b0e66-207">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="b0e66-208">Fonctions et opérateurs intégrés</span><span class="sxs-lookup"><span data-stu-id="b0e66-208">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="b0e66-209">Entity SQL prend en charge un sous-ensemble des fonctions et des opérateurs intégrés de Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b0e66-209">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="b0e66-210">Ces opérateurs et ces fonctions seront vraisemblablement pris en charge par les principaux fournisseurs de stockage.</span><span class="sxs-lookup"><span data-stu-id="b0e66-210">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="b0e66-211">Entity SQL utilise les fonctions spécifiques au magasin déclarées dans un manifeste du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="b0e66-211">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="b0e66-212">En outre, la Entity Framework vous permet de déclarer des fonctions de magasin existantes intégrées et définies par l’utilisateur, pour que les Entity SQL utilisent.</span><span class="sxs-lookup"><span data-stu-id="b0e66-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="b0e66-213">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="b0e66-213">Hints</span></span>  
 <span data-ttu-id="b0e66-214">Entity SQL ne fournit pas de mécanismes pour les indicateurs de requête.</span><span class="sxs-lookup"><span data-stu-id="b0e66-214">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="b0e66-215">Résultats d'une requête de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="b0e66-215">Batching Query Results</span></span>  
 <span data-ttu-id="b0e66-216">Entity SQL ne prend pas en charge le traitement par lot des résultats de requête.</span><span class="sxs-lookup"><span data-stu-id="b0e66-216">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="b0e66-217">Par exemple, voici une instruction Transact-SQL valide (envoi en tant que lot) :</span><span class="sxs-lookup"><span data-stu-id="b0e66-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="b0e66-218">Toutefois, l’équivalent Entity SQL n’est pas pris en charge :</span><span class="sxs-lookup"><span data-stu-id="b0e66-218">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="b0e66-219">Entity SQL prend en charge uniquement une instruction de requête produisant des résultats par commande.</span><span class="sxs-lookup"><span data-stu-id="b0e66-219">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e66-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0e66-220">See also</span></span>

- [<span data-ttu-id="b0e66-221">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0e66-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="b0e66-222">Expressions non prises en charge</span><span class="sxs-lookup"><span data-stu-id="b0e66-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
