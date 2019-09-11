---
title: Génération SQL à partir d'arborescences de commandes - meilleures pratiques
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 9859c7df941ae6681c991001e0d1e5a50c7ffc60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855001"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="b0499-102">Génération SQL à partir d'arborescences de commandes - meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="b0499-102">Generating SQL from Command Trees - Best Practices</span></span>

<span data-ttu-id="b0499-103">Les arborescences de commandes de requête de sortie modèlent de façon précise les requêtes pouvant être exprimées en SQL.</span><span class="sxs-lookup"><span data-stu-id="b0499-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="b0499-104">Toutefois, les développeurs de fournisseur sont confrontés à des problèmes courants lors de la génération SQL d’une arborescence de commandes de sortie.</span><span class="sxs-lookup"><span data-stu-id="b0499-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="b0499-105">Cette rubrique expose ces difficultés.</span><span class="sxs-lookup"><span data-stu-id="b0499-105">This topic discusses these challenges.</span></span> <span data-ttu-id="b0499-106">Dans la rubrique suivante, le fournisseur d'exemples indique comment résoudre ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="b0499-106">In the next topic, the sample provider shows how to address these challenges.</span></span>

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="b0499-107">Grouper des nœuds DbExpression dans une instruction SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="b0499-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>

<span data-ttu-id="b0499-108">Une instruction SQL type possède une structure imbriquée de la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="b0499-108">A typical SQL statement has a nested structure of the following shape:</span></span>

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

<span data-ttu-id="b0499-109">Une ou plusieurs clauses peuvent être vides.</span><span class="sxs-lookup"><span data-stu-id="b0499-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="b0499-110">Une instruction SELECT imbriquée peut se produire dans une des lignes.</span><span class="sxs-lookup"><span data-stu-id="b0499-110">A nested SELECT statement could occur in any of the lines.</span></span>

<span data-ttu-id="b0499-111">Une éventuelle traduction d’une arborescence de commandes de requête en instruction SQL SELECT produirait une sous-requête pour chaque opérateur de relation.</span><span class="sxs-lookup"><span data-stu-id="b0499-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="b0499-112">Cela entraîne toutefois des sous-requêtes imbriquées inutiles et difficiles à lire.</span><span class="sxs-lookup"><span data-stu-id="b0499-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="b0499-113">Dans certaines banques de données, la requête risque de mal s'effectuer.</span><span class="sxs-lookup"><span data-stu-id="b0499-113">On some data stores, the query may perform poorly.</span></span>

<span data-ttu-id="b0499-114">Prenons comme exemple l’arborescence de commandes de requête suivante.</span><span class="sxs-lookup"><span data-stu-id="b0499-114">As an example, consider the following query command tree</span></span>

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

<span data-ttu-id="b0499-115">Une traduction inefficace produit :</span><span class="sxs-lookup"><span data-stu-id="b0499-115">An inefficient translation would produce:</span></span>

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

<span data-ttu-id="b0499-116">Notez que chaque nœud d'expression relationnelle devient une nouvelle instruction SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="b0499-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>

<span data-ttu-id="b0499-117">Il est donc important de regrouper autant de nœuds d'expression que possible en une instruction SQL SELECT unique tout en préservant leur exactitude.</span><span class="sxs-lookup"><span data-stu-id="b0499-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>

<span data-ttu-id="b0499-118">Cette agrégation pour l'exemple présenté ci-dessus aurait pour résultat :</span><span class="sxs-lookup"><span data-stu-id="b0499-118">The result of such aggregation for the example presented above would be:</span></span>

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="b0499-119">Aplanir des jointures dans une instruction SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="b0499-119">Flatten Joins in a SQL SELECT Statement</span></span>

<span data-ttu-id="b0499-120">Un cas d'agrégation de plusieurs nœuds en une instruction SQL SELECT unique consiste en l'agrégation de plusieurs expressions de jointure en une instruction SQL SELECT unique.</span><span class="sxs-lookup"><span data-stu-id="b0499-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="b0499-121">DbJoinExpression représente une jointure unique entre deux entrées.</span><span class="sxs-lookup"><span data-stu-id="b0499-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="b0499-122">Dans le cadre d'une instruction SQL SELECT unique, plusieurs jointures peuvent toutefois être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b0499-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="b0499-123">Dans ce cas les jointures sont effectuées dans l'ordre spécifié.</span><span class="sxs-lookup"><span data-stu-id="b0499-123">In that case the joins are performed in the order specified.</span></span>

