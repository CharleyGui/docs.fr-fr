---
title: Collections de schémas SQL Server
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 0f65bbf2534eb7167baacb1405a8ce6e9769c23f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794334"
---
# <a name="sql-server-schema-collections"></a>Collections de schémas SQL Server
Le fournisseur de données Microsoft .NET Framework pour SQL Server prend en charge d’autres collections de schémas en plus des collections de schémas courantes. Les collections de schémas varient légèrement selon la version de SQL Server que vous utilisez. Pour déterminer la liste des collections de schémas prises en charge, appelez la méthode **GetSchema** sans argument ou avec le nom de la collection de schémas « MetaDataCollections ». Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu’elles prennent en charge et le nombre d’éléments d’identification qu’elles utilisent.  
  
## <a name="databases"></a>Bases de données  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|database_name|String|Nom de la base de données.|  
|dbid|Int16|ID de la base de données.|  
|create_date|DateTime|Date de création de la base de données.|  
  
## <a name="foreign-keys"></a>Clés étrangères  
  
|ColumnName|Type de données|Description|  
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
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Catalogue auquel l'index appartient.|  
|constraint_schema|String|Schéma contenant l'index.|  
|constraint_name|String|Nom de l'index.|  
|table_catalog|String|Nom de la table auquel l'index est associé.|  
|table_schema|String|Schéma contenant la table à laquelle l'index est associé.|  
|table_name|String|Nom de table.|  
|nom_index|String|Nom de l’index.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, les colonnes suivantes sont été ajoutées à la collection de schémas Indexes afin de prendre en charge de nouveaux types de données spatiales, flux de fichiers et colonnes fragmentées. Ces colonnes ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|type_desc|String|Le type de l'index est l'un des suivants :<br /><br /> -SEGMENT DE MÉMOIRE<br />-CLUSTER<br />-NON-CLUSTER<br />-   XML<br />-SPATIAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|constraint_catalog|String|Catalogue auquel l'index appartient.|  
|constraint_schema|String|Schéma contenant l'index.|  
|constraint_name|String|Nom de l'index.|  
|table_catalog|String|Nom de la table auquel l'index est associé.|  
|table_schema|String|Schéma contenant la table à laquelle l'index est associé.|  
|table_name|String|Nom de table.|  
|column_name|String|Nom de la colonne à laquelle l'index est associé.|  
|ordinal_position|Int32|Position du numéro de colonne.|  
|KeyType|Byte|Type d'objet.|  
|nom_index|String|Nom de l’index.|  
  
## <a name="procedures"></a>Procédures  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nom spécifique du catalogue.|  
|SPECIFIC_SCHEMA|String|Nom spécifique du schéma.|  
|SPECIFIC_NAME|String|Nom spécifique du catalogue.|  
|ROUTINE_CATALOG|String|Catalogue auquel appartient la procédure stockée.|  
|ROUTINE_SCHEMA|String|Schéma contenant la procédure stockée.|  
|ROUTINE_NAME|String|Nom de la procédure stockée.|  
|ROUTINE_TYPE|String|Retourne PROCEDURE pour les procédures stockées et FUNCTION pour les fonctions.|  
|CREATED|DateTime|Heure à laquelle la procédure a été créée.|  
|LAST_ALTERED|DateTime|Heure à laquelle la procédure a été modifiée pour la dernière fois.|  
  
