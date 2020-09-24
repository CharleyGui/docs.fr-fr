---
title: Transactions distribuées
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: b6553d50039ca0f4888f0610b187c6b419a462b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153195"
---
# <a name="distributed-transactions"></a>Transactions distribuées

Une transaction est un ensemble de tâches liées entre elles qui échouent (abort) ou réussissent (commit) globalement, entre autres choses. Une *transaction distribuée* est une transaction qui affecte plusieurs ressources. Pour qu’une transaction distribuée soit validée, l’ensemble des participants doivent garantir que tout changement apporté aux données sera permanent. Ces modifications doivent persister même en cas de panne du système ou de tout autre événement imprévu. Il suffit qu’un seul des participants n’apporte pas cette garantie pour que l’ensemble de la transaction échoue et toutes les modifications apportées aux données dans le cadre de la transaction sont annulées.  
  
> [!NOTE]
> Une exception est levée lorsque vous tentez de valider ou d’annuler une transaction si `DataReader` démarre pendant que la transaction est active.  
  
## <a name="working-with-systemtransactions"></a>Utilisation de System.Transactions  

 Dans .NET Framework, les transactions distribuées sont gérées via l’API dans l’espace de noms <xref:System.Transactions>. L’API <xref:System.Transactions> délègue la gestion de transaction distribuée à un moniteur de transaction tel que le Microsoft Distributed Transaction Coordinator (MS DTC) lorsque plusieurs gestionnaires de ressources persistants sont impliqués. Pour plus d’informations, consultez [principes de base des transactions](../transactions/transaction-fundamentals.md).  
  
 ADO.NET 2.0 a introduit la prise en charge de l’inscription dans une transaction distribuée à l’aide de la méthode `EnlistTransaction`, qui inscrit une connexion dans une instance <xref:System.Transactions.Transaction>. Dans les versions précédentes d’ADO.NET, l’inscription explicite dans des transactions distribuées était effectuée à l’aide de la méthode `EnlistDistributedTransaction` d’une connexion afin d’inscrire une connexion dans une instance de l’objet <xref:System.EnterpriseServices.ITransaction>, qui est prise en charge à des fins de compatibilité ascendante. Pour plus d’informations sur les transactions Enterprise Services, consultez [interopérabilité avec Enterprise Services et les transactions com+](../transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Lors de l’utilisation d’une transaction <xref:System.Transactions> avec le fournisseur .NET Framework pour SQL Server en relation avec une base de données SQL Server, un <xref:System.Transactions.Transaction> léger est automatiquement utilisé. La transaction peut être promue en transaction totalement distribuée en fonction des besoins. Pour plus d’informations, consultez [intégration de System. transactions à SQL Server](system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
> Le nombre maximal de transactions distribuées auxquelles une base de données Oracle peut participer à un moment donné a la valeur 10 par défaut. Après la 10e transaction lors d'une connexion à une base de données Oracle, une exception est levée. Oracle ne prend pas en charge `DDL` à l’intérieur d’une transaction distribuée.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Inscription automatique dans une transaction distribuée  

 L'inscription automatique est la méthode par défaut (et conseillée) pour intégrer des connexions ADO.NET avec `System.Transactions`. Un objet Connection est automatiquement inscrit dans une transaction distribuée existante s’il détermine qu’une transaction est active, ce qui, pour `System.Transaction`, signifie que `Transaction.Current` n’a pas la valeur null. Une inscription de transaction automatique se produit lors de l’ouverture de la connexion. Elle ne se produit pas ensuite, même si une commande est exécutée dans le cadre d’une transaction. Vous pouvez désactiver l'inscription automatique dans des transactions existantes en spécifiant `Enlist=false` comme paramètre de chaîne de connexion pour un <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> ou `OLE DB Services=-7` comme paramètre de chaîne de connexion pour un <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Pour plus d'informations sur les paramètres de chaîne de connexion Oracle et ODBC, voir <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> et <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Inscription manuelle dans une transaction distribuée  

 Si l'inscription automatique est désactivée ou si vous devez inscrire une transaction qui a été démarrée après l'ouverture de la connexion, vous pouvez l'inscrire dans une transaction distribuée existante en utilisant la méthode `EnlistTransaction` de l'objet <xref:System.Data.Common.DbConnection> pour le fournisseur avec lequel vous travaillez. L'inscription dans une transaction distribuée existante garantit que si la transaction vient à être annulée ou validée, les modifications apportées par le code dans la source de données seront elles aussi validées ou annulées.  
  
 L’inscription dans des transactions distribuées s’applique en particulier lors du regroupement d’objets métier. Si un objet métier est regroupé avec une connexion ouverte, l'inscription automatique dans la transaction se produit uniquement lorsque cette connexion est ouverte. Si plusieurs transactions sont effectuées à l’aide de l’objet métier regroupé, la connexion ouverte pour cet objet n’est pas automatiquement inscrite dans les nouvelles transactions lancées. Dans ce cas, vous pouvez désactiver l'inscription de transaction automatique pour la connexion et inscrire la connexion dans des transactions à l'aide de `EnlistTransaction`.  
  
 `EnlistTransaction` accepte un argument unique de type <xref:System.Transactions.Transaction> qui est une référence à la transaction existante. Après avoir appelé la méthode `EnlistTransaction` de la connexion, toutes les modifications apportées à la source de données à l’aide de la connexion sont incluses dans la transaction. Le fait de passer une valeur null désinscrit la connexion de l’inscription de transaction distribuée actuelle. Notez que la connexion doit être ouverte avant l'appel de `EnlistTransaction`.  
  
> [!NOTE]
> Une fois qu’une connexion est explicitement inscrite sur une transaction, il n’est plus possible de la désinscrire ou de l’inscrire dans une autre transaction tant que la première transaction n’est pas terminée.  
  
> [!CAUTION]
> `EnlistTransaction` lève une exception si la connexion a déjà entamé une transaction à l'aide de la méthode <xref:System.Data.Common.DbConnection.BeginTransaction%2A> de la connexion. Toutefois, si la transaction est une transaction locale démarrée dans la source de données (par exemple, l'exécution explicite de l'instruction BEGIN TRANSACTION à l'aide d'un <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` annule la transaction locale et s'inscrit dans la transaction distribuée existante comme requis. Vous ne recevrez pas de notification indiquant que la transaction locale a été annulée et que vous devez gérer les transactions locales non lancées à l’aide de <xref:System.Data.Common.DbConnection.BeginTransaction%2A>. Si vous utilisez le fournisseur de données .NET Framework pour SQL Server (`SqlClient`) avec SQL Server, toute tentative d'inscription lève une exception. Les autres cas ne sont pas détectés.  
  
## <a name="promotable-transactions-in-sql-server"></a>Transactions pouvant être promues dans SQL Server  

 SQL Server prend en charge les transactions pouvant être promues dans lesquelles une transaction légère locale peut être automatiquement promue en transaction distribuée uniquement si c’est requis. Une transaction pouvant être promue n'invoque pas la charge supplémentaire d'une transaction distribuée à moins qu'elle ne soit requise. Pour plus d’informations et pour obtenir un exemple de code, consultez [intégration de System. transactions avec SQL Server](system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Configuration de transactions distribuées  

 Vous devrez peut-être activer MS DTC sur le réseau afin d'utiliser des transactions distribuées. Si le Pare-feu Windows est activé, vous devez autoriser le service MS DTC à utiliser le réseau ou à ouvrir le port MS DTC.  
  
## <a name="see-also"></a>Voir aussi

- [Transactions et accès simultané](transactions-and-concurrency.md)
- [Intégration de System.Transactions à SQL Server](system-transactions-integration-with-sql-server.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
