---
title: Différences entre Entity SQL et Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e809cea2f853eed51d28e55f81a411f7af2e5a33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854476"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Différences entre Entity SQL et Transact-SQL
Cette rubrique décrit les différences entre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Héritage et prise en charge des relations  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]fonctionne directement avec les schémas d’entité conceptuels et prend en charge des fonctionnalités de modèle conceptuel telles que l’héritage et les relations.  
  
 Lors de l’utilisation de l’héritage, il est souvent utile de sélectionner des instances d’un sous-type à partir d’une collection d’instances de supertype. L’opérateur [OfType](oftype-entity-sql.md) dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (comme `oftype` dans C# les séquences) fournit cette fonctionnalité.  
  
## <a name="support-for-collections"></a>Prise en charge des collections  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traite les collections comme des entités de première classe. Par exemple :  
  
- Les expressions de collection sont valides dans une clause `from`.  
  
- Les sous-requêtes `in` et `exists` ont été généralisées pour autoriser toute collection.  
  
     Une sous-requête est un type de collection. `e1 in e2` et `exists(e)` sont les constructions [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui permettent d'effectuer ces opérations.  
  
- Les opérations de définition, telles que `union`, `intersect` et `except`, s’appliquent à présent aux collections.  
  
- Les jointures s’appliquent aux collections.  
  
## <a name="support-for-expressions"></a>Prise en charge des expressions  
 Transact-SQL contient des sous-requêtes (tables) et des expressions (lignes et colonnes).  
  
 Pour prendre en charge les collections et les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] collections imbriquées, transforme tout en une expression. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]est plus composable que Transact-SQL : chaque expression peut être utilisée n’importe où. Les expressions de requête génèrent toujours des collections des types projetés et peuvent être utilisées partout où une expression de collection est autorisée. Pour plus d’informations sur les expressions Transact-SQL qui ne [!INCLUDE[esql](../../../../../../includes/esql-md.md)]sont pas prises en charge dans, consultez [expressions non prises en charge](unsupported-expressions-entity-sql.md).  
  
 Les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivantes sont toutes valides :  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Traitement uniforme des sous-requêtes  
 En raison de son importance sur les tables, Transact-SQL effectue une interprétation contextuelle des sous-requêtes. Par exemple, une sous-requête dans `from` la clause est considérée comme un multiensemble (table). En revanche, la même sous-requête utilisée dans la clause `select` est considérée comme une sous-requête scalaire. De même, une sous-requête utilisée sur le côté gauche d' `in` un opérateur est considérée comme une sous-requête scalaire, tandis que le côté droit est supposé être une sous-requête de multiensemble.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] élimine ces différences. Une expression a une interprétation uniforme qui ne dépend pas du contexte dans lequel elle est utilisée. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]considère toutes les sous-requêtes comme des sous-requêtes de multiensemble. Si une valeur scalaire est souhaitée à partir de la sous [!INCLUDE[esql](../../../../../../includes/esql-md.md)] -requête `anyelement` , fournit l’opérateur qui opère sur une collection (dans ce cas, la sous-requête) et extrait une valeur singleton de la collection.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Éviter des contraintes implicites pour les sous-requêtes  
 Un effet secondaire connexe du traitement uniforme des sous-requêtes est la conversion implicite des sous-requêtes en valeurs scalaires. En particulier, dans Transact-SQL, un multiensemble de lignes (avec un champ unique) est converti implicitement en une valeur scalaire dont le type de données est celui du champ.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge cette contrainte implicite. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit l'opérateur ANYELEMENT pour extraire une valeur singleton d'une collection et une clause `select value` pour éviter de créer un wrapper de ligne pendant une expression de requête.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select value : éviter le wrapper de ligne implicite  
 La clause SELECT dans une sous-requête Transact-SQL crée implicitement un wrapper de ligne autour des éléments de la clause. Cela implique que nous ne pouvons pas créer de collections de scalaires ou d’objets. Transact-SQL autorise une contrainte implicite entre un RowType avec un champ et une valeur singleton du même type de données.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit la clause `select value` pour ignorer la construction de ligne implicite. Un seul élément peut être spécifié dans une clause `select value`. Lorsqu’une telle clause est utilisée, aucun wrapper de ligne n’est construit autour des éléments de la clause `select` et une collection de la forme souhaitée peut être générée, par exemple : `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit également le constructeur de ligne pour construire des lignes arbitraires. `select` accepte un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, comme suit :  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Corrélation gauche et utilisation d'alias  
 Dans Transact-SQL, les expressions d’une étendue donnée (une clause unique `select` comme `from`ou) ne peuvent pas faire référence à des expressions définies précédemment dans la même portée. Certains dialectes de SQL (y compris Transact-SQL) prennent en charge des formes limitées de `from` celles-ci dans la clause.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]généralise les corrélations gauches `from` dans la clause et les traite uniformément. Les expressions dans la clause `from` peuvent référencer des définitions antérieures (définitions à gauche) dans la même clause sans nécessiter une syntaxe supplémentaire.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] impose également des restrictions supplémentaires sur les requêtes qui impliquent des clauses `group by`. Les expressions dans `select` la clause `having` et la clause de ces requêtes peuvent uniquement faire `group by` référence aux clés par le biais de leurs alias. La construction suivante est valide dans Transact-SQL, mais pas dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Pour effectuer cette opération dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Référencement de colonnes (propriétés) de tables (collections)  
 Toutes les références de colonne dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doivent être qualifiées avec l'alias de la table. La construction suivante (en supposant `a` que est une colonne valide de `T`la table) est valide dans Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]mais pas dans.  
  
```  
select a from T  
```  
  
 La forme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est :  
  
```  
select t.a as A from T as t  
```  
  
 Les alias de la table sont facultatifs dans la clause `from`. Le nom de la table est utilisé comme alias implicite. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] autorise également la forme suivante :  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Navigation dans les objets  
 Transact-SQL utilise la notation « . » pour référencer les colonnes d’une table (une ligne). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] étend cette notation (empruntée des langages de programmation) pour prendre en charge la navigation dans les propriétés d'un objet.  
  
 Par exemple, si `p` est une expression de type Person, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous référence la ville de l'adresse de cette personne.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Aucune prise en charge pour *  
 Transact-SQL prend en charge la syntaxe Unqualified * comme alias pour la ligne entière, et \* la syntaxe qualifiée\*(t.) comme raccourci pour les champs de cette table. En outre, Transact-SQL autorise un agrégat count (\*) spécial, qui comprend des valeurs NULL.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge la construction *. Les requêtes Transact-SQL de la `select * from T` forme `select T1.* from T1, T2...` et peuvent être exprimées `select value t from T as t` [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sous `select value t1 from T1 as t1, T2 as t2...`la forme et, respectivement. En outre, ces constructions gèrent l'héritage (capacité des valeurs à être substituées), tandis que les variantes `select *` sont restreintes aux propriétés de niveau supérieur du type déclaré.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge l'agrégat `count(*)`. Utilisez plutôt `count(0)`.  
  
## <a name="changes-to-group-by"></a>Modifications apportées à Group By  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge les alias des clés `group by`. Les expressions dans la clause `select` et la clause `having` doivent faire référence aux clés `group by` par le biais de ces alias. Par exemple, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... équivaut à l’instruction Transact-SQL suivante :  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Agrégats basés sur des collections  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge deux types d'agrégats.  
  
 Les agrégats basés sur des collections opèrent sur des collections et produisent le résultat agrégé. Ils peuvent apparaître n'importe où dans la requête et ne requièrent pas de clause `group by`. Par exemple :  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend également en charge les agrégats de style SQL. Par exemple :  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>Utilisation des clauses ORDER BY  
 Transact-SQL permet de spécifier des clauses ORDER BY uniquement dans la sélection. FROM . WHERE le plus élevé. Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vous pouvez utiliser une expression ORDER BY imbriquée et elle peut être placée n'importe où dans la requête, mais le classement dans une requête imbriquée n'est pas conservé.  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Identificateurs  
 Dans Transact-SQL, la comparaison des identificateurs est basée sur le classement de la base de données active. Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les identificateurs respectent toujours la casse et les accents (autrement dit, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distingue les caractères accentués et non accentués ; par exemple, « a » n'est pas égal à « à »). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traite les versions des lettres qui apparaissent identiques mais qui proviennent de pages de codes différentes comme des caractères différents. Pour plus d’informations, consultez [jeu de caractères d’entrée](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Fonctionnalités Transact-SQL non disponibles dans Entity SQL  
 La fonctionnalité Transact-SQL suivante n’est pas disponible [!INCLUDE[esql](../../../../../../includes/esql-md.md)]dans.  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ne fournit actuellement aucune prise en charge pour les instructions DML (Insert, Update, Delete).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit aucune prise en charge pour DDL dans la version actuelle.  
  
 Programmation impérative  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ne prend pas en charge la programmation impérative, contrairement à Transact-SQL. Utilisez un langage de programmation à la place.  
  
 Fonctions de regroupement  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas encore de prise en charge pour les fonctions de regroupement (par exemple, CUBE, ROLLUP et GROUPING_SET).  
  
 Fonctions analytiques  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas (encore) de prise en charge pour les fonctions analytiques.  
  
 Fonctions et opérateurs intégrés  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]prend en charge un sous-ensemble des fonctions et des opérateurs intégrés de Transact-SQL. Ces opérateurs et ces fonctions seront vraisemblablement pris en charge par les principaux fournisseurs de stockage. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]utilise les fonctions spécifiques au magasin déclarées dans un manifeste du fournisseur. En outre, le Entity Framework vous permet de déclarer des fonctions de magasin existantes intégrées et définies par l’utilisateur, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour que utilise.  
  
 Indicateurs  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas de mécanismes pour les indicateurs de requête.  
  
 Résultats d'une requête de traitement par lot  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge les résultats d'une requête de traitement par lot. Par exemple, voici une instruction Transact-SQL valide (envoi en tant que lot) :  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Toutefois, l'équivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas pris en charge :  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend uniquement en charge une seule instruction de requête générant un résultat par commande.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)
- [Expressions non prises en charge](unsupported-expressions-entity-sql.md)
