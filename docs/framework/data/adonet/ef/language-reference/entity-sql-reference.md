---
title: Référence Entity SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 987aa5c05b88d684e050721077d704b29e546aab
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542122"
---
# <a name="entity-sql-reference"></a>Référence Entity SQL

Cette section contient des Articles de référence Entity SQL. Cet article résume et regroupe les opérateurs Entity SQL par catégorie.

## <a name="arithmetic-operators"></a>Opérateurs arithmétiques

Les opérateurs arithmétiques effectuent des opérations mathématiques sur deux expressions d'au moins un type numérique. Le tableau suivant répertorie les opérateurs arithmétiques Entity SQL :

|Opérateur|Utiliser|
|--------------|---------|
|[+ (Ajout)](add.md)|Addition.|
|[/ (Diviser)](divide-entity-sql.md)|Division.|
|[% (Modulo)](modulo-entity-sql.md)|Retourne le reste d'une division.|
|[* (Multiplication)](multiply-entity-sql.md)|Multiplication.|
|[- (Négatif)](negative-entity-sql.md)|Négation.|
|[- (Soustraction)](subtract-entity-sql.md)|Soustraction.|

## <a name="canonical-functions"></a>Fonctions canoniques

Les fonctions canoniques sont prises en charge par tous les fournisseurs de données et peuvent être utilisées par toutes les technologies de requête. Le tableau suivant répertorie les fonctions canoniques :

