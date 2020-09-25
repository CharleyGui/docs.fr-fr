---
title: System.DateTime, méthodes
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: e3bffb1f47c19ccf7ea59151cd3545a15d59f1f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203486"
---
# <a name="systemdatetime-methods"></a>System.DateTime, méthodes

Les méthodes, propriétés et opérateurs pris en charge par LINQ to SQL suivants peuvent être utilisés dans les requêtes LINQ to SQL. Lorsqu'une méthode, une propriété ou un opérateur n'est pas pris en charge, LINQ to SQL ne peut pas traduire le membre à des fins d'exécution sur SQL Server. Vous pouvez utiliser ces membres dans votre code, ceux-ci devant toutefois être évalués avant la traduction de la requête en données Transact-SQL ou après l'extraction des résultats de la base de données.  
  
## <a name="supported-systemdatetime-members"></a>Membres System.DateTime pris en charge  

 Une fois mappés dans le modèle objet ou le fichier de mappage externe, LINQ to SQL vous permet d'appeler les membres <xref:System.DateTime?displayProperty=nameWithType> suivants à l'intérieur des requêtes LINQ to SQL.  
  
|Méthodes <xref:System.DateTime> prises en charge|Opérateurs <xref:System.DateTime> pris en charge|Propriétés <xref:System.DateTime> prises en charge|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a>Membres non pris en charge par LINQ to SQL  

 Les membres suivants ne sont pas pris en charge à l'intérieur des requêtes LINQ to SQL.  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a>Exemple de traduction de méthode  

 Toutes les méthodes prises en charge par LINQ to SQL sont traduites en données Transact-SQL avant d'être envoyées à SQL Server. Prenons l'exemple du modèle suivant :  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 Lorsqu'il est reconnu, il est traduit en appel direct à la fonction `DATEDIFF` SQL Server, comme suit :  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a>Méthodes de date et d'heure SQLMethods  

 Outre les méthodes proposées par la structure <xref:System.DateTime>, LINQ to SQL fournit également celles répertoriées dans le tableau suivant à partir de la classe <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> pour l'utilisation des données de date et d'heure.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](query-concepts.md)
- [Création du modèle objet](creating-the-object-model.md)
- [Mappage de type SQL-CLR](sql-clr-type-mapping.md)
- [Fonctions et types de données](data-types-and-functions.md)
