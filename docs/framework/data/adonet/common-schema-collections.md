---
title: Collections de schémas courantes
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: b6c2c89101f3304a0cab014de2def22195541471
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249472"
---
# <a name="common-schema-collections"></a>Collections de schémas courantes
Les collections de schémas communes sont les collections de schémas implémentées par chacun des fournisseurs .NET Framework managés. Vous pouvez interroger un fournisseur géré par .NET Framework pour déterminer la liste des collections de schémas pris en charge en appelant la méthode **GetSchema** sans arguments, ou avec le nom de collection de schémas "MetaDataCollections". Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu’elles prennent en charge et le nombre d’éléments d’identification qu’elles utilisent. Ces collections décrivent toutes les colonnes requises. Les fournisseurs sont libres d'ajouter des colonnes s'ils le souhaitent. Par exemple, `SqlClient` et `OracleClient` ajoutent ParameterName à la collection de restrictions.  
  
 Si un fournisseur est incapable de déterminer la valeur d'une colonne obligatoire, il retourne la valeur null.  
  
 Pour plus d’informations sur l’utilisation des méthodes **GetSchema,** voir [GetSchema et Schema Collections](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Cette collection de schémas expose des informations sur toutes les collections de schémas prises en charge par le fournisseur .NET Framework managé actuellement utilisé pour se connecter à la base de données.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|CollectionName|string|Le nom de la collection à transmettre à la méthode **GetSchema** pour retourner la collection.|  
|NumberOfRestrictions|int|Nombre de restrictions qui peuvent être spécifiées pour la collection.|  
|NumberOfIdentifierParts|int|Nombre de parties dans le nom d'objet identificateur/base de données composite. Par exemple, dans SQL Server, ce serait 3 pour les tables et 4 pour les colonnes. Dans Oracle, ce serait 2 pour les tables et 3 pour les colonnes.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Cette collection de schémas expose des informations sur la source de données à laquelle le fournisseur .NET Framework managé est actuellement connecté.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|string|Expression régulière pour mettre en correspondance les séparateurs composites dans un identificateur composite. Par exemple, «\\.» (pour SQL Server)\@ ou " \\&#124;". (pour Oracle).<br /><br /> Un identificateur composite est généralement ce qui est utilisé pour un nom\@d’objet de base de données, par exemple: pubs.dbo.authors ou pubs dbo.authors.<br /><br /> Pour SQL Server, utilisez\\l’expression régulière " . Pour OracleClient,\@ utilisez « \\&#124;».<br /><br /> Pour ODBC, utilisez Catalog_name_seperator.<br /><br /> Pour OLE DB, utilisez DBLITERAL_CATALOG_SEPARATOR ou DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|string|Nom du produit auquel accède le fournisseur, tel que « Oracle » ou « SQLServer ».|  
|DataSourceProductVersion|string|Indique la version du produit auquel accède le fournisseur, dans le format natif des sources de données et non dans un format Microsoft.<br /><br /> Dans certains cas, DataSourceProductVersion et DataSourceProductVersionNormalized ont la même valeur. Dans le cas d'OLE DB et d'ODBC, ces valeurs sont toujours identiques étant donné qu'elles sont mappées sur le même appel de fonction dans l'API native sous-jacente.|  
|DataSourceProductVersionNormalized|string|Version normalisée pour la source de données, telle qu'elle peut être comparée à `String.Compare()`. Son format est identique pour toutes les versions du fournisseur afin d'empêcher la version 10 d'opérer un tri entre les versions 1 et 2.<br /><br /> Par exemple, le fournisseur Oracle utilise un format de "nn.nn.nn.nn.nn.nn.nn" pour sa version normalisée, ce qui provoque un retour d’une source de données Oracle 8i "08.01.07.04.01". SQL Server utilise le format typique de Microsoft "nn.nn.nnnn".<br /><br /> Dans certains cas, DataSourceProductVersion et DataSourceProductVersionNormalized ont la même valeur. Dans le cas d'OLE DB et d'ODBC, ces valeurs sont toujours identiques étant donné qu'elles sont mappées sur le même appel de fonction dans l'API native sous-jacente.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Spécifie la relation entre les colonnes dans une clause GROUP BY et les colonnes non agrégées dans la liste de sélection.|  
|IdentifierPattern|string|Expression régulière qui correspond à un identificateur et dont la valeur de correspondance est l'identificateur. Par exemple, « [A-Za-z0-9_#$] ».|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indique si des identificateurs non entourés de guillemets sont traités ou non comme respectant la casse.|  
|OrderByColumnsInSelect|bool|Spécifie si les colonnes d'une clause ORDER BY doivent figurer dans la liste de sélection. Une valeur true indique qu'elles doivent obligatoirement figurer dans la liste de sélection ; une valeur false indique qu'elles ne doivent pas obligatoirement figurer dans la liste de sélection.|  
|ParameterMarkerFormat|string|Chaîne de format représentant la manière de formater un paramètre.<br /><br /> Si les paramètres nommés sont pris en charge par la source de données, le premier espace réservé dans cette chaîne doit être l'emplacement où le nom de paramètre doit être formaté.<br /><br /> Par exemple, si la source de données s’attend à ce que les{0}paramètres soient nommés et préfixés avec un «:« ce serait «: «. En cas de formatage avec un nom de paramètre « p1 », la chaîne obtenue est « :p1 ».<br /><br /> Si la source de données s’attend à\@ce que les paramètres soient préfixés avec le ', mais les noms les incluent déjà, ce serait ',{0}et le résultat de la mise en forme d’un paramètre nommé "\@p1' serait simplement "\@p1 ".<br /><br /> Pour les sources de données qui ne s’attendent pas à des paramètres nommés et s’attendent à l’utilisation du caractère «?», la chaîne de format peut être spécifiée comme simplement «?», qui ignorerait le nom du paramètre. Pour OLE DB nous revenons '?'.|  
|ParameterMarkerPattern|string|Expression régulière représentant un marqueur de paramètre. Elle a pour valeur de correspondance éventuelle le nom de paramètre.<br /><br /> Par exemple, si les paramètres nommés sont pris en charge par un «\@personnage principal\@qui sera inclus dans le nom du paramètre, ce serait : » ([A-Za-z0-9 $]MD]MD.<br /><br /> Cependant, si les paramètres nommés sont pris en charge par un «:» comme le personnage principal et il ne fait pas partie du nom\*du paramètre, ce serait: ":([A-Za-z0-9 $$] )".<br /><br /> Bien sûr, si la source de données ne prend pas en charge les paramètres nommés, ce serait tout simplement "?".|  
|ParameterNameMaxLength|int|Longueur maximale d'un nom de paramètre en caractères. Si les noms de paramètres sont pris en charge, Visual Studio attend que la valeur minimale de longueur maximale soit de 30 caractères.<br /><br /> Si la source de données ne prend pas en charge les paramètres nommés, cette propriété retourne zéro.|  
|ParameterNamePattern|string|Expression régulière représentant les noms de paramètre valides. Les différentes sources de données ont des règles différentes concernant les caractères qui peuvent être utilisés pour les noms de paramètre.<br /><br /> Si les noms de paramètre sont pris en charge, Visual Studio attend que les caractères « \p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd} » correspondent à l'ensemble minimal pris en charge de caractères valides pour les noms de paramètre.|  
|QuotedIdentifierPattern|string|Expression régulière qui correspond à un identificateur entre guillemets et qui a pour valeur de correspondance l'identificateur proprement dit, sans les guillemets. Par exemple, si la source de données utilisait des doubles citations pour identifier\\les identifiants \\cités, ce serait : « ([) &#124;«\\) ».|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indique si des identificateurs entourés de guillemets sont traités ou non comme respectant la casse.|  
|StatementSeparatorPattern|string|Expression régulière représentant le séparateur d'instruction.|  
|StringLiteralPattern|string|Expression régulière qui correspond à un littéral de chaîne et dont la valeur de correspondance est le littéral proprement dit. Par exemple, si la source de données utilisait des citations uniques pour identifier les chaînes, ce serait : « ([]&#124;')»)»)|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Spécifie les types d'instructions SQL jointes prises en charge par la source de données.|  
  
## <a name="datatypes"></a>DataTypes  
 Cette collection de schémas expose des informations sur les types de données pris en charge par la base de données à laquelle le fournisseur .NET Framework managé est actuellement connecté.  
  
|ColumnName|DataType|Description|  
|----------------|--------------|-----------------|  
|TypeName|string|Nom du type de données spécifique au fournisseur.|  
|ProviderDbType|int|La valeur de type spécifique au fournisseur qui doit être utilisée lors de la spécifier le type d’un paramètre. Par exemple, SqlDbType.Money ou OracleType.Blob.|  
|ColumnSize|long|La longueur d'une colonne ou d'un paramètre non numérique fait référence à la longueur maximale ou à la longueur définie pour ce type par le fournisseur.<br /><br /> Pour les données de type caractère, il s'agit de la longueur maximale ou de la longueur en unités définie par la source de données. Le concept d'Oracle consiste à spécifier une longueur, puis à spécifier la taille de stockage réelle de certains types de données caractère. Cela définit uniquement la longueur en unités pour Oracle.<br /><br /> Pour les données de type date-heure, il s'agit de la longueur de la représentation de chaîne (en supposant la précision maximale autorisée de la partie fractions de secondes).<br /><br /> Si les données sont de type numérique, il s'agit de la limite supérieure de la précision maximale du type de données.|  
|CreateFormat|string|Chaîne de format représentant la manière d'ajouter cette colonne à une instruction de définition de données, telle que CREATE TABLE. Chaque élément dans le tableau CreateParameter doit être représenté par un « marqueur de paramètre » dans la chaîne de format.<br /><br /> Par exemple, le type de données SQL DECIMAL nécessite une précision et une échelle. Dans ce cas, la chaîne de format{0}{1}serait "DECIMAL( , )".|  
|CreateParameters|string|Paramètres de création à spécifier lors de la création d'une colonne de ce type de données. Les paramètres de création sont répertoriés dans la chaîne, avec des virgules de séparation, dans l'ordre dans lequel ils doivent être fournis.<br /><br /> Par exemple, le type de données SQL DECIMAL nécessite une précision et une échelle. Dans ce cas, les paramètres de création doivent contenir la chaîne « precision, scale ».<br /><br /> Dans une commande de texte pour créer une colonne DECIMAL avec une précision de 10 et une échelle{0}{1}de 2, la valeur de la colonne CreateFormat pourrait être DECIMAL(, ) et la spécification de type complet serait DECIMAL(10,2).|  
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
|LittéraleSuffix|string|Suffixe appliqué à un littéral donné.|  
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
|ReservedWord (en)|string|Mot réservé spécifique au fournisseur.|  
  
## <a name="see-also"></a>Voir aussi

- [Récupération des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Collections GetSchema et Schema](getschema-and-schema-collections.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
