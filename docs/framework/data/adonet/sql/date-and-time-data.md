---
title: Données de date et d'heure
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: bdcbaffe1be4933b89c7bf0d3a11e1bb871bc2bd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450296"
---
# <a name="date-and-time-data"></a>Données de date et d'heure
SQL Server 2008 introduit de nouveaux types de manipulation de données de date et d'heure. Ces nouveaux types de données incluent des types distincts pour la date et l’heure, ainsi que des types de données développés prenant en charge une plage plus vaste de valeurs, la précision et les fuseaux horaires. À partir du .NET Framework version 3.5 Service Pack (SP) 1, le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>) assure la prise en charge complète de l’ensemble des nouvelles fonctionnalités du moteur de base de données SQL Server 2008. Vous devez installer le .NET Framework 3.5 SP1 (ou version ultérieure) pour utiliser ces nouvelles fonctionnalités avec SqlClient.  
  
 Les versions de SQL Server antérieures à SQL Server 2008 n'incluaient que deux types de données pour l'utilisation des valeurs de date et d'heure : `datetime` et `smalldatetime`. Ces deux types de données contiennent à la fois les valeurs de date et d’heure, ce qui rend difficile l’utilisation de l’une sans l’autre. Par ailleurs, ces types de données prennent uniquement en charge les dates postérieures à l'introduction du calendrier grégorien en Angleterre en 1753. En outre, ces anciens types de données sont incompatibles avec les fuseaux horaires, ce qui rend difficile la gestion de données provenant de différents fuseaux horaires.  
  
 Une documentation complète sur les types de données SQL Server est disponible dans la documentation en ligne de SQL Server. Le tableau suivant répertorie les rubriques de base spécifiques à la version relatives aux données de date et d'heure.  
  
 **Documentation SQL Server**  
  
