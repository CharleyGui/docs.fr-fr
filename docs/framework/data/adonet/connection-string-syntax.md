---
title: Syntaxe des chaînes de connexion
description: En savoir plus sur la syntaxe des chaînes de connexion dans ADO.NET. La syntaxe de chaque fournisseur est documentée dans sa propriété ConnectionString.
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 5942307535e9a6e10009f193289daf94a07cd950
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148401"
---
# <a name="connection-string-syntax"></a>Syntaxe des chaînes de connexion

Chaque fournisseur de données .NET Framework a un objet `Connection` qui hérite de <xref:System.Data.Common.DbConnection> et d'une propriété <xref:System.Data.Common.DbConnection.ConnectionString%2A> spécifique au fournisseur. La syntaxe de chaîne de connexion spécifique à chaque fournisseur est documentée dans sa propriété `ConnectionString`. Le tableau suivant répertorie les quatre fournisseurs de données inclus dans le .NET Framework.  
  
|fournisseur de données .NET Framework|Description|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Fournit l'accès aux données pour Microsoft SQL Server. Pour plus d'informations sur la syntaxe de chaîne de connexion, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|Fournit un accès aux données pour les sources de données exposées à l'aide de OLE DB. Pour plus d'informations sur la syntaxe de chaîne de connexion, consultez <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|Fournit un accès aux données pour les sources de données exposées à l'aide de ODBC. Pour plus d'informations sur la syntaxe de chaîne de connexion, consultez <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Fournit un accès aux données pour Oracle version 8.1.7 ou ultérieure. Pour plus d'informations sur la syntaxe de chaîne de connexion, consultez <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Builders de chaînes de connexion  

 ADO.NET 2.0 a introduit les générateurs de chaînes de connexion suivants pour les fournisseurs de données .NET Framework.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Les générateurs de chaînes de connexion vous permettent de générer des chaînes de connexion valides lors de l'exécution, vous évitant ainsi d'avoir à concaténer manuellement les valeurs de chaîne dans votre code. Pour plus d’informations, consultez [Builders de chaînes de connexion](connection-string-builders.md).  

## <a name="windows-authentication"></a>Authentification Windows  

 Nous vous recommandons d’utiliser l’authentification Windows (parfois appelée *sécurité intégrée*) pour vous connecter aux sources de données qui la prennent en charge. La syntaxe employée dans la chaîne de connexion varie en fonction du fournisseur. Le tableau suivant présente la syntaxe de l'authentification Windows utilisée avec les fournisseurs de données .NET Framework.  
  
