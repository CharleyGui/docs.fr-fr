---
title: Mappage de la méthode CLR aux fonctions de chaînes canoniques
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 6f14ad8d9e8f919fe820447cc991b102319b38d5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251226"
---
# <a name="clr-method-to-canonical-function-mapping"></a>Mappage de la méthode CLR aux fonctions de chaînes canoniques

Entity Framework fournit un ensemble de fonctions canoniques chargées d'implémenter des fonctionnalités communes à de nombreux systèmes de base de données, notamment la manipulation de chaînes et les fonctions mathématiques. Cela permet aux développeurs de cibler un large éventail de systèmes de base de données. Lorsqu'elles sont appelées via une technologie de requête comme LINQ to Entities, ces fonctions canoniques sont traduites dans la fonction de magasin correspondante du fournisseur utilisé. Les appels de fonction peuvent ainsi être exprimés sous une forme commune dans toutes les sources de données, ce qui procure une expérience de requête cohérente. Les opérateurs au niveau du bit AND, OR, NOT et XOR sont également mappés à des fonctions canoniques lorsque l'opérande est de type numérique. Dans le cas des opérandes booléens, les opérateurs au niveau du bit AND, OR, NOT et XOR calculent les opérations logiques AND, OR, NOT et XOR de leurs opérandes. Pour plus d’informations, consultez [fonctions canoniques](canonical-functions.md).

Pour les scénarios LINQ, les requêtes exécutées sur Entity Framework impliquent le mappage de certaines méthodes CLR aux méthodes au niveau de la source de données sous-jacente au moyen de fonctions canoniques. Les appels de méthode d'une requête LINQ to Entities qui ne sont pas explicitement mappés à une fonction canonique entraîneront la levée d'une exception d'exécution <xref:System.NotSupportedException>.

## <a name="systemstring-method-static-mapping"></a>Mappage de la méthode System.String (statique)

|Méthode System.String (statique)|Fonction canonique|
|-------------------------------------|------------------------|
|System.String Concat(String `str0`, String `str1`)|Concat(`str0`, `str1`)|
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat(Concat(`str0`, `str1`), `str2`)|
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat(Concat(Concat(`str0`, `str1`), `str2`), `str3`)|
|Boolean Equals(String `a`, String `b`)|= (opérateur)|
|Boolean IsNullOrEmpty(String `value`)|(IsNull(`value`)) OR Length(`value`) = 0|
|Boolean op_Equality(String `a`, String `b`)|= (opérateur)|
|Boolean op_Inequality(String `a` , String `b`)|!= (opérateur)|
|Microsoft.VisualBasic.Strings.Trim(String `str`)|Trim(`str`)|
|Microsoft.VisualBasic.Strings.LTrim(String `str`)|Ltrim(`str`)|
|Microsoft.VisualBasic.Strings.RTrim(String `str`)|Rtrim(`str`)|
|Microsoft.VisualBasic.Strings.Len(String `expression`)|Length(`expression`)|
|Microsoft.VisualBasic.Strings.Left(String `str`, Int32 `Length`)|Left(`str`, `Length`)|
|Microsoft.VisualBasic.Strings.Mid(String `str`, Int32 `Start`, Int32 `Length`)|Substring(`str`, `Start`, `Length`)|
|Microsoft.VisualBasic.Strings.Right(String `str`, Int32 `Length`)|Right(`str`, `Length`)|
|Microsoft.VisualBasic.Strings.UCase(String `Value`)|ToUpper(`Value`)|
|Microsoft.VisualBasic.Strings.LCase(String Value)|ToLower(`Value`)|

## <a name="systemstring-method-instance-mapping"></a>Mappage de la méthode System.String (d'instance)

