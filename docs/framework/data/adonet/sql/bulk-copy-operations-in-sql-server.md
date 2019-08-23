---
title: Opérations de copie en bloc dans SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: efa13eb1633fce3b59040ef8da79dba0f6ea81d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918063"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Opérations de copie en bloc dans SQL Server
Microsoft SQL Server comprend un utilitaire de ligne de commande populaire nommé **BCP** pour la copie en bloc rapide de fichiers volumineux dans des tables ou des vues dans des bases de données SQL Server. La classe <xref:System.Data.SqlClient.SqlBulkCopy> vous permet d'écrire des solutions de code managé qui offrent une fonctionnalité similaire. Il existe d'autres manières de charger des données dans une table SQL Server (par exemple, des instructions INSERT) mais <xref:System.Data.SqlClient.SqlBulkCopy> présente un avantage sensible sur le plan des performances.  
  
 La classe <xref:System.Data.SqlClient.SqlBulkCopy> permet d'écrire des données uniquement dans des tables SQL Server. Toutefois, la source de données n'est pas limitée à SQL Server ; n'importe quelle source de données peut être utilisée, pour autant que les données puissent être chargées dans une instance de <xref:System.Data.DataTable> ou lues avec une instance de <xref:System.Data.IDataReader>.  
  
 La classe <xref:System.Data.SqlClient.SqlBulkCopy> vous permet d'effectuer :  
  
- une opération unique de copie en bloc ;  
  
- plusieurs opérations de copie en bloc ;  
  
- une opération de copie en bloc à l'intérieur d'une transaction.  
  
> [!NOTE]
> Lorsque vous utilisez .NET Framework version 1,1 ou antérieure (qui ne prend pas <xref:System.Data.SqlClient.SqlBulkCopy> en charge la classe), vous pouvez exécuter l’instruction SQL Server Transact-SQL <xref:System.Data.SqlClient.SqlCommand> **Bulk Insert** à l’aide de l’objet.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemple de configuration de copie en bloc](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Décrit les tables utilisées dans les exemples de copie en bloc et fournit des scripts SQL pour créer les tables dans la base de données AdventureWorks.  
  
 [Opérations uniques de copie en bloc](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Décrit comment effectuer une copie en bloc unique de données dans une instance de SQL Server à l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy> et comment effectuer l'opération de copie en bloc à l'aide d'instructions Transact-SQL et de la classe <xref:System.Data.SqlClient.SqlCommand>.  
  
 [Plusieurs opérations de copie en bloc](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Décrit comment effectuer plusieurs opérations de copie en bloc de données dans une instance de SQL Server à l'aide de la classe <xref:System.Data.SqlClient.SqlBulkCopy>.  
  
 [Transaction et opérations de copie en bloc](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Décrit comment effectuer une opération de copie en bloc à l'intérieur d'une transaction, y compris comment valider ou annuler la transaction.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
