---
title: ADO.NET et LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 0bebc8d890325ec4ab090470952e11b90d0e37ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248121"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET et LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]fait partie de la famille de technologies ADO.NET. Il est basé sur les services fournis par le modèle de fournisseur ADO.NET. Vous pouvez donc mélanger [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] du code avec des applications ADO.NET existantes et migrer les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]solutions ADO.net actuelles vers. L'illustration suivante fournit une vue d'ensemble de la relation.  
  
 ![LINQ to SQL et ADO.net](./media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>connexions  
 Vous pouvez fournir une connexion ADO.NET existante lorsque vous créez un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Data.Linq.DataContext> Toutes les opérations sur <xref:System.Data.Linq.DataContext> (y compris les requêtes) utilisent cette connexion fournie. Si la connexion est déjà ouverte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] conserve-la lorsque vous n’en avez plus besoin.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Vous pouvez toujours accéder à la connexion et la fermer à l'aide de la propriété <xref:System.Data.Linq.DataContext.Connection%2A>, comme dans le code suivant :  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transactions  
 Vous pouvez fournir à votre <xref:System.Data.Linq.DataContext> votre propre transaction de base de données lorsque votre application a déjà initialisé la transaction et que vous souhaitez impliquer votre <xref:System.Data.Linq.DataContext>.  
  
 La méthode recommandée pour effectuer des transactions avec le .NET Framework consiste à utiliser <xref:System.Transactions.TransactionScope> l’objet. Grâce à cette approche, vous pouvez effectuer des transactions distribuées qui fonctionnent sur les bases de données et d'autres gestionnaires de ressources résidant en mémoire. Les portées de transactions requièrent des ressources pour démarrer. Elles effectuent leur propre promotion en transactions distribuées uniquement lorsque la portée de la transaction comporte plusieurs connexions.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Vous ne pouvez pas utiliser cette approche pour toutes les bases de données. Par exemple, la connexion SqlClient ne peut pas promouvoir les transactions système lorsqu’elle fonctionne sur un serveur SQL Server 2000. Elle s’inscrit automatiquement à une transaction distribuée complète à chaque fois qu’elle voit qu’une portée de transaction est utilisée.  
  
## <a name="direct-sql-commands"></a>Commandes SQL directes  
 Il peut arriver que la capacité du <xref:System.Data.Linq.DataContext> en termes d'interrogation ou de soumission de modifications soit insuffisante pour la tâche spécialisée que vous souhaitez effectuer. Dans ce cas, vous pouvez utiliser la méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> pour transmettre des commandes SQL à la base de données et convertir les résultats de la requête en objets.  
  
 Par exemple, supposons que les données de la classe `Customer` sont réparties sur deux tables (customer1 et customer2). La requête suivante retourne une séquence d'objets `Customer` :  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tant que les noms des colonnes dans les résultats tabulaires correspondent aux propriétés des colonnes de votre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] classe d’entité, crée vos objets à partir d’une requête SQL.  
  
### <a name="parameters"></a>Paramètres  
 La méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> accepte les paramètres. Le code suivant exécute une requête paramétrée :  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Les paramètres sont exprimés dans le texte de requête en utilisant la même notation avec accolades utilisée par `Console.WriteLine()` et `String.Format()`. `String.Format()` utilise la chaîne de requête fournie et substitue les paramètres entre accolades par des noms de paramètre générés tels que `@p0`, `@p1` …, `@p(n)`.  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
- [Guide pratique : Réutiliser une connexion entre une commande ADO.NET et un DataContext](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
