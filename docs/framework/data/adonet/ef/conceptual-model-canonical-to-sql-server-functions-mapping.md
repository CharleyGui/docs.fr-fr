---
title: Mappage du modèle conceptuel canonique aux fonctions SQL Server
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: 495a662cbab84c2686e4c31945c30d6f82d117cb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153116"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>Mappage du modèle conceptuel canonique aux fonctions SQL Server

Cette rubrique décrit comment les fonctions canoniques de modèle conceptuel sont mappées aux fonctions SQL Server correspondantes.  
  
## <a name="date-and-time-functions"></a>Fonctions de date et heure  

 Le tableau suivant décrit le mappage des fonctions de date et d'heure :  
  
|Fonctions canoniques|Fonctions SQL Server|  
|-------------------------|--------------------------|  
|[AddDays(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime(year, month, day, hour, minute, second)](./language-reference/date-and-time-canonical-functions.md)|Pour SQL Server 2000 et SQL Server 2005, une valeur au format `datetime` est créée sur le serveur. Pour SQL Server 2008 et les versions ultérieures, une valeur `datetime2` est créée sur le serveur.|  
|[CreateDateTimeOffset(year, month, day, hour, minute, second, tzoffset)](./language-reference/date-and-time-canonical-functions.md)|Une valeur au format `datetimeoffset` est créée sur le serveur.<br /><br /> Fonction non prise en charge dans SQL Server 2000 et SQL Server 2005.|  
|[CreateTime(hour, minute, second)](./language-reference/date-and-time-canonical-functions.md)|Une valeur au format `time` est créée sur le serveur.<br /><br /> Fonction non prise en charge dans SQL Server 2000 et SQL Server 2005.|  
|[CurrentDateTime ()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTime()` dans SQL Server 2008.<br /><br /> `GetDate()` dans SQL Server 2000 et SQL Server 2005.|  
|[CurrentDateTimeOffset()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()` dans SQL Server 2008.<br /><br /> Fonction non prise en charge dans SQL Server 2000 et SQL Server 2005.|  
|[CurrentUtcDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()` dans SQL Server 2008. `GetUtcDate()` dans SQL Server 2000 et SQL Server 2005.|  
|[DayOfYear(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes(DateTimeOffset)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Millisecond(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minute(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate(expression)](./language-reference/date-and-time-canonical-functions.md)|Pour les SQL Server 2000 et SQL Server 2005, une `datetime` valeur mise en forme tronquée est créée sur le serveur. Pour SQL Server 2008 et versions ultérieures, une `datetime2` valeur ou tronquée `datetimeoffset` est créée sur le serveur.|  
|[Year(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>Fonctions d’agrégation  

 Le tableau suivant décrit le mappage des fonctions d'agrégation :  
  
|Fonctions canoniques|Fonctions SQL Server|  
|-------------------------|--------------------------|  
|[Avg(expression)](./language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](./language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count (expression)](./language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min (expression)](./language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max (expression)](./language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev(expression)](./language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP(expression)](./language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum (expression)](./language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var(expression)](./language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP(expression)](./language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>Fonctions mathématiques  

 Le tableau suivant décrit le mappage des fonctions mathématiques :  
  
|Fonctions canoniques|Fonctions SQL Server|  
|-------------------------|--------------------------|  
|[Abs(valeur)](./language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Ceiling(valeur)](./language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor(valeur)](./language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power(valeur)](./language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round(valeur)](./language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[Tronquer](./language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>Fonctions de chaîne  

 Le tableau suivant décrit le mappage des fonctions de chaîne :  
  
|Fonctions canoniques|Fonctions SQL Server|  
|-------------------------|--------------------------|  
|[Contains(string, target)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat(string1, string2)](./language-reference/string-canonical-functions.md)|string1 + string2|  
|[EndsWith(string, target)](./language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **Remarque** La `CHARINDEX` fonction retourne `false` si le `string` est stocké dans une colonne de chaîne de longueur fixe et `target` est une constante. Dans ce cas, la chaîne entière est recherchée, y compris les éventuels espaces de remplissage de fin. Une solution de contournement possible consiste à découper les données dans la chaîne de longueur fixe avant de passer la chaîne à la fonction `EndsWith`, comme dans l'exemple suivant : `EndsWith(TRIM(string), target)`|  
|[IndexOf(target, string2)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Left (string1, length)](./language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Length (string)](./language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right (string1, length)](./language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Replace (string1, string2, string3)](./language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Inverse (chaîne)](./language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](./language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith(string, target)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring(string, start, length)](./language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower(string)](./language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper(string)](./language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>Fonctions de bits  

 Le tableau suivant décrit le mappage des fonctions de bits :  
  
|Fonctions canoniques|Fonctions SQL Server|  
|-------------------------|--------------------------|  
|[BitWiseAnd (value1, value2)](./language-reference/bitwise-canonical-functions.md)|valeur1 & value2|  
|[BitWiseNot (value)](./language-reference/bitwise-canonical-functions.md)|~value|  
|[BitWiseOr (value1, value2)](./language-reference/bitwise-canonical-functions.md)|valeur1 &#124; value2|  
|[BitWiseXor (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 ^ value2|
