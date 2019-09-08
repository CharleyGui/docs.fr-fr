---
title: Collections de schémas Oracle
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: cb91a90ae7323283556954caa401646a2063a37e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783294"
---
# <a name="oracle-schema-collections"></a>Collections de schémas Oracle

Le fournisseur de données Microsoft .NET Framework pour Oracle prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes.

- Colonnes

- Index

- IndexColumns

- Procédures

- Séquences

- Synonymes

- Tables

- Utilisateurs

- Affichages

- Fonctions

- Packages

- PackageBodies

- Arguments

- UniqueKeys

- PrimaryKeys

- ForeignKeys

- ForeignKeyColumns

- ProcedureParameters

## <a name="columns"></a>Colonnes

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de la table, de la vue ou du cluster.|
|TABLE_NAME|String|Nom de table, de vue ou de cluster.|
|COLUMN_NAME|String|Nom de la colonne.|
|ID|Decimal|Numéro de séquence de la colonne lors de sa création.|
|DATATYPE|String|Type de données de la colonne.|
|LENGTH|Decimal|Longueur de la colonne en octets.|
|PRECISION|Decimal|Précision décimale du type de données NUMBER ; précision binaire du type de données FLOAT, null pour tous les autres types de données.|
|SCALE|Decimal|Chiffres à droite de la virgule décimale dans un nombre.|
|NULLABLE|String|Indique si une colonne accepte les valeurs NULL. La valeur est N s'il y a une contrainte NOT NULL sur la colonne ou si la colonne fait partie d'une PRIMARY KEY.|

