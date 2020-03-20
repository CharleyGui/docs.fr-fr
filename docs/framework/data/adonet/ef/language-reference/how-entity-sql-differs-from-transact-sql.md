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
# <a name="how-entity-sql-differs-from-transact-sql"></a>Différences entre Entity SQL et Transact-SQL
Ce sujet décrit les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] différences entre Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Héritage et prise en charge des relations  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]travaille directement avec les schémas d’entités conceptuelles et prend en charge les caractéristiques conceptuelles du modèle telles que l’héritage et les relations.  
  
 Lors de l’utilisation de l’héritage, il est souvent utile de sélectionner des instances d’un sous-type à partir d’une collection d’instances de supertype. [L’opérateur oftype](oftype-entity-sql.md) (semblable [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à `oftype` dans les séquences C) fournit cette capacité.  
  
## <a name="support-for-collections"></a>Prise en charge des collections  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traite les collections en tant qu’entités de première classe. Par exemple :  
  
- Les expressions de collection sont valides dans une clause `from`.  
  
- Les sous-requêtes `in` et `exists` ont été généralisées pour autoriser toute collection.  
  
     Une sous-requête est un type de collection. `e1 in e2` et `exists(e)` sont les constructions [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui permettent d'effectuer ces opérations.  
  
- Les opérations de définition, telles que `union`, `intersect` et `except`, s’appliquent à présent aux collections.  
  
- Les jointures s’appliquent aux collections.  
  
## <a name="support-for-expressions"></a>Prise en charge des expressions  
 Transact-SQL a des sous-ques (tables) et des expressions (lignes et colonnes).  
  
 Soutenir les collections et [!INCLUDE[esql](../../../../../../includes/esql-md.md)] les collections imbriquées, tout fait une expression. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]est plus composable que Transact-SQL, chaque expression peut être utilisée n’importe où. Les expressions de requête génèrent toujours des collections des types projetés et peuvent être utilisées partout où une expression de collection est autorisée. Pour plus d’informations sur les expressions [!INCLUDE[esql](../../../../../../includes/esql-md.md)]De Transact-SQL qui ne sont pas prises en charge, voir [Expressions non soutenues](unsupported-expressions-entity-sql.md).  
  
 Les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivantes sont toutes valides :  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Traitement uniforme des sous-requêtes  
 Compte tenu de l’accent mis sur les tableaux, Transact-SQL effectue une interprétation contextuelle des sous-ques. Par exemple, une sous-fertilité dans la `from` clause est considérée comme un multicart (tableau). En revanche, la même sous-requête utilisée dans la clause `select` est considérée comme une sous-requête scalaire. De même, une sous-fertilité utilisée `in` sur le côté gauche d’un opérateur est considérée comme une sous-querie scalaire, tandis que le côté droit devrait être une sous-fertilité multi-ensemble.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] élimine ces différences. Une expression a une interprétation uniforme qui ne dépend pas du contexte dans lequel elle est utilisée. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]considère toutes les sous-ques comme des sous-ques multiseques. Si une valeur scalaire est souhaitée [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à `anyelement` partir de la sous-querie, fournit l’opérateur qui fonctionne sur une collection (dans ce cas, la sous-querie), et extrait une valeur singleton de la collection.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Éviter des contraintes implicites pour les sous-requêtes  
 Un effet secondaire connexe du traitement uniforme des sous-requêtes est la conversion implicite des sous-requêtes en valeurs scalaires. Plus précisément, dans Transact-SQL, un multi-ensemble de lignes (avec un seul champ) est implicitement converti en une valeur scalaire dont le type de données est celui du champ.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge cette contrainte implicite. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit l'opérateur ANYELEMENT pour extraire une valeur singleton d'une collection et une clause `select value` pour éviter de créer un wrapper de ligne pendant une expression de requête.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select Value : éviter le wrapper de ligne implicite  
 La clause de sélection dans une sous-fertilité Transact-SQL crée implicitement un emballage de ligne autour des éléments de la clause. Cela implique que nous ne pouvons pas créer de collections de scalaires ou d’objets. La transact-SQL permet une coercition implicite entre un tapageur avec un champ, et une valeur singleton du même type de données.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit la clause `select value` pour ignorer la construction de ligne implicite. Un seul élément peut être spécifié dans une clause `select value`. Lorsqu’une telle clause est utilisée, aucun wrapper de ligne n’est construit autour des éléments de la clause `select` et une collection de la forme souhaitée peut être générée, par exemple : `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit également le constructeur de ligne pour construire des lignes arbitraires. `select` accepte un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, comme suit :  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Corrélation gauche et utilisation d'alias  
 Dans l’article de Transact-SQL, les `select` expressions `from`d’une portée donnée (une seule clause comme ou ) ne peuvent pas faire référence à des expressions définies plus tôt dans la même portée. Certains dialectes de SQL (y compris Transact-SQL) `from` supportent des formes limitées de ceux-ci dans la clause.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]généralise les corrélations `from` laissées dans la clause et les traite uniformément. Les expressions dans la clause `from` peuvent référencer des définitions antérieures (définitions à gauche) dans la même clause sans nécessiter une syntaxe supplémentaire.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] impose également des restrictions supplémentaires sur les requêtes qui impliquent des clauses `group by`. Les expressions `select` de `having` la clause et de la `group by` clause de ces requêtes ne peuvent se référer qu’aux clés via leurs pseudonymes. La construction suivante est valable dans Transact-SQL mais ne sont pas dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Pour effectuer cette opération dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Référencement de colonnes (propriétés) de tables (collections)  
 Toutes les références de colonne dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doivent être qualifiées avec l'alias de la table. La construction suivante `a` (en supposant `T`qu’il s’agit d’une [!INCLUDE[esql](../../../../../../includes/esql-md.md)]colonne de table valide) est valable dans Transact-SQL mais pas dans .  
  
```sql  
SELECT a FROM T
```  
  
 La forme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est :  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Les alias de la table sont facultatifs dans la clause `from`. Le nom de la table est utilisé comme alias implicite. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] autorise également la forme suivante :  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Navigation dans les objets  
 Transact-SQL utilise la notation "." pour le référencement des colonnes de (une rangée de) une table. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] étend cette notation (empruntée des langages de programmation) pour prendre en charge la navigation dans les propriétés d'un objet.  
  
 Par exemple, si `p` est une expression de type Person, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous référence la ville de l'adresse de cette personne.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Aucune prise en charge pour *  
 La transact-SQL prend en charge la syntaxe non qualifiée \* comme un alias\*pour l’ensemble de la rangée, et la syntaxe qualifiée (t. ) comme un raccourci pour les champs de cette table. De plus, Transact-SQL permet un\*compte spécial( ) agrégat, qui comprend des nuls.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge la construction *. Questions de Transact-SQL `select * from T` de `select T1.* from T1, T2...` la forme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` et `select value t1 from T1 as t1, T2 as t2...`peut être exprimée dans comme et , respectivement. En outre, ces constructions gèrent l'héritage (capacité des valeurs à être substituées), tandis que les variantes `select *` sont restreintes aux propriétés de niveau supérieur du type déclaré.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge l'agrégat `count(*)`. Utilisez `count(0)` à la place.  
  
## <a name="changes-to-group-by"></a>Modifications apportées à Group By  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge les alias des clés `group by`. Les expressions dans la clause `select` et la clause `having` doivent faire référence aux clés `group by` par le biais de ces alias. Par exemple, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... est équivalent à la Transact-SQL suivante :  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Agrégats basés sur des collections  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge deux types d'agrégats.  
  
 Les agrégats basés sur des collections opèrent sur des collections et produisent le résultat agrégé. Ils peuvent apparaître n'importe où dans la requête et ne requièrent pas de clause `group by`. Par exemple :  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend également en charge les agrégats de style SQL. Par exemple :  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Utilisation des clauses ORDER BY  
Transact-SQL `ORDER BY` permet de préciser les clauses `SELECT .. FROM .. WHERE` uniquement dans le bloc le plus élevé. En [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vous pouvez utiliser `ORDER BY` une expression imbriquée et il peut être placé n’importe où dans la requête, mais la commande dans une requête imbriquée n’est pas préservée.  
  
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
  
## <a name="identifiers"></a>Identificateurs  
 Dans Transaction-SQL, la comparaison des identifiants est basée sur la compilation de la base de données actuelle. Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les identificateurs respectent toujours la casse et les accents (autrement dit, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distingue les caractères accentués et non accentués ; par exemple, « a » n'est pas égal à « à »). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traite les versions des lettres qui apparaissent identiques mais qui proviennent de pages de codes différentes comme des caractères différents. Pour plus d’informations, voir [Input Character Set](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Fonctionnalités Transact-SQL non disponibles dans Entity SQL  
 La fonctionnalité Transact-SQL suivante n’est pas disponible en [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]actuellement ne fournit aucun support pour les instructions DML (insert, mise à jour, supprimer).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit aucune prise en charge pour DDL dans la version actuelle.  
  
 Programmation impérative  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ne fournit aucun soutien à la programmation impérative, contrairement à Transact-SQL. Utilisez un langage de programmation à la place.  
  
 Fonctions de regroupement  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas encore de prise en charge pour les fonctions de regroupement (par exemple, CUBE, ROLLUP et GROUPING_SET).  
  
 Fonctions analytiques  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas (encore) de prise en charge pour les fonctions analytiques.  
  
 Fonctions et opérateurs intégrés  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]prend en charge un sous-ensemble de Transact-SQL construits dans des fonctions et des opérateurs. Ces opérateurs et ces fonctions seront vraisemblablement pris en charge par les principaux fournisseurs de stockage. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]utilise les fonctions spécifiques au magasin déclarées dans un manifeste du fournisseur. En outre, le cadre d’entité vous permet de déclarer les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fonctions de magasin existantes intégrées et définies par l’utilisateur, pour l’utiliser.  
  
 Indicateurs  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas de mécanismes pour les indicateurs de requête.  
  
 Résultats d'une requête de traitement par lot  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge les résultats d'une requête de traitement par lot. Par exemple, ce qui suit est valide Transact-SQL (envoi sous forme de lot) :  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Toutefois, l'équivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas pris en charge :  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend uniquement en charge une seule instruction de requête générant un résultat par commande.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
- [Expressions non prises en charge](unsupported-expressions-entity-sql.md)
