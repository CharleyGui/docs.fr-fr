---
title: Fonctions système
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 0d46429ac958e6f5db4d51947669784303af783b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156496"
---
# <a name="system-functions"></a>Fonctions système

Le fournisseur de données .NET Framework pour SQL Server (SqlClient) fournit les fonctions système suivantes :  
  
|Fonction|Description|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Retourne la valeur de somme de contrôle. `CHECKSUM` est destiné à être utilisé dans la création d'index de hachage.<br /><br /> **Arguments**<br /><br /> `value`:,,,,,, `Boolean` `Byte` ,,,, `Int16` `Int32` `Int64` `Single` `Decimal` `Double` `DateTime` `String` `Binary` , Ou `Guid` . Vous pouvez spécifier un, deux ou trois valeurs.<br /><br /> **Valeur renvoyée**<br /><br /> Valeur absolue de l'expression spécifiée.<br /><br /> **Exemple**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Produit la date et l'heure actuelles dans le format utilisé de manière interne par SQL Server pour les valeurs `DateTime` avec une précision de 7 dans SQL Server 2008 et une précision de 3 dans SQL Server 2005.<br /><br /> **Valeur renvoyée**<br /><br /> Date et heure système actuelles sous la forme d'une valeur `DateTime`.<br /><br /> **Exemple**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Retourne le nom de l'utilisateur actuel.<br /><br /> **Valeur renvoyée**<br /><br /> `String` ASCII.<br /><br /> **Exemple**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Retourne le nombre d'octets utilisés pour représenter une expression.<br /><br /> **Arguments**<br /><br /> `expression`:,,,,,, `Boolean` `Byte` `Int16` `Int32` `Int64` `Single` `Decimal` , `Double` , `DateTime` ,,,,, `Time` `DateTimeOffset` `String` `Binary` Ou `Guid` .<br /><br /> **Valeur renvoyée**<br /><br /> Taille des propriétés sous la forme d'une valeur `Int32`.<br /><br /> **Exemple**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Renvoie le nom de la station de travail.<br /><br /> **Valeur renvoyée**<br /><br /> `String` Unicode.<br /><br /> **Exemple**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Détermine si une expression d'entrée est une date valide.<br /><br /> **Arguments**<br /><br /> `expression`:,,,,,, `Boolean` `Byte` `Int16` `Int32` `Int64` `Single` `Decimal` , `Double` , `DateTime` ,,,,, `Time` `DateTimeOffset` `String` `Binary` Ou `Guid` .<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`. Un (1) si l'expression d'entrée est une date valide. Zéro (0) dans le cas contraire.<br /><br /> **Exemple**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Détermine si une expression est un type numérique valide.<br /><br /> **Arguments**<br /><br /> `expression`:,,,,,, `Boolean` `Byte` `Int16` `Int32` `Int64` `Single` `Decimal` , `Double` , `DateTime` ,,,,, `Time` `DateTimeOffset` `String` `Binary` Ou `Guid` .<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`. Un (1) si l'expression d'entrée est une date valide. Zéro (0) dans le cas contraire.<br /><br /> **Exemple**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Crée une valeur unique de type Guid.<br /><br /> **Valeur renvoyée**<br /><br /> `Guid`<br /><br /> **Exemple**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Renvoie le nom d'utilisateur de base de données à partir du numéro d'identification spécifié.<br /><br /> **Arguments**<br /><br /> `expression` : Numéro d'identification `Int32` associé à un utilisateur de base de données.<br /><br /> **Valeur renvoyée**<br /><br /> `String` Unicode.<br /><br /> **Exemple**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Pour plus d’informations sur les `String` fonctions prises en charge par SqlClient, consultez [fonctions de chaîne (Transact-SQL)](/sql/t-sql/functions/string-functions-transact-sql).
  
## <a name="see-also"></a>Voir aussi

- [Langage d'Entity SQL](./language-reference/entity-sql-language.md)
- [Fonctions SqlClient pour l'Entity Framework](sqlclient-for-ef-functions.md)