## <a name="procedure-parameters"></a>Paramètres de procédure  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|String|Nom du catalogue de la procédure pour laquelle ceci est un paramètre.|  
|SPECIFIC_SCHEMA|String|Schéma contenant la procédure dont ce paramètre fait partie.|  
|SPECIFIC_NAME|String|Nom de la procédure dont ce paramètre fait partie.|  
|ORDINAL_POSITION|Int32|Position ordinale du paramètre commençant à 1. Pour la valeur de retour d'une procédure, cela donne 0.|  
|PARAMETER_MODE|String|Retourne IN pour un paramètre d'entrée, OUT pour un paramètre de sortie et INOUT pour un paramètre d'entrée/sortie.|  
|IS_RESULT|String|Retourne YES s'il indique que le résultat de la procédure est une fonction. Sinon, retourne NO.|  
|AS_LOCATOR|String|Retourne YES s'il est déclaré comme pointeur. Sinon, retourne NO.|  
|PARAMETER_NAME|String|Nom du paramètre. NULL si ceci correspond à la valeur de retour d'une fonction.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longueur maximale en caractères pour des types de données binaires ou sous forme de caractères. Sinon, retourne NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Longueur maximale en octets pour des types de données binaires ou sous forme de caractères. Sinon, retourne NULL.|  
|COLLATION_CATALOG|String|Nom de catalogue du classement du paramètre. S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|COLLATION_SCHEMA|String|Retourne toujours NULL.|  
|COLLATION_NAME|String|Nom du classement du paramètre. S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|CHARACTER_SET_CATALOG|String|Nom de catalogue de l'ensemble de caractères du paramètre. S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours NULL.|  
|CHARACTER_SET_NAME|String|Nom du jeu de caractères du paramètre. S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|NUMERIC_PRECISION|Byte|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, retourne NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, retourne NULL.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, retourne NULL.|  
|DATETIME_PRECISION|Int16|Précision en secondes fractionnelles si le type de paramètre est datetime ou smalldatetime. Sinon, retourne NULL.|  
|INTERVAL_TYPE|String|NULL. Réservé pour un usage futur de SQL Server.|  
|INTERVAL_PRECISION|Int16|NULL. Réservé pour un usage futur de SQL Server.|  
  
## <a name="tables"></a>Tables  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|TABLE_TYPE|String|Type de table. Peut être VIEW ou BASE TABLE.|  
  
## <a name="columns"></a>Colonnes  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|COLUMN_NAME|String|Nom de la colonne.|  
|ORDINAL_POSITION|Int32|Numéro d'identification de colonne.|  
|COLUMN_DEFAULT|String|Valeur par défaut de la colonne|  
|IS_NULLABLE|String|Prise en charge des valeurs null dans la colonne. Si cette colonne autorise les valeurs NULL, elle retourne YES. Dans le cas contraire, elle retourne No.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Longueur maximale en caractères pour les données binaires, sous forme de caractères, de texte ou d'image. Sinon, la valeur NULL est retournée.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Longueur maximale en octets pour les données binaires, sous forme de caractères, de texte ou d'image. Sinon, la valeur NULL est retournée.|  
|NUMERIC_PRECISION|Octet non signé|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|NUMERIC_PRECISION_RADIX|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|DATETIME_PRECISION|Int16|Code Subtype pour les types de données d'intervalle datetime et SQL-92. Pour les autres types de données, la valeur NULL est retournée.|  
|CHARACTER_SET_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte. Sinon, la valeur NULL est retournée.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours NULL.|  
|CHARACTER_SET_NAME|String|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte. Sinon, la valeur NULL est retournée.|  
|COLLATION_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte. Sinon, cette colonne a une valeur NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, les colonnes suivantes sont été ajoutées à la collection de schémas Columns afin de prendre en charge de nouveaux types de données spatiales, flux de fichiers et colonnes fragmentées. Ces colonnes ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|String|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS_SPARSE|String|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS_COLUMN_SET|String|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, la collection de schémas AllColumns a été ajoutée afin de permettre la prise en charge des colonnes fragmentées. AllColumns n'est pas prise en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
 AllColumns présente les mêmes restrictions et schéma DataTable résultant que la collection de schémas Columns. La seule différence vient du fait que la collection AllColumns inclut des colonnes d'ensembles de colonnes qui ne sont pas incluses dans la collection de schémas Columns. Le tableau suivant décrit ces colonnes.  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|COLUMN_NAME|String|Nom de la colonne.|  
