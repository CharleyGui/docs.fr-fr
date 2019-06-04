---
title: Différences entre Entity SQL et Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 54d7a3fa8ce6e8a0aba6194bfc034eb4d47dbf60
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489931"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Différences entre Entity SQL et Transact-SQL
Cette rubrique décrit les différences entre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Héritage et prise en charge des relations  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fonctionne directement avec les schémas d’entité conceptuels et prend en charge des fonctionnalités telles que l’héritage et les relations de modèle conceptuel.  
  
 Lors de l’utilisation de l’héritage, il est souvent utile de sélectionner des instances d’un sous-type à partir d’une collection d’instances de supertype. Le [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) opérateur dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semblable à `oftype` dans C# séquences) offre cette possibilité.  
  
## <a name="support-for-collections"></a>Prise en charge des collections  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traite les collections en tant qu’entités de première classe. Exemple :  
  
- Les expressions de collection sont valides dans une clause `from`.  
  
- Les sous-requêtes `in` et `exists` ont été généralisées pour autoriser toute collection.  
  
     Une sous-requête est un type de collection. `e1 in e2` et `exists(e)` sont les constructions [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui permettent d'effectuer ces opérations.  
  
- Les opérations de définition, telles que `union`, `intersect` et `except`, s’appliquent à présent aux collections.  
  
- Les jointures s’appliquent aux collections.  
  
## <a name="support-for-expressions"></a>Prise en charge des expressions  
 Transact-SQL a des sous-requêtes (tables) et des expressions (lignes et colonnes).  
  
 Pour prendre en charge les collections et les collections imbriquées, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transforme tout en expression. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est plus composable que Transact-SQL, chaque expression peut être utilisée n’importe où. Les expressions de requête génèrent toujours des collections des types projetés et peuvent être utilisées partout où une expression de collection est autorisée. Pour plus d’informations sur les expressions de Transact-SQL qui ne sont pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultez [Expressions non prises en charge](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
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
 Étant donné l’accent porté sur les tables, Transact-SQL effectue une interprétation contextuelle des sous-requêtes. Par exemple, une sous-requête dans la `from` clause est considérée comme un multiset (table). En revanche, la même sous-requête utilisée dans la clause `select` est considérée comme une sous-requête scalaire. De même, une sous-requête utilisée sur le côté gauche d’un `in` opérateur est considéré comme une sous-requête scalaire, tandis que le côté droit est supposé être une sous-requête de type multiset.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] élimine ces différences. Une expression a une interprétation uniforme qui ne dépend pas du contexte dans lequel elle est utilisée. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en compte toutes les sous-requêtes comme des sous-requêtes de type multiset. Si une valeur scalaire est souhaitée à partir de la sous-requête, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit le `anyelement` opérateur qui opère sur une collection (dans ce cas, la sous-requête) et extrait une valeur singleton de la collection.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Éviter des contraintes implicites pour les sous-requêtes  
 Un effet secondaire connexe du traitement uniforme des sous-requêtes est la conversion implicite des sous-requêtes en valeurs scalaires. Plus précisément, dans Transact-SQL, un multiensemble de lignes (avec un champ unique) est converti implicitement en une valeur scalaire dont le type de données est celui du champ.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge cette contrainte implicite. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit l'opérateur ANYELEMENT pour extraire une valeur singleton d'une collection et une clause `select value` pour éviter de créer un wrapper de ligne pendant une expression de requête.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select value : éviter le wrapper de ligne implicite  
 La clause select dans une sous-requête de Transact-SQL crée implicitement un wrapper de ligne autour des éléments dans la clause. Cela implique que nous ne pouvons pas créer de collections de scalaires ou d’objets. Transact-SQL autorise une contrainte implicite entre un rowtype avec un champ et une valeur singleton du même type de données.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit la clause `select value` pour ignorer la construction de ligne implicite. Un seul élément peut être spécifié dans une clause `select value`. Lorsqu’une telle clause est utilisée, aucun wrapper de ligne n’est construit autour des éléments de la clause `select` et une collection de la forme souhaitée peut être générée, par exemple : `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit également le constructeur de ligne pour construire des lignes arbitraires. `select` accepte un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, comme suit :  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Corrélation gauche et utilisation d'alias  
 Dans Transact-SQL, les expressions dans une étendue donnée (une clause unique comme `select` ou `from`) ne peut pas référencer des expressions définies précédemment dans la même portée. Certains dialectes SQL (y compris Transact-SQL) ne prennent pas en charge des formes limitées de ces éléments dans le `from` clause.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] généralise les corrélations gauches dans la `from` clause et les traite uniformément. Les expressions dans la clause `from` peuvent référencer des définitions antérieures (définitions à gauche) dans la même clause sans nécessiter une syntaxe supplémentaire.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] impose également des restrictions supplémentaires sur les requêtes qui impliquent des clauses `group by`. Expressions dans les `select` clause et `having` clause de telles requêtes peut-être faire référence uniquement à la `group by` clés par le biais de leurs alias. La construction suivante est valide dans Transact-SQL, mais ne sont pas dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Pour effectuer cette opération dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Référencement de colonnes (propriétés) de tables (collections)  
 Toutes les références de colonne dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doivent être qualifiées avec l'alias de la table. La construction suivante (en supposant que `a` est une colonne de table valide `T`) est valide dans Transact-SQL, mais pas dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
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
 Transact-SQL utilise le «. » pour référencer les colonnes de (une ligne de) une table. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] étend cette notation (empruntée des langages de programmation) pour prendre en charge la navigation dans les propriétés d'un objet.  
  
 Par exemple, si `p` est une expression de type Person, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous référence la ville de l'adresse de cette personne.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Aucune prise en charge pour *  
 Transact-SQL prend en charge le non qualifiée * syntaxe en tant qu’alias pour la ligne entière et qualifié \* syntaxe (t.\*) comme raccourci pour les champs de la table. En outre, permet de Transact-SQL pour un compte spécial (\*) agrégat, qui inclut les valeurs NULL.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge la construction *. Les requêtes Transact-SQL de la forme `select * from T` et `select T1.* from T1, T2...` peuvent être exprimées dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] comme `select value t from T as t` et `select value t1 from T1 as t1, T2 as t2...`, respectivement. En outre, ces constructions gèrent l'héritage (capacité des valeurs à être substituées), tandis que les variantes `select *` sont restreintes aux propriétés de niveau supérieur du type déclaré.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge l'agrégat `count(*)`. Utilisez plutôt `count(0)`.  
  
## <a name="changes-to-group-by"></a>Modifications apportées à Group By  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge les alias des clés `group by`. Les expressions dans la clause `select` et la clause `having` doivent faire référence aux clés `group by` par le biais de ces alias. Par exemple, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... est équivalente à l’instruction Transact-SQL suivante :  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Agrégats basés sur des collections  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge deux types d'agrégats.  
  
 Les agrégats basés sur des collections opèrent sur des collections et produisent le résultat agrégé. Ils peuvent apparaître n'importe où dans la requête et ne requièrent pas de clause `group by`. Exemple :  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend également en charge les agrégats de style SQL. Exemple :  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>Utilisation des clauses ORDER BY  
 Transact-SQL autorise les clauses ORDER BY doit être spécifié uniquement dans le bloc SELECT... FROM . WHERE le plus élevé. Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vous pouvez utiliser une expression ORDER BY imbriquée et elle peut être placée n'importe où dans la requête, mais le classement dans une requête imbriquée n'est pas conservé.  
  
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
 Dans Transact-SQL, la comparaison d’identificateurs est basée sur le classement de la base de données actuelle. Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les identificateurs respectent toujours la casse et les accents (autrement dit, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distingue les caractères accentués et non accentués ; par exemple, « a » n'est pas égal à « à »). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traite les versions des lettres qui apparaissent identiques mais qui proviennent de pages de codes différentes comme des caractères différents. Pour plus d’informations, consultez [du jeu de caractères entrée](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Fonctionnalités Transact-SQL non disponibles dans Entity SQL  
 Les fonctionnalités suivantes de Transact-SQL ne sont pas disponible dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit actuellement aucune prise en charge pour les instructions DML (insérer, mettre à jour, supprimer).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit aucune prise en charge pour DDL dans la version actuelle.  
  
 Programmation impérative  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit aucune prise en charge pour la programmation impérative, contrairement à Transact-SQL. Utilisez un langage de programmation à la place.  
  
 Fonctions de regroupement  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas encore de prise en charge pour les fonctions de regroupement (par exemple, CUBE, ROLLUP et GROUPING_SET).  
  
 Fonctions analytiques  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas (encore) de prise en charge pour les fonctions analytiques.  
  
 Fonctions et opérateurs intégrés  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge un sous-ensemble de Transact-SQL généré dans les fonctions et opérateurs. Ces opérateurs et ces fonctions seront vraisemblablement pris en charge par les principaux fournisseurs de stockage. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] utilise les fonctions spécifiques aux magasins déclarées dans le manifeste du fournisseur. En outre, le [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] vous permet de déclarer intégrées et fonctions définies par l’utilisateur existant de magasin pour [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à utiliser.  
  
 Indicateurs  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne fournit pas de mécanismes pour les indicateurs de requête.  
  
 Résultats d'une requête de traitement par lot  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne prend pas en charge les résultats d'une requête de traitement par lot. Par exemple, ce qui suit est Transact-SQL valide (envoi en tant que lot) :  
  
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

- [Vue d’ensemble d’Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Expressions non prises en charge](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