|Méthode System.String (d'instance)|Fonction canonique|Notes|
|---------------------------------------|------------------------|-----------|
|Boolean Contains(String `value`)|`this` LIKE '%`value`%'|Si `value` n’est pas une constante, cela mappe à IndexOf (`this`, `value`) > 0|
|Boolean EndsWith(String `value`)|`this`LIKE `'` '% `value`|Si `value` n'est pas une constante, cela mappe à Right (`this`, length(`value`)) = `value`.|
|Boolean StartsWith(String `value`)|`this` LIKE '`value`%'|Si `value` n'est pas une constante, cela mappe à IndexOf (`this`, `value`) = 1.|
|Longueur|Length(`this`)||
|Int32 IndexOf(String `value`)|IndexOf(`this`, `value`) - 1||
|System.String Insert(Int32 `startIndex`, String `value`)|Concat(Concat(Substring(`this`, 1, `startIndex`), `value`), Substring(`this`, `startIndex`+1, Length(`this`) - `startIndex`))||
|System.String Remove(Int32 `startIndex`)|Substring(`this`, 1, `startIndex`)||
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (sous-chaîne`this`(, 1 `startIndex`,), sous-`this`chaîne `startIndex` (, +   +  `count` + 1,`this`longueur ()`startIndex`-(`count`)))|La méthode Remove(`startIndex`, `count`) n'est prise en charge que si `count` est un entier supérieur ou égal à 0.|
|System.String Replace(String `oldValue`, String `newValue`)|Replace(`this`, `oldValue`, `newValue`)||
|System.String Substring(Int32 `startIndex`)|Substring(`this`, `startIndex` +1, Length(`this`) - `startIndex`)||
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Substring (`this`, `startIndex` + 1, `length`)||
|System.String ToLower()|ToLower(`this`)||
|System.String ToUpper()|ToUpper(`this`)||
|System.String Trim()|Trim(`this`)||
|System.String TrimEnd(Char[] `trimChars`)|RTrim(`this`)||
|System.String TrimStart(Char[]`trimChars`)|LTrim(`this`)||
|Boolean Equals(String `value`)|= (opérateur)||

## <a name="systemdatetime-method-static-mapping"></a>Mappage de la méthode System.DateTime (statique)

|Méthode System.DateTime (statique)|Fonction canonique|Notes|
|---------------------------------------|------------------------|-----------|
|Boolean Equals(DateTime `t1`, DateTime `t2`)|= (opérateur)||
|System.DateTime.Now|CurrentDateTime()||
|System.DateTime.UtcNow|CurrentUtcDateTime()||
|Boolean op_Equality(DateTime `d1`, DateTime `d2`)|= (opérateur)||
|Boolean op_GreaterThan(DateTime `t1`, DateTime `t2`)|opérateur >||
|Boolean op_GreaterThanOrEqual(DateTime `t1`, DateTime `t2`)|> =, opérateur||
|Boolean op_Inequality(DateTime `t1`, DateTime `t2`)|!= (opérateur)||
|Op_LessThan booléen (DateTime `t1`, DateTime `t2`)|opérateur <||
|Boolean op_LessThanOrEqual(DateTime `t1`, DateTime `t2`)|< =, opérateur||
|Microsoft.VisualBasic.DateAndTime.DatePart( _<br /><br /> ByVal `Interval` comme DateInterval,\_<br /><br /> ByVal `DateValue` comme DateTime,\_<br /><br /> ByVal `FirstDayOfWeekValue` facultatif comme FirstDayOfWeek = vbSunday,\_<br /><br /> ByVal `FirstWeekOfYearValue` facultatif comme FirstWeekOfYear = vbFirstJan1\_<br /><br /> ) As Integer||Consultez la section concernant la fonction DatePart pour plus d'informations.|
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||
|Microsoft.VisualBasic.DateAndTime.Year(DateTime `TimeValue`)|Year()||
|Microsoft.VisualBasic.DateAndTime.Month(DateTime `TimeValue`)|Month()||
|Microsoft.VisualBasic.DateAndTime.Day(DateTime `TimeValue`)|Day()||
|Microsoft.VisualBasic.DateAndTime.Hour(DateTime `TimeValue`)|Hour()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minute()||
|Microsoft.VisualBasic.DateAndTime.Second(DateTime `TimeValue`)|Second()||

## <a name="systemdatetime-method-instance-mapping"></a>Mappage de la méthode System.DateTime (d'instance)

|Méthode System.DateTime (instance)|Fonction canonique|
|-----------------------------------------|------------------------|
|Boolean Equals(DateTime `value`)|= (opérateur)|
|jour|Day(`this`)|
|Heure|Hour(`this`)|
|Milliseconde|Millisecond(`this`)|
|Minute|Minute(`this`)|
|Mois|Month(`this`)|
|Seconde|Second(`this`)|
|Year|Year(`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>Mappage de la méthode System.DateTimeOffset (d'instance)

Mappage indiqué pour les méthodes `get` sur les propriétés répertoriées.

|Mappage de la méthode System.DateTimeOffset (d'instance)|Fonction canonique|Notes|
|-----------------------------------------------|------------------------|-----------|
|jour|Day(`this`)|Non pris en charge dans SQL Server 2005.|
|Heure|Hour(`this`)|Non pris en charge dans SQL Server 2005.|
|Milliseconde|Millisecond(`this`)|Non pris en charge dans SQL Server 2005.|
|Minute|Minute(`this`)|Non pris en charge dans SQL Server 2005.|
|Mois|Month(`this`)|Non pris en charge dans SQL Server 2005.|
|Seconde|Second(`this`)|Non pris en charge dans SQL Server 2005.|
|Year|Year(`this`)|Non pris en charge dans SQL Server 2005.|

> [!NOTE]
> La méthode <xref:System.DateTimeOffset.Equals%2A> retourne `true` si les objets <xref:System.DateTimeOffset> comparés sont égaux ; sinon `false`. La méthode <xref:System.DateTimeOffset.CompareTo%2A> retourne 0, 1 ou -1 selon que l'objet <xref:System.DateTimeOffset> comparé est égal, supérieur ou inférieur, respectivement.

## <a name="systemdatetimeoffset-method-static-mapping"></a>Mappage de la méthode System.DateTimeOffset (statique)

Mappage indiqué pour les méthodes `get` sur les propriétés répertoriées.

|Mappage de la méthode System.DateTimeOffset (statique)|Fonction canonique|Notes|
|---------------------------------------------|------------------------|-----------|
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Non pris en charge dans SQL Server 2005.|

## <a name="systemtimespan-method-instance-mapping"></a>Mappage de la méthode System.TimeSpan (d'instance)

Mappage indiqué pour les méthodes `get` sur les propriétés répertoriées.

|Mappage de la méthode System.TimeSpan (d'instance)|Fonction canonique|Notes|
|-----------------------------------------|------------------------|-----------|
|Heures|Hour(`this`)|Non pris en charge dans SQL Server 2005.|
|Millisecondes|Millisecond(`this`)|Non pris en charge dans SQL Server 2005.|
|Minutes|Minute(`this`)|Non pris en charge dans SQL Server 2005.|
|Secondes|Second(`this`)|Non pris en charge dans SQL Server 2005.|

> [!NOTE]
> La méthode <xref:System.TimeSpan.Equals%2A> retourne `true` si les objets <xref:System.TimeSpan> comparés sont égaux ; sinon `false`. La méthode <xref:System.TimeSpan.CompareTo%2A> retourne 0, 1 ou -1 selon que l'objet <xref:System.TimeSpan> comparé est égal, supérieur ou inférieur, respectivement.

### <a name="datepart-function"></a>Fonction DatePart

La fonction `DatePart` est mappée à l'une des diverses fonctions canoniques, en fonction de la valeur de `Interval`. Le tableau suivant présente le mappage de la fonction canonique pour les valeurs de `Interval` prises en charge :

|Valeur d'intervalle|Fonction canonique|
|--------------------|------------------------|
|DateInterval.Year|Year()|
|DateInterval.Month|Month()|
|DateInterval.Day|Day()|
|DateInterval.Hour|Hour()|
|DateInterval.Minute|Minute()|
|DateInterval.Second|Second()|

## <a name="mathematical-function-mapping"></a>Mappage de fonctions mathématiques

|Méthode CLR|Fonction canonique|
|----------------|------------------------|
|System.Decimal.Ceiling(Decimal `d`)|Ceiling(`d`)|
|System.Decimal.Floor(Decimal `d`)|Floor(`d`)|
|System.Decimal.Round(Decimal `d`)|Round(`d`)|
|System.Math.Ceiling(Decimal `d`)|Ceiling(`d`)|
|System.Math.Floor(Decimal `d`)|Floor(`d`)|
|System.Math.Round(Decimal `d`)|Round(`d`)|
|System.Math.Ceiling(Double `a`)|Ceiling(`a`)|
|System.Math.Floor(Double `a`)|Floor(`a`)|
|System.Math.Round(Double `a`)|Round(`a`)|
|System.Math.Round(valeur Double, chiffres Int16)|Round(valeur, chiffres)|
|System.Math.Round(valeur Double, chiffres Int32)|Round(valeur, chiffres)|
|System.Math.Round(valeur Decimal, chiffres Int16)|Round(valeur, chiffres)|
|System.Math.Round(valeur Decimal, chiffres Int32)|Round(valeur, chiffres)|
|System.Math.Abs(valeur Int16)|Abs(valeur)|
|System.Math.Abs(valeur Int32)|Abs(valeur)|
|System.Math.Abs(valeur Int64)|Abs(valeur)|
|System.Math.Abs(valeur Byte)|Abs(valeur)|
|System.Math.Abs(valeur Single)|Abs(valeur)|
|System.Math.Abs(valeur Double)|Abs(valeur)|
|System.Math.Abs(valeur Decimal)|Abs(valeur)|
|System.Math.Truncate(valeur Double, chiffres Int16)|Truncate(valeur, chiffres)|
|System.Math.Truncate(valeur Double, chiffres Int32)|Truncate(valeur, chiffres)|
|System.Math.Truncate(valeur Decimal, chiffres Int16)|Truncate(valeur, chiffres)|
|System.Math.Truncate(valeur Decimal, chiffres Int32)|Truncate(valeur, chiffres)|
|System.Math.Power(valeur Int32, exposant Int64)|Power(valeur, exposant)|
|System.Math.Power(valeur Int32, exposant Double)|Power(valeur, exposant)|
|System.Math.Power(valeur Int32, exposant Decimal)|Power(valeur, exposant)|
|System.Math.Power(valeur Int64, exposant Int64)|Power(valeur, exposant)|
|System.Math.Power(valeur Int64, exposant Double)|Power(valeur, exposant)|
|System.Math.Power(valeur Int64, exposant Decimal)|Power(valeur, exposant)|
|System.Math.Power(valeur Double, exposant Int64)|Power(valeur, exposant)|
|System.Math.Power(valeur Double, exposant Double)|Power(valeur, exposant)|
|System.Math.Power(valeur Double, exposant Decimal)|Power(valeur, exposant)|
|System.Math.Power(valeur Decimal, exposant Int64)|Power(valeur, exposant)|
|System.Math.Power(valeur Decimal, exposant Double)|Power(valeur, exposant)|
|System.Math.Power(valeur Decimal, exposant Decimal)|Power(valeur, exposant)|

## <a name="bitwise-operator-mapping"></a>Mappage d'opérateurs de bits

|Opérateur de bits|Fonction canonique pour les opérandes non booléens|Fonction canonique pour les opérandes booléens|
|----------------------|--------------------------------------------------|---------------------------------------------|
|Opérateur de bits AND|BitWiseAnd|op1 AND op2|
|Opérateur de bits OR|BitWiseOr|op1 OR op2|
|Opérateur de bits NOT|BitWiseNot|NOT(op)|
|Opérateur de bits XOR|BitWiseXor|((op1 AND NOT(op2)) OR (NOT(op1) AND op2))|

## <a name="other-mapping"></a>Autre mappage

|Méthode|Fonction canonique|
|------------|------------------------|
|Guid.NewGuid()|NewGuid()|

## <a name="see-also"></a>Voir aussi

- [LINQ to Entities](linq-to-entities.md)
