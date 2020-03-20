---
title: Fonctions d'agrégation (SqlClient pour Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150647"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Fonctions d'agrégation (SqlClient pour Entity Framework)
Le fournisseur de données .NET Framework pour SQL Server (SqlClient) fournit des fonctions d'agrégation. Les fonctions d'agrégation effectuent des calculs sur un ensemble de valeurs d'entrée et retournent une valeur. Ces fonctions se trouvent dans l'espace de noms SqlServer, lequel est disponible lorsque vous utilisez SqlClient. La propriété d’espace de noms d’un fournisseur permet à Entity Framework de découvrir le préfixe attribué par ce fournisseur à des constructions spécifiques, telles que des types et des fonctions.  
  
 Voici les fonctions d’agrégats SqlClient.  

## <a name="avgexpression"></a>AVG (expression)

Retourne la moyenne des valeurs d'une collection. Les valeurs NULL sont ignorées.

**Arguments**

Un `Int32` `Int64`, `Double`, `Decimal`, et .

**Valeur de rendement**

Type d'élément `expression`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG (collection)

 Retourne la somme de contrôle des valeurs d’une collection. Les valeurs NULL sont ignorées.

 **Arguments**

 Une collection`Int32`( ).

 **Valeur de rendement**

 `Int32`.

 **Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a>COUNT (expression)

Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `Int32`.

**Arguments**

Une\<collection T>, où T est l’un des types suivants:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(non retourné dans SQL Server 2000)|

**Valeur de rendement**

`Int32`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a>COUNT_BIG(expression)

Retourne le nombre d’éléments d’une collection sous la forme d’une valeur `bigint`.

 **Arguments**

 Une collection (T), où T est l’un des types suivants :

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(non retourné dans SQL Server 2000)|

**Valeur de rendement**

`Int64`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX(expression)

Retourne la valeur maximale contenue dans la collection.

**Arguments**

Une collection (T), où T est l’un des types suivants :

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Valeur de rendement**

Type d'élément `expression`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN (expression)

Retourne la valeur minimale contenue dans une collection.

**Arguments**

Une collection (T), où T est l’un des types suivants :

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Valeur de rendement**

Type d'élément `expression`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV(expression)

Renvoie l'écart type statistique de toutes les valeurs dans l'expression spécifiée.

**Arguments**

Une collection`Double`( ).

**Valeur de rendement**

`Double`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP (expression)

Renvoie l'écart type de remplissage pour toutes les valeurs de l'expression spécifiée.

**Arguments**

Une collection`Double`( ).

**Valeur de rendement**

`Double`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM(expression)

Retourne la somme de toutes les valeurs de la collection.

**Arguments**

Une collection (T) où T est `Int32` `Int64`l’un des types suivants: , , `Double`, `Decimal`.

**Valeur de rendement**

Type d'élément `expression`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR (expression)

Renvoie la variance statistique de toutes les valeurs de l'expression spécifiée.

**Arguments**

Une collection`Double`( ).

**Valeur de rendement**

`Double`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP (expression)

Renvoie la variance statistique de remplissage pour toutes les valeurs de l'expression spécifiée.

**Arguments**

Une collection`Double`( ).

**Valeur de rendement**

`Double`.

**Exemple**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d'agrégation (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Langage d'Entity SQL](./language-reference/entity-sql-language.md)
- [Fonctions d'agrégation canoniques](./language-reference/aggregate-canonical-functions.md)
