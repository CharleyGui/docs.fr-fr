---
title: Fonctions de date et d'heure canoniques
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 9b7650990232face3a7c3673a6fb789912acf15c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148280"
---
# <a name="date-and-time-canonical-functions"></a>Fonctions de date et d'heure canoniques

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] comprend des fonctions canoniques de date et d'heure.  
  
## <a name="remarks"></a>Notes  

 Le tableau suivant présente les fonctions canoniques de date et d’heure [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . `datetime` est une <xref:System.DateTime> valeur.  
  
|Fonction|Description|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Ajoute le nombre `number` spécifié de nanosecondes à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime`, `DateTimeOffset` ou `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddMicroseconds(expression,number)`|Ajoute le nombre `number` spécifié de microsecondes à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime`, `DateTimeOffset` ou `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddMilliseconds(expression,number)`|Ajoute le nombre `number` spécifié de millisecondes à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime`, `DateTimeOffset` ou `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddSeconds(expression,number)`|Ajoute le nombre `number` spécifié de secondes à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime`, `DateTimeOffset` ou `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddMinutes(expression,number)`|Ajoute le nombre `number` spécifié de minutes à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime`, `DateTimeOffset` ou `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddHours(expression,number)`|Ajoute le nombre `number` spécifié d'heures à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime`, `DateTimeOffset` ou `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddDays(expression,number)`|Ajoute le nombre `number` spécifié de jours à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime` ou `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddMonths(expression,number)`|Ajoute le nombre `number` spécifié de mois à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime` ou `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`AddYears(expression,number)`|Ajoute le nombre `number` spécifié d'années à l'`expression`.<br /><br /> **Arguments**<br /><br /> `expression` : `DateTime` ou `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Retourne une nouvelle valeur `DateTime` correspondant aux date et heure actuelles du serveur dans le fuseau horaire du serveur.<br /><br /> **Arguments**<br /><br /> `year`, `month`, `day`, `hour`, `minute` : `Int16` et `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Valeur renvoyée**<br /><br /> `DateTime`|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|Retourne une nouvelle valeur `DateTimeOffset` correspondant aux date et heure actuelles du serveur par rapport au temps universel (UTC, Universal Time Coordinated).<br /><br /> **Arguments**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Valeur renvoyée**<br /><br /> `DateTimeOffset`|  
|`CreateTime(hour,minute,second)`|Retourne une nouvelle valeur `Time` correspondant à l'heure actuelle.<br /><br /> **Arguments**<br /><br /> `hour` et `minute` : `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Valeur renvoyée**<br /><br /> `Time`|  
|`CurrentDateTime()`|Retourne une valeur `DateTime` correspondant aux date et heure actuelles du serveur dans le fuseau horaire de ce dernier.<br /><br /> **Valeur renvoyée**<br /><br /> `DateTime`|  
|`CurrentDateTimeOffset()`|Retourne la date, l'heure et le décalage actuels sous forme de valeur `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> `DateTimeOffset`|  
|`CurrentUtcDateTime()`|Retourne une valeur <xref:System.DateTime> correspondant aux date et heure actuelles du serveur dans le fuseau horaire UTS.<br /><br /> **Valeur renvoyée**<br /><br /> `DateTime`|  
|`Day(expression)`|Retourne la composante jour d'`expression` sous forme d'une valeur `Int32` comprise entre 1 et 31.<br /><br /> **Arguments**<br /><br /> `DateTime` et `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|Retourne la composante jour d'`expression` sous la forme d'une valeur `Int32` comprise entre 1 et 366, où 366 correspond au dernier jour d'une année bissextile.<br /><br /> **Arguments**<br /><br /> `DateTime` ou `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffNanoseconds(startExpression,endExpression)`|Retourne la différence, en nanosecondes, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime`, `DateTimeOffset` ou `Time`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffMilliseconds(startExpression,endExpression)`|Retourne la différence, en millisecondes, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime`, `DateTimeOffset` ou `Time`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffMicroseconds(startExpression,endExpression)`|Retourne la différence, en microsecondes, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime`, `DateTimeOffset` ou `Time`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffSeconds(startExpression,endExpression)`|Retourne la différence, en secondes, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime`, `DateTimeOffset` ou `Time`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffMinutes(startExpression,endExpression)`|Retourne la différence, en minutes, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime`, `DateTimeOffset` ou `Time`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffHours(startExpression,endExpression)`|Retourne la différence, en heures, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime`, `DateTimeOffset` ou `Time`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffDays(startExpression,endExpression)`|Retourne la différence, en jours, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` ou `DateTimeOffset`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffMonths(startExpression,endExpression)`|Retourne la différence, en mois, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` ou `DateTimeOffset`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`DiffYears(startExpression,endExpression)`|Retourne la différence, en années, entre `startExpression` et `endExpression`.<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` ou `DateTimeOffset`. **Remarque :** `startExpression` et `endExpression` doivent être du même type.   <br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`GetTotalOffsetMinutes(datetimeoffset)`|Retourne le nombre de minutes correspondant au décalage de `datetimeoffset` par rapport à l'heure GMT. Cette valeur est généralement comprise entre +780 et -780 (+ ou - 13 heures). **Remarque :**  Cette fonction est prise en charge uniquement dans SQL Server 2008. <br /><br /> **Arguments**<br /><br /> `DateTimeOffset`<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`Hour(expression)`|Retourne la composante heure d'`expression` sous la forme d'une valeur `Int32` comprise entre 0 et 23.<br /><br /> **Arguments**<br /><br /> `DateTime, Time` et `DateTimeOffset`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|Retourne la composante millisecondes d'`expression` sous la forme d'une valeur `Int32` comprise entre 0 et 999.<br /><br /> **Arguments**<br /><br /> `DateTime, Time` et `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.|  
|`Minute(expression)`|Retourne la composante minutes d'`expression` sous la forme d'une valeur `Int32` comprise entre 0 et 59.<br /><br /> **Arguments**<br /><br /> `DateTime, Time` ou `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|Retourne la composante mois d'`expression` sous la forme d'une valeur `Int32` comprise entre 1 et 12.<br /><br /> **Arguments**<br /><br /> `DateTime` ou `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|Retourne la composante secondes d'`expression` sous forme de valeur `Int32` comprise entre 0 et 59.<br /><br /> **Arguments**<br /><br /> `DateTime, Time` et `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|Retourne l'`expression` avec les valeurs d'heure tronquées.<br /><br /> **Arguments**<br /><br /> `DateTime` ou `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Type d'élément `expression`.|  
|`Year(expression)`|Retourne la partie année de `expression` en tant que `Int32` `YYYY` .<br /><br /> **Arguments**<br /><br /> `DateTime` et `DateTimeOffset`.<br /><br /> **Valeur renvoyée**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Ces fonctions retournent `null` si une entrée de valeur `null` est fournie.  
  
 Des fonctionnalités équivalentes sont disponibles dans le fournisseur managé Client Microsoft SQL. Pour plus d’informations, consultez [SqlClient pour les fonctions de Entity Framework](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions canoniques](canonical-functions.md)
