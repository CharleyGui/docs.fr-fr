---
title: DbConnection, DbCommand et DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 3075999c15fccc3a41c191297a146c362b3638e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183323"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand et DbException

Une fois que vous avez créé un <xref:System.Data.Common.DbProviderFactory> et un <xref:System.Data.Common.DbConnection>, vous pouvez utiliser des commandes et des lecteurs de données pour extraire des données de la source de données.  
  
## <a name="retrieving-data-example"></a>Exemple d'extraction de données  

 Cet exemple utilise un objet `DbConnection` comme argument. Un <xref:System.Data.Common.DbCommand> est créé pour sélectionner des données à partir de la table Categories en spécifiant le <xref:System.Data.Common.DbCommand.CommandText%2A> pour une instruction SQL SELECT. Le code suppose que la table Categories existe au niveau de la source de données. La connexion est ouverte et les données sont extraites à l'aide d'un <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Exemple d'exécution d'une commande  

 Cet exemple utilise un objet `DbConnection` comme argument. Si le `DbConnection` est valide, la connexion est ouverte et un <xref:System.Data.Common.DbCommand> est créé et exécuté. Le <xref:System.Data.Common.DbCommand.CommandText%2A> est spécifié pour une instruction SQL INSERT, qui effectue une insertion dans la table Categories, dans la base de données Northwind. Le code suppose que la base de données Northwind existe au niveau de la source de données et que la syntaxe SQL utilisée dans l'instruction INSERT est valide pour le fournisseur spécifié. Les erreurs qui se produisent au niveau de la source de données sont traitées par le bloc de code <xref:System.Data.Common.DbException> et toutes les autres exceptions sont traitées dans le bloc <xref:System.Exception>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Gestion des erreurs de données avec DbException  

 La classe <xref:System.Data.Common.DbException> correspond à la classe de base pour toutes les exceptions levées pour le compte d'une source de données. Vous pouvez l'utiliser dans votre code de gestion des exceptions pour gérer les exceptions levées par des fournisseurs différents sans avoir à référencer une classe d'exception spécifique. Le fragment de code ci-dessous montre comment utiliser <xref:System.Data.Common.DbException> pour afficher les informations relatives aux erreurs retournées par la source de données à l'aide des propriétés <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> et <xref:System.Exception.Message%2A>. La sortie indiquera le type d'erreur, la source indiquant le nom du fournisseur, un code d'erreur et le message associé à l'erreur.  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [DbProviderFactories](dbproviderfactories.md)
- [Obtention d'un DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [Modification des données avec un DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
