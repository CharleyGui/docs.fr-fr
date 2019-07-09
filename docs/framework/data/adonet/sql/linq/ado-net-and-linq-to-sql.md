---
title: ADO.NET et LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 6a6e057b45c1305a889ce4ed915b437a29ab2794
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662065"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET et LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fait partie de la famille ADO.NET de technologies. Il est basé sur les services fournis par le modèle de fournisseur ADO.NET. Vous pouvez donc combiner [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de code avec les applications ADO.NET existantes et migrer des solutions ADO.NET actuelles à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. L'illustration suivante fournit une vue d'ensemble de la relation.  
  
 ![LINQ to SQL et ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Connexions  
 Vous pouvez fournir une connexion ADO.NET existante lorsque vous créez un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Toutes les opérations sur les <xref:System.Data.Linq.DataContext> (y compris les requêtes) vous pouvez utiliser de connexion fournie. Si la connexion est déjà ouverte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ferme comme lorsque vous avez terminé avec lui.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Vous pouvez toujours accéder à la connexion et la fermer à l'aide de la propriété <xref:System.Data.Linq.DataContext.Connection%2A>, comme dans le code suivant :  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transactions  
 Vous pouvez fournir à votre <xref:System.Data.Linq.DataContext> votre propre transaction de base de données lorsque votre application a déjà initialisé la transaction et que vous souhaitez impliquer votre <xref:System.Data.Linq.DataContext>.  
  
 La méthode préférée de transactions avec le .NET Framework consiste à utiliser le <xref:System.Transactions.TransactionScope> objet. Grâce à cette approche, vous pouvez effectuer des transactions distribuées qui fonctionnent sur les bases de données et d'autres gestionnaires de ressources résidant en mémoire. Les portées de transactions requièrent des ressources pour démarrer. Elles effectuent leur propre promotion en transactions distribuées uniquement lorsque la portée de la transaction comporte plusieurs connexions.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Vous ne pouvez pas utiliser cette approche pour toutes les bases de données. Par exemple, la connexion SqlClient ne peut pas promouvoir des transactions système lorsqu’elle fonctionne sur un serveur SQL Server 2000. Elle s’inscrit automatiquement à une transaction distribuée complète à chaque fois qu’elle voit qu’une portée de transaction est utilisée.  
  
## <a name="direct-sql-commands"></a>Commandes SQL directes  
 Il peut arriver que la capacité du <xref:System.Data.Linq.DataContext> en termes d'interrogation ou de soumission de modifications soit insuffisante pour la tâche spécialisée que vous souhaitez effectuer. Dans ce cas, vous pouvez utiliser la méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> pour transmettre des commandes SQL à la base de données et convertir les résultats de la requête en objets.  
  
 Par exemple, supposons que les données de la classe `Customer` sont réparties sur deux tables (customer1 et customer2). La requête suivante retourne une séquence d'objets `Customer` :  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tant que les noms de colonne dans les résultats sous forme de tableau correspondent aux propriétés des colonnes de votre classe d’entité, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée vos objets à partir de n’importe quelle requête SQL.  
  
### <a name="parameters"></a>Paramètres  
 La méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> accepte les paramètres. Le code suivant exécute une requête paramétrée :  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Les paramètres sont exprimés dans le texte de requête en utilisant la même notation avec accolades utilisée par `Console.WriteLine()` et `String.Format()`. `String.Format()` utilise la chaîne de requête fournie et substitue les paramètres entre accolades par des noms de paramètre générés tels que `@p0`, `@p1` …, `@p(n)`.  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Guide pratique pour Réutiliser une connexion entre une commande ADO.NET et un DataContext](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
