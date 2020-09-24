---
title: Modification des données avec les procédures stockées
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 65116a48533fd6ce86894c6a4522929285f8e1f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150750"
---
# <a name="modifying-data-with-stored-procedures"></a>Modification des données avec les procédures stockées

Les procédures stockées peuvent accepter des données en tant que paramètres d'entrée et retourner des données en tant que paramètres de sortie, jeux de résultats et valeurs de retour. L'exemple ci-dessous montre comment ADO.NET envoie et reçoit des paramètres d'entrée, des paramètres de sortie et des valeurs de retour. L'exemple insère un nouvel enregistrement dans une table où la colonne de clé primaire est une colonne d'identité dans une base de données SQL Server.  
  
> [!NOTE]
> Si vous utilisez des procédures stockées SQL Server pour modifier ou supprimer des données à l'aide de <xref:System.Data.SqlClient.SqlDataAdapter>, assurez-vous que vous n'utilisez pas SET NOCOUNT ON dans la définition de procédure stockée. En effet, le nombre de lignes affectées retourné serait alors la valeur zéro, ce que `DataAdapter` interprète comme un conflit d'accès concurrentiel. Dans ce cas, l'exception <xref:System.Data.DBConcurrencyException> est levée.  
  
## <a name="example"></a>Exemple  

 L’exemple utilise la procédure stockée suivante pour insérer une nouvelle catégorie dans la table des **catégories** **Northwind** . La procédure stockée prend la valeur dans la colonne **CategoryName** comme paramètre d’entrée et utilise la fonction SCOPE_IDENTITY () pour récupérer la nouvelle valeur du champ Identity, **CategoryID**, et la renvoyer dans un paramètre OUTPUT. L’instruction return utilise la @ROWCOUNT fonction @ pour retourner le nombre de lignes insérées.  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 L'exemple de code suivant utilise la procédure stockée `InsertCategory` présentée ci-dessus comme source pour <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> de <xref:System.Data.SqlClient.SqlDataAdapter>. Le paramètre de sortie `@Identity` se reflète dans <xref:System.Data.DataSet> après que l'enregistrement a été inséré dans la base de données lors de l'appel de la méthode `Update` de <xref:System.Data.SqlClient.SqlDataAdapter>. Le code récupère également la valeur de retour.  
  
> [!NOTE]
> Lorsque vous utilisez <xref:System.Data.OleDb.OleDbDataAdapter> , vous devez spécifier des paramètres avec un <xref:System.Data.ParameterDirection> de **returnValue** avant les autres paramètres.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Exécution d’une commande](executing-a-command.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
