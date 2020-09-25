---
title: Mappage de type SQL-CLR
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 313fd81bd84a99e4a2d32925a7d3bb4776f8472b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203538"
---
# <a name="sql-clr-type-mapping"></a>Mappage de type SQL-CLR

Dans vbtecdlinq, le modèle de données d'une base de données relationnelle mappe à un modèle objet qui est exprimé dans le langage de programmation de votre choix. Lors de l'exécution de l'application, LINQ to SQL traduit les requêtes LINQ dans le modèle objet en SQL et les envoie à la base de données pour exécution. Lorsque la base de données retourne les résultats, LINQ to SQL traduit ces derniers en objets que vous pouvez utiliser dans votre propre langage de programmation.  
  
 Pour convertir des données entre le modèle objet et la base de données, vous devez définir un *mappage de type* . LINQ to SQL utilise un mappage de type pour faire correspondre chaque type CLR (Common Language Runtime) à un type SQL Server particulier. Vous pouvez définir des mappages de types et d'autres informations de mappage, telles que la structure de la base de données et les relations entre les tables, à l'intérieur du modèle objet à l'aide du mappage basé sur des attributs. Vous pouvez également spécifier les informations de mappage en dehors du modèle objet à l'aide d'un fichier de mappage externe. Pour plus d’informations, consultez [mappage basé sur les attributs](attribute-based-mapping.md) et [mappage externe](external-mapping.md).  
  
 Cette rubrique aborde les points suivants :  
  