|ORDINAL_POSITION|Int32|Numéro d'identification de colonne.|  
|COLUMN_DEFAULT|String|Valeur par défaut de la colonne|  
|IS_NULLABLE|String|Prise en charge des valeurs null dans la colonne. Si cette colonne autorise les valeurs NULL, elle retourne YES. Dans le cas contraire, elle retourne NO.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longueur maximale en caractères pour les données binaires, sous forme de caractères, de texte ou d'image. Sinon, la valeur NULL est retournée.|  
|CHARACTER_OCTET_LENGTH|Int32|Longueur maximale en octets pour les données binaires, sous forme de caractères, de texte ou d'image. Sinon, la valeur NULL est retournée.|  
|NUMERIC_PRECISION|Octet non signé|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|NUMERIC_PRECISION_RADIX|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|DATETIME_PRECISION|Int16|Code Subtype pour les types de données d'intervalle datetime et SQL-92. Pour les autres types de données, la valeur NULL est retournée.|  
|CHARACTER_SET_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte. Sinon, la valeur NULL est retournée.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours NULL.|  
|CHARACTER_SET_NAME|String|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte. Sinon, la valeur NULL est retournée.|  
|COLLATION_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte. Sinon, cette colonne a une valeur NULL.|  
|IS_FILESTREAM|String|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS_SPARSE|String|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS_COLUMN_SET|String|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, la collection de schémas ColumnSetColumns a été ajoutée afin de permettre la prise en charge des colonnes fragmentées. ColumnSetColumns n'est pas prise en charge dans les versions précédentes de .NET Framework et SQL Server. La collection de schémas ColumnSetColumns retourne le schéma de toutes les colonnes dans un ensemble de colonnes. Le tableau suivant décrit ces colonnes.  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la table.|  
|TABLE_SCHEMA|String|Schéma contenant la table.|  
|TABLE_NAME|String|Nom de la table.|  
|COLUMN_NAME|String|Nom de la colonne.|  
|ORDINAL_POSITION|Int32|Numéro d'identification de colonne.|  
|COLUMN_DEFAULT|String|Valeur par défaut de la colonne|  
|IS_NULLABLE|String|Prise en charge des valeurs null dans la colonne. Si cette colonne autorise les valeurs NULL, elle retourne YES. Dans le cas contraire, elle retourne NO.|  
|DATA_TYPE|String|Type de données fourni par le système.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Longueur maximale en caractères pour les données binaires, sous forme de caractères, de texte ou d'image. Sinon, la valeur NULL est retournée.|  
|CHARACTER_OCTET_LENGTH|Int32|Longueur maximale en octets pour les données binaires, sous forme de caractères, de texte ou d'image. Sinon, la valeur NULL est retournée.|  
|NUMERIC_PRECISION|Octet non signé|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|NUMERIC_PRECISION_RADIX|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|NUMERIC_SCALE|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires. Sinon, la valeur NULL est retournée.|  
|DATETIME_PRECISION|Int16|Code Subtype pour les types de données d'intervalle datetime et SQL-92. Pour les autres types de données, la valeur NULL est retournée.|  
|CHARACTER_SET_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte. Sinon, la valeur NULL est retournée.|  
|CHARACTER_SET_SCHEMA|String|Retourne toujours NULL.|  
|CHARACTER_SET_NAME|String|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte. Sinon, la valeur NULL est retournée.|  
|COLLATION_CATALOG|String|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte. Sinon, cette colonne a une valeur NULL.|  
|IS_FILESTREAM|String|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS_SPARSE|String|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS_COLUMN_SET|String|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
## <a name="users"></a>Utilisateurs  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|uid|Int16|ID d'utilisateur, unique dans cette base de données. 1 est le propriétaire de base de données.|  
|nom_utilisateur|String|Nom d'utilisateur ou nom de groupe, unique dans cette base de données.|  
|createdate|DateTime|Date d'ajout du compte.|  
|updatedate|DateTime|Date à laquelle le compte a été modifié pour la dernière fois.|  
  
## <a name="views"></a>Affichages  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|String|Catalogue de la vue.|  
|TABLE_SCHEMA|String|Schéma contenant la vue.|  
|TABLE_NAME|String|Nom de la vue.|  
|CHECK_OPTION|String|Type de WITH CHECK OPTION. Est CASCADE si la vue originale a été créée à l'aide de WITH CHECK OPTION. Dans le cas contraire, retourne NONE.|  
|IS_UPDATABLE|String|Indique si la vue peut être mise à jour. Retourne toujours NO.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|Type de données|Description|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|String|Catalogue de la vue.|  
|VIEW_SCHEMA|String|Schéma contenant la vue.|  
|VIEW_NAME|String|Nom de la vue.|  
|TABLE_CATALOG|String|Catalogue de la table associée à cette vue.|  
|TABLE_SCHEMA|String|Schéma contenant la table associée à cette vue.|  
|TABLE_NAME|String|Nom de la table associée à cette vue. Table de base.|  
|COLUMN_NAME|String|Nom de la colonne.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|Type de données|Description|  
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

- [Récupération des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