## <a name="indexes"></a>Index

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de l'index.|
|INDEX_NAME|String|Nom de l'index.|
|INDEX_TYPE|String|Type d'index (NORMAL, BITMAP, FUNCTION-BASED NORMAL, FUNCTION-BASED BITMAP ou DOMAIN).|
|TABLE_OWNER|String|Propriétaire de l'objet indexé.|
|TABLE_NAME|String|Nom de l'objet indexé.|
|TABLE_TYPE|String|Type de l'objet indexé (par exemple, TABLE, CLUSTER).|
|UNIQUENESS|String|Indique si l'index est UNIQUE ou NONUNIQUE.|
|COMPRESSION|String|Indique si l'index est activé (ENABLED) ou désactivé (DISABLED).|
|PREFIX_LENGTH|Decimal|Nombre de colonnes dans le préfixe de la clé de compression.|
|TABLESPACE_NAME|String|Nom de l'espace de table contenant l'index.|
|INI_TRANS|Decimal|Nombre initial de transactions.|
|MAX_TRANS|Decimal|Nombre maximal de transactions.|
|INITIAL_EXTENT|Decimal|Taille de l'extension initiale.|
|NEXT_EXTENT|Decimal|Taille des étendues secondaires.|
|MIN_EXTENTS|Decimal|Nombre minimal d'étendues autorisées dans le segment.|
|MAX_EXTENTS|Decimal|Nombre maximal d'extensions autorisées dans le segment.|
|PCT_INCREASE|Decimal|Pourcentage d'augmentation dans la taille d'extension.|
|PCT_THRESHOLD|Decimal|Pourcentage seuil de l'espace de bloc autorisé par entrée d'index.|
|INCLUDE_COLUMN|Decimal|ID de colonne de la dernière colonne à inclure dans un index (sans dépassement) de clé primaire de table indexée. Cette colonne est mappée sur la colonne COLUMN_ID des vues de dictionnaire de données *_TAB_COLUMNS.|
|FREELISTS|Decimal|Nombre de listes libres de processus allouées à ce segment.|
|FREELIST_GROUPS|Decimal|Nombre de groupes de liste libre alloués à ce segment.|
|PCT_FREE|Decimal|Pourcentage minimal d'espace libre dans un bloc.|
|LOGGING|String|Informations de connexion.|
|BLEVEL|Decimal|B*-Niveau de l'arborescence : profondeur de l'index à partir de son bloc racine jusqu'à ses blocs feuille. Une profondeur 0 indique que le bloc racine et le bloc feuille sont identiques.|
|LEAF_BLOCKS|Decimal|Nombre de blocs feuille dans l'index|
|DISTINCT_KEYS|Decimal|Nombre de valeurs indexées distinctes. Pour les index qui appliquent des contraintes UNIQUE et PRIMARY KEY, cette valeur est égale au nombre de lignes de la table (USER_TABLES.NUM_ROWS).|
|AVG_LEAF_BLOCKS_PER_KEY|Decimal|Nombre moyen de blocs feuille dans lesquels chaque valeur distincte de l'index apparaît arrondie au nombre entier le plus proche. Pour les index qui appliquent des contraintes UNIQUE et PRIMARY KEY, cette valeur est toujours 1.|
|AVG_LEAF_BLOCKS_PER_KEY|Decimal|Nombre moyen de blocs de données de la table sur lesquels pointe une valeur distincte de l'index, arrondie au nombre entier le plus proche. Cette statistique est le nombre moyen de blocs de données qui contiennent des lignes contenant une valeur données pour les colonnes indexées.|
|CLUSTERING_FACTOR|Decimal|Indique la quantité de commande des lignes de la table en se basant sur les valeurs de l'index.|
|STATUT|String|Indique si un index non partitionné est valide (VALID) ou inutilisable (UNUSABLE).|
|NUM_ROWS|Decimal|Nombre de lignes de l'index.|
|SAMPLE_SIZE|Decimal|Taille de l'exemple utilisé pour analyser l'index.|
|LAST_ANALYZED|DateTime|Date à laquelle cet index a été analysé pour la dernière fois.|
|DEGREE|String|Nombre de threads par instance pour l'analyse de l'index.|
|INSTANCES|String|Nombre d'instances via lesquelles les index doivent être analysés.|
|PARTITIONED|String|Indique si cet index est partitionné (oui &#124; non).|
|TEMPORARY|String|Indique si l'index figure dans une table temporaire.|
|GENERATED|String|Indique si le nom de l’index est généré par le&#124;système (Y N).|
|SECONDARY|String|Indique si l’index est un objet secondaire créé par la méthode ODCIIndexCreate de la cartouche de données Oracle9i&#124;(Y N).|
|BUFFER_POOL|String|Nom du pool de tampons par défaut à utiliser pour les blocs d'index.|
|USER_STATS|String|Indique si les statistiques ont été entrées directement par l'utilisateur.|
|DURATION|String|Indique la durée d'une table temporaire : 1) SYS $ SESSION : les lignes sont conservées pendant la durée de la session, 2) SYS $ TRANSACTION : les lignes sont supprimées après validation, 3) null pour la table permanente.|
|PCT_DIRECT_ACCESS|Decimal|Pour un index secondaire sur une table indexée, pourcentage de lignes avec une prédiction VALID|
|ITYP_OWNER|String|Pour un index de domaine, propriétaire du type d'index.|
|ITYP_NAME|String|Pour un index de domaine, nom du type d'index.|
|PARAMETERS|String|Pour un index de domaine, chaîne de paramètres.|
|GLOBAL_STATS|String|Pour des index partitionnés, indique si les statistiques ont été collectées en analysant l'index dans son ensemble (YES) ou ont été estimées sur la base de statistiques relatives aux partitions et sous-partitions d'index sous-jacentes (NO).|
|DOMIDX_STATUS|String|Indique l'état de l'index de domaine. NULL : l'index spécifié n'est pas un index de domaine. VALID : l'index est un index de domaine valide. IDXTYP_INVLD : le type d'index de cet index de domaine n'est pas valide.|
|DOMIDX_OPSTATUS|String|Indique l'état d'une opération effectuée sur un index de domaine : NULL : l'index spécifié n'est pas un index de domaine. VALID : l'opération a été effectuée sans erreur. FAILED : l'opération a échoué en générant une erreur.|
|FUNCIDX_STATUS|String|Indique l'état d'un index basé sur une fonction : NULL : il ne s’agit pas d’un index basé sur une fonction, activé : l’index basé sur une fonction est activé, désactivé : l’index basé sur une fonction est désactivé.|
|JOIN_INDEX|String|Indique s'il s'agit ou non d'un index de jointure.|

## <a name="indexcolumns"></a>IndexColumns

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|INDEX_OWNER|String|Propriétaire de l'index.|
|INDEX_NAME|String|Nom de l'index.|
|TABLE_OWNER|String|Propriétaire de la table ou du cluster.|
|TABLE_NAME|String|Nom de la table ou du cluster.|
|COLUMN_NAME|String|Nom ou attribut de colonne d'une colonne de type objet.|
|COLUMN_POSITION|Decimal|Position de colonne ou d'attribut dans l'index.|
|COLUMN_LENGTH|Decimal|Longueur indexée de la colonne.|
|CHAR_LENGTH|Decimal|Longueur maximale de points de code de la colonne.|
|DESCEND|String|Indique si la colonne est triée en ordre décroissant.|

## <a name="procedures"></a>Procédures

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de l'objet.|
|OBJECT_NAME|String|Nom de l'objet.|
|SUBOBJECT_NAME|String|Nom du sous-objet (par exemple, partition).|
|OBJECT_ID|Decimal|Numéro d'objet de dictionnaire de l'objet.|
|DATA_OBJECT_ID|Decimal|Numéro d'objet de dictionnaire du segment contenant l'objet.|
|LAST_DDL_TIME|DateTime|Horodateur de la dernière modification de l'objet résultant d'une commande DDL (par exemple, d'octroi ou de révocation).|
|TIMESTAMP|String|Horodateur de la spécification de l'objet (données de type caractère).|
|STATUT|String|État de l'objet (VALID, INVALID ou N/A).|
|TEMPORARY|String|Indique si l'objet est temporaire (la session actuelle ne peut voir que les données placées dans cet objet proprement dit).|
|GENERATED|String|Le nom de cet objet a-t-il été généré par le système ? (Y &#124; N).|
|SECONDARY|String|Indique s’il s’agit d’un objet secondaire créé par la méthode ODCIIndexCreate de la cartouche de &#124; données Oracle9i (Y N).|
|CREATED|DateTime|Date à laquelle l'objet a été créé.|

## <a name="sequences"></a>Séquences

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|SEQUENCE_OWNER|String|Nom du propriétaire de la séquence.|
|SEQUENCE_NAME|String|Nom de la séquence.|
|MIN_VALUE|Decimal|Valeur minimale de la séquence.|
|MAX_VALUE|Decimal|Valeur maximale de la séquence.|
|INCREMENT_BY|Decimal|Valeur d'incrémentation de la séquence.|
|CYCLE_FLAG|String|Indique si la séquence reprend au début lorsqu'elle atteint la limite.|
|ORDER_FLAG|String|Indique si les numéros de séquence sont générés dans l'ordre.|
|CACHE_SIZE|Decimal|Nombre de numéros de séquence à mettre en cache.|
|LAST_NUMBER|Decimal|Dernier numéro de séquence écrit sur le disque. Si une séquence utilise une mise en cache, le numéro écrit sur le disque est le dernier numéro placé dans la cache de la séquence. Ce numéro est probablement supérieur au dernier numéro de séquence utilisé.|

## <a name="synonyms"></a>Synonymes

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire du synonyme.|
|SYNONYM_NAME|String|Nom du synonyme.|
|TABLE_OWNER|String|Propriétaire de l'objet référencé par le synonyme.|
|TABLE_NAME|String|Nom de l'objet référencé par le synonyme.|
|DB_LINK|String|Nom du lien de base de données éventuellement référencé.|

## <a name="tables"></a>Tables

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de la table.|
|TABLE_NAME|String|Nom de la table.|
|TYPE|String|Type de table.|

## <a name="users"></a>Utilisateurs

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|NAME|String|Nom de l'utilisateur.|
|ID|Decimal|Numéro d'ID de l'utilisateur.|
|CREATEDATE|DateTime|Date de création de l'utilisateur.|

## <a name="views"></a>Affichages

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de la vue.|
|VIEW_NAME|String|Nom de la vue.|
|TEXT_LENGTH|Decimal|Longueur du texte de la vue.|
|TEXT|String|Texte de la vue.|
|TYPE_TEXT_LENGTH|Decimal|Longueur de la clause type de la vue typée.|
|TYPE_TEXT|String|Clause type de la vue typée.|
|OID_TEXT_LENGTH|Decimal|Longueur de la clause WITH OID de la vue typée.|
|OID_TEXT|String|Clause WITH OID de la vue typée.|
|VIEW_TYPE_OWNER|String|Propriétaire du type de la vue s'il s'agit d'une vue typée.|
|VIEW_TYPE|String|Type de la vue s'il s'agit d'une vue typée.|
|SUPERVIEW_NAME|String|Nom de la super-vue.|

## <a name="functions"></a>Fonctions

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de l'objet.|
|OBJECT_NAME|String|Nom de l'objet.|
|SUBOBJECT_NAME|String|Nom du sous-objet (par exemple, partition).|
|OBJECT_ID|Decimal|Numéro d'objet de dictionnaire de l'objet.|
|DATA_OBJECT_ID|Decimal|Numéro d'objet de dictionnaire du segment contenant l'objet.|
|OBJECT_TYPE|String|Type de l'objet.|
|CREATED|DateTime|Date à laquelle l'objet a été créé.|
|LAST_DDL_TIME|DateTime|Horodateur de la dernière modification de l'objet résultant d'une commande DDL (par exemple, d'octroi ou de révocation).|
|TIMESTAMP|String|Horodateur de la spécification de l'objet (données de type caractère).|
|STATUT|String|État de l'objet (VALID, INVALID ou N/A).|
|TEMPORARY|String|Indique si l'objet est temporaire (la session actuelle ne peut voir que les données placées dans cet objet proprement dit).|
|GENERATED|String|Le nom de cet objet a-t-il été généré par le système ? (Y &#124; N).|
|SECONDARY|String|Indique s’il s’agit d’un objet secondaire créé par la méthode ODCIIndexCreate de la cartouche de &#124; données Oracle9i (Y N).|

## <a name="packages"></a>Packages

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de l'objet.|
|OBJECT_NAME|String|Nom de l'objet.|
|SUBOBJECT_NAME|String|Nom du sous-objet (par exemple, partition).|
|OBJECT_ID|Decimal|Numéro d'objet de dictionnaire de l'objet.|
|DATA_OBJECT_ID|Decimal|Numéro d'objet de dictionnaire du segment contenant l'objet.|
|LAST_DDL_TIME|DateTime|Horodateur de la dernière modification de l'objet résultant d'une commande DDL (par exemple, d'octroi ou de révocation).|
|TIMESTAMP|String|Horodateur de la spécification de l'objet (données de type caractère).|
|STATUT|String|État de l'objet (VALID, INVALID ou N/A).|
|TEMPORARY|String|Indique si l'objet est temporaire (la session actuelle ne peut voir que les données placées dans cet objet proprement dit).|
|GENERATED|String|Le nom de cet objet a-t-il été généré par le système ? (Y &#124; N).|
|SECONDARY|String|Indique s’il s’agit d’un objet secondaire créé par la méthode ODCIIndexCreate de la cartouche de &#124; données Oracle9i (Y N).|
|CREATED|DateTime|Date à laquelle l'objet a été créé.|

## <a name="packagebodies"></a>PackageBodies

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de l'objet.|
|OBJECT_NAME|String|Nom de l'objet.|
|SUBOBJECT_NAME|String|Nom du sous-objet (par exemple, partition).|
|OBJECT_ID|Decimal|Numéro d'objet de dictionnaire de l'objet.|
|DATA_OBJECT_ID|Decimal|Numéro d'objet de dictionnaire du segment contenant l'objet.|
|LAST_DDL_TIME|DateTime|Horodateur de la dernière modification de l'objet résultant d'une commande DDL (par exemple, d'octroi ou de révocation).|
|TIMESTAMP|String|Horodateur de la spécification de l'objet (données de type caractère).|
|STATUT|String|État de l'objet (VALID, INVALID ou N/A).|
|TEMPORARY|String|Indique si l'objet est temporaire (la session actuelle ne peut voir que les données placées dans cet objet proprement dit).|
|GENERATED|String|Le nom de cet objet a-t-il été généré par le système ? (Y &#124; N).|
|SECONDARY|String|Indique s’il s’agit d’un objet secondaire créé par la méthode ODCIIndexCreate de la cartouche de &#124; données Oracle9i (Y N).|
|CREATED|DateTime|Date à laquelle l'objet a été créé.|

## <a name="arguments"></a>Arguments

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Nom du propriétaire de l'objet.|
|PACKAGE_NAME|String|Nom du package.|
|OBJECT_NAME|String|Nom de la procédure ou de la fonction.|
|ARGUMENT_NAME|String|Nom de l’argument.|
|POSITION|Decimal|Position dans la liste d’arguments ou NULL pour une valeur de retour de fonction.|
|SEQUENCE|Decimal|Séquence d'arguments, y compris tous les niveaux d'imbrication.|
|DEFAULT_VALUE|String|Valeur par défaut de l'argument.|
|DEFAULT_LENGTH|Decimal|Longueur de la valeur par défaut de l’argument.|
|IN_OUT|String|Direction de l’argument (IN, OUT ou IN/OUT).|
|DATA_LENGTH|Decimal|Longueur de la colonne en octets.|
|DATA_PRECISION|Decimal|Longueur en chiffres décimaux (NUMBER) ou en chiffres binaires (FLOAT).|
|DATA_SCALE|Decimal|Chiffres à droite de la virgule décimale dans un nombre.|
|DATA_TYPE|String|Type de données de l'argument.|

## <a name="uniquekeys"></a>UniqueKeys

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de la définition de contrainte.|
|CONSTRAINT_NAME|String|Nom de la définition de contrainte.|
|TABLE_NAME|String|Nom associé à la table (ou la vue) avec une définition de contrainte.|
|SEARCH_CONDITION|String|Texte de la condition de recherche d'une contrainte de validation.|
|R_OWNER|String|Propriétaire de la table à laquelle fait référence une contrainte référentielle.|
|R_CONSTRAINT_NAME|String|Nom de la définition de contrainte unique pour une table référencée.|
|DELETE_RULE|String|Règle de suppression pour une contrainte référentielle (CASCADE ou NO ACTION).|
|STATUT|String|État d'application d'une contrainte (ENABLED ou DISABLED).|
|DEFERRABLE|String|Indique si la contrainte peut être différée.|
|VALIDATED|String|Indique si toutes les données obéissent à la contrainte (VALIDATED ou NOT VALIDATED).|
|GENERATED|String|Indique si le nom de la contrainte est généré par l'utilisateur ou le système.|
|BAD|String|La valeur YES indique que cette contrainte spécifie un siècle de façon ambiguë. Pour éviter les erreurs résultant de cette ambiguïté, réécrivez la contrainte à l'aide de la fonction TO_DATE avec une année à quatre chiffres.|
|RELY|String|Indique si une contrainte activée est appliquée ou non appliquée.|
|LAST_CHANGE|DateTime|Indique quand la contrainte a été activée ou désactivée pour la dernière fois.|
|INDEX_OWNER|String|Nom de l'utilisateur propriétaire de l'index.|
|INDEX_NAME|String|Nom de l'index.|

## <a name="primarykeys"></a>PrimaryKeys

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de la définition de contrainte.|
|CONSTRAINT_NAME|String|Nom de la définition de contrainte.|
|TABLE_NAME|String|Nom associé à la table (ou la vue) avec une définition de contrainte.|
|SEARCH_CONDITION|String|Texte de la condition de recherche d'une contrainte de validation.|
|R_OWNER|String|Propriétaire de la table à laquelle fait référence une contrainte référentielle.|
|R_CONSTRAINT_NAME|String|Nom de la définition de contrainte unique pour une table référencée.|
|DELETE_RULE|String|Règle de suppression pour une contrainte référentielle (CASCADE ou NO ACTION).|
|STATUT|String|État d'application d'une contrainte (ENABLED ou DISABLED).|
|DEFERRABLE|String|Indique si la contrainte peut être différée.|
|VALIDATED|String|Indique si toutes les données obéissent à la contrainte (VALIDATED ou NOT VALIDATED).|
|GENERATED|String|Indique si le nom de la contrainte est généré par l'utilisateur ou le système.|
|BAD|String|La valeur YES indique que cette contrainte spécifie un siècle de façon ambiguë. Pour éviter les erreurs résultant de cette ambiguïté, réécrivez la contrainte à l'aide de la fonction TO_DATE avec une année à quatre chiffres.|
|RELY|String|Indique si une contrainte activée est appliquée ou non appliquée.|
|LAST_CHANGE|DateTime|Indique quand la contrainte a été activée ou désactivée pour la dernière fois.|
|INDEX_OWNER|String|Nom de l'utilisateur propriétaire de l'index.|
|INDEX_NAME|String|Nom de l'index.|

## <a name="foreignkeys"></a>ForeignKeys

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|PRIMARY_KEY_CONSTRAINT_NAME|String|Nom de la définition de contrainte.|
|PRIMARY_KEY_OWNER|String|Propriétaire de la définition de contrainte.|
|PRIMARY_KEY_TABLE_NAME|String|Nom associé à la table (ou la vue) avec une définition de contrainte.|
|FOREIGN_KEY_OWNER|String|Propriétaire de la définition de contrainte.|
|FOREIGN_KEY_CONSTRAINT_NAME|String|Nom de la définition de contrainte.|
|FOREIGN_KEY_TABLE_NAME|String|Nom associé à la table (ou la vue) avec une définition de contrainte.|
|SEARCH_CONDITION|String|Texte de la condition de recherche d'une contrainte de validation.|
|R_OWNER|String|Propriétaire de la table à laquelle fait référence une contrainte référentielle.|
|R_CONSTRAINT_NAME|String|Nom de la définition de contrainte unique pour une table référencée.|
|DELETE_RULE|String|Règle de suppression pour une contrainte référentielle (CASCADE ou NO ACTION).|
|STATUT|String|État d'application d'une contrainte (ENABLED ou DISABLED).|
|VALIDATED|String|Indique si toutes les données obéissent à la contrainte (VALIDATED ou NOT VALIDATED).|
|GENERATED|String|Indique si le nom de la contrainte est généré par l'utilisateur ou le système.|
|RELY|String|Indique si une contrainte activée est appliquée ou non appliquée.|
|LAST_CHANGE|DateTime|Indique quand la contrainte a été activée ou désactivée pour la dernière fois.|
|INDEX_OWNER|String|Nom de l'utilisateur propriétaire de l'index.|
|INDEX_NAME|String|Nom de l'index.|

## <a name="foreignkeycolumns"></a>ForeignKeyColumns

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de la définition de contrainte.|
|CONSTRAINT_NAME|String|Nom de la définition de contrainte.|
|TABLE_NAME|String|Nom de la table contenant la définition de contrainte.|
|COLUMN_NAME|String|Nom de la colonne ou de l'attribut de la colonne de type d'objet spécifié dans la définition de contrainte.|
|POSITION|Decimal|Position originale de la colonne ou de l'attribut dans la définition de l'objet.|

## <a name="procedureparameters"></a>ProcedureParameters

|ColumnName|Type de données|Description|
|----------------|--------------|-----------------|
|OWNER|String|Propriétaire de l'objet.|
|OBJECT_NAME|String|Nom de la procédure ou de la fonction.|
|PACKAGE_NAME|String|Nom de la procédure ou de la fonction.|
|OBJECT_ID|Decimal|Numéro de l'objet.|
|OVERLOAD|String|Identificateur unique de surcharge.|
|ARGUMENT_NAME|String|Nom de l’argument.|
|POSITION|Decimal|Position dans la liste d’arguments ou NULL pour une valeur de retour de fonction.|
|SEQUENCE|Decimal|Séquence d'arguments, y compris tous les niveaux d'imbrication.|
|DATA_LEVEL|Decimal|Profondeur d’imbrication de l’argument pour les types composites.|
|DATA_TYPE|String|Type de données de l'argument.|
|DEFAULT_VALUE|String|Valeur par défaut de l'argument.|
|DEFAULT_LENGTH|Decimal|Longueur de la valeur par défaut de l'argument.|
|IN_OUT|String|Direction de l’argument (IN, OUT ou IN/OUT).|
|DATA_LENGTH|Decimal|Longueur de la colonne (en octets).|
|DATA_PRECISION|Decimal|Longueur en chiffres décimaux (NUMBER) ou en chiffres binaires (FLOAT).|
|DATA_SCALE|Decimal|Chiffres à droite de la virgule décimale dans un nombre.|
|RADIX|Decimal|Radical d’argument pour un nombre.|
|CHARACTER_SET_NAME|String|Nom de l’ensemble de caractères pour l’argument.|
|TYPE_OWNER|String|Propriétaire du type de l’argument.|
|TYPE_NAME|String|Nom du type de l'argument. Si le type est un type de package local (c'est-à-dire qu'il est déclaré dans une spécification de package), cette colonne affiche le nom du package.|
|TYPE_SUBNAME|String|Pertinent uniquement pour les types de package locaux. Affiche le nom du type déclaré dans le package identifié dans la colonne TYPE_NAME.|
|TYPE_LINK|String|Pertinent uniquement pour les types de package locaux lorsque le package identifié dans la colonne TYPE_NAME est un package distant. Cette colonne affiche le lien de base de données utilisé pour faire référence au package distant.|
|PLS_TYPE|String|Pour les arguments numériques, nom du type PL/SQL de l’argument. Sinon, Null.|
|CHAR_LENGTH|Decimal|Limite de caractères pour les données de type string.|
|CHAR_USED|String|Indique si la limite d'octets (B) ou la limite de caractères (C) est officielle pour la chaîne.|

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
