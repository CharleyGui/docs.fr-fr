---
title: Transactions locales
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: a0b713ab0b81cb2f0661212dae22db34b7f9f3ae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175393"
---
# <a name="local-transactions"></a>Transactions locales

Les transactions dans ADO.NET sont utilisées lorsque vous souhaitez lier plusieurs tâches ensemble afin qu’elles s’exécutent comme une seule unité de travail. Par exemple, imaginez qu'une application effectue deux tâches. Premièrement, elle met à jour une table avec des informations de commande. Deuxièmement, elle met à jour une table qui contient des informations de stock, en débitant les articles commandés. Si l’une des tâches échoue, les deux mises à jour sont annulées.  
  
## <a name="determining-the-transaction-type"></a>Détermination du type de transaction  

 Une transaction est considérée comme une transaction locale lorsqu’il s’agit d’une transaction en une seule phase et qu’elle est gérée directement par la base de données. Une transaction est considérée comme une transaction distribuée lorsqu’elle est coordonnée par un moniteur de transaction et utilise des mécanismes de prévention de défaillance (tels qu’une validation en deux phases) pour la résolution des transactions.  
  
 Chaque fournisseur de données .NET Framework possède son propre `Transaction` objet pour effectuer des transactions locales. Si vous avez besoin qu’une transaction soit effectuée dans une base de données SQL Server, sélectionnez une transaction <xref:System.Data.SqlClient>. Pour une transaction Oracle, utilisez le fournisseur <xref:System.Data.OracleClient>. En outre, il existe une <xref:System.Data.Common.DbTransaction> classe qui est disponible pour écrire du code indépendant du fournisseur qui requiert des transactions.  
  
> [!NOTE]
> Les transactions sont plus efficaces lorsqu’elles sont exécutées sur le serveur. Si vous utilisez une base de données SQL Server qui utilise beaucoup des transactions explicites, envisagez de les écrire sous la forme de procédures stockées à l’aide de l’instruction Transact-SQL BEGIN TRANSACTION.
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Exécution d’une transaction à l’aide d’une connexion unique  

 Dans ADO.NET, vous contrôlez les transactions avec l' `Connection` objet. Vous pouvez initier une transaction locale avec la méthode `BeginTransaction`. Après avoir commencé une transaction, vous pouvez inscrire une commande dans cette transaction avec la propriété `Transaction` d’un objet `Command`. Vous pouvez ensuite valider ou annuler les modifications apportées à la source de données en fonction de la réussite ou de l’échec des composants de la transaction.  
  
> [!NOTE]
> La méthode `EnlistDistributedTransaction` ne doit pas être utilisée pour une transaction locale.  
  
 La portée de la transaction est limitée à la connexion. L’exemple suivant exécute une transaction explicite consistant en deux commandes distinctes dans le bloc `try`. Les commandes exécutent des instructions INSERT sur la table production. ScrapReason de l’exemple de base de données AdventureWorks SQL Server, qui sont validées si aucune exception n’est levée. Le code dans le bloc `catch` annule la transaction en cas d'exception. En cas d'annulation de la transaction ou de fermeture de la connexion avant que la transaction ne soit terminée, celle-ci est automatiquement annulée.  
  
## <a name="example"></a>Exemple  

 Procédez comme suit pour effectuer une transaction.  
  
1. Appelez la méthode <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> de l’objet <xref:System.Data.SqlClient.SqlConnection> pour marquer le début de la transaction. La méthode <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> retourne une référence à la transaction. Cette référence est affectée aux objets <xref:System.Data.SqlClient.SqlCommand> inscrits dans la transaction.  
  
2. Assignez l'objet `Transaction` à la propriété <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> de l'objet <xref:System.Data.SqlClient.SqlCommand> à exécuter. Si une commande est exécutée sur une connexion sur laquelle une transaction est active et si l’objet `Transaction` n’a pas été affecté à la propriété `Transaction` de l’objet `Command`, une exception est levée.  
  
3. Exécutez les commandes requises.  
  
4. Appelez la méthode <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> de l'objet <xref:System.Data.SqlClient.SqlTransaction> pour effectuer la transaction ou la méthode <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> pour y mettre fin. Si la connexion est fermée ou libérée avant que l’une des méthodes <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> ou <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> ait été exécutée, la transaction est annulée.  
  
 L’exemple de code suivant illustre la logique transactionnelle à l’aide de ADO.NET avec Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Transactions et accès simultané](transactions-and-concurrency.md)
- [Transactions distribuées](distributed-transactions.md)
- [Intégration de System.Transactions à SQL Server](system-transactions-integration-with-sql-server.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
