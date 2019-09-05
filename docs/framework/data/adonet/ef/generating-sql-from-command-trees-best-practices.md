---
title: Génération SQL à partir d'arborescences de commandes - meilleures pratiques
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 366e27f8c8a04c5d2507ab37459ad6d5abc255ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251573"
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Génération SQL à partir d'arborescences de commandes - meilleures pratiques

Les arborescences de commandes de requête de sortie modèlent de façon précise les requêtes pouvant être exprimées en SQL. Toutefois, les développeurs de fournisseur sont confrontés à des problèmes courants lors de la génération SQL d’une arborescence de commandes de sortie. Cette rubrique expose ces difficultés. Dans la rubrique suivante, le fournisseur d'exemples indique comment résoudre ces problèmes.

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Grouper des nœuds DbExpression dans une instruction SQL SELECT

Une instruction SQL type possède une structure imbriquée de la forme suivante :

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

Une ou plusieurs clauses peuvent être vides.  Une instruction SELECT imbriquée peut se produire dans une des lignes.

Une éventuelle traduction d’une arborescence de commandes de requête en instruction SQL SELECT produirait une sous-requête pour chaque opérateur de relation. Cela entraîne toutefois des sous-requêtes imbriquées inutiles et difficiles à lire.  Dans certaines banques de données, la requête risque de mal s'effectuer.

Prenons comme exemple l’arborescence de commandes de requête suivante.

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

Une traduction inefficace produit :

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

Notez que chaque nœud d'expression relationnelle devient une nouvelle instruction SQL SELECT.

Il est donc important de regrouper autant de nœuds d'expression que possible en une instruction SQL SELECT unique tout en préservant leur exactitude.

Cette agrégation pour l'exemple présenté ci-dessus aurait pour résultat :

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a>Aplanir des jointures dans une instruction SQL SELECT

Un cas d'agrégation de plusieurs nœuds en une instruction SQL SELECT unique consiste en l'agrégation de plusieurs expressions de jointure en une instruction SQL SELECT unique. DbJoinExpression représente une jointure unique entre deux entrées. Dans le cadre d'une instruction SQL SELECT unique, plusieurs jointures peuvent toutefois être spécifiées. Dans ce cas les jointures sont effectuées dans l'ordre spécifié.

Les jointures externes à gauche (jointures qui apparaissent en tant qu'enfant gauche d'une autre jointure) peuvent être aplanies plus facilement dans une instruction SQL SELECT unique. Prenons comme exemple l’arborescence de commandes de requête suivante :

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

Cela peut être traduit correctement par :

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

Toutefois, les jointures externes qui ne sont pas à gauche ne sont pas faciles à aplanir et vous ne devez pas essayer de le faire. Par exemple, les jointures dans l'arborescence de commandes de requête suivante :

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

se traduirait en une instruction SQL SELECT avec une sous-requête.

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a>Redirection d'alias d'entrée

Pour expliquer la redirection d'alias d'entrée, considérez la structure des expressions relationnelles, telles que DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression et DbSkipExpression.

Chacun de ces types possède une ou plusieurs propriétés Input qui décrivent une collection d'entrée. Une variable de liaison correspondant à chaque entrée est utilisée pour représenter chaque élément de cette entrée pendant la traversée d'une collection. La variable de liaison est utilisée en cas de référence à l'élément d'entrée, par exemple dans la propriété Predicate d'un DbFilterExpression ou la propriété Projection d'un DbProjectExpression.

Lors de l’agrégation de nœuds d’expression relationnelle supplémentaires en instruction SQL SELECT unique et lors de l’évaluation d’une expression appartenant à une expression relationnelle (par exemple faisant partie de la propriété Projection d’un DbProjectExpression), la variable de liaison utilisée risque de ne pas être identique à l’alias de l’entrée, étant donné que plusieurs liaisons d’expression doivent être redirigées vers une étendue unique.  Ce problème s'appelle le changement de nom d'alias.

Prenons le premier exemple de cette rubrique. Si nous effectuons une traduction naïve et que nous traduisons Projection a.x (DbPropertyExpression (a, x)), il est correct de le traduire par `a.x` parce que nous avons attribué à l’entrée « a » comme alias pour correspondre à la variable de liaison.  Toutefois, lorsque vous regroupez les deux nœuds dans une instruction SQL SELECT unique, vous devez traduire le même DbPropertyExpression en `b.x`, car l'entrée a « b » pour alias.

## <a name="join-alias-flattening"></a>Aplanissement d'alias de jointure

Contrairement à toute autre expression relationnelle dans une arborescence de commandes de sortie, DbJoinExpression produit un type de résultat qui consiste en une ligne composée de deux colonnes, chacune correspondant à l’une des entrées. Lorsqu’un DbPropertyExpression est créé pour accéder à une propriété scalaire provenant d’une jointure, il se trouve sur un autre DbPropertyExpression.

Les exemples incluent « a.b.y » dans l'exemple 2 et « b.c.y » dans l'exemple 3. Toutefois dans les instructions SQL correspondantes, ils sont référencés en tant que « b.y ». Cette redéfinition d'alias est appelée aplanissement d'alias de jointure.

## <a name="column-name-and-extent-alias-renaming"></a>Changement du nom de colonne et du nom d'alias d'étendue

Si une requête SQL SELECT ayant une jointure doit être exécutée avec une projection, lors de l'énumération de toutes les colonnes participantes des entrées, un conflit de noms peut se produire, si plusieurs entrées ont le même nom de colonne. Utilisez un nom différent pour la colonne afin d'éviter le conflit.

Lors de l'aplanissement des jointures, les tables participantes (ou sous-requêtes) peuvent également avoir des conflits d'alias, auquel cas elles doivent être renommées.

## <a name="avoid-select-"></a>Éviter SELECT *

N'utilisez pas `SELECT *` pour sélectionner des tables de base. Le modèle de stockage d' [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] une application ne peut inclure qu’un sous-ensemble des colonnes qui se trouvent dans la table de base de données. Dans ce cas, `SELECT *` peut produire un résultat incorrect. À la place, vous devez spécifier toutes les colonnes participantes en utilisant les noms de colonne du type de résultat des expressions participantes.

## <a name="reuse-of-expressions"></a>Réutilisation d'expressions

Les expressions peuvent être réutilisées dans l’arborescence de commandes de requête transmise par [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Ne partez pas du principe que chaque expression apparaît une seule fois que dans l’arborescence de commandes de requête.

## <a name="mapping-primitive-types"></a>Mappage de types primitifs

Lorsque vous mappez des types conceptuels (EDM) à des types de fournisseur, vous devez mapper au type le plus large (Int32) afin que toutes les valeurs possibles puissent correspondre. Évitez également de mapper aux types qui ne peuvent pas être utilisés pour de nombreuses opérations, comme les types d' `ntext` objets BLOB (par exemple, dans SQL Server).

## <a name="see-also"></a>Voir aussi

- [Génération SQL](sql-generation.md)
