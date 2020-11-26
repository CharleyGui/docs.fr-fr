---
title: Collections de schémas courantes
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: f822de27e53554aba4011a701f59a8feda847c67
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91203811"
---
# <a name="common-schema-collections"></a>Collections de schémas courantes

Les collections de schémas communes sont les collections de schémas implémentées par chacun des fournisseurs .NET Framework managés. Vous pouvez interroger un fournisseur managé .NET Framework pour déterminer la liste des collections de schémas prises en charge en appelant la méthode **GetSchema** sans argument ou avec le nom de la collection de schémas « MetaDataCollections ». Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu’elles prennent en charge et le nombre d’éléments d’identification qu’elles utilisent. Ces collections décrivent toutes les colonnes requises. Les fournisseurs sont libres d'ajouter des colonnes s'ils le souhaitent. Par exemple, `SqlClient` et `OracleClient` ajoutent ParameterName à la collection de restrictions.  
  
 Si un fournisseur est incapable de déterminer la valeur d'une colonne obligatoire, il retourne la valeur null.  
  
 Pour plus d’informations sur l’utilisation des méthodes **GetSchema** , consultez [GetSchema et collections de schémas](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  

 Cette collection de schémas expose des informations sur toutes les collections de schémas prises en charge par le fournisseur .NET Framework managé actuellement utilisé pour se connecter à la base de données.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|CollectionName|string|Nom de la collection à passer à la méthode **GetSchema** pour retourner la collection.|  
|NumberOfRestrictions|int|Nombre de restrictions qui peuvent être spécifiées pour la collection.|  
|NumberOfIdentifierParts|int|Nombre de parties dans le nom d'objet identificateur/base de données composite. Par exemple, dans SQL Server, ce serait 3 pour les tables et 4 pour les colonnes. Dans Oracle, ce serait 2 pour les tables et 3 pour les colonnes.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  

 Cette collection de schémas expose des informations sur la source de données à laquelle le fournisseur .NET Framework managé est actuellement connecté.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|string|Expression régulière pour mettre en correspondance les séparateurs composites dans un identificateur composite. Par exemple, «\\.» (pour SQL Server) ou « \@&#124;\\ ». (pour Oracle).<br /><br /> Un identificateur composite est généralement ce qui est utilisé pour un nom d’objet de base de données, par exemple : pubs. dbo. Authors ou pubs \@ dbo. Authors.<br /><br /> Pour SQL Server, utilisez l’expression régulière « \\ . ». Pour OracleClient, utilisez « \@&#124;\\ . ».<br /><br /> Pour ODBC, utilisez Catalog_name_seperator.<br /><br /> Pour OLE DB, utilisez DBLITERAL_CATALOG_SEPARATOR ou DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|string|Nom du produit auquel accède le fournisseur, tel que « Oracle » ou « SQLServer ».|  
|DataSourceProductVersion|string|Indique la version du produit auquel accède le fournisseur, dans le format natif des sources de données et non dans un format Microsoft.<br /><br /> Dans certains cas, DataSourceProductVersion et DataSourceProductVersionNormalized ont la même valeur. Dans le cas d'OLE DB et d'ODBC, ces valeurs sont toujours identiques étant donné qu'elles sont mappées sur le même appel de fonction dans l'API native sous-jacente.|  
|DataSourceProductVersionNormalized|string|Version normalisée pour la source de données, telle qu'elle peut être comparée à `String.Compare()`. Son format est identique pour toutes les versions du fournisseur afin d'empêcher la version 10 d'opérer un tri entre les versions 1 et 2.<br /><br /> Par exemple, le fournisseur Oracle utilise un format « nn. nn. nn. nn. NN » pour sa version normalisée, ce qui amène une source de données Oracle 8i à retourner « 08.01.07.04.01 ». SQL Server utilise le format « nn. nn. nnnn » standard de Microsoft.<br /><br /> Dans certains cas, DataSourceProductVersion et DataSourceProductVersionNormalized ont la même valeur. Dans le cas d'OLE DB et d'ODBC, ces valeurs sont toujours identiques étant donné qu'elles sont mappées sur le même appel de fonction dans l'API native sous-jacente.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Spécifie la relation entre les colonnes dans une clause GROUP BY et les colonnes non agrégées dans la liste de sélection.|  
|IdentifierPattern|string|Expression régulière qui correspond à un identificateur et dont la valeur de correspondance est l'identificateur. Par exemple, « [A-Za-z0-9_#$] ».|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indique si des identificateurs non entourés de guillemets sont traités ou non comme respectant la casse.|  
|OrderByColumnsInSelect|bool|Spécifie si les colonnes d'une clause ORDER BY doivent figurer dans la liste de sélection. Une valeur true indique qu'elles doivent obligatoirement figurer dans la liste de sélection ; une valeur false indique qu'elles ne doivent pas obligatoirement figurer dans la liste de sélection.|  
|ParameterMarkerFormat|string|Chaîne de format représentant la manière de formater un paramètre.<br /><br /> Si les paramètres nommés sont pris en charge par la source de données, le premier espace réservé dans cette chaîne doit être l'emplacement où le nom de paramètre doit être formaté.<br /><br /> Par exemple, si la source de données s’attend à ce que les paramètres soient nommés et précédés du préfixe «  : », il s’agit de «  : {0} ». En cas de formatage avec un nom de paramètre « p1 », la chaîne obtenue est « :p1 ».<br /><br /> Si la source de données s’attend à ce que les paramètres aient le préfixe « \@ », mais que les noms les incluent déjà, il s’agit {0} de « », et le résultat de la mise en forme d’un paramètre nommé « \@ P1 » est simplement « \@ P1 ».<br /><br /> Pour les sources de données qui n’attendent pas de paramètres nommés et qui attendent l’utilisation du caractère «  ? », la chaîne de format peut être spécifiée comme simplement «  ? », ce qui ignore le nom du paramètre. Pour OLE DB nous retournons «  ? ».|  
|ParameterMarkerPattern|string|Expression régulière représentant un marqueur de paramètre. Elle a pour valeur de correspondance éventuelle le nom de paramètre.<br /><br /> Par exemple, si les paramètres nommés sont pris en charge avec un caractère d’inversion « \@ » qui sera inclus dans le nom du paramètre, il s’agit de : « ( \@ [A-Za-z0-9_ $ #] *) ».<br /><br /> Toutefois, si les paramètres nommés sont pris en charge avec' : 'comme caractère de début et qu’il ne fait pas partie du nom de paramètre, il s’agit de : " :([A-Za-z0-9_ $ #] \* )".<br /><br /> Bien entendu, si la source de données ne prend pas en charge les paramètres nommés, il s’agit simplement de «  ? ».|  
|ParameterNameMaxLength|int|Longueur maximale d'un nom de paramètre en caractères. Si les noms de paramètres sont pris en charge, Visual Studio attend que la valeur minimale de longueur maximale soit de 30 caractères.<br /><br /> Si la source de données ne prend pas en charge les paramètres nommés, cette propriété retourne zéro.|  
|ParameterNamePattern|string|Expression régulière représentant les noms de paramètre valides. Les différentes sources de données ont des règles différentes concernant les caractères qui peuvent être utilisés pour les noms de paramètre.<br /><br /> Si les noms de paramètre sont pris en charge, Visual Studio attend que les caractères « \p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd} » correspondent à l'ensemble minimal pris en charge de caractères valides pour les noms de paramètre.|  
|QuotedIdentifierPattern|string|Expression régulière qui correspond à un identificateur entre guillemets et qui a pour valeur de correspondance l'identificateur proprement dit, sans les guillemets. Par exemple, si la source de données a utilisé des guillemets doubles pour identifier des identificateurs entre guillemets, il s’agit de : « (([^ \\ »] &#124;\\ « \\ ») *)».|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indique si des identificateurs entourés de guillemets sont traités ou non comme respectant la casse.|  
|StatementSeparatorPattern|string|Expression régulière représentant le séparateur d'instruction.|  
|StringLiteralPattern|string|Expression régulière qui correspond à un littéral de chaîne et dont la valeur de correspondance est le littéral proprement dit. Par exemple, si la source de données a utilisé des guillemets simples pour identifier des chaînes, il s’agit de : "(' ([^ '] &#124; ' ') * ')" '|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Spécifie les types d'instructions SQL jointes prises en charge par la source de données.|  
  
## <a name="datatypes"></a>DataTypes  

 Cette collection de schémas expose des informations sur les types de données pris en charge par la base de données à laquelle le fournisseur .NET Framework managé est actuellement connecté.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|TypeName|string|Nom du type de données spécifique au fournisseur.|  
|ProviderDbType|int|Valeur de type spécifique au fournisseur qui doit être utilisée lors de la spécification du type d’un paramètre. Par exemple, SqlDbType.Money ou OracleType.Blob.|  
|ColumnSize|long|La longueur d'une colonne ou d'un paramètre non numérique fait référence à la longueur maximale ou à la longueur définie pour ce type par le fournisseur.<br /><br /> Pour les données de type caractère, il s'agit de la longueur maximale ou de la longueur en unités définie par la source de données. Le concept d'Oracle consiste à spécifier une longueur, puis à spécifier la taille de stockage réelle de certains types de données caractère. Cela définit uniquement la longueur en unités pour Oracle.<br /><br /> Pour les données de type date-heure, il s'agit de la longueur de la représentation de chaîne (en supposant la précision maximale autorisée de la partie fractions de secondes).<br /><br /> Si les données sont de type numérique, il s'agit de la limite supérieure de la précision maximale du type de données.|  
|CreateFormat|string|Chaîne de format représentant la manière d'ajouter cette colonne à une instruction de définition de données, telle que CREATE TABLE. Chaque élément dans le tableau CreateParameter doit être représenté par un « marqueur de paramètre » dans la chaîne de format.<br /><br /> Par exemple, le type de données SQL DECIMAL nécessite une précision et une échelle. Dans ce cas, la chaîne de format serait « DECIMAL ( {0} , {1} ) ».|  
|CreateParameters|string|Paramètres de création à spécifier lors de la création d'une colonne de ce type de données. Les paramètres de création sont répertoriés dans la chaîne, avec des virgules de séparation, dans l'ordre dans lequel ils doivent être fournis.<br /><br /> Par exemple, le type de données SQL DECIMAL nécessite une précision et une échelle. Dans ce cas, les paramètres de création doivent contenir la chaîne « precision, scale ».<br /><br /> Dans une commande de texte pour créer une colonne DÉCIMALe avec une précision de 10 et une échelle de 2, la valeur de la colonne CreateFormat peut être DECIMAL ( {0} , {1} )» et la spécification de type complète serait Decimal (10, 2).|  
|DataType|string|Nom du type .NET Framework du type de données.|  
|IsAutoincrementable|bool|true — Les valeurs de ce type de données peuvent être auto-incrémentées.<br /><br /> false — Les valeurs de ce type de données ne peuvent pas être auto-incrémentées.<br /><br /> Notez que cela indique simplement si une colonne de ce type de données peut être auto-incrémentée, pas que toutes les colonnes de ce type le sont.|  
|IsBestMatch|bool|true — Le type de données est la meilleure correspondance entre tous les types de données du magasin de données et le type de données .NET Framework indiqué par la valeur de la colonne DataType.<br /><br /> false — Le type de données n'est pas la meilleure correspondance.<br /><br /> Pour chaque ensemble de lignes dans lequel la valeur de la colonne DataType est identique, la colonne IsBestMatch est définie comme true dans une seule ligne.|  
|IsCaseSensitive|bool|true — Le type de données est un type de caractère respectant la casse.<br /><br /> false — Le type de données n'est pas un type de caractère ou ne respecte pas la casse.|  
|IsFixedLength|bool|true — Les colonnes de ce type de données créées par la DDL sont de longueur fixe.<br /><br /> false — Les colonnes de ce type de données créées par la DDL sont de longueur variable.<br /><br /> DBNull.Value — Il est impossible de déterminer si le fournisseur mappera ce champ avec une colonne de longueur fixe ou variable.|  
|IsFixedPrecisionScale|bool|true — Le type de données a une précision et une échelle fixes.<br /><br /> false — Le type de données n'a pas de précision ni d'échelle fixes.|  
|IsLong|bool|true — Le type de données contient des données très longues ; la définition de données très longues est spécifique au fournisseur.<br /><br /> false — Le type de données ne contient pas de données très longues.|  
|IsNullable|bool|true — Le type de données est Nullable.<br /><br /> false — Le type de données n'est pas Nullable.<br /><br /> DBNull.Value — Il est impossible de déterminer si le type de données est Nullable.|  
|IsSearchable|bool|true — Le type de données peut être utilisé dans une clause WHERE avec tout opérateur, à l'exception du prédicat LIKE.<br /><br /> false — Le type de données ne peut pas être utilisé dans une clause WHERE avec un opérateur, à l’exception du prédicat LIKE.|  
|IsSearchableWithLike|bool|true — Le type de données peut être utilisé avec le prédicat LIKE.<br /><br /> false — Le type de données ne peut pas être utilisé avec le prédicat LIKE.|  
|IsUnsigned|bool|true — Le type de données n'est pas signé.<br /><br /> false — Le type de données est signé.<br /><br /> DBNull.Value — Non applicable au type de données.|  
|MaximumScale|short|Si l'indicateur de type est un type numérique, il correspond au nombre maximal de chiffres autorisés à droite de la virgule décimale. Sinon, c'est DBNull.Value.|  
|MinimumScale|short|Si l'indicateur de type est un type numérique, il correspond au nombre minimal de chiffres autorisés à droite de la virgule décimale. Sinon, c'est DBNull.Value.|  
|IsConcurrencyType|bool|true — Le type de données est mis à jour par la base de données à chaque modification de la ligne et la valeur de la colonne diffère de toutes les valeurs précédentes.<br /><br /> false — Le type de données n'est pas mis à jour par la base de données à chaque modification de la ligne.<br /><br /> DBNull.Value — La base de données ne prend pas en charge ce type de données.|  
|IsLiteralSupported|bool|true — Le type de données peut être exprimé comme littéral.<br /><br /> false — Le type de données ne peut pas être exprimé comme littéral.|  
|LiteralPrefix|string|Préfixe appliqué à un littéral donné.|  
|LiteralSuffix|string|Suffixe appliqué à un littéral donné.|  
|NativeDataType|String|NativeDataType est une colonne spécifique à OLE DB pour l'exposition du type OLE DB du type de données.|  
  
## <a name="restrictions"></a>Restrictions  

 Cette collection de schémas expose des informations sur les restrictions prises en charge par le fournisseur .NET Framework managé actuellement utilisé pour se connecter à la base de données.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|CollectionName|string|Nom de la collection à laquelle ces restrictions s'appliquent.|  
|RestrictionName|string|Nom de la restriction dans la collection.|  
|RestrictionDefault|string|Ignoré.|  
|RestrictionNumber|int|Emplacement réel des restrictions de collections dans lequel figure cette restriction particulière.|  
  
## <a name="reservedwords"></a>ReservedWords  

 Cette collection de schémas expose des informations sur les mots réservés par la base de données à laquelle le fournisseur .NET Framework managé est actuellement connecté.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|ReservedWord|string|Mot réservé spécifique au fournisseur.|  
  
## <a name="see-also"></a>Voir aussi

- [Extraction des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Collections GetSchema et Schema](getschema-and-schema-collections.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
