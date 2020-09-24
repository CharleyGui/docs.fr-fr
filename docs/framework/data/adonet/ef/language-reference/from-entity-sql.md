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
# <a name="from-entity-sql"></a>FROM (Entity SQL)

Spécifie la collection utilisée dans les instructions [Select](select-entity-sql.md) .

## <a name="syntax"></a>Syntaxe

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a>Arguments

`expression` \
Toute expression de requête valide qui produit une collection à utiliser comme source dans une instruction `SELECT`.

## <a name="remarks"></a>Notes

Une clause `FROM` est une liste séparée par des virgules d'un ou de plusieurs éléments de clause `FROM`. La clause `FROM` peut être utilisée pour spécifier une ou plusieurs sources pour une instruction `SELECT`. La forme la plus simple d’une clause `FROM` est une expression de requête unique qui identifie une collection et un alias utilisés comme source dans une instruction `SELECT`, comme illustré dans l’exemple suivant :

`FROM C as c`

## <a name="from-clause-items"></a>Éléments de clause FROM

Chaque élément de clause `FROM` fait référence à une collection source dans la requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge les classes d'éléments de clause `FROM` suivantes : éléments de clause `FROM` simples, éléments de clause `JOIN FROM` et éléments de clause `APPLY FROM`. Chacun de ces éléments de clause `FROM` est décrite en détail dans les sections suivantes.

### <a name="simple-from-clause-item"></a>Élément de clause FROM simple

L'élément de clause `FROM` le plus simple est une expression unique qui identifie une collection et un alias. L’expression peut être simplement un jeu d’entités, une sous-requête ou toute autre expression qui est un type collection. Par exemple :

```sql
LOB.Customers as c
```

La spécification d'un alias est facultative. Une autre spécification de l'élément de clause FROM pourrait être la suivante :

```sql
LOB.Customers
```

Si aucun alias n'est spécifié, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente d'en générer un basé sur l'expression de collection.

### <a name="join-from-clause-item"></a>Élément de clause JOIN FROM

Un élément de clause `JOIN FROM` représente une jointure entre deux éléments de clause `FROM`. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge les jointures croisées, les jointures internes, les jointures externes gauches et droites, ainsi que les jointures externes entières. Toutes ces jointures sont prises en charge de la même façon qu’elles sont prises en charge dans Transact-SQL. Comme dans Transact-SQL, les deux `FROM` éléments de clause impliqués dans le `JOIN` doivent être indépendants. Autrement dit, ils ne peuvent pas être corrélés. Un `CROSS APPLY` ou un `OUTER APPLY` peut être utilisé pour ces cas.

#### <a name="cross-joins"></a>Jointures croisées

Une expression de requête `CROSS JOIN` génère le produit cartésien des deux collections, comme illustré dans l’exemple suivant :

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>Jointures internes

Un `INNER JOIN` génère un produit cartésien limité des deux collections, comme illustré dans l’exemple suivant :

`FROM C AS c [INNER] JOIN D AS d ON e`

L’expression de requête précédente traite une combinaison de chaque élément de la collection à gauche associé à chaque élément de la collection à droite, où la condition `ON` est vérifiée (True). Si aucune condition `ON` n'est spécifiée, un `INNER JOIN` dégénère en `CROSS JOIN`.

#### <a name="left-outer-joins-and-right-outer-joins"></a>Jointures externes gauches et jointures externes droites

Une expression de requête `OUTER JOIN` génère un produit cartésien limité des deux collections, comme illustré dans l'exemple suivant :

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

L’expression de requête précédente traite une combinaison de chaque élément de la collection à gauche associé à chaque élément de la collection à droite, où la condition `ON` est vérifiée (True). Si la condition `ON` n'est pas vérifiée (False), l'expression traite tout de même une instance unique de l'élément à gauche associé à l'élément à droite, avec la valeur Null.

Un `RIGHT OUTER JOIN` peut être exprimé de la même manière.

#### <a name="full-outer-joins"></a>Jointures externes entières

Un `FULL OUTER JOIN` explicite génère un produit cartésien limité des deux collections, comme illustré dans l’exemple suivant :

`FROM C AS c FULL OUTER JOIN D AS d ON e`

L’expression de requête précédente traite une combinaison de chaque élément de la collection à gauche associé à chaque élément de la collection à droite, où la condition `ON` est vérifiée (True). Si la condition `ON` n'est pas vérifiée (False), l'expression traite tout de même une instance de l'élément à gauche associé à l'élément à droite, avec la valeur Null. Il traite également une instance de l'élément à droite associé à l'élément à gauche, avec la valeur Null.

> [!NOTE]
> Pour préserver la compatibilité avec SQL-92, dans Transact-SQL, le mot clé OUTER est facultatif. Par conséquent, `LEFT JOIN`, `RIGHT JOIN` et `FULL JOIN` sont synonymes de `LEFT OUTER JOIN`, `RIGHT OUTER JOIN` et `FULL OUTER JOIN`.