|Fonction|Type|
|--------------|----------|
|[Fonctions canoniques Entity SQL d'agrégation](aggregate-canonical-functions.md)|Décrit les fonctions d’agrégation Entity SQL canoniques.|
|[Fonctions mathématiques canoniques](math-canonical-functions.md)|Décrit les fonctions canoniques Entity SQLs mathématiques.|
|[Fonctions de chaînes canoniques](string-canonical-functions.md)|Décrit les fonctions de chaîne Entity SQL canoniques.|
|[Fonctions de date et d'heure canoniques](date-and-time-canonical-functions.md)|Traite de la date et de l’heure Entity SQL des fonctions canoniques.|
|[Fonctions de chaînes canoniques au niveau du bit](bitwise-canonical-functions.md)|Décrit les fonctions canoniques Entity SQL au niveau du bit.|
|[Autres fonctions canoniques](other-canonical-functions.md)|Décrit les fonctions qui ne sont pas considérées comme des fonctions au niveau du bit, des fonctions de date/heure, des fonctions de chaîne, des fonctions mathématiques ni des fonctions d'agrégation.|

## <a name="comparison-operators"></a>Opérateurs de comparaison

Des opérateurs de comparaison sont définis pour les types suivants : `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time`, `DateTimeOffset`. La promotion de type implicite intervient pour les opérandes avant application de l’opérateur de comparaison. Les opérateurs de comparaison produisent toujours des valeurs booléennes. Lorsque au moins l’un des opérandes est `null`, le résultat est `null`.

L'égalité et l'inégalité sont définies pour tout type d'objet qui possède une identité, comme le type `Boolean`. Les objets non primitifs possédant une identité sont considérés comme égaux s'ils partagent la même identité. Le tableau suivant répertorie les Entity SQL opérateurs de comparaison :

|Opérateur|Description|
|--------------|-----------------|
|[= (Égal à)](equals-entity-sql.md)|Compare l'égalité de deux expressions.|
|[> (Supérieur à)](greater-than-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure à celle de l'expression de droite.|
|[>= (Supérieur ou égal à)](greater-than-or-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite.|
|[n’est \[ pas \] null](isnull-entity-sql.md)|Détermine si une expression de requête a la valeur NULL.|
|[< (Inférieur à)](less-than-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure à celle de l'expression de droite.|
|[<= (Inférieur ou égal à)](less-than-or-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite.|
|[\[NON \] compris entre](between-entity-sql.md)|Détermine si une expression a pour résultat une valeur contenue dans une plage spécifiée.|
|[\!= (Différent de)](not-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si l’expression de gauche n’est pas égale à l’expression de droite.|
|[\[NON \] similaire](like-entity-sql.md)|Détermine si une chaîne de caractères donnée correspond à un modèle spécifié.|

## <a name="logical-and-case-expression-operators"></a>Opérateurs logiques and case expression

Les opérateurs logiques testent le caractère vrai ou faux d'une condition. L'expression CASE évalue un ensemble d'expressions booléennes pour déterminer le résultat. Le tableau suivant répertorie les opérateurs logiques and CASE expression :

|Opérateur|Description|
|--------------|-----------------|
|[&&  (AND logique)](and-entity-sql.md)|AND logique.|
|[\! (NOT logique)](not-entity-sql.md)|NOT logique.|
|[&#124;&#124;  (OR logique)](or-entity-sql.md)|OR logique.|
|[CASE](case-entity-sql.md)|Évalue un ensemble d'expressions booléennes pour déterminer le résultat.|
|[THEN](then-entity-sql.md)|Résultat d’une clause [When](/previous-versions/dotnet/netframework-4.0/bb387119(v=vs.100)) lorsqu’elle prend la valeur true.|

## <a name="query-operators"></a>Opérateurs de requête

Les opérateurs de requête permettent de définir des expressions de requête qui retournent des données d'entité. Le tableau suivant répertorie les opérateurs de requête :

|Opérateur|Utiliser|
|--------------|---------|
|[FROM](from-entity-sql.md)|Spécifie la collection qui est utilisée dans les instructions [Select](select-entity-sql.md) .|
|[GROUP BY](group-by-entity-sql.md)|Spécifie les groupes dans lesquels les objets retournés par une expression de requête ([Select](select-entity-sql.md)) doivent être placés.|
|[GroupPartition](grouppartition-entity-sql.md)|Retourne une collection de valeurs d'argument, projetées en dehors de la partition de groupe à laquelle l'agrégat est associé.|
|[HAVING](having-entity-sql.md)|Indique un critère de recherche pour un groupe ou une fonction d'agrégation.|
|[SÉPAR](limit-entity-sql.md)|Utilisé avec la clause [order by](order-by-entity-sql.md) pour effectuer la pagination physique.|
|[ORDER BY](order-by-entity-sql.md)|Spécifie l’ordre de tri utilisé sur les objets retournés dans une instruction [Select](select-entity-sql.md) .|
|[SELECT](select-entity-sql.md)|Spécifie les éléments dans la projection qui sont retournés par une requête.|
|[SAUT](skip-entity-sql.md)|Utilisé avec la clause [order by](order-by-entity-sql.md) pour effectuer la pagination physique.|
|[TOP](top-entity-sql.md)|Spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.|
|[WHERE](where-entity-sql.md)|Filtre de manière conditionnelle les données qui sont retournées par une requête.|

## <a name="reference-operators"></a>Opérateurs de référence

Une référence est un pointeur logique (clé étrangère) vers une entité spécifique dans un jeu d'entités spécifique. Entity SQL prend en charge les opérateurs suivants pour construire, déconstruire et parcourir les références :

|Opérateur|Utiliser|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Crée les références à une entité dans un jeu d'entités.|
|[DEREF](deref-entity-sql.md)|Déréférence une valeur de référence et génère le résultat de ce déréférencement.|
|[KEY](key-entity-sql.md)|Extrait la clé d'une référence ou d'une expression d'entité.|
|[Sélectionnez](navigate-entity-sql.md)|Vous permet de naviguer sur la relation d'un type d'entité jusqu'à un autre|
|[Réf](ref-entity-sql.md)|Retourne une référence à une instance d'entité.|

## <a name="set-operators"></a>Opérateurs de jeu

Entity SQL fournit diverses opérations Set puissantes. Cela comprend des opérateurs de jeu similaires aux opérateurs Transact-SQL tels que UNION, INTERSECT, EXCEPT et EXISTs. Entity SQL prend également en charge les opérateurs pour l’élimination des doublons (SET), les tests d’appartenance (IN) et les jointures (jointure). Le tableau suivant répertorie les opérateurs de jeu de Entity SQL :

|Opérateur|Utiliser|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Extrait un élément d'une collection à valeurs multiples.|
|[EXCEPT](except-entity-sql.md)|Retourne une collection de valeurs distinctes de l’expression de requête à gauche de l’opérande EXCEPT qui ne sont pas également retournées à partir de l’expression de requête à droite de l’opérande EXCEPT.|
|[\[n' \] existe pas](exists-entity-sql.md)|Détermine si une collection est vide.|
|[ÉCRASÉ](flatten-entity-sql.md)|Convertit une collection de collections en collection plane.|
|[\[PAS \] dans](in-entity-sql.md)|Détermine si une valeur correspond à une valeur incluse dans une collection.|
|[INTERSECT](intersect-entity-sql.md)|Retourne une collection de valeurs distinctes qui sont retournées par les expressions de requête tant à gauche qu'à droite de l'opérande INTERSECT.|
|[OVERLAPS](overlaps-entity-sql.md)|Détermine si deux collections ont des éléments en commun.|
|[SET](set-entity-sql.md)|Permet de convertir une collection d’objets en un ensemble en produisant une nouvelle collection dans laquelle tous les éléments en double ont été supprimés.|
|[UNION](union-entity-sql.md)|Combine les résultats de deux requêtes, ou plus, en une collection unique.|

## <a name="type-operators"></a>Opérateurs de type

Entity SQL fournit des opérations qui permettent de construire, d’interroger et de manipuler le type d’une expression (valeur). Le tableau suivant répertorie les opérateurs utilisés pour travailler avec les types :

|Opérateur|Utiliser|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Convertit une expression d'un type de données à un autre.|
|[COLLECTE](collection-entity-sql.md)|Utilisé dans une opération de [fonction](function-entity-sql.md) pour déclarer une collection de types d’entités ou de types complexes.|
|[n’est \[ pas \] de](isof-entity-sql.md)|Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous-types.|
|[OFTYPE](oftype-entity-sql.md)|Retourne une collection d'objets à partir d'une expression de requête d'un type spécifique.|
|[Constructeur de type nommé](named-type-constructor-entity-sql.md)|Permet de créer des instances de types d'entités ou de types complexes.|
|[MULTISET](multiset-entity-sql.md)|Crée une instance d'un multiensemble à partir d'une liste de valeurs.|
|[ROW](row-entity-sql.md)|Construit des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.|
|[TREAT](treat-entity-sql.md)|Traite un objet d'un type de base déterminé en tant qu'objet du type dérivé spécifié.|

## <a name="other-operators"></a>Autres opérateurs

Le tableau suivant répertorie d’autres opérateurs de Entity SQL :

|Opérateur|Utiliser|
|--------------|---------|
|[+ (Concaténation de chaîne)](string-concatenation-entity-sql.md)|Utilisé pour concaténer des chaînes dans Entity SQL.|
|[. (Accès aux membres)](member-access-entity-sql.md)|Permet d'accéder à la valeur d'une propriété ou d'un champ d'une instance de type de modèle conceptuel structurel.|
|[-- (commentaire)](comment-entity-sql.md)|Ajoutez Entity SQL commentaires.|
|[FUNCTION](function-entity-sql.md)|Définit une fonction incluse qui peut être exécutée dans une requête Entity SQL.|

## <a name="see-also"></a>Voir aussi

- [Langage d'Entity SQL](entity-sql-language.md)
