---
title: Modification des données avec un DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 5272a53ae0b3ac1888d01dc2a59778c6c7231619
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150763"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Modification des données avec un DbDataAdapter

La méthode <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> d'un objet <xref:System.Data.Common.DbProviderFactory> produit un objet <xref:System.Data.Common.DbDataAdapter> fortement typé pour le fournisseur de données sous-jacent spécifié lors de la création de la fabrique. Vous pouvez ensuite utiliser un objet <xref:System.Data.Common.DbCommandBuilder> pour créer des commandes permettant d'insérer, de mettre à jour et de supprimer des données d'un <xref:System.Data.DataSet> dans une source de données.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Extraction de données à l'aide d'un DbDataAdapter  

 Cet exemple montre comment créer un `DbDataAdapter` fortement typé reposant sur un nom de fournisseur et une chaîne de connexion. Le code utilise la méthode <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> de l'objet <xref:System.Data.Common.DbProviderFactory> pour créer un <xref:System.Data.Common.DbConnection>. Ensuite, le code utilise la méthode <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> pour créer un <xref:System.Data.Common.DbCommand> afin de sélectionner des données en définissant ses propriétés `CommandText` et `Connection`. Enfin, le code crée un objet <xref:System.Data.Common.DbDataAdapter> à l'aide de la méthode <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> et définit sa propriété `SelectCommand`. La méthode `Fill` du `DbDataAdapter` charge les données dans un <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Modification des données avec un DbDataAdapter  

 Cet exemple montre comment modifier des données dans un `DataTable` à l'aide d'un <xref:System.Data.Common.DbDataAdapter> en utilisant un <xref:System.Data.Common.DbCommandBuilder> pour générer les commandes requises pour la mise à jour des données au niveau de la source de données. La propriété <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> du `DbDataAdapter` est définie de manière à récupérer le CustomerID et le CompanyName dans la table Customers. La méthode <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> est utilisée pour définir la propriété <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, la méthode <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> est utilisée pour définir la propriété <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> et la méthode <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> est utilisée pour définir la propriété <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A>. Le code ajoute une nouvelle ligne à la table Customers et met à jour la source de données. Il localise ensuite la ligne ajoutée en recherchant le CustomerID, qui est la clé primaire définie pour la table Customers. Il modifie le CompanyName et met à jour la source de données. Enfin, le code supprime la ligne.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Gestion des paramètres  

 Les fournisseurs de données .NET Framework gèrent différemment la dénomination et la spécification des paramètres et des espaces réservés de paramètres. Cette syntaxe est adaptée à une source de données spécifique, comme cela est décrit dans le tableau ci-dessous.  
  
|Fournisseur de données|Syntaxe d'attribution de noms aux paramètres|  
|-------------------|-----------------------------|  
|`SqlClient`|Utilise des paramètres nommés au format `@`*nom_paramètre*.|  
|`OracleClient`|Utilise des paramètres nommés au format `:`*nom_paramètre* (ou *nom_paramètre*).|  
|`OleDb`|Utilise des marqueurs de paramètres positionnels indiqués par un point d'interrogation (`?`).|  
|`Odbc`|Utilise des marqueurs de paramètres positionnels indiqués par un point d'interrogation (`?`).|  
  
 Le modèle Factory n'est pas utile pour créer des objets `DbCommand` et `DbDataAdapter` paramétrés. Vous devrez créer une branche dans votre code pour créer des paramètres qui sont adaptés à votre fournisseur de données.  
  
> [!IMPORTANT]
> Le fait d'éviter tous les paramètres spécifiques au fournisseur en utilisant la concaténation de chaînes pour construire des instructions SQL directes n'est pas recommandé pour des raisons de sécurité. L'utilisation de la concaténation de chaînes au lieu de paramètres rend votre application vulnérable aux attaques par injection de code SQL.  
  
## <a name="see-also"></a>Voir aussi

- [DbProviderFactories](dbproviderfactories.md)
- [Obtention d'un DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand et DbException](dbconnection-dbcommand-and-dbexception.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