### <a name="apply-clause-item"></a>Élément de clause APPLY

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge deux sortes de clauses `APPLY` : `CROSS APPLY` et `OUTER APPLY`.

Un `CROSS APPLY` produit un appariement unique de chaque élément de la collection située à gauche avec un élément de la collection produite en évaluant l’expression située à droite. Avec un `CROSS APPLY`, l’expression à droite dépend fonctionnellement de l’élément à gauche, comme illustré dans l’exemple de collection associé suivant :

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

Le comportement de `CROSS APPLY` est semblable à la liste de jointures. Si l’expression à droite correspond à une collection vide, le `CROSS APPLY` ne produit pas d’appariement pour cette instance de l’élément à gauche.

Un `OUTER APPLY` ressemble à un `CROSS APPLY`, excepté qu’un appariement est toujours produit même quand l’expression à droite correspond à une collection vide. Voici un exemple de `OUTER APPLY` :

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> Contrairement à Transact-SQL, il n’est pas nécessaire d’effectuer une étape de non imbrication explicite dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .

> [!NOTE]
> `CROSS` les `OUTER APPLY` opérateurs et ont été introduits dans SQL Server 2005. Dans certains cas, le pipeline de requête peut produire une instruction Transact-SQL qui contient des opérateurs `CROSS APPLY` et/ou `OUTER APPLY`. Dans la mesure où certains fournisseurs principaux, y compris les versions de SQL Server antérieures à SQL Server 2005, ne prennent pas en charge ces opérateurs, de telles requêtes ne peuvent pas être exécutées sur ces fournisseurs principaux.
>
> Voici certains scénarios classiques susceptibles d’aboutir à la présence d’opérateurs `CROSS APPLY` et/ou `OUTER APPLY` dans la requête de sortie : une sous-requête corrélée avec la pagination, AnyElement sur une sous-requête corrélée ou sur une collection produite par navigation, requêtes LINQ qui utilisent des méthodes de regroupement acceptant un sélecteur d’élément, une requête dans laquelle un `CROSS APPLY` ou un `OUTER APPLY` sont spécifiés explicitement, une requête qui a une construction `DEREF` sur une construction `REF`.

## <a name="multiple-collections-in-the-from-clause"></a>Collections multiples dans la clause FROM

La clause `FROM` peut contenir plusieurs collections séparées par des virgules. Dans ces cas particuliers, les collections sont supposées être jointes. Considérez ces jointures comme des CROSS JOIN à n directions.

Dans l’exemple suivant, `C` et `D` sont des collections indépendantes, mais `c.Names` dépend de `C` .

```sql
FROM C AS c, D AS d, c.Names AS e
```

L'exemple précédent équivaut logiquement à l'exemple suivant :

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Corrélation de gauche

 Les éléments dans la clause `FROM` peuvent faire référence à des éléments spécifiés dans des clauses antérieures. Dans l'exemple suivant, `C` et `D` sont des collections indépendantes, mais `c.Names` dépend de `C` :

```sql
from C as c, D as d, c.Names as e
```

Cela équivaut logiquement à :

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>Sémantique

Logiquement, les collections de la clause `FROM` sont supposées faire partie d’une jointure croisée à `n` directions (sauf dans le cas d’une jointure croisée unidirectionnelle). Les alias de la clause `FROM` sont traités de gauche à droite et sont ajoutés à l'étendue actuelle pour référence ultérieure. La clause `FROM` est supposée produire un multiensemble de lignes. Il y aura un champ pour chaque élément dans la clause `FROM` qui représente un élément unique de cet élément de collection.

La clause `FROM` produit logiquement un multiensemble de lignes de type Row(c, d, e) où les champs c, d et e sont supposés être du type d'élément `C`, `D` et `c.Names`.

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduit un alias pour chaque élément de clause `FROM` simple de l'étendue. Par exemple, dans l'extrait de clause FROM suivant, les noms introduits dans l'étendue sont c, d et e.

```sql
from (C as c join D as d) cross apply c.Names as e
```

Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (contrairement à Transact-SQL), la `FROM` clause introduit uniquement les alias dans l’étendue. Toutes les références à des colonnes (propriétés) de ces collections doivent être qualifiées avec l'alias.

## <a name="pulling-up-keys-from-nested-queries"></a>Appel de clés à partir de requêtes imbriquées

Certains types des requêtes qui requièrent l'appel de clés à partir d'une requête imbriquée ne sont pas pris en charge. Par exemple, la requête suivante est valide :

```sql
select c.Orders from Customers as c
```

Toutefois, la requête suivante n'est pas valide, car la requête imbriquée n'a pas de clés :

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Expressions de requête](query-expressions-entity-sql.md)
- [Types structurés Nullable](nullable-structured-types-entity-sql.md)
