---
title: Obtention d'un DbProviderFactory
description: Découvrez comment obtenir un DbProviderFactory à partir de la classe DbProviderFactories pour travailler avec des sources de données spécifiques dans le .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 0bf95f1773c832a4666c1b33336f963b674052ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150737"
---
# <a name="obtaining-a-dbproviderfactory"></a>Obtention d'un DbProviderFactory

Le processus d'obtention d'un objet <xref:System.Data.Common.DbProviderFactory> implique de passer des informations à propos d'un fournisseur de données à la classe <xref:System.Data.Common.DbProviderFactories>. En fonction de ces informations, la méthode <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> crée une fabrique de fournisseurs fortement typée. Par exemple, pour créer un objet <xref:System.Data.SqlClient.SqlClientFactory>, vous pouvez passer à `GetFactory` une chaîne avec le nom du fournisseur spécifié comme « System.Data.SqlClient ». L'autre surcharge de `GetFactory` prend un objet <xref:System.Data.DataRow>. Une fois que vous avez créé la fabrique de fournisseurs, vous pouvez ensuite utiliser ses méthodes pour créer des objets supplémentaires. Parmi les méthodes d'un `SqlClientFactory`, citons <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> et <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
> Les objets <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory> .NET Framework et les classes <xref:System.Data.OleDb.OleDbFactory> fournissent des fonctionnalités similaires.  
  
## <a name="registering-dbproviderfactories"></a>Inscription de DbProviderFactories  

 Chaque .NET Framework fournisseur de données qui prend en charge une classe basée sur des fabriques inscrit des informations de configuration dans la section **DbProviderFactories** du fichier **machine.config** sur l’ordinateur local. Le fragment de fichier de configuration suivant montre la syntaxe et le format de <xref:System.Data.SqlClient>.  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"
     description=".Net Framework Data Provider for SqlServer"
     type="System.Data.SqlClient.SqlClientFactory, System.Data,
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 L’attribut **invariant** identifie le fournisseur de données sous-jacent. Cette syntaxe d'attribution de nom en trois parties est également utilisée lors de la création d'une fabrique et pour l'identification du fournisseur dans un fichier de configuration d'application de manière à ce que le nom du fournisseur, ainsi que sa chaîne de connexion associée, puissent être récupérés au moment de l'exécution.  
  
## <a name="retrieving-provider-information"></a>Récupération des informations relatives aux fournisseurs  

 Vous pouvez récupérer les informations relatives à tous les fournisseurs de données installés sur l'ordinateur local à l'aide de la méthode <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A>. Elle retourne un <xref:System.Data.DataTable> nommé **DbProviderFactories** qui contient les colonnes décrites dans le tableau suivant.  
  
|Numéro de colonne|Nom de la colonne|Exemple de sortie|Description|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Nom**|Fournisseur de données SqlClient|Nom lisible pour le fournisseur de données|  
|1|**Description**|Fournisseur de données .NET Framework pour SqlServer|Description lisible pour le fournisseur de données|  
|2|**InvariantName**|System.Data.SqlClient|Nom qui peut être utilisé de façon programmée pour faire référence au fournisseur de données|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Nom qualifié complet de la classe de fabrique, contenant suffisamment d'informations pour instancier l'objet|  
  
 Cette `DataTable` peuvent servir à autoriser un utilisateur à sélectionner un objet <xref:System.Data.DataRow> au moment de l'exécution. La `DataRow` sélectionnée puis peut être passée à la méthode <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> pour créer un objet <xref:System.Data.Common.DbProviderFactory> fortement typé. Un objet <xref:System.Data.DataRow> sélectionné peut être passé à la méthode `GetFactory` pour créer l'objet `DbProviderFactory` souhaité.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Liste des classes de fabrique de fournisseurs installées  

 Cet exemple montre comment utiliser la méthode <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> pour retourner un objet <xref:System.Data.DataTable> contenant des informations sur les fournisseurs installés. Le code itère au sein de chaque ligne dans la `DataTable`, en affichant des informations pour chaque fournisseur installé dans la fenêtre de console.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Utilisation de fichiers de configuration d'application pour stocker des informations sur les fabriques  

 Le modèle de conception utilisé pour travailler avec les fabriques implique le stockage des informations de fournisseur et de chaîne de connexion dans un fichier de configuration d’application, par exemple **app.config** pour une application Windows, et **web.config** pour une application ASP.net.  
  
 Le fragment de fichier de configuration suivant montre comment enregistrer deux chaînes de connexion nommées : « NorthwindSQL » pour une connexion dans la base de données Northwind dans SQL Server, et « NorthwindAccess » pour une connexion dans la base de données Northwind dans Access/Jet. Le nom **invariant** est utilisé pour l’attribut **providerName** .  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"
     providerName="System.Data.SqlClient"
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"
     providerName="System.Data.OleDb"
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Récupération d'une chaîne de connexion à l'aide du nom du fournisseur  

 Pour créer une fabrique de fournisseurs, vous devez fournir une chaîne de connexion ainsi que le nom du fournisseur. Cet exemple montre comment récupérer une chaîne de connexion à partir d’un fichier de configuration d’application en passant le nom du fournisseur dans le format invariant «*System. Data. ProviderName*». Le code itère au sein de l'objet <xref:System.Configuration.ConnectionStringSettingsCollection>. Il retourne la propriété <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> en cas de réussite; sinon `null` (`Nothing` dans Visual Basic). S'il existe plusieurs entrées pour un fournisseur, la première occurrence trouvée est retournée. Pour plus d’informations et pour obtenir des exemples de récupération de chaînes de connexion à partir de fichiers de configuration, consultez [chaînes de connexion et fichiers de configuration](connection-strings-and-configuration-files.md).  
  
> [!NOTE]
> Une référence à `System.Configuration.dll` est requise pour que le code s'exécute.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Création des objets DbProviderFactory et DbConnection  

 Cet exemple montre comment créer un <xref:System.Data.Common.DbProviderFactory> objet et <xref:System.Data.Common.DbConnection> en lui passant le nom du fournisseur au format «*System. Data. ProviderName*» et une chaîne de connexion. Un objet `DbConnection` est retourné en cas de réussite ; `null` (`Nothing` dans Visual Basic) en cas d'erreur.  
  
 Le code obtient `DbProviderFactory` en appelant <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. La méthode <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> crée ensuite l'objet <xref:System.Data.Common.DbConnection> et la propriété <xref:System.Data.Common.DbConnection.ConnectionString%2A> prend la valeur de la chaîne de connexion.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [DbProviderFactories](dbproviderfactories.md)
- [Chaînes de connexion](connection-strings.md)
- [Utilisation des classes de configuration](/previous-versions/aspnet/ms228063(v=vs.100))
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
