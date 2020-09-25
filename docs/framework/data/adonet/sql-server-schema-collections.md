---
title: Collections de schémas SQL Server
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: ebb0cea20aede3d04e37536c7c615678e109337a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197662"
---
# <a name="sql-server-schema-collections"></a>Collections de schémas SQL Server

Le fournisseur de données Microsoft .NET Framework pour SQL Server prend en charge d’autres collections de schémas en plus des collections de schémas courantes. Les collections de schémas varient légèrement selon la version de SQL Server que vous utilisez. Pour déterminer la liste des collections de schémas prises en charge, appelez la méthode **GetSchema** sans argument ou avec le nom de la collection de schémas « MetaDataCollections ». Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu’elles prennent en charge et le nombre d’éléments d’identification qu’elles utilisent.  
  
## <a name="databases"></a>Bases de données  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|database_name|String|Nom de la base de données.|  
|dbid|Int16|ID de la base de données.|  
|create_date|DateTime|Date de création de la base de données.|  
  
## <a name="foreign-keys"></a>Clés étrangères  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|String|Catalogue auquel la contrainte appartient.|  
|CONSTRAINT_SCHEMA|String|Schéma contenant la contrainte.|  
|CONSTRAINT_NAME|String|Nom.|  
|TABLE_CATALOG|String|Nom de la table dont la contrainte fait partie.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table|  
|CONSTRAINT_TYPE|String|Type de contrainte. Seul « FOREIGN KEY » est autorisé.|  
|IS_DEFERRABLE|String|Indique si la contrainte peut être différée. Retourne NO.|  
|INITIALLY_DEFERRED|String|Indique si la contrainte est initialement différée. Retourne NO.|  
  
## <a name="indexes"></a>Index  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Catalogue auquel l'index appartient.|  
|constraint_schema|String|Schéma contenant l'index.|  
|constraint_name|String|Nom de l'index.|  
|table_catalog|String|Nom de la table auquel l'index est associé.|  
|table_schema|String|Schéma contenant la table à laquelle l'index est associé.|  
|table_name|String|Nom de table.|  
|index_name|String|Nom de l’index.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  

 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, les colonnes suivantes sont été ajoutées à la collection de schémas Indexes afin de prendre en charge de nouveaux types de données spatiales, flux de fichiers et colonnes fragmentées. Ces colonnes ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|type_desc|String|Le type de l'index est l'un des suivants :<br /><br /> -Segment de mémoire<br />-CLUSTER<br />-Non-CLUSTER<br />-XML<br />-SPATIAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Catalogue auquel l'index appartient.|  
|constraint_schema|String|Schéma contenant l'index.|  
|constraint_name|String|Nom de l'index.|  
|table_catalog|String|Nom de la table auquel l'index est associé.|  
|table_schema|String|Schéma contenant la table à laquelle l'index est associé.|  
|table_name|String|Nom de table.|  
|column_name|String|Nom de la colonne à laquelle l'index est associé.|  
|ordinal_position|Int32|Position ordinale de la colonne.|  
|KeyType|Byte|Type d'objet.|  
|index_name|String|Nom de l’index.|  
  
## <a name="procedures"></a>Procédures  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nom spécifique du catalogue.|  
|SPECIFIC_SCHEMA|String|Nom spécifique du schéma.|  
|SPECIFIC_NAME|String|Nom spécifique du catalogue|  
|ROUTINE_CATALOG|String|Catalogue auquel appartient la procédure stockée.|  
|ROUTINE_SCHEMA|String|Schéma contenant la procédure stockée.|  
|ROUTINE_NAME|String|Nom de la procédure stockée.|  
|ROUTINE_TYPE|String|Retourne PROCEDURE pour les procédures stockées et FUNCTION pour les fonctions.|  
|CREATED|DateTime|Heure à laquelle la procédure a été créée.|  
|LAST_ALTERED|DateTime|Heure à laquelle la procédure a été modifiée pour la dernière fois.|  
  
