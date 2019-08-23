---
title: Transactions et accès simultané
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c78031150d9b1209372dece49813dfcf0a03b9d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965210"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="1182b-102">Transactions et accès simultané</span><span class="sxs-lookup"><span data-stu-id="1182b-102">Transactions and Concurrency</span></span>
<span data-ttu-id="1182b-103">Une transaction est composée d’une seule commande ou d’un groupe de commandes qui s’exécutent sous forme de package.</span><span class="sxs-lookup"><span data-stu-id="1182b-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="1182b-104">Les transactions vous permettent de combiner plusieurs opérations en une seule unité de travail.</span><span class="sxs-lookup"><span data-stu-id="1182b-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="1182b-105">Si une panne se produit pendant la transaction, toutes les mises à jour sont ramenées dans l’état qui était le leur avant le début de la transaction.</span><span class="sxs-lookup"><span data-stu-id="1182b-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="1182b-106">Une transaction doit être conforme aux propriétés ACID (atomicité, cohérence, isolation et durabilité) afin de garantir la cohérence des données.</span><span class="sxs-lookup"><span data-stu-id="1182b-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="1182b-107">La plupart des systèmes de bases de données relationnelles, tels que Microsoft SQL Server, prennent en charge des transactions en offrant des fonctionnalités de verrouillage, de journalisation et de gestion des transactions lorsqu’une application cliente exécute une opération de mise à jour, d’insertion ou de suppression.</span><span class="sxs-lookup"><span data-stu-id="1182b-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1182b-108">Les transactions impliquant plusieurs ressources peuvent réduire l'accès concurrentiel si des verrous sont conservés trop longtemps.</span><span class="sxs-lookup"><span data-stu-id="1182b-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="1182b-109">Par conséquent, réduisez autant que possible les transactions.</span><span class="sxs-lookup"><span data-stu-id="1182b-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="1182b-110">Si une transaction implique plusieurs tables dans la même base de données ou le même serveur, des transactions explicites dans des procédures stockées fonctionnent souvent mieux.</span><span class="sxs-lookup"><span data-stu-id="1182b-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="1182b-111">Vous pouvez créer des transactions dans des procédures stockées SQL Server à l'aide des instructions Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION` et `ROLLBACK TRANSACTION`.</span><span class="sxs-lookup"><span data-stu-id="1182b-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="1182b-112">Pour plus d'informations, voir la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1182b-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="1182b-113">Les transactions impliquant différents gestionnaires de ressources, telles qu’une transaction entre SQL Server et Oracle, requièrent une transaction distribuée.</span><span class="sxs-lookup"><span data-stu-id="1182b-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1182b-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1182b-114">In This Section</span></span>  
 [<span data-ttu-id="1182b-115">Transactions locales</span><span class="sxs-lookup"><span data-stu-id="1182b-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="1182b-116">Montre comment effectuer des transactions sur une base de données.</span><span class="sxs-lookup"><span data-stu-id="1182b-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="1182b-117">Transactions distribuées</span><span class="sxs-lookup"><span data-stu-id="1182b-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="1182b-118">Décrit comment effectuer des transactions distribuées dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1182b-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="1182b-119">Intégration de System.Transactions à SQL Server</span><span class="sxs-lookup"><span data-stu-id="1182b-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="1182b-120">Décrit <xref:System.Transactions> l’intégration avec SQL Server pour l’utilisation de transactions distribuées.</span><span class="sxs-lookup"><span data-stu-id="1182b-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="1182b-121">Accès concurrentiel optimiste</span><span class="sxs-lookup"><span data-stu-id="1182b-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="1182b-122">Décrit les accès concurrentiels optimiste et pessimiste et la manière de tester les violations d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="1182b-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1182b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1182b-123">See also</span></span>

- [<span data-ttu-id="1182b-124">Notions de base des transactions</span><span class="sxs-lookup"><span data-stu-id="1182b-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [<span data-ttu-id="1182b-125">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="1182b-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="1182b-126">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="1182b-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="1182b-127">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="1182b-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="1182b-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="1182b-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="1182b-129">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="1182b-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
