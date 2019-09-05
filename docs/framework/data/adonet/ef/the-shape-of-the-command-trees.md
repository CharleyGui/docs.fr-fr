---
title: Forme des arborescences de commandes
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: a3568f3deeaeeb31b69b41ac7c767001b792a8eb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248219"
---
# <a name="the-shape-of-the-command-trees"></a>Forme des arborescences de commandes

Le module de génération SQL est chargé de la génération d’une requête SQL spécifique principale basée sur une expression de l’arborescence de commandes de la requête d’entrée donnée. Cette section traite des caractéristiques, des propriétés et de la structure des arborescences de commandes de requête.

## <a name="query-command-trees-overview"></a>Vue d’ensemble des arborescences de commandes de requête

Une arborescence de commandes de requête est une représentation de modèle objet d'une requête. Les arborescences de commandes de requête ont deux objectifs :

- exprimer une requête d'entrée spécifiée par rapport à [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ;

- exprimer une requête de sortie qui est donnée à un fournisseur et décrire une requête par rapport au serveur.

Les arborescences de commandes de requête prennent en charge des sémantiques plus riches que les requêtes conformes SQL:1999, notamment l'utilisation des collections imbriquées et des opérations de type, telles que vérifier si une entité est d'un type particulier ou filtrer des jeux selon un type.

La propriété DBQueryCommandTree.Query est la racine de l’arborescence d’expression qui décrit la logique de requête. La propriété DBQueryCommandTree.Parameters contient une liste des paramètres utilisés dans la requête. L'arborescence d'expression est composée d'objets DbExpression.

Un objet DbExpression représente un calcul. Plusieurs types d'expressions sont fournis par [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour composer des expressions de requête, notamment des constantes, des variables, des fonctions, des constructeurs et des opérateurs relationnels standard comme filtre et jointure. Chaque objet DbExpression a une propriété ResultType qui représente le type du résultat produit par cette expression. Ce type est exprimé sous la forme d'un TypeUsage.

## <a name="shapes-of-the-output-query-command-tree"></a>Formes de l’arborescence de commandes de requête de sortie

Les arborescences de commandes de requête de sortie représentent les requêtes relationnelles (SQL) précisément et adhèrent à des règles beaucoup plus strictes que celles qui s’appliquent aux arborescences de commandes de requête. Elles contiennent en général des constructions qui se traduisent facilement en SQL.

Les arborescences de commandes d’entrée sont exprimées par rapport au modèle conceptuel, qui prend en charge des propriétés de navigation, des associations entre entités et l’héritage. Les arborescences de commandes de sortie sont exprimées par rapport au modèle de stockage. Les arborescences de commandes d’entrée vous permettent de projeter des collections imbriquées, contrairement aux arborescences de commandes de sortie.

Les arborescences de commandes de requête de sortie sont construites à l'aide d'un sous-ensemble des objets DbExpression disponibles et même certaines expressions dans ce sous-ensemble ont une utilisation restreinte.

Les opérations de type, telles que vérifier si une expression donnée est d’un type particulier ou les jeux de filtrage basés sur un type, ne sont pas présentes dans les arborescences de commandes de sortie.

Dans les arborescences de commandes de sortie, seules les expressions qui retournent des valeurs booléennes sont utilisées pour les projections et uniquement pour des prédicats dans les expressions qui requièrent un prédicat, comme un filtre ou une instruction de casse.

La racine d'une arborescence de commandes de requête de sortie est un objet DbProjectExpression.

### <a name="expression-types-not-present-in-output-query-command-trees"></a>Types d’expression non présents dans les arborescences de commandes de requête de sortie

Les types d’expression suivants ne sont pas valides dans une arborescence de commandes de requête de sortie et n’ont pas besoin d’être gérés par les fournisseurs :

- DbDerefExpression

- DbEntityRefExpression

- DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>Limitations relatives aux expressions et remarques

De nombreuses expressions peuvent être utilisées uniquement de façon restreinte dans les arborescences de commandes de requête de sortie :

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

Les types de fonction suivants peuvent être passés :

- Fonctions canoniques reconnues par l'espace de noms Edm.