- [Mappage de type par défaut](#DefaultTypeMapping)  
  
- [Matrice de comportement au moment de l'exécution de mappages de types](#BehaviorMatrix)  
  
- [Différences de comportement entre l'exécution CLR et l'exécution SQL](#BehaviorDiffs)  
  
- [Mappage d'enum](#EnumMapping)  
  
- [Mappage de types numériques](#NumericMapping)  
  
- [Mappage de texte et mappage XML](#TextMapping)  
  
- [Mappage de types de date et d'heure](#DateMapping)  
  
- [Mappage de types binaires](#BinaryMapping)  
  
- [Mappages divers](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>

## <a name="default-type-mapping"></a>Mappage de type par défaut  

 Vous pouvez créer automatiquement le modèle objet ou le fichier de mappage externe à l'aide du Concepteur Objet/Relationnel (Concepteur O/R) ou de l'outil de ligne de commande SQLMetal. Les mappages de types par défaut pour ces outils définissent les types CLR qui sont choisis pour mapper à des colonnes à l'intérieur de la base de données SQL Server. Pour plus d’informations sur l’utilisation de ces outils, consultez [création du modèle objet](creating-the-object-model.md).  
  
 Vous pouvez également utiliser la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A> pour créer une base de données SQL Server basée sur les informations de mappage contenues dans le modèle objet ou le fichier de mappage externe. Les mappages de types par défaut pour la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A> définissent le type des colonnes SQL Server qui sont créées pour mapper aux types CLR définis dans le modèle objet. Pour plus d’informations, consultez [Comment : créer dynamiquement une base de données](how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>

## <a name="type-mapping-run-time-behavior-matrix"></a>Matrice de comportement au moment de l'exécution de mappages de types  

 Le diagramme suivant présente le comportement au moment de l'exécution attendu de mappages de types spécifiques lorsque des données sont récupérées de la base de données ou enregistrées dans celle-ci. À l'exception de la sérialisation, LINQ to SQL ne prend pas en charge le mappage entre des types de données CLR ou SQL Server qui ne sont pas spécifiés dans cette matrice. Pour plus d’informations sur la prise en charge de la sérialisation, consultez [sérialisation binaire](#BinarySerialization).  

![Table de mappage de type de données CLR SQL SQL Server](./media/sql-clr-type-mapping.png)

> [!NOTE]
> Certains mappages de types peuvent entraîner des exceptions de dépassement de capacité ou de perte de données lors de la traduction à partir de la base de données ou vers celle-ci.  
  
### <a name="custom-type-mapping"></a>Mappage de type personnalisé  

 Avec LINQ to SQL, vous n'êtes pas limité aux mappages de types par défaut utilisés par le Concepteur O/R, SQLMetal et la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Vous pouvez créer des mappages de types personnalisés en les spécifiant explicitement dans un fichier DBML. Ce fichier vous permet ensuite de créer le fichier de code du modèle objet et de mappage. Pour plus d’informations, consultez [mappages de types personnalisés SQL-CLR](sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>

## <a name="behavior-differences-between-clr-and-sql-execution"></a>Différences de comportement entre l'exécution CLR et l'exécution SQL  

 En raison des différences de précision et d'exécution entre le CLR et SQL Server, vous pouvez obtenir des résultats différents ou un comportement différent en fonction de l'endroit où vous effectuez vos calculs. Les calculs effectués dans des requêtes LINQ to SQL sont en fait traduits en données Transact-SQL, puis exécutés sur la base de données SQL Server. Les calculs effectués en dehors de requêtes LINQ to SQL sont exécutés dans le contexte du CLR.  
  
 Par exemple, voici quelques différences de comportement entre le CLR et SQL Server :  
  
- SQL Server trie certains types de données différemment des données de type équivalent dans le CLR. Par exemple, le type de données SQL Server `UNIQUEIDENTIFIER` est trié différemment du type de données CLR <xref:System.Guid?displayProperty=nameWithType>.  
  
- SQL Server gère certaines opérations de comparaison de chaînes différemment par rapport au CLR. Dans SQL Server, le comportement de comparaison de chaînes dépend des paramètres de classement définis sur le serveur. Pour plus d’informations, consultez [utilisation des classements](/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105)) dans le documentation en ligne de Microsoft SQL Server.  
  
- SQL Server peut retourner des valeurs différentes pour certaines fonctions mappées par rapport au CLR. Par exemple, les fonctions d'égalité sont différentes car SQL Server considère que deux chaînes sont égales si elles ne diffèrent que par l'espace en fin de chaîne, tandis que le CLR les considère alors comme différentes.  
  
<a name="EnumMapping"></a>

## <a name="enum-mapping"></a>Mappage d'enum  

 LINQ to SQL prend en charge le mappage du type <xref:System.Enum?displayProperty=nameWithType> CLR à des types SQL Serveur de deux façons :  
  
- Mappage à des types numériques SQL (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Lorsque vous mappez un type <xref:System.Enum?displayProperty=nameWithType> CLR à un type numérique SQL, vous mappez la valeur entière sous-jacente du type <xref:System.Enum?displayProperty=nameWithType> CLR à la valeur de la colonne de la base de données SQL Server. Par exemple, si un type <xref:System.Enum?displayProperty=nameWithType> nommé `DaysOfWeek` contient un membre nommé `Tue` ayant la valeur entière sous-jacente 3, ce membre mappe à une valeur 3 de la base de données.  
  
- Mappage à des types texte SQL (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Lorsque vous mappez un type <xref:System.Enum?displayProperty=nameWithType> CLR à un type texte SQL, la valeur de la base de données SQL est mappée aux noms des membres <xref:System.Enum?displayProperty=nameWithType> CLR. Par exemple, si un type <xref:System.Enum?displayProperty=nameWithType> nommé `DaysOfWeek` contient un membre nommé `Tue` ayant la valeur entière sous-jacente 3, ce membre mappe à une valeur `Tue` de la base de données.  
  
> [!NOTE]
> Lors du mappage de types texte SQL à un type <xref:System.Enum?displayProperty=nameWithType> CLR, incluez uniquement les noms des membres <xref:System.Enum> dans la colonne SQL mappée. Les autres valeurs ne sont pas prises en charge dans la colonne SQL mappée à <xref:System.Enum>.  
  
 Le Concepteur O/R et l'outil de ligne de commande SQLMetal ne peuvent pas mapper automatiquement un type à une classe <xref:System.Enum> CLR. Vous devez configurer explicitement ce mappage en personnalisant un fichier DBML destiné à être utilisé par le Concepteur O/R et SQLMetal. Pour plus d’informations sur le mappage de type personnalisé, consultez [mappages de types personnalisés SQL-CLR](sql-clr-custom-type-mappings.md).  
  
 Étant donné qu’une colonne SQL destinée à l’énumération sera du même type que les autres colonnes numériques et de texte ; ces outils ne reconnaîtront pas votre intention et le mappage par défaut comme décrit dans les sections de mappage [numérique](#NumericMapping) et de [texte et de mappage XML](#TextMapping) suivantes. Pour plus d’informations sur la génération de code avec le fichier DBML, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md).  
  
 La méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> crée une colonne SQL de type numérique pour mapper un type <xref:System.Enum?displayProperty=nameWithType> CLR.  
  
<a name="NumericMapping"></a>

## <a name="numeric-mapping"></a>Mappage de types numériques  

 LINQ to SQL vous permet de mapper de nombreux types numériques CLR et SQL Server. Il présente les types CLR que le Concepteur O/R et SQLMetal sélectionnent lors de la création d'un modèle objet ou d'un fichier de mappage externe basé sur votre base de données.  
  
|Type SQL Server|Mappage de type CLR par défaut utilisé par le Concepteur O/R et SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=nameWithType>|  
|`TINYINT`|<xref:System.Int16?displayProperty=nameWithType>|  
|`INT`|<xref:System.Int32?displayProperty=nameWithType>|  
|`BIGINT`|<xref:System.Int64?displayProperty=nameWithType>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`MONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=nameWithType>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=nameWithType>|  
  
 Le tableau suivant présente les mappages de types par défaut utilisés par la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> pour définir le type des colonnes SQL Server qui sont créées pour mapper aux types CLR définis dans votre modèle objet ou votre fichier de mappage externe.  
  
|Type CLR|Type SQL Server par défaut utilisé par <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|`BIT`|  
|<xref:System.Byte?displayProperty=nameWithType>|`TINYINT`|  
|<xref:System.Int16?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=nameWithType>|`INT`|  
|<xref:System.Int64?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.SByte?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=nameWithType>|`INT`|  
|<xref:System.UInt32?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=nameWithType>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=nameWithType>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=nameWithType>|`REAL`|  
|<xref:System.Double?displayProperty=nameWithType>|`FLOAT`|  
  
 Vous pouvez choisir de nombreux autres mappages numériques, mais certains peuvent entraîner des exceptions de dépassement de capacité ou de perte de données lors de la traduction à partir de la base de données ou vers celle-ci. Pour plus d’informations, consultez la [matrice de comportement du mappage de type au moment](#BehaviorMatrix)de l’exécution.  
  
### <a name="decimal-and-money-types"></a>Types decimal et money  

 La précision par défaut du `DECIMAL` type de SQL Server (18 chiffres décimaux à gauche et à droite de la virgule décimale) est nettement inférieure à la précision du <xref:System.Decimal?displayProperty=nameWithType> type CLR auquel il est associé par défaut. Cela peut entraîner une perte de précision lorsque vous enregistrez des données dans la base de données. Toutefois, l’inverse peut se produire si le type `DECIMAL` SQL Server est configuré avec une précision supérieure à 29 chiffres. Lorsqu'un type `DECIMAL` SQL Server a été configuré avec une précision supérieure à celle du type <xref:System.Decimal?displayProperty=nameWithType> CLR, une perte de précision peut se produire lors de la récupération de données de la base de données.  
  
 Les types `MONEY` et `SMALLMONEY` SQL Server, qui sont également associés au type <xref:System.Decimal?displayProperty=nameWithType> CLR par défaut, ont une précision beaucoup plus faible, ce qui peut entraîner des exceptions de dépassement de capacité ou de perte de données lors de l'enregistrement de données dans la base de données.  
  
<a name="TextMapping"></a>

## <a name="text-and-xml-mapping"></a>Mappage de texte et mappage XML  

 Il existe également de nombreux types basés sur du texte et types XML que vous pouvez mapper à l'aide de LINQ to SQL. Il présente les types CLR que le Concepteur O/R et SQLMetal sélectionnent lors de la création d'un modèle objet ou d'un fichier de mappage externe basé sur votre base de données.  
  
|Type SQL Server|Mappage de type CLR par défaut utilisé par le Concepteur O/R et SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 Le tableau suivant présente les mappages de types par défaut utilisés par la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> pour définir le type des colonnes SQL Server qui sont créées pour mapper aux types CLR définis dans votre modèle objet ou votre fichier de mappage externe.  
  
|Type CLR|Type SQL Server par défaut utilisé par <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Type personnalisé implémentant `Parse()` et `ToString()`|`NVARCHAR(MAX)`|  
  
 Vous pouvez choisir de nombreux autres mappages basés sur du texte et mappages XML, mais certains peuvent entraîner des exceptions de dépassement de capacité ou de perte de données lors de la traduction à partir de la base de données ou vers celle-ci. Pour plus d’informations, consultez la [matrice de comportement du mappage de type au moment](#BehaviorMatrix)de l’exécution.  
  
### <a name="xml-types"></a>Types XML  

 Le type de données `XML` SQL Server est disponible à partir de Microsoft SQL Server 2005. Vous pouvez mapper le type de données `XML` SQL Server à <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> ou <xref:System.String>. Si la colonne stocke des fragments XML qui ne peuvent pas être lus dans <xref:System.Xml.Linq.XElement>, la colonne doit être mappée à <xref:System.String> pour éviter des erreurs d'exécution. Les fragments XML qui doivent être mappés à <xref:System.String> incluent les éléments suivants :  
  
- Séquence d'éléments XML  
  
- Attributs  
  
- Identificateurs publics  
  
- Commentaires  
  
 Bien que vous puissiez mapper <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> à SQL Server comme indiqué dans la matrice de comportement de l’exécution du [mappage de type](#BehaviorMatrix), la méthode n' <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> a pas de mappage de type SQL Server par défaut pour ces types.  
  
### <a name="custom-types"></a>Types personnalisés  

 Si une classe implémente `Parse()` et `ToString()` , vous pouvez mapper l’objet à n’importe quel type de texte SQL ( `CHAR` , `NCHAR` , `VARCHAR` , `NVARCHAR` , `TEXT` , `NTEXT` , `XML` ). L'objet est stocké dans la base de données en envoyant la valeur retournée par `ToString()` à la colonne de la base de données mappée. L'objet est reconstruit en appelant `Parse()` sur la chaîne retournée par la base de données.  
  
> [!NOTE]
> LINQ to SQL ne prend pas en charge la sérialisation à l'aide de <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>

## <a name="date-and-time-mapping"></a>Mappage de types de date et d'heure  

 LINQ to SQL vous permet de mapper de nombreux types de date et d'heure SQL Server. Il présente les types CLR que le Concepteur O/R et SQLMetal sélectionnent lors de la création d'un modèle objet ou d'un fichier de mappage externe basé sur votre base de données.  
  
|Type SQL Server|Mappage de type CLR par défaut utilisé par le Concepteur O/R et SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 Le tableau suivant présente les mappages de types par défaut utilisés par la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> pour définir le type des colonnes SQL Server qui sont créées pour mapper aux types CLR définis dans votre modèle objet ou votre fichier de mappage externe.  
  
|Type CLR|Type SQL Server par défaut utilisé par <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Vous pouvez choisir de nombreux autres mappages de types de date et d'heure, mais certains peuvent entraîner des exceptions de dépassement de capacité ou de perte de données lors de la traduction à partir de la base de données ou vers celle-ci. Pour plus d’informations, consultez la [matrice de comportement du mappage de type au moment](#BehaviorMatrix)de l’exécution.  
  
> [!NOTE]
> Les types `DATETIME2`, `DATETIMEOFFSET`, `DATE` et `TIME` SQL Server sont disponibles à partir de Microsoft SQL Server 2008. LINQ to SQL prend en charge le mappage à ces nouveaux types à partir de .NET Framework version 3.5 SP1.  
  
### <a name="systemdatetime"></a>System.DateTime  

 La plage et la précision du type <xref:System.DateTime?displayProperty=nameWithType> CLR sont supérieures à celles du type `DATETIME` SQL Server, qui est le mappage de type par défaut pour la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>. Afin d'éviter les exceptions liées à des dates en dehors de la plage de `DATETIME`, utilisez `DATETIME2`, qui est disponible à partir de Microsoft SQL Server 2008. `DATETIME2` peut correspondre à la plage et à la précision du CLR <xref:System.DateTime?displayProperty=nameWithType> .  
  
 Les dates SQL Server n’ont aucun concept de <xref:System.TimeZone>, une fonctionnalité qui est largement prise en charge dans le CLR. Les valeurs <xref:System.TimeZone> sont enregistrées telles quelles dans la base de données sans conversion <xref:System.TimeZone>, indépendamment des informations <xref:System.DateTimeKind> d'origine. Lorsque les valeurs <xref:System.DateTime> sont récupérées de la base de données, leur valeur est chargé telle quelle dans un <xref:System.DateTime> avec un <xref:System.DateTimeKind> de <xref:System.DateTimeKind.Unspecified>. Pour plus d’informations sur les méthodes prises en charge <xref:System.DateTime?displayProperty=nameWithType> , consultez [méthodes System. DateTime](system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  

 Microsoft SQL Server 2008 et .NET Framework 3.5 SP1 vous permettent de mapper le type <xref:System.TimeSpan?displayProperty=nameWithType> CLR au type `TIME` SQL Server. Toutefois, il y a une grande différence entre la plage prise en charge par le type <xref:System.TimeSpan?displayProperty=nameWithType> CLR et celle prise en charge par le type `TIME` SQL Server. Les valeurs de mappage inférieures à 0 ou supérieures à 23:59:59.9999999 heures sur le type `TIME` SQL entraînent des exceptions de dépassement de capacité. Pour plus d’informations, consultez [System. TimeSpan, méthodes](system-timespan-methods.md).  
  
 Dans Microsoft SQL Server 2000 et SQL Server 2005, vous ne pouvez pas mapper des champs de base de données à <xref:System.TimeSpan>. Toutefois, les opérations sur <xref:System.TimeSpan> sont prises en charge car des valeurs <xref:System.TimeSpan> peuvent être retournées par la soustraction <xref:System.DateTime> ou introduites dans une expression sous forme de variable littérale ou liée.  
  
<a name="BinaryMapping"></a>

## <a name="binary-mapping"></a>Mappage de types binaires  

 Il existe de nombreux types SQL Server que vous pouvez mapper au type <xref:System.Data.Linq.Binary?displayProperty=nameWithType> CLR. Le tableau suivant présente les types SQL Server qui entraînent la définition d'un type <xref:System.Data.Linq.Binary?displayProperty=nameWithType> CLR par le Concepteur O/R et SQLMetal lors de la création d'un modèle objet ou d'un fichier de mappage externe basé sur votre base de données.  
  
|Type SQL Server|Mappage de type CLR par défaut utilisé par le Concepteur O/R et SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)` avec l' `FILESTREAM` attribut|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 Le tableau suivant présente les mappages de types par défaut utilisés par la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> pour définir le type des colonnes SQL Server qui sont créées pour mapper aux types CLR définis dans votre modèle objet ou votre fichier de mappage externe.  
  
|Type CLR|Type SQL Server par défaut utilisé par <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Vous pouvez choisir de nombreux autres mappages de types binaires, mais certains peuvent entraîner des exceptions de dépassement de capacité ou de perte de données lors de la traduction à partir de la base de données ou vers celle-ci. Pour plus d’informations, consultez la [matrice de comportement du mappage de type au moment](#BehaviorMatrix)de l’exécution.  
  
### <a name="sql-server-filestream"></a>FILESTREAM SQL Server  

 L'attribut `FILESTREAM` des colonnes `VARBINARY(MAX)` est disponible à partir de Microsoft SQL Server 2008 ; vous pouvez mapper à cet attribut à l'aide de LINQ to SQL à partir de .NET Framework version 3.5 SP1.  
  
 Bien que vous puissiez mapper des colonnes `VARBINARY(MAX)` avec l'attribut `FILESTREAM` à des objets <xref:System.Data.Linq.Binary>, la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> ne peut pas créer automatiquement des colonnes avec l'attribut `FILESTREAM`. Pour plus d’informations sur `FILESTREAM` , consultez [vue d’ensemble de FileStream](/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105)).  
  
<a name="BinarySerialization"></a>

### <a name="binary-serialization"></a>Sérialisation binaire  

 Si une classe implémente l'interface <xref:System.Runtime.Serialization.ISerializable>, vous pouvez sérialiser un objet en n'importe quel champ binaire SQL (`BINARY`, `VARBINARY`, `IMAGE`). L'objet est sérialisé et désérialisé en fonction de la façon dont l'interface <xref:System.Runtime.Serialization.ISerializable> est implémentée. Pour plus d’informations, consultez [sérialisation binaire](../../../../../standard/serialization/binary-serialization.md).
  
<a name="MiscMapping"></a>

## <a name="miscellaneous-mapping"></a>Mappages divers  

 Le tableau suivant présente les mappages de types par défaut pour divers types qui n'ont pas encore été mentionnés. Il présente les types CLR que le Concepteur O/R et SQLMetal sélectionnent lors de la création d'un modèle objet ou d'un fichier de mappage externe basé sur votre base de données.  
  
|Type SQL Server|Mappage de type CLR par défaut utilisé par le Concepteur O/R et SQLMetal|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 Le tableau suivant présente les mappages de types par défaut utilisés par la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> pour définir le type des colonnes SQL Server qui sont créées pour mapper aux types CLR définis dans votre modèle objet ou votre fichier de mappage externe.  
  
|Type CLR|Type SQL Server par défaut utilisé par <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ to SQL ne prend en charge aucun autre mappage de type pour ces types divers.  Pour plus d’informations, consultez la [matrice de comportement du mappage de type au moment](#BehaviorMatrix)de l’exécution.  
  
## <a name="see-also"></a>Voir aussi

- [Mappage basé sur les attributs](attribute-based-mapping.md)
- [Mappage externe](external-mapping.md)
- [Fonctions et types de données](data-types-and-functions.md)
- [Incompatibilité entre types SQL-CLR](sql-clr-type-mismatches.md)