|Fournisseur|Syntaxe|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true` lève une exception lors de son utilisation avec le fournisseur `OleDb`.  
  
## <a name="sqlclient-connection-strings"></a>Chaînes de connexion SqlClient  

La syntaxe pour une chaîne de connexion <xref:System.Data.SqlClient.SqlConnection> est documentée dans la propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>. La propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> vous permet d'obtenir ou de définir une chaîne de connexion pour une base de données SQL Server. Si vous devez vous connecter à une version antérieure de SQL Server, utilisez le fournisseur de données .NET Framework pour OleDb (<xref:System.Data.OleDb>). La plupart des mots clés de chaîne connexion sont aussi mappés à des propriétés dans le <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
> La valeur par défaut du `Persist Security Info` mot clé est `false` . L'attribution au mot clé de la valeur `true` ou `yes` permet d'obtenir de la connexion des informations sensibles pour la sécurité, par exemple l'ID utilisateur et le mot de passe, une fois la connexion ouverte. Conservez la `Persist Security Info` valeur `false` pour vous assurer qu’une source non approuvée n’a pas accès aux informations de chaîne de connexion sensibles.  

### <a name="windows-authentication-with-sqlclient"></a>Authentification Windows avec SqlClient

 Chacune des formes de syntaxe suivantes utilise l’authentification Windows pour se connecter à la base de données **AdventureWorks** sur un serveur local.  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Authentification SQL Server avec SqlClient

 L'authentification Windows est la solution préférée pour se connecter à SQL Server. Cependant, si l'authentification SQL Server est requise, utilisez la syntaxe suivante pour spécifier un nom d'utilisateur et un mot de passe.  Dans cet exemple, des astérisques servent à représenter un nom d'utilisateur et un mot de passe valides.  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Lorsque vous vous connectez à Azure SQL Database ou à Azure SQL Data Warehouse et fournissez une connexion au format, assurez-vous `user@servername` que la `servername` valeur de la connexion correspond à la valeur fournie pour `Server=` .

> [!NOTE]
> L'authentification Windows est prioritaire sur les comptes de connexion SQL Server. Si vous spécifiez Integrated Security=true ainsi qu'un nom d'utilisateur et un mot de passe, ces derniers seront ignorés pour utiliser l'authentification Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Se connecter à une instance nommée de SQL Server

Pour vous connecter à une instance nommée de SQL Server, utilisez la syntaxe *Server serveur\instance Name* .  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Vous pouvez également définir la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> du `SqlConnectionStringBuilder` sur le nom d'instance lors de la création d'une chaîne de connexion. La propriété <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> d'un objet <xref:System.Data.SqlClient.SqlConnection> est en lecture seule.  
  
### <a name="type-system-version-changes"></a>Modifications de la version de système de type  

 Le `Type System Version` mot clé dans un <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> spécifie la représentation côté client des types de SQL Server. Pour plus d'informations sur le mot clé <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>, consultez `Type System Version`.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Connexion et attachement aux instances utilisateur de SQL Server Express  

 Les instances utilisateur sont une fonctionnalité de SQL Server Express. Elles permettent à un utilisateur qui s'exécute sur un compte Windows local disposant de privilèges minimum de se connecter à une base de données SQL Server et de l'exécuter sans nécessiter de privilèges d'administrateur. Une instance utilisateur s'exécute avec les informations d'identification Windows de l'utilisateur, pas en tant que service.  
  
 Pour plus d’informations sur l’utilisation des instances utilisateur, consultez [SQL Server Express des instances utilisateur](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Utilisation de TrustServerCertificate  

 Le `TrustServerCertificate` mot clé est valide uniquement lors de la connexion à une instance de SQL Server avec un certificat valide. Lorsque `TrustServerCertificate` a la valeur `true`, la couche de transport fait appel au protocole SSL pour chiffrer le canal et ignore la chaîne du certificat pour valider la confiance.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> Si `TrustServerCertificate` a la valeur `true` et le chiffrement est activé, le niveau de chiffrement spécifié sur le serveur sera utilisé même si  `Encrypt` a la valeur `false` dans la chaîne de connexion. Sinon, la connexion échouera.  
  
### <a name="enabling-encryption"></a>Activation du chiffrement  

 Pour activer le chiffrement lorsqu’un certificat n’a pas été configuré sur le serveur, les options **forcer le chiffrement du protocole** et **faire confiance au certificat de serveur** doivent être définies dans Gestionnaire de configuration SQL Server. Dans ce cas, le chiffrement utilise un certificat de serveur auto-signé sans validation si aucun certificat vérifiable n'a été fourni sur le serveur.  
  
 Les paramètres d'application ne peuvent pas réduire le niveau de la sécurité configurée dans SQL Server, mais peuvent éventuellement la renforcer. Une application peut demander le chiffrement en définissant les `TrustServerCertificate` `Encrypt` Mots clés et sur `true` , garantissant ainsi que le chiffrement a lieu, même lorsqu’un certificat de serveur n’a pas été configuré et **forcer le chiffrement du protocole** n’a pas été configuré pour le client. Toutefois, si `TrustServerCertificate` n'est pas activé dans la configuration cliente, un certificat de serveur fourni est toujours nécessaire.  
  
 Le tableau ci-dessous décrit tous les cas.  
  
|Paramètre client Forcer le chiffrement du protocole|Paramètre client Faire confiance au certificat de serveur|Attribut/chaîne de connexion Chiffrer/Utiliser le chiffrement pour les données|Attribut/chaîne de connexion Faire confiance au certificat de serveur|Résultats|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Non |N/A|Non (par défaut)|Ignoré|Aucun chiffrement ne se produit.|  
|Non |N/A|Oui|Non (par défaut)|Le chiffrement se produit uniquement s'il existe un certificat de serveur vérifiable ; sinon, la tentative de connexion échoue.|  
|Non |N/A|Oui|Oui|Le chiffrement se produit toujours, mais peut utiliser un certificat de serveur auto-signé.|  
|Oui|Non |Ignoré|Ignoré|Le chiffrement se produit uniquement s’il existe un certificat de serveur vérifiable ; dans le cas contraire, la tentative de connexion échoue.|  
|Oui|Oui|Non (par défaut)|Ignoré|Le chiffrement se produit toujours, mais peut utiliser un certificat de serveur auto-signé.|  
|Oui|Oui|Oui|Non (par défaut)|Le chiffrement se produit uniquement s’il existe un certificat de serveur vérifiable ; dans le cas contraire, la tentative de connexion échoue.|  
|Oui|Oui|Oui|Oui|Le chiffrement se produit toujours, mais peut utiliser un certificat de serveur auto-signé.|  
  
 Pour plus d’informations, consultez [Utilisation du chiffrement sans validation](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Chaînes de connexion OleDb  

 La propriété <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> d'un <xref:System.Data.OleDb.OleDbConnection> vous permet d'obtenir et de définir une chaîne de connexion pour une source de données OLE DB, telle que Microsoft Access. Vous pouvez également créer une chaîne de connexion `OleDb` au moment de l'exécution à l'aide de la classe <xref:System.Data.OleDb.OleDbConnectionStringBuilder>.  
  
### <a name="oledb-connection-string-syntax"></a>Syntaxe de chaîne de connexion OleDb  

 Vous devez spécifier un nom de fournisseur pour une chaîne de connexion <xref:System.Data.OleDb.OleDbConnection>. La chaîne de connexion suivante se connecte à une base de données Microsoft Access à l'aide du fournisseur Jet. Notez que les mots clés `User ID` et `Password` sont facultatifs si la base de données n'est pas sécurisée (par défaut).  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 Si la base de données Jet est sécurisée à l'aide d'une sécurité au niveau utilisateur, vous devez fournir l'emplacement du fichier d'informations de groupe de travail (.mdw). Le fichier d'informations de groupe de travail permet de valider les informations d'identification présentées dans la chaîne de connexion.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> Il est possible de fournir des informations de connexion pour un **OleDbConnection** dans un fichier Universal Data Link (UDL); Toutefois, vous devez éviter de le faire. Les fichiers UDL n'étant pas chiffrés, ils exposent les informations de chaîne de connexion en texte brut. Comme un fichier UDL est une ressource basée sur un fichier externe pour votre application, il n'est pas possible de le sécuriser à l'aide du .NET Framework. Les fichiers UDL ne sont pas pris en charge pour **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Utilisation de DataDirectory pour se connecter à Access/Jet  

 `DataDirectory` n'est pas exclusif à `SqlClient`. Il peut être aussi utilisé avec les fournisseurs de données .NET <xref:System.Data.OleDb> et <xref:System.Data.Odbc>. L’exemple de chaîne <xref:System.Data.OleDb.OleDbConnection> suivant illustre la syntaxe nécessaire pour se connecter au fichier Northwind.mdb situé dans le dossier app_data de l’application. La base de données système (System.mdw) est également stockée à cet emplacement.  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Il n'est pas nécessaire de définir l'emplacement de la base de données système dans la chaîne de connexion si la base de données Access/Jet n'est pas sécurisée. La sécurité est désactivée par défaut et tous les utilisateurs se connectent avec le profil intégré d'utilisateur Admin et à l'aide d'un mot de passe vide. Même lorsque la sécurité au niveau utilisateur est correctement implémentée, une base de données Jet reste vulnérable aux attaques. Par conséquent, le stockage d'informations sensibles dans une base de données Access/Jet n'est pas recommandé en raison de la défaillance inhérente de son modèle de sécurité basé sur un fichier.  
  
### <a name="connecting-to-excel"></a>Connexion à Excel  

 Le fournisseur Microsoft Jet permet de se connecter à un classeur Excel. Dans la chaîne de connexion suivante, le mot clé `Extended Properties` définit des propriétés spécifiques à Excel. « HDR=Yes; » indique que la première ligne contient des noms de colonne, pas des données, et « IMEX=1; » indique au pilote de toujours lire les colonnes de données « intermixed » comme du texte.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Notez que le caractère guillemet double requis pour `Extended Properties` doit également être entouré de guillemets doubles.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Syntaxe de chaîne de connexion au fournisseur Data Shape  

 Utilisez les mots clés `Provider` et `Data Provider` lorsque vous utilisez le fournisseur Microsoft Data Shape. L'exemple suivant utilise le fournisseur Shape pour se connecter à une instance locale de SQL Server.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a>Chaînes de connexion Odbc  

 La propriété <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> d'un <xref:System.Data.Odbc.OdbcConnection> vous permet d'obtenir ou de définir une chaîne de connexion pour une source de données OLE DB. Les chaînes de connexion ODBC sont également prises en charge par le <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 La chaîne de connexion suivante utilise le pilote Microsoft Text.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Utilisation de DataDirectory pour se connecter à Visual FoxPro  

 L'exemple de chaîne de connexion <xref:System.Data.Odbc.OdbcConnection> suivant illustre l'utilisation de `DataDirectory` pour se connecter à un fichier Microsoft Visual FoxPro.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Chaînes de connexion Oracle  

 La propriété <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> d'un <xref:System.Data.OracleClient.OracleConnection> vous permet d'obtenir ou de définir une chaîne de connexion pour une source de données OLE DB. Les chaînes de connexion Oracle sont également prises en charge par le <xref:System.Data.OracleClient.OracleConnectionStringBuilder>.  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Pour plus d'informations sur la syntaxe de chaîne de connexion ODBC, consultez <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Chaînes de connexion](connection-strings.md)
- [Connexion à une source de données](connecting-to-a-data-source.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
