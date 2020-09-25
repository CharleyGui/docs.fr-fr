---
title: Différences entre Entity SQL et Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 9433e7a7ffdc3a7e32900981dca95eefde32f290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204435"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Différences entre Entity SQL et Transact-SQL

Cet article décrit les différences entre Entity SQL et Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Héritage et prise en charge des relations  

 Entity SQL fonctionne directement avec les schémas d’entité conceptuels et prend en charge des fonctionnalités de modèle conceptuel telles que l’héritage et les relations.  
  
 Lors de l’utilisation de l’héritage, il est souvent utile de sélectionner des instances d’un sous-type à partir d’une collection d’instances de supertype. L’opérateur [OfType](oftype-entity-sql.md) dans Entity SQL (semblable à `oftype` dans les séquences C#) fournit cette fonctionnalité.  
  
## <a name="support-for-collections"></a>Prise en charge des collections  

 Entity SQL traite les collections comme des entités de première classe. Par exemple :  
  
- Les expressions de collection sont valides dans une clause `from`.  
  
- Les sous-requêtes `in` et `exists` ont été généralisées pour autoriser toute collection.  
  
     Une sous-requête est un type de collection. `e1 in e2` et `exists(e)` sont les constructions de Entity SQL pour effectuer ces opérations.  
  
- Les opérations de définition, telles que `union`, `intersect` et `except`, s’appliquent à présent aux collections.  
  
- Les jointures s’appliquent aux collections.  
  
## <a name="support-for-expressions"></a>Prise en charge des expressions  

 Transact-SQL contient des sous-requêtes (tables) et des expressions (lignes et colonnes).  
  
 Pour prendre en charge les collections et les collections imbriquées, Entity SQL transforme tout en une expression. Entity SQL est plus composable que Transact-SQL, chaque expression peut être utilisée n’importe où. Les expressions de requête génèrent toujours des collections des types projetés et peuvent être utilisées partout où une expression de collection est autorisée. Pour plus d’informations sur les expressions Transact-SQL qui ne sont pas prises en charge dans Entity SQL, consultez [expressions non prises en charge](unsupported-expressions-entity-sql.md).  
  
 Les requêtes Entity SQL valides sont les suivantes :  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Traitement uniforme des sous-requêtes  

 En raison de son importance sur les tables, Transact-SQL effectue une interprétation contextuelle des sous-requêtes. Par exemple, une sous-requête dans la `from` clause est considérée comme un multiensemble (table). En revanche, la même sous-requête utilisée dans la clause `select` est considérée comme une sous-requête scalaire. De même, une sous-requête utilisée sur le côté gauche d’un `in` opérateur est considérée comme une sous-requête scalaire, tandis que le côté droit est supposé être une sous-requête de multiensemble.  
  
 Entity SQL élimine ces différences. Une expression a une interprétation uniforme qui ne dépend pas du contexte dans lequel elle est utilisée. Entity SQL considère toutes les sous-requêtes comme des sous-requêtes de multiensemble. Si une valeur scalaire est souhaitée à partir de la sous-requête, Entity SQL fournit l' `anyelement` opérateur qui opère sur une collection (dans ce cas, la sous-requête) et extrait une valeur singleton de la collection.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Éviter des contraintes implicites pour les sous-requêtes  

 Un effet secondaire connexe du traitement uniforme des sous-requêtes est la conversion implicite des sous-requêtes en valeurs scalaires. En particulier, dans Transact-SQL, un multiensemble de lignes (avec un champ unique) est converti implicitement en une valeur scalaire dont le type de données est celui du champ.  
  
 Entity SQL ne prend pas en charge cette contrainte implicite. Entity SQL fournit l' `ANYELEMENT` opérateur pour extraire une valeur Singleton d’une collection et une `select value` clause pour éviter de créer un wrapper de ligne pendant une expression de requête.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select Value : éviter le wrapper de ligne implicite  

 La clause SELECT dans une sous-requête Transact-SQL crée implicitement un wrapper de ligne autour des éléments de la clause. Cela implique que nous ne pouvons pas créer de collections de scalaires ou d’objets. Transact-SQL autorise une contrainte implicite entre une `rowtype` avec un champ et une valeur singleton du même type de données.  
  
 Entity SQL fournit la `select value` clause pour ignorer la construction de ligne implicite. Un seul élément peut être spécifié dans une clause `select value`. Lorsqu’une telle clause est utilisée, aucun Wrapper de ligne n’est construit autour des éléments de la `select` clause, et une collection de la forme souhaitée peut être produite, par exemple, `select value a` .  
  
 Entity SQL fournit également le constructeur de ligne pour construire des lignes arbitraires. `select` prend un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs :  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Corrélation gauche et utilisation d'alias  

 Dans Transact-SQL, les expressions d’une étendue donnée (une clause unique comme `select` ou `from` ) ne peuvent pas faire référence à des expressions définies précédemment dans la même portée. Certains dialectes de SQL (y compris Transact-SQL) prennent en charge des formes limitées de celles-ci dans la `from` clause.  
  
 Entity SQL généralise les corrélations gauches dans la `from` clause et les traite uniformément. Les expressions dans la clause `from` peuvent référencer des définitions antérieures (définitions à gauche) dans la même clause sans nécessiter une syntaxe supplémentaire.  
  
 Entity SQL impose également des restrictions supplémentaires sur les requêtes qui impliquent des `group by` clauses. Les expressions dans la `select` clause et la `having` clause de ces requêtes peuvent uniquement faire référence aux `group by` clés par le biais de leurs alias. La construction suivante est valide dans Transact-SQL, mais n’est pas dans Entity SQL :  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Pour effectuer cette opération dans Entity SQL :  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Référencement de colonnes (propriétés) de tables (collections)  

 Toutes les références de colonnes dans Entity SQL doivent être qualifiées avec l’alias de table. La construction suivante (en supposant que `a` est une colonne valide de la table `T` ) est valide dans Transact-SQL, mais pas dans Entity SQL.  
  
```sql  
SELECT a FROM T
```  
  
 Le formulaire Entity SQL est  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Les alias de la table sont facultatifs dans la clause `from`. Le nom de la table est utilisé comme alias implicite. Entity SQL autorise également le formulaire suivant :  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Navigation dans les objets  

 Transact-SQL utilise la notation « . » pour référencer les colonnes d’une table (une ligne). Entity SQL étend cette notation (empruntée des langages de programmation) pour prendre en charge la navigation dans les propriétés d’un objet.  
  
 Par exemple, si `p` est une expression de type Person, voici la syntaxe Entity SQL pour référencer la ville de l’adresse de cette personne.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Aucune prise en charge de \*  

 Transact-SQL prend en charge la \* syntaxe non qualifiée en tant qu’alias pour la ligne entière, et la syntaxe qualifiée \* (t. \* ) comme raccourci pour les champs de cette table. En outre, Transact-SQL autorise un agrégat count ( \* ) spécial, qui comprend des valeurs NULL.  
  
 Entity SQL ne prend pas en charge la construction *. Les requêtes Transact-SQL de la forme `select * from T` et `select T1.* from T1, T2...` peuvent être exprimées en Entity SQL sous la forme `select value t from T as t` et `select value t1 from T1 as t1, T2 as t2...` , respectivement. En outre, ces constructions gèrent l'héritage (capacité des valeurs à être substituées), tandis que les variantes `select *` sont restreintes aux propriétés de niveau supérieur du type déclaré.  
  
 Entity SQL ne prend pas en charge l' `count(*)` agrégat. Utilisez `count(0)` à la place.  
  
## <a name="changes-to-group-by"></a>Modifications apportées à Group By  

 Entity SQL prend en charge l’alias des `group by` clés. Les expressions dans la clause `select` et la clause `having` doivent faire référence aux clés `group by` par le biais de ces alias. Par exemple, cette syntaxe de Entity SQL :  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... équivaut à l’instruction Transact-SQL suivante :  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Agrégats basés sur des collections  

 Entity SQL prend en charge deux types d’agrégats.  
  
 Les agrégats basés sur des collections opèrent sur des collections et produisent le résultat agrégé. Ils peuvent apparaître n'importe où dans la requête et ne requièrent pas de clause `group by`. Par exemple :  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 Entity SQL prend également en charge les agrégats de style SQL. Par exemple :  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Utilisation des clauses ORDER BY  

Transact-SQL autorise `ORDER BY` la spécification de clauses uniquement dans le bloc le plus haut `SELECT .. FROM .. WHERE` . Dans Entity SQL, vous pouvez utiliser une expression imbriquée `ORDER BY` et elle peut être placée n’importe où dans la requête, mais l’ordre dans une requête imbriquée n’est pas conservé.  
  
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

 Dans Transact-SQL, la comparaison des identificateurs est basée sur le classement de la base de données active. Dans Entity SQL, les identificateurs respectent toujours la casse et respectent les accents (autrement dit, Entity SQL fait la distinction entre les caractères accentués et non accentués ; par exemple, « a » n’est pas égal à « à »). Entity SQL traite les versions des lettres qui s’affichent de la même façon, mais qui proviennent de différentes pages de codes comme des caractères différents. Pour plus d’informations, consultez [jeu de caractères d’entrée](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Fonctionnalités Transact-SQL non disponibles dans Entity SQL  

 La fonctionnalité Transact-SQL suivante n’est pas disponible dans Entity SQL.  
  
 DML  
 Entity SQL ne fournit actuellement aucune prise en charge des instructions DML (insertion, mise à jour, suppression).  
  
 DDL  
 Entity SQL n’offre aucune prise en charge de DDL dans la version actuelle.  
  
 Programmation impérative  
 Entity SQL n’offre aucune prise en charge de la programmation impérative, contrairement à Transact-SQL. Utilisez un langage de programmation à la place.  
  
 Fonctions de regroupement  
 Entity SQL ne fournit pas encore de prise en charge pour les fonctions de regroupement (par exemple CUBE, ROLLUP et GROUPING_SET).  
  
 Fonctions analytiques  
 Entity SQL ne permet pas (encore) de prendre en charge les fonctions analytiques.  
  
 Fonctions et opérateurs intégrés  
 Entity SQL prend en charge un sous-ensemble des fonctions et des opérateurs intégrés de Transact-SQL. Ces opérateurs et ces fonctions seront vraisemblablement pris en charge par les principaux fournisseurs de stockage. Entity SQL utilise les fonctions spécifiques au magasin déclarées dans un manifeste du fournisseur. En outre, la Entity Framework vous permet de déclarer des fonctions de magasin existantes intégrées et définies par l’utilisateur, pour que les Entity SQL utilisent.  
  
 Indicateurs  
 Entity SQL ne fournit pas de mécanismes pour les indicateurs de requête.  
  
 Résultats d'une requête de traitement par lot  
 Entity SQL ne prend pas en charge le traitement par lot des résultats de requête. Par exemple, voici une instruction Transact-SQL valide (envoi en tant que lot) :  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Toutefois, l’équivalent Entity SQL n’est pas pris en charge :  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 Entity SQL prend en charge uniquement une instruction de requête produisant des résultats par commande.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
- [Expressions non prises en charge](unsupported-expressions-entity-sql.md)
