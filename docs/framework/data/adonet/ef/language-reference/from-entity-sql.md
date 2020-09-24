---
title: FROM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 8affac82fb1813aa0282540b5dc2f47d42234a1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148051"
---
# <a name="from-entity-sql"></a><span data-ttu-id="f54d0-102">FROM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f54d0-102">FROM (Entity SQL)</span></span>

<span data-ttu-id="f54d0-103">Spécifie la collection utilisée dans les instructions [Select](select-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="f54d0-103">Specifies the collection used in [SELECT](select-entity-sql.md) statements.</span></span>

## <a name="syntax"></a><span data-ttu-id="f54d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f54d0-104">Syntax</span></span>

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a><span data-ttu-id="f54d0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f54d0-105">Arguments</span></span>

`expression` \
<span data-ttu-id="f54d0-106">Toute expression de requête valide qui produit une collection à utiliser comme source dans une instruction `SELECT`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="f54d0-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f54d0-107">Remarks</span></span>

<span data-ttu-id="f54d0-108">Une clause `FROM` est une liste séparée par des virgules d'un ou de plusieurs éléments de clause `FROM`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="f54d0-109">La clause `FROM` peut être utilisée pour spécifier une ou plusieurs sources pour une instruction `SELECT`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="f54d0-110">La forme la plus simple d’une clause `FROM` est une expression de requête unique qui identifie une collection et un alias utilisés comme source dans une instruction `SELECT`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f54d0-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>

`FROM C as c`

## <a name="from-clause-items"></a><span data-ttu-id="f54d0-111">Éléments de clause FROM</span><span class="sxs-lookup"><span data-stu-id="f54d0-111">FROM Clause Items</span></span>

<span data-ttu-id="f54d0-112">Chaque élément de clause `FROM` fait référence à une collection source dans la requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f54d0-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f54d0-113">prend en charge les classes d'éléments de clause `FROM` suivantes : éléments de clause `FROM` simples, éléments de clause `JOIN FROM` et éléments de clause `APPLY FROM`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="f54d0-114">Chacun de ces éléments de clause `FROM` est décrite en détail dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="f54d0-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>

### <a name="simple-from-clause-item"></a><span data-ttu-id="f54d0-115">Élément de clause FROM simple</span><span class="sxs-lookup"><span data-stu-id="f54d0-115">Simple FROM Clause Item</span></span>

<span data-ttu-id="f54d0-116">L'élément de clause `FROM` le plus simple est une expression unique qui identifie une collection et un alias.</span><span class="sxs-lookup"><span data-stu-id="f54d0-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="f54d0-117">L’expression peut être simplement un jeu d’entités, une sous-requête ou toute autre expression qui est un type collection.</span><span class="sxs-lookup"><span data-stu-id="f54d0-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="f54d0-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f54d0-118">The following is an example:</span></span>

```sql
LOB.Customers as c
```

<span data-ttu-id="f54d0-119">La spécification d'un alias est facultative.</span><span class="sxs-lookup"><span data-stu-id="f54d0-119">The alias specification is optional.</span></span> <span data-ttu-id="f54d0-120">Une autre spécification de l'élément de clause FROM pourrait être la suivante :</span><span class="sxs-lookup"><span data-stu-id="f54d0-120">An alternate specification of the above from clause item could be the following:</span></span>

```sql
LOB.Customers
```

<span data-ttu-id="f54d0-121">Si aucun alias n'est spécifié, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente d'en générer un basé sur l'expression de collection.</span><span class="sxs-lookup"><span data-stu-id="f54d0-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>

### <a name="join-from-clause-item"></a><span data-ttu-id="f54d0-122">Élément de clause JOIN FROM</span><span class="sxs-lookup"><span data-stu-id="f54d0-122">JOIN FROM Clause Item</span></span>

<span data-ttu-id="f54d0-123">Un élément de clause `JOIN FROM` représente une jointure entre deux éléments de clause `FROM`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f54d0-124">prend en charge les jointures croisées, les jointures internes, les jointures externes gauches et droites, ainsi que les jointures externes entières.</span><span class="sxs-lookup"><span data-stu-id="f54d0-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="f54d0-125">Toutes ces jointures sont prises en charge de la même façon qu’elles sont prises en charge dans Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="f54d0-125">All these joins are supported similar to the way that they are supported in Transact-SQL.</span></span> <span data-ttu-id="f54d0-126">Comme dans Transact-SQL, les deux `FROM` éléments de clause impliqués dans le `JOIN` doivent être indépendants.</span><span class="sxs-lookup"><span data-stu-id="f54d0-126">As in Transact-SQL, the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="f54d0-127">Autrement dit, ils ne peuvent pas être corrélés.</span><span class="sxs-lookup"><span data-stu-id="f54d0-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="f54d0-128">Un `CROSS APPLY` ou un `OUTER APPLY` peut être utilisé pour ces cas.</span><span class="sxs-lookup"><span data-stu-id="f54d0-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>

#### <a name="cross-joins"></a><span data-ttu-id="f54d0-129">Jointures croisées</span><span class="sxs-lookup"><span data-stu-id="f54d0-129">Cross Joins</span></span>

<span data-ttu-id="f54d0-130">Une expression de requête `CROSS JOIN` génère le produit cartésien des deux collections, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f54d0-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a><span data-ttu-id="f54d0-131">Jointures internes</span><span class="sxs-lookup"><span data-stu-id="f54d0-131">Inner Joins</span></span>

<span data-ttu-id="f54d0-132">Un `INNER JOIN` génère un produit cartésien limité des deux collections, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f54d0-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c [INNER] JOIN D AS d ON e`

<span data-ttu-id="f54d0-133">L’expression de requête précédente traite une combinaison de chaque élément de la collection à gauche associé à chaque élément de la collection à droite, où la condition `ON` est vérifiée (True).</span><span class="sxs-lookup"><span data-stu-id="f54d0-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="f54d0-134">Si aucune condition `ON` n'est spécifiée, un `INNER JOIN` dégénère en `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>

#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="f54d0-135">Jointures externes gauches et jointures externes droites</span><span class="sxs-lookup"><span data-stu-id="f54d0-135">Left Outer Joins and Right Outer Joins</span></span>

<span data-ttu-id="f54d0-136">Une expression de requête `OUTER JOIN` génère un produit cartésien limité des deux collections, comme illustré dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f54d0-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

<span data-ttu-id="f54d0-137">L’expression de requête précédente traite une combinaison de chaque élément de la collection à gauche associé à chaque élément de la collection à droite, où la condition `ON` est vérifiée (True).</span><span class="sxs-lookup"><span data-stu-id="f54d0-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="f54d0-138">Si la condition `ON` n'est pas vérifiée (False), l'expression traite tout de même une instance unique de l'élément à gauche associé à l'élément à droite, avec la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="f54d0-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>

<span data-ttu-id="f54d0-139">Un `RIGHT OUTER JOIN` peut être exprimé de la même manière.</span><span class="sxs-lookup"><span data-stu-id="f54d0-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>

#### <a name="full-outer-joins"></a><span data-ttu-id="f54d0-140">Jointures externes entières</span><span class="sxs-lookup"><span data-stu-id="f54d0-140">Full Outer Joins</span></span>

<span data-ttu-id="f54d0-141">Un `FULL OUTER JOIN` explicite génère un produit cartésien limité des deux collections, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f54d0-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>

`FROM C AS c FULL OUTER JOIN D AS d ON e`

<span data-ttu-id="f54d0-142">L’expression de requête précédente traite une combinaison de chaque élément de la collection à gauche associé à chaque élément de la collection à droite, où la condition `ON` est vérifiée (True).</span><span class="sxs-lookup"><span data-stu-id="f54d0-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="f54d0-143">Si la condition `ON` n'est pas vérifiée (False), l'expression traite tout de même une instance de l'élément à gauche associé à l'élément à droite, avec la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="f54d0-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="f54d0-144">Il traite également une instance de l'élément à droite associé à l'élément à gauche, avec la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="f54d0-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>

> [!NOTE]
> <span data-ttu-id="f54d0-145">Pour préserver la compatibilité avec SQL-92, dans Transact-SQL, le mot clé OUTER est facultatif.</span><span class="sxs-lookup"><span data-stu-id="f54d0-145">To preserve compatibility with SQL-92, in Transact-SQL the OUTER keyword is optional.</span></span> <span data-ttu-id="f54d0-146">Par conséquent, `LEFT JOIN`, `RIGHT JOIN` et `FULL JOIN` sont synonymes de `LEFT OUTER JOIN`, `RIGHT OUTER JOIN` et `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>

### <a name="apply-clause-item"></a><span data-ttu-id="f54d0-147">Élément de clause APPLY</span><span class="sxs-lookup"><span data-stu-id="f54d0-147">APPLY Clause Item</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f54d0-148">prend en charge deux sortes de clauses `APPLY` : `CROSS APPLY` et `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>

<span data-ttu-id="f54d0-149">Un `CROSS APPLY` produit un appariement unique de chaque élément de la collection située à gauche avec un élément de la collection produite en évaluant l’expression située à droite.</span><span class="sxs-lookup"><span data-stu-id="f54d0-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="f54d0-150">Avec un `CROSS APPLY`, l’expression à droite dépend fonctionnellement de l’élément à gauche, comme illustré dans l’exemple de collection associé suivant :</span><span class="sxs-lookup"><span data-stu-id="f54d0-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

<span data-ttu-id="f54d0-151">Le comportement de `CROSS APPLY` est semblable à la liste de jointures.</span><span class="sxs-lookup"><span data-stu-id="f54d0-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="f54d0-152">Si l’expression à droite correspond à une collection vide, le `CROSS APPLY` ne produit pas d’appariement pour cette instance de l’élément à gauche.</span><span class="sxs-lookup"><span data-stu-id="f54d0-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>

<span data-ttu-id="f54d0-153">Un `OUTER APPLY` ressemble à un `CROSS APPLY`, excepté qu’un appariement est toujours produit même quand l’expression à droite correspond à une collection vide.</span><span class="sxs-lookup"><span data-stu-id="f54d0-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="f54d0-154">Voici un exemple de `OUTER APPLY` :</span><span class="sxs-lookup"><span data-stu-id="f54d0-154">The following is an example of an `OUTER APPLY`:</span></span>

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> <span data-ttu-id="f54d0-155">Contrairement à Transact-SQL, il n’est pas nécessaire d’effectuer une étape de non imbrication explicite dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f54d0-155">Unlike in Transact-SQL, there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="f54d0-156">`CROSS` les `OUTER APPLY` opérateurs et ont été introduits dans SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="f54d0-156">`CROSS` and `OUTER APPLY` operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="f54d0-157">Dans certains cas, le pipeline de requête peut produire une instruction Transact-SQL qui contient des opérateurs `CROSS APPLY` et/ou `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="f54d0-158">Dans la mesure où certains fournisseurs principaux, y compris les versions de SQL Server antérieures à SQL Server 2005, ne prennent pas en charge ces opérateurs, de telles requêtes ne peuvent pas être exécutées sur ces fournisseurs principaux.</span><span class="sxs-lookup"><span data-stu-id="f54d0-158">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>
>
> <span data-ttu-id="f54d0-159">Voici certains scénarios classiques susceptibles d’aboutir à la présence d’opérateurs `CROSS APPLY` et/ou `OUTER APPLY` dans la requête de sortie : une sous-requête corrélée avec la pagination, AnyElement sur une sous-requête corrélée ou sur une collection produite par navigation, requêtes LINQ qui utilisent des méthodes de regroupement acceptant un sélecteur d’élément, une requête dans laquelle un `CROSS APPLY` ou un `OUTER APPLY` sont spécifiés explicitement, une requête qui a une construction `DEREF` sur une construction `REF`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>

## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="f54d0-160">Collections multiples dans la clause FROM</span><span class="sxs-lookup"><span data-stu-id="f54d0-160">Multiple Collections in the FROM Clause</span></span>

<span data-ttu-id="f54d0-161">La clause `FROM` peut contenir plusieurs collections séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f54d0-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="f54d0-162">Dans ces cas particuliers, les collections sont supposées être jointes.</span><span class="sxs-lookup"><span data-stu-id="f54d0-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="f54d0-163">Considérez ces jointures comme des CROSS JOIN à n directions.</span><span class="sxs-lookup"><span data-stu-id="f54d0-163">Think of these as an n-way CROSS JOIN.</span></span>

<span data-ttu-id="f54d0-164">Dans l’exemple suivant, `C` et `D` sont des collections indépendantes, mais `c.Names` dépend de `C` .</span><span class="sxs-lookup"><span data-stu-id="f54d0-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>

```sql
FROM C AS c, D AS d, c.Names AS e
```

<span data-ttu-id="f54d0-165">L'exemple précédent équivaut logiquement à l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f54d0-165">The previous example is logically equivalent to the following example:</span></span>

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a><span data-ttu-id="f54d0-166">Corrélation de gauche</span><span class="sxs-lookup"><span data-stu-id="f54d0-166">Left Correlation</span></span>

 <span data-ttu-id="f54d0-167">Les éléments dans la clause `FROM` peuvent faire référence à des éléments spécifiés dans des clauses antérieures.</span><span class="sxs-lookup"><span data-stu-id="f54d0-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="f54d0-168">Dans l'exemple suivant, `C` et `D` sont des collections indépendantes, mais `c.Names` dépend de `C` :</span><span class="sxs-lookup"><span data-stu-id="f54d0-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>

```sql
from C as c, D as d, c.Names as e
```

<span data-ttu-id="f54d0-169">Cela équivaut logiquement à :</span><span class="sxs-lookup"><span data-stu-id="f54d0-169">This is logically equivalent to:</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a><span data-ttu-id="f54d0-170">Sémantique</span><span class="sxs-lookup"><span data-stu-id="f54d0-170">Semantics</span></span>

<span data-ttu-id="f54d0-171">Logiquement, les collections de la clause `FROM` sont supposées faire partie d’une jointure croisée à `n` directions (sauf dans le cas d’une jointure croisée unidirectionnelle).</span><span class="sxs-lookup"><span data-stu-id="f54d0-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="f54d0-172">Les alias de la clause `FROM` sont traités de gauche à droite et sont ajoutés à l'étendue actuelle pour référence ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f54d0-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="f54d0-173">La clause `FROM` est supposée produire un multiensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="f54d0-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="f54d0-174">Il y aura un champ pour chaque élément dans la clause `FROM` qui représente un élément unique de cet élément de collection.</span><span class="sxs-lookup"><span data-stu-id="f54d0-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>

<span data-ttu-id="f54d0-175">La clause `FROM` produit logiquement un multiensemble de lignes de type Row(c, d, e) où les champs c, d et e sont supposés être du type d'élément `C`, `D` et `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="f54d0-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f54d0-176">introduit un alias pour chaque élément de clause `FROM` simple de l'étendue.</span><span class="sxs-lookup"><span data-stu-id="f54d0-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="f54d0-177">Par exemple, dans l'extrait de clause FROM suivant, les noms introduits dans l'étendue sont c, d et e.</span><span class="sxs-lookup"><span data-stu-id="f54d0-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

<span data-ttu-id="f54d0-178">Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (contrairement à Transact-SQL), la `FROM` clause introduit uniquement les alias dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="f54d0-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike Transact-SQL), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="f54d0-179">Toutes les références à des colonnes (propriétés) de ces collections doivent être qualifiées avec l'alias.</span><span class="sxs-lookup"><span data-stu-id="f54d0-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>

## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="f54d0-180">Appel de clés à partir de requêtes imbriquées</span><span class="sxs-lookup"><span data-stu-id="f54d0-180">Pulling Up Keys from Nested Queries</span></span>

<span data-ttu-id="f54d0-181">Certains types des requêtes qui requièrent l'appel de clés à partir d'une requête imbriquée ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f54d0-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="f54d0-182">Par exemple, la requête suivante est valide :</span><span class="sxs-lookup"><span data-stu-id="f54d0-182">For example, the following query is valid:</span></span>

```sql
select c.Orders from Customers as c
```

<span data-ttu-id="f54d0-183">Toutefois, la requête suivante n'est pas valide, car la requête imbriquée n'a pas de clés :</span><span class="sxs-lookup"><span data-stu-id="f54d0-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a><span data-ttu-id="f54d0-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f54d0-184">See also</span></span>

- [<span data-ttu-id="f54d0-185">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f54d0-185">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f54d0-186">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="f54d0-186">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="f54d0-187">Types structurés Nullable</span><span class="sxs-lookup"><span data-stu-id="f54d0-187">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