<span data-ttu-id="b0499-124">Les jointures externes à gauche (jointures qui apparaissent en tant qu'enfant gauche d'une autre jointure) peuvent être aplanies plus facilement dans une instruction SQL SELECT unique.</span><span class="sxs-lookup"><span data-stu-id="b0499-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="b0499-125">Prenons comme exemple l’arborescence de commandes de requête suivante :</span><span class="sxs-lookup"><span data-stu-id="b0499-125">For example, consider the following query command tree:</span></span>

```
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

<span data-ttu-id="b0499-126">Cela peut être traduit correctement par :</span><span class="sxs-lookup"><span data-stu-id="b0499-126">This can be correctly translated into:</span></span>

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

<span data-ttu-id="b0499-127">Toutefois, les jointures externes qui ne sont pas à gauche ne sont pas faciles à aplanir et vous ne devez pas essayer de le faire.</span><span class="sxs-lookup"><span data-stu-id="b0499-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="b0499-128">Par exemple, les jointures dans l'arborescence de commandes de requête suivante :</span><span class="sxs-lookup"><span data-stu-id="b0499-128">For example, the joins in the following query command tree:</span></span>

```
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

<span data-ttu-id="b0499-129">se traduirait en une instruction SQL SELECT avec une sous-requête.</span><span class="sxs-lookup"><span data-stu-id="b0499-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a><span data-ttu-id="b0499-130">Redirection d'alias d'entrée</span><span class="sxs-lookup"><span data-stu-id="b0499-130">Input Alias Redirecting</span></span>

<span data-ttu-id="b0499-131">Pour expliquer la redirection d'alias d'entrée, considérez la structure des expressions relationnelles, telles que DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression et DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="b0499-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>

<span data-ttu-id="b0499-132">Chacun de ces types possède une ou plusieurs propriétés Input qui décrivent une collection d'entrée. Une variable de liaison correspondant à chaque entrée est utilisée pour représenter chaque élément de cette entrée pendant la traversée d'une collection.</span><span class="sxs-lookup"><span data-stu-id="b0499-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="b0499-133">La variable de liaison est utilisée en cas de référence à l'élément d'entrée, par exemple dans la propriété Predicate d'un DbFilterExpression ou la propriété Projection d'un DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="b0499-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>

<span data-ttu-id="b0499-134">Lors de l’agrégation de nœuds d’expression relationnelle supplémentaires en instruction SQL SELECT unique et lors de l’évaluation d’une expression appartenant à une expression relationnelle (par exemple faisant partie de la propriété Projection d’un DbProjectExpression), la variable de liaison utilisée risque de ne pas être identique à l’alias de l’entrée, étant donné que plusieurs liaisons d’expression doivent être redirigées vers une étendue unique.</span><span class="sxs-lookup"><span data-stu-id="b0499-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="b0499-135">Ce problème s'appelle le changement de nom d'alias.</span><span class="sxs-lookup"><span data-stu-id="b0499-135">This problem is called alias renaming.</span></span>

<span data-ttu-id="b0499-136">Prenons le premier exemple de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b0499-136">Consider the first example in this topic.</span></span> <span data-ttu-id="b0499-137">Si nous effectuons une traduction naïve et que nous traduisons Projection a.x (DbPropertyExpression (a, x)), il est correct de le traduire par `a.x` parce que nous avons attribué à l’entrée « a » comme alias pour correspondre à la variable de liaison.</span><span class="sxs-lookup"><span data-stu-id="b0499-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="b0499-138">Toutefois, lorsque vous regroupez les deux nœuds dans une instruction SQL SELECT unique, vous devez traduire le même DbPropertyExpression en `b.x`, car l'entrée a « b » pour alias.</span><span class="sxs-lookup"><span data-stu-id="b0499-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>

## <a name="join-alias-flattening"></a><span data-ttu-id="b0499-139">Aplanissement d'alias de jointure</span><span class="sxs-lookup"><span data-stu-id="b0499-139">Join Alias Flattening</span></span>

<span data-ttu-id="b0499-140">Contrairement à toute autre expression relationnelle dans une arborescence de commandes de sortie, DbJoinExpression produit un type de résultat qui consiste en une ligne composée de deux colonnes, chacune correspondant à l’une des entrées.</span><span class="sxs-lookup"><span data-stu-id="b0499-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="b0499-141">Lorsqu’un DbPropertyExpression est créé pour accéder à une propriété scalaire provenant d’une jointure, il se trouve sur un autre DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="b0499-141">When a DbPropertyExpression is built to access a scalar property originating from a join, it is over another DbPropertyExpression.</span></span>