- Fonctions intégrées (magasin) reconnues par le BuiltInAttribute.

- Fonctions définies par l'utilisateur.

Les fonctions canoniques (consultez [fonctions canoniques](./language-reference/canonical-functions.md) pour plus d’informations) sont spécifiées dans le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]cadre du, et les fournisseurs doivent fournir des implémentations pour les fonctions canoniques en fonction de ces spécifications. Les fonctions de magasin sont basées sur les spécifications présentes dans le manifeste du fournisseur correspondant. Les fonctions définies par l'utilisateur sont basées sur les spécifications présentes dans le SSDL.

De plus, les fonctions qui ont l'attribut NiladicFunction n'ont pas d'arguments et doivent être traduites sans parenthèses à la fin.  Autrement dit, pour  *\<nomfonction >* au lieu de  *\<nomfonction > ()* .

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

DbNewInstanceExpression peut se produire uniquement dans les deux cas suivants :

- En tant que propriété Projection de DbProjectExpression.  Dans ce cas d'utilisation, les limitations suivantes s'appliquent :

  - Le type de résultat doit être un type de ligne.

  - Chacun de ses arguments est une expression qui produit un résultat avec un type primitif. En général, chaque argument est une expression scalaire, comme un PropertyExpression sur un DbVariableReferenceExpression, un appel de fonction ou un calcul arithmétique de DbPropertyExpression sur un DbVariableReferenceExpression ou un appel de fonction. Toutefois, une expression qui représente une sous-requête scalaire peut également se produire dans la liste d'arguments pour un DbNewInstanceExpression. Une expression qui représente une sous-requête scalaire est une arborescence d’expression qui représente une sous-requête qui retourne exactement une ligne et une colonne d’un type primitif avec une racine d’objet DbElementExpression

- Avec un type de retour de collection, auquel cas il définit une nouvelle collection des expressions fournies comme arguments.

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

Un DbVariableReferenceExpression doit être l'enfant d'un nœud DbPropertyExpression.

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

La propriété Aggregates d'un DbGroupByExpression peut avoir uniquement des éléments de type DbFunctionAggregate. Il n'existe pas d'autres types d'agrégation.

#### <a name="dblimitexpression"></a>DbLimitExpression

La propriété Limit peut être uniquement un DbConstantExpression ou un DbParameterReferenceExpression. De plus, la propriété WithTies a toujours la valeur False à partir de la version 3.5 du .NET Framework.

#### <a name="dbscanexpression"></a>DbScanExpression

Lorsqu’il est utilisé dans les arborescences de commandes de sortie, DbScanExpression représente efficacement une analyse sur une table, une vue ou une requête de magasin, représentée par EntitySetBase :: target.

Si la propriété de métadonnées « définition de la requête » de la cible n’est pas null, elle représente une requête, le texte de requête pour lequel est fourni dans cette propriété de métadonnées dans le langage spécifique du fournisseur (ou le dialecte) tel que spécifié dans la définition de schéma du magasin.

Sinon, la cible représente une table ou une vue. Son préfixe de schéma est soit dans la propriété de métadonnées « Schema », si elle n’est pas null, soit le nom du conteneur d’entités.  Le nom de la table ou de la vue est la propriété de métadonnées « table », si elle n’est pas null, sinon la propriété Name de la base du jeu d’entités.

Toutes ces propriétés proviennent de la définition de l'EntitySet correspondant dans le fichier de définition de schéma du magasin (SSDL).

### <a name="using-primitive-types"></a>Utilisation de types primitifs

Lorsque les types primitifs sont référencés dans les arborescences de commandes de sortie, ils sont en général référencés dans les types primitifs du modèle conceptuel. Toutefois, pour certaines expressions, les fournisseurs ont besoin du type primitif du magasin correspondant. Les exemples de telles expressions sont notamment DbCastExpression et éventuellement DbNullExpression, si le fournisseur doit effectuer un cast de la valeur Null vers le type correspondant. Dans ces cas, les fournisseurs doivent effectuer le mappage au type de fournisseur selon le type du type primitif et ses facettes.

## <a name="see-also"></a>Voir aussi

- [Génération SQL](sql-generation.md)