## <a name="procedure-parameters"></a>Paramètres de procédure  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nom du catalogue de la procédure pour laquelle ceci est un paramètre.|  
|SPECIFIC_SCHEMA|String|Schéma contenant la procédure dont ce paramètre fait partie.|  
|SPECIFIC_NAME|String|Nom de la procédure dont ce paramètre fait partie.|  
|ORDINAL_POSITION|Int32|Position ordinale du paramètre en commençant à 1. Pour la valeur de retour d'une procédure, cela donne 0.|  
|PARAMETER_MODE|String|Retourne IN pour un paramètre d'entrée, OUT pour un paramètre de sortie et INOUT pour un paramètre d'entrée/sortie.|  
|IS_RESULT|String|Retourne YES s'il indique que le résultat de la procédure est une fonction. Dans le cas contraire, la valeur retournée est NO.|  
|AS_LOCATOR|String|Retourne YES si l'élément est déclaré comme localisateur. Dans le cas contraire, la valeur retournée est NO.|  
|PARAMETER_NAME|String|Nom du paramètre. NULL si ceci correspond à la valeur retournée d'une fonction.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longueur maximale en caractères des données de type binaire ou caractère. Dans le cas contraire, la valeur NULL est retournée.|  
|CHARACTER_OCTET_LENGTH|Int32|Longueur maximale en octets des données de type binaire ou caractère. Dans le cas contraire, la valeur NULL est retournée.|  
|COLLATION_CATALOG|String|Nom de catalogue du classement du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|COLLATION_SCHEMA|String|Retourne toujours la valeur Null.|  
|COLLATION_NAME|String|Nom du classement du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|CHARACTER_SET_CATALOG|String|Nom de catalogue du jeu de caractères du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours la valeur Null.|  
|CHARACTER_SET_NAME|String|Nom du jeu de caractères du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|NUMERIC_PRECISION|Byte|Précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|DATETIME_PRECISION|Int16|Précision en secondes fractionnelles si le type de paramètre est datetime ou smalldatetime. Dans le cas contraire, la valeur NULL est retournée.|  
|INTERVAL_TYPE|String|NULL. Réservé pour un usage futur de SQL Server.|  
|INTERVAL_PRECISION|Int16|NULL. Réservé pour un usage futur de SQL Server.|  
  
## <a name="tables"></a>Tables  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|TABLE_TYPE|String|Type de table. Peut être VIEW ou BASE TABLE.|  
  
## <a name="columns"></a>Colonnes  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|COLUMN_NAME|String|Nom de la colonne.|  
|ORDINAL_POSITION|Int32|Numéro d'identification de colonne.|  
|COLUMN_DEFAULT|String|Valeur par défaut de la colonne|  
|IS_NULLABLE|String|Valeur NULL possible dans la colonne. Si cette colonne autorise les valeurs NULL, elle retourne YES. Dans le cas contraire, elle retourne No.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Longueur maximale (en caractères) des données de type binaire, caractère, texte et image. Renvoie NULL dans les autres cas.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Longueur maximale, en octets, des données de type binaire, caractère, texte et image. Renvoie NULL dans les autres cas.|  
|NUMERIC_PRECISION|Octet non signé|Précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|DATETIME_PRECISION|Int16|Code de sous-type pour le type de données datetime et pour le type de données interval de SQL-92. Renvoie NULL pour les autres types de données.|  
|CHARACTER_SET_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte. Renvoie NULL dans les autres cas.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours la valeur Null.|  
|CHARACTER_SET_NAME|String|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte. Renvoie NULL dans les autres cas.|  
|COLLATION_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte. Sinon, cette colonne est NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  

 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, les colonnes suivantes sont été ajoutées à la collection de schémas Columns afin de prendre en charge de nouveaux types de données spatiales, flux de fichiers et colonnes fragmentées. Ces colonnes ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS_SPARSE|String|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS_COLUMN_SET|String|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  

 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, la collection de schémas AllColumns a été ajoutée afin de permettre la prise en charge des colonnes fragmentées. AllColumns n'est pas prise en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
 AllColumns présente les mêmes restrictions et schéma DataTable résultant que la collection de schémas Columns. La seule différence vient du fait que la collection AllColumns inclut des colonnes d'ensembles de colonnes qui ne sont pas incluses dans la collection de schémas Columns. Le tableau suivant décrit ces colonnes.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|COLUMN_NAME|String|Nom de la colonne.|  