1. [Utilisation des données de date et d’heure](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Types de données de date et d'heure introduits dans SQL Server 2008  
 Le tableau suivant décrit les nouveaux types de données de date et d'heure.  
  
|Type de données SQL Server|Description|  
|--------------------------|-----------------|  
|`date`|Le type de données `date` est situé dans une plage comprise entre le 1er janvier 01 et le 31 décembre 9999, avec une précision d’un jour. La valeur par défaut est le 1er janvier 1900. La taille de stockage est de 3 octets.|  
|`time`|Le type de données `time` stocke les valeurs d’heure uniquement en fonction d’une horloge au format 24 heures. Le type de données `time` présente une plage comprise entre 00:00:00.0000000 et 23:59:59.9999999 avec une précision de 100 nanosecondes. La valeur par défaut est 00:00:00.0000000 (minuit). Le type de données `time` prend en charge une précision à la fraction de seconde, et la taille de stockage varie entre trois et six octets, en fonction de la précision spécifiée.|  
|`datetime2`|Le type de données `datetime2` combine la plage et la précision des types de données `date` et `time` en un seul type de données.<br /><br /> Les valeurs par défaut et les formats littéraux de chaîne sont identiques à ceux définis dans les types de données `date` et `time`.|  
|`datetimeoffset`|Le type de données `datetimeoffset` présente toutes les fonctionnalités du type de données `datetime2` avec en plus un décalage horaire. Le décalage horaire est représenté sous la forme [+&#124;-] HH:MM. HH est un nombre à deux chiffres, compris entre 00 et 14, qui représente le nombre d’heures dans le décalage de fuseau horaire. MM est un nombre à deux chiffres, compris entre 00 et 59, qui représente le nombre de minutes supplémentaires dans le décalage de fuseau horaire. Les formats d’heure sont pris en charge jusqu’à une précision de 100 nanosecondes. Le signe + ou  - obligatoire indique si le décalage est ajouté ou soustrait de l'heure universelle UTC (Universal Time Coordinate ou heure de Greenwich) pour obtenir l'heure locale.|  
  
> [!NOTE]
> Pour plus d’informations sur l’utilisation du mot clé `Type System Version`, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Format et ordre de la date  
 La façon dont SQL Server analyse les valeurs de date et d'heure dépend non seulement de la version du système de type et de celle du serveur, mais également des paramètres de format et de langue par défaut du serveur. Les chaînes de date fonctionnant pour les formats de date d'une langue peuvent ne pas être reconnues si la requête est exécutée par une connexion qui utilise une autre langue ou une autre définition des formats de date.  
  
 L'instruction Transact-SQL SET LANGUAGE définit implicitement le DATEFORMAT qui détermine l'ordre des parties de la date. Vous pouvez utiliser l'instruction SET DATEFORMAT Transact-SQL sur une connexion pour lever l'ambiguïté pour des valeurs de date en classant les parties de date dans l'ordre MDY, DMY, YMD, YDM, MYD ou DYM.  
  
 Si vous ne spécifiez pas de DATEFORMAT pour la connexion, SQL Server utilise la langue par défaut associée à la connexion. Par exemple, une chaîne de date '01/02/03' serait interprétée sous la forme MDY (2 janvier 2003) sur un serveur dont le paramètre de langue est Anglais États-Unis, et sous la forme DMY (1er février 2003) sur un serveur dont le paramètre de langue est Anglais britannique. L'année est déterminée en utilisant la règle de l'année de troncature de SQL Server, qui définit la date de troncature pour l'assignation de la valeur relative au siècle. Pour plus d’informations, consultez l' [option année de coupure à deux chiffres](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).  
  
> [!NOTE]
> Le format de date YDM n'est pas pris en charge lors de la conversion d'un format de chaîne en `date`, `time`, `datetime2` ou `datetimeoffset`.  
  
 Pour plus d’informations sur la façon dont SQL Server interprète les données de date et d’heure, consultez [utilisation des données de date et d’heure](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).  
  
## <a name="datetime-data-types-and-parameters"></a>Types de données et paramètres de date/heure  
 Les énumérations suivantes ont été ajoutées à l'objet <xref:System.Data.SqlDbType> pour prendre en charge les nouveaux types de données de date et d'heure.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Vous pouvez spécifier le type de données d’un objet <xref:System.Data.SqlClient.SqlParameter> à l’aide de l’une des énumérations <xref:System.Data.SqlDbType> précédentes. 

> [!NOTE]
> Vous ne pouvez pas définir la propriété `DbType` d’un `SqlParameter` sur `SqlDbType.Date`.

 Vous pouvez également spécifier le type d’un objet <xref:System.Data.SqlClient.SqlParameter> de manière générique en attribuant à la propriété <xref:System.Data.SqlClient.SqlParameter.DbType%2A> d’un objet `SqlParameter` une valeur d’énumération <xref:System.Data.DbType> particulière. Les valeurs d’énumération suivantes ont été ajoutées à l’objet <xref:System.Data.DbType> pour prendre en charge les types de données `datetime2` et `datetimeoffset` :  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Ces nouvelles énumérations complètent les énumérations `Date`, `Time` et `DateTime` qui existaient dans les versions antérieures du .NET Framework.  
  
 Le type de fournisseur de données .NET Framework d'un objet paramètre est déduit du type .NET Framework de la valeur de l'objet paramètre, ou du `DbType` de l'objet paramètre. Aucun type de données <xref:System.Data.SqlTypes> nouveau n'a été introduit pour prendre en charge les nouveaux types de données de date et d'heure. Le tableau suivant décrit les mappages entre les types de données de date et d'heure SQL Server 2008 et les types de données CLR.  
  
|Type de données SQL Server|Type .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Date|System.DateTime|Date|Date|  
|time|System.TimeSpan|Temps|Temps|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|DATETIME|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Propriétés SqlParameter  
 Le tableau suivant décrit les propriétés `SqlParameter` pertinentes pour les types de données de date et d'heure.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Obtient ou définit si une valeur peut être nulle. Lorsque vous envoyez une valeur de paramètre null au serveur, vous devez spécifier <xref:System.DBNull>, plutôt que `null` (`Nothing` dans Visual Basic). Pour plus d’informations sur les valeurs Null de base de données, consultez [Handling Null Values](handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Obtient ou définit le nombre maximal de chiffres utilisés pour représenter la valeur. Ce paramètre est ignoré pour les types de données de date et d'heure.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Obtient ou définit le nombre de décimales à laquelle la partie heure de la valeur est résolue pour `Time`, `DateTime2`, et `DateTimeOffset`. La valeur par défaut est 0, ce qui signifie que l'échelle réelle est déduite de la valeur et envoyée au serveur.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignoré pour les types de données de date et d'heure|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Obtient ou définit la valeur du paramètre.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Obtient ou définit la valeur du paramètre.|  
  
> [!NOTE]
> Les valeurs d'heure inférieures à zéro ou égales ou supérieures à 24 heures lèvent une exception <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Création de paramètres  
 Vous pouvez créer un objet <xref:System.Data.SqlClient.SqlParameter> à l’aide de son constructeur ou en l’ajoutant à une collection <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> en appelant la méthode `Add` de <xref:System.Data.SqlClient.SqlParameterCollection>. La méthode `Add` prendra comme entrée les arguments de constructeur ou un objet paramètre existant.  
  
 Les sections suivantes présentées dans cette rubrique fournissent des exemples montrant comment spécifier des paramètres de date et d'heure. Pour obtenir des exemples supplémentaires d’utilisation des paramètres, consultez [Configuration des paramètres et des types de données de paramètre](../configuring-parameters-and-parameter-data-types.md) et des [paramètres DataAdapter](../dataadapter-parameters.md).  
  
### <a name="date-example"></a>Exemple relatif au paramètre date  
 Le fragment de code suivant montre comment spécifier un paramètre `date`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Exemple relatif au paramètre time  
 Le fragment de code suivant montre comment spécifier un paramètre `time`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Exemple relatif au paramètre datetime2  
 Le fragment de code suivant montre comment spécifier un paramètre `datetime2` avec à la fois les parties de date et d'heure.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Exemple relatif au paramètre DateTimeOffset  
 Le fragment de code suivant montre comment spécifier un paramètre `DateTimeOffSet` avec une date, une heure et un décalage horaire de 0.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
 Vous pouvez entrer des paramètres à l'aide de la méthode `AddWithValue` d'un objet <xref:System.Data.SqlClient.SqlCommand>, comme indiqué dans le fragment de code suivant. Cependant, la méthode `AddWithValue` ne vous permet pas de spécifier <xref:System.Data.SqlClient.SqlParameter.DbType%2A> ni <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pour le paramètre.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 Le paramètre `@date` peut mapper à un type de données `date`, `datetime` ou `datetime2` sur le serveur. Lors de l'utilisation de nouveaux types de données `datetime`, vous devez affecter explicitement le type de données de l'instance à la propriété <xref:System.Data.SqlDbType> du paramètre. L'utilisation de <xref:System.Data.SqlDbType.Variant> ou la fourniture implicite de valeurs de paramètre peut provoquer des problèmes de compatibilité descendante avec les types de données `datetime` et `smalldatetime`.  
  
 Le tableau suivant indique les `SqlDbTypes` déduits selon les types CLR :  
  
|Type CLR|SqlDbType déduit|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Récupération des données de date et d'heure  
 Le tableau suivant décrit les méthodes utilisées pour récupérer des valeurs de date et d’heure SQL Server 2008.  
  
|Méthode SqlClient|Description|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Récupère la valeur de colonne spécifiée sous la forme d’une structure <xref:System.DateTime>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Récupère la valeur de colonne spécifiée sous la forme d’une structure <xref:System.DateTimeOffset>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Retourne le type correspondant au type spécifique au fournisseur sous-jacent pour le champ. Retourne les mêmes types que `GetFieldType` pour les nouveaux types de date et d'heure.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Récupère la valeur de la colonne spécifiée. Retourne les mêmes types que `GetValue` pour les nouveaux types de date et d'heure.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Récupère les valeurs dans le tableau spécifié.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Récupère la valeur de colonne sous forme d'objet <xref:System.Data.SqlTypes.SqlString>. Un objet <xref:System.InvalidCastException> est généré si les données ne peuvent pas être exprimées sous la forme d'un `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Récupère des données de colonne comme son `SqlDbType` par défaut. Retourne les mêmes types que `GetValue` pour les nouveaux types de date et d'heure.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Récupère les valeurs dans le tableau spécifié.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Récupère la valeur de colonne sous forme de chaîne si la version de système de type a la valeur SQL Server 2005. Un objet <xref:System.InvalidCastException> est généré si les données ne peuvent pas être exprimées sous la forme d'une chaîne.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Récupère la valeur de colonne spécifiée sous la forme d’une structure <xref:System.TimeSpan>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Récupère la valeur de la colonne spécifiée comme son type CLR sous-jacent.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Récupère les valeurs de colonne dans un tableau.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Retourne un objet <xref:System.Data.DataTable> qui décrit les métadonnées du jeu de résultats.|  
  
> [!NOTE]
> Les nouveaux `SqlDbTypes` de date et d'heure ne sont pas pris en charge pour le code exécuté en mode in-process dans SQL Server. Une exception est levée si l'un de ces types est passé au serveur.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Spécification des valeurs de date et d'heure en tant que littéraux  
 Vous pouvez spécifier des types de données de date et d'heure en utilisant de nombreux formats littéraux de chaîne différents que SQL Server évalue ensuite lors de l'exécution, en les convertissant en structures de date/heure internes. SQL Server  reconnaît les données de date et d'heure entre des guillemets simples ('). Les exemples suivants présentent certains formats :  
  
- Formats de date alphabétique, tels que `'October 15, 2006'`.  
  
- Formats de date numérique, tels que `'10/15/2006'`.  
  
- Formats de chaîne non séparée, tels que `'20061015'` qui serait interprété sous la forme « 15 octobre 2006 » si vous utilisez le format de date ISO standard.  
  
> [!NOTE]
> La documentation complète relative à l'ensemble des formats littéraux de chaîne et autres fonctionnalités des types de données de date et d'heure est disponible dans la documentation en ligne de SQL Server.  
  
 Les valeurs d'heure inférieures à zéro ou égales ou supérieures à 24 heures lèvent une exception <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-books-online"></a>Ressources dans la documentation en ligne de SQL Server.  
 Pour plus d’informations sur l’utilisation des valeurs de date et d’heure dans SQL Server, consultez les ressources suivantes dans Documentation en ligne de SQL Server.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Types de données et fonctions de date et d’heure (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Fournit une vue d’ensemble de tous les types de données et fonctions de date et d’heure Transact-SQL.|  
|[Utilisation des données de date et d’heure](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Fournit des informations sur les fonctions et types de données de date et d’heure, ainsi que des exemples d’utilisation.|  
|[Types de données (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|Décrit les types de données système dans SQL Server.|  
  
## <a name="see-also"></a>Voir aussi

- [Mappages de types de données SQL Server](../sql-server-data-type-mappings.md)
- [Configuration des paramètres et des types de données des paramètres](../configuring-parameters-and-parameter-data-types.md)
- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