<span data-ttu-id="b0499-142">Les exemples incluent « a.b.y » dans l'exemple 2 et « b.c.y » dans l'exemple 3.</span><span class="sxs-lookup"><span data-stu-id="b0499-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="b0499-143">Toutefois dans les instructions SQL correspondantes, ils sont référencés en tant que « b.y ».</span><span class="sxs-lookup"><span data-stu-id="b0499-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="b0499-144">Cette redéfinition d'alias est appelée aplanissement d'alias de jointure.</span><span class="sxs-lookup"><span data-stu-id="b0499-144">This re-aliasing is called join alias flattening.</span></span>

## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="b0499-145">Changement du nom de colonne et du nom d'alias d'étendue</span><span class="sxs-lookup"><span data-stu-id="b0499-145">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="b0499-146">Si une requête SQL SELECT ayant une jointure doit être exécutée avec une projection, lors de l'énumération de toutes les colonnes participantes des entrées, un conflit de noms peut se produire, si plusieurs entrées ont le même nom de colonne.</span><span class="sxs-lookup"><span data-stu-id="b0499-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="b0499-147">Utilisez un nom différent pour la colonne afin d'éviter le conflit.</span><span class="sxs-lookup"><span data-stu-id="b0499-147">Use a different name for the column to avoid the collision.</span></span>

<span data-ttu-id="b0499-148">Lors de l'aplanissement des jointures, les tables participantes (ou sous-requêtes) peuvent également avoir des conflits d'alias, auquel cas elles doivent être renommées.</span><span class="sxs-lookup"><span data-stu-id="b0499-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>

## <a name="avoid-select-"></a><span data-ttu-id="b0499-149">Éviter SELECT \*</span><span class="sxs-lookup"><span data-stu-id="b0499-149">Avoid SELECT \*</span></span>

<span data-ttu-id="b0499-150">N'utilisez pas `SELECT *` pour sélectionner des tables de base.</span><span class="sxs-lookup"><span data-stu-id="b0499-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="b0499-151">Le modèle de stockage d’une application Entity Framework ne peut inclure qu’un sous-ensemble des colonnes qui se trouvent dans la table de base de données.</span><span class="sxs-lookup"><span data-stu-id="b0499-151">The storage model in an Entity Framework application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="b0499-152">Dans ce cas, `SELECT *` peut produire un résultat incorrect.</span><span class="sxs-lookup"><span data-stu-id="b0499-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="b0499-153">À la place, vous devez spécifier toutes les colonnes participantes en utilisant les noms de colonne du type de résultat des expressions participantes.</span><span class="sxs-lookup"><span data-stu-id="b0499-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>

## <a name="reuse-of-expressions"></a><span data-ttu-id="b0499-154">Réutilisation d'expressions</span><span class="sxs-lookup"><span data-stu-id="b0499-154">Reuse of Expressions</span></span>

<span data-ttu-id="b0499-155">Les expressions peuvent être réutilisées dans l’arborescence de commandes de requête transmise par l’Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b0499-155">Expressions may be reused in the query command tree passed by the Entity Framework.</span></span> <span data-ttu-id="b0499-156">Ne partez pas du principe que chaque expression apparaît une seule fois que dans l’arborescence de commandes de requête.</span><span class="sxs-lookup"><span data-stu-id="b0499-156">Do not assume that each expression appears only once in the query command tree.</span></span>

## <a name="mapping-primitive-types"></a><span data-ttu-id="b0499-157">Mappage de types primitifs</span><span class="sxs-lookup"><span data-stu-id="b0499-157">Mapping Primitive Types</span></span>

<span data-ttu-id="b0499-158">Lorsque vous mappez des types conceptuels (EDM) à des types de fournisseur, vous devez mapper au type le plus large (Int32) afin que toutes les valeurs possibles puissent correspondre.</span><span class="sxs-lookup"><span data-stu-id="b0499-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="b0499-159">Évitez également de mapper aux types qui ne peuvent pas être utilisés pour de nombreuses opérations, comme les types d' `ntext` objets BLOB (par exemple, dans SQL Server).</span><span class="sxs-lookup"><span data-stu-id="b0499-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0499-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0499-160">See also</span></span>

- [<span data-ttu-id="b0499-161">Génération SQL</span><span class="sxs-lookup"><span data-stu-id="b0499-161">SQL Generation</span></span>](sql-generation.md)