|ORDINAL_POSITION|Int32|Numéro d'identification de colonne.|  
|COLUMN_DEFAULT|String|Valeur par défaut de la colonne|  
|IS_NULLABLE|String|Valeur NULL possible dans la colonne. Si cette colonne autorise les valeurs NULL, elle retourne YES. Dans le cas contraire, elle renvoie NO.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longueur maximale (en caractères) des données de type binaire, caractère, texte et image. Renvoie NULL dans les autres cas.|  
|CHARACTER_OCTET_LENGTH|Int32|Longueur maximale, en octets, des données de type binaire, caractère, texte et image. Renvoie NULL dans les autres cas.|  
|NUMERIC_PRECISION|Octet non signé|Précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|DATETIME_PRECISION|Int16|Code de sous-type pour le type de données datetime et pour le type de données interval de SQL-92. Renvoie NULL pour les autres types de données.|  
|CHARACTER_SET_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte. Renvoie NULL dans les autres cas.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours la valeur Null.|  
|CHARACTER_SET_NAME|String|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte. Renvoie NULL dans les autres cas.|  
|COLLATION_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte. Sinon, cette colonne est NULL.|  
|IS_FILESTREAM|String|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS_SPARSE|String|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS_COLUMN_SET|String|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  

 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, la collection de schémas ColumnSetColumns a été ajoutée afin de permettre la prise en charge des colonnes fragmentées. ColumnSetColumns n'est pas prise en charge dans les versions précédentes de .NET Framework et SQL Server. La collection de schémas ColumnSetColumns retourne le schéma de toutes les colonnes dans un ensemble de colonnes. Le tableau suivant décrit ces colonnes.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|COLUMN_NAME|String|Nom de la colonne.|  
|ORDINAL_POSITION|Int32|Numéro d'identification de colonne.|  
|COLUMN_DEFAULT|String|Valeur par défaut de la colonne|  
|IS_NULLABLE|String|Valeur NULL possible dans la colonne. Si cette colonne autorise les valeurs NULL, elle retourne YES. Dans le cas contraire, elle renvoie NO.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longueur maximale (en caractères) des données de type binaire, caractère, texte et image. Renvoie NULL dans les autres cas.|  
|CHARACTER_OCTET_LENGTH|Int32|Longueur maximale, en octets, des données de type binaire, caractère, texte et image. Renvoie NULL dans les autres cas.|  
|NUMERIC_PRECISION|Octet non signé|Précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approchées ou exactes, des données de type entier ou monétaire. Renvoie NULL dans les autres cas.|  
|DATETIME_PRECISION|Int16|Code de sous-type pour le type de données datetime et pour le type de données interval de SQL-92. Renvoie NULL pour les autres types de données.|  
|CHARACTER_SET_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte. Renvoie NULL dans les autres cas.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours la valeur Null.|  
|CHARACTER_SET_NAME|String|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte. Renvoie NULL dans les autres cas.|  
|COLLATION_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte. Sinon, cette colonne est NULL.|  
|IS_FILESTREAM|String|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS_SPARSE|String|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS_COLUMN_SET|String|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
## <a name="users"></a>Utilisateurs  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|uid|Int16|ID d'utilisateur, unique dans cette base de données. 1 est le propriétaire de base de données.|  
|nom_utilisateur|String|Nom d'utilisateur ou nom de groupe, unique dans cette base de données.|  
|createdate|DateTime|Date de l'ajout du compte.|  
|updatedate|DateTime|Date de la dernière modification du compte.|  
  
## <a name="views"></a>Les vues  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la vue.|  
|TABLE_SCHEMA|String|Schéma contenant la vue.|  
|TABLE_NAME|String|Nom de la vue.|  
|CHECK_OPTION|String|Type de WITH CHECK OPTION. Est CASCADE si la vue originale a été créée à l'aide de WITH CHECK OPTION. Renvoie NONE dans le cas contraire.|  
|IS_UPDATABLE|String|Spécifie si la vue peut être mise à jour. Renvoie toujours NO.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Catalogue de la vue.|  
|VIEW_SCHEMA|String|Schéma contenant la vue.|  
|VIEW_NAME|String|Nom de la vue.|  
|TABLE_CATALOG|String|Catalogue de la table associée à cette vue.|  
|TABLE_SCHEMA|String|Schéma contenant la table associée à cette vue.|  
|TABLE_NAME|String|Nom de la table associée à cette vue. Table de base.|  
|COLUMN_NAME|String|Nom de la colonne.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|assembly_name|String|Nom du fichier pour l'assembly.|  
|udt_name|String|Nom de la classe pour l'assembly.|  
|version_major|Object|Numéro de version principale.|  
|version_minor|Object|Numéro de version secondaire.|  
|version_build|Object|Numéro de build.|  
|version_revision|Object|Numéro de révision.|  
|culture_info|Object|Informations de culture associées à cet UDT.|  
|public_key|Object|Clé publique utilisée par cet assembly.|  
|is_fixed_length|Boolean|Indique si la longueur du type est toujours identique à max_length.|  
|max_length|Int16|Longueur maximale du type en octets.|  
|Create_Date|DateTime|Date à laquelle l'assembly a été créé/enregistré.|  
|Permission_set_desc|String|Nom convivial de l'ensemble d'autorisations/niveau de sécurité pour l'assembly.|  
  
## <a name="see-also"></a>Voir aussi

- [Extraction des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
