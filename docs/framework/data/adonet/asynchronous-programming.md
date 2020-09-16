---
title: Programmation asynchrone
description: En savoir plus sur la programmation asynchrone dans le Fournisseur de données .NET Framework pour SQL Server, y compris les améliorations introduites dans .NET Framework 4,5.
ms.date: 10/18/2018
ms.assetid: 85da7447-7125-426e-aa5f-438a290d1f77
ms.openlocfilehash: b8f718e0def2ab0b6953ed121eb916f282562d32
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558470"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="a4fe6-103">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="a4fe6-103">Asynchronous Programming</span></span>

<span data-ttu-id="a4fe6-104">Cette rubrique décrit la prise en charge de la programmation asynchrone dans le .NET Framework Fournisseur de données pour SQL Server (SqlClient), y compris les améliorations apportées à la prise en charge des fonctionnalités de programmation asynchrone introduites dans .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-104">This topic discusses support for asynchronous programming in the .NET Framework Data Provider for SQL Server (SqlClient) including enhancements made to support asynchronous programming functionality that was introduced in .NET Framework 4.5.</span></span>

## <a name="legacy-asynchronous-programming"></a><span data-ttu-id="a4fe6-105">Programmation asynchrone héritée</span><span class="sxs-lookup"><span data-stu-id="a4fe6-105">Legacy Asynchronous Programming</span></span>

<span data-ttu-id="a4fe6-106">Avant .NET Framework 4,5, la programmation asynchrone avec SqlClient était effectuée avec les méthodes et la `Asynchronous Processing=true` propriété de connexion suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4fe6-106">Prior to .NET Framework 4.5, asynchronous programming with SqlClient was done with the following methods and the `Asynchronous Processing=true` connection property:</span></span>

1. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A?displayProperty=nameWithType>

2. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A?displayProperty=nameWithType>

3. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A?displayProperty=nameWithType>

<span data-ttu-id="a4fe6-107">Cette fonctionnalité reste dans SqlClient dans .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-107">This functionality remains in SqlClient in .NET Framework 4.5.</span></span>

> [!TIP]
> <span data-ttu-id="a4fe6-108">À partir de la .NET Framework 4,5, ces méthodes héritées n’ont plus besoin `Asynchronous Processing=true` de la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-108">Beginning in the .NET Framework 4.5, these legacy methods no longer require `Asynchronous Processing=true` in the connection string.</span></span>

## <a name="asynchronous-programming-features-added-in-net-framework-45"></a><span data-ttu-id="a4fe6-109">Fonctionnalités de programmation asynchrone ajoutées à .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="a4fe6-109">Asynchronous Programming Features Added in .NET Framework 4.5</span></span>

<span data-ttu-id="a4fe6-110">La nouvelle fonctionnalité de programmation asynchrone fournit une technique simple pour rendre le code asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-110">The new asynchronous programming feature provides a simple technique to make code asynchronous.</span></span>

<span data-ttu-id="a4fe6-111">Pour plus d’informations sur la fonctionnalité de programmation asynchrone qui a été introduite dans .NET Framework 4,5, consultez :</span><span class="sxs-lookup"><span data-stu-id="a4fe6-111">For more information about the asynchronous programming feature that was introduced in .NET Framework 4.5, see:</span></span>

- [<span data-ttu-id="a4fe6-112">Programmation asynchrone en C#</span><span class="sxs-lookup"><span data-stu-id="a4fe6-112">Asynchronous programming in C#</span></span>](../../../csharp/async.md)

- [<span data-ttu-id="a4fe6-113">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4fe6-113">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)

- [<span data-ttu-id="a4fe6-114">Utilisation des nouvelles méthodes Async de SqlDataReader dans .NET 4,5 (partie 1)</span><span class="sxs-lookup"><span data-stu-id="a4fe6-114">Using SqlDataReader’s new async methods in .NET 4.5 (Part 1)</span></span>](/archive/blogs/adonet/using-sqldatareaders-new-async-methods-in-net-4-5)

- [<span data-ttu-id="a4fe6-115">Utilisation des nouvelles méthodes Async de SqlDataReader dans .NET 4,5 (partie 2)</span><span class="sxs-lookup"><span data-stu-id="a4fe6-115">Using SqlDataReader’s new async methods in .NET 4.5 (Part 2)</span></span>](/archive/blogs/adonet/using-sqldatareaders-new-async-methods-in-net-4-5-part-2-examples)

<span data-ttu-id="a4fe6-116">Lorsque votre interface utilisateur ne répond pas ou votre serveur ne monte pas en charge, il est probable que vous votre code doit être plus asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-116">When your user interface is unresponsive or your server does not scale, it is likely that you need your code to be more asynchronous.</span></span> <span data-ttu-id="a4fe6-117">Écrire du code asynchrone implique en général l'installation d'un rappel (également appelé suite) pour exprimer la logique qui se produit après que l'opération asynchrone s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-117">Writing asynchronous code has traditionally involved installing a callback (also called continuation) to express the logic that occurs after the asynchronous operation finishes.</span></span> <span data-ttu-id="a4fe6-118">Cela complique la structure du code asynchrone par rapport au code synchrone.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-118">This complicates the structure of asynchronous code as compared with synchronous code.</span></span>

<span data-ttu-id="a4fe6-119">Vous pouvez maintenant appeler des méthodes asynchrones sans utiliser de rappels, et sans fractionner votre code entre plusieurs méthodes ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-119">You can now call into asynchronous methods without using callbacks, and without splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="a4fe6-120">Le modificateur `async` spécifie qu'une méthode est asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-120">The `async` modifier specifies that a method is asynchronous.</span></span> <span data-ttu-id="a4fe6-121">Lors de l’appel d’une méthode `async`, une tâche est retournée.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-121">When calling an `async` method, a task is returned.</span></span> <span data-ttu-id="a4fe6-122">Lorsque l' `await` opérateur est appliqué à une tâche, la méthode actuelle se termine immédiatement.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-122">When the `await` operator is applied to a task, the current method exits immediately.</span></span> <span data-ttu-id="a4fe6-123">Lorsque la tâche se termine, l’exécution reprend dans la même méthode.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-123">When the task finishes, execution resumes in the same method.</span></span>

> [!WARNING]
> <span data-ttu-id="a4fe6-124">Les appels asynchrones ne sont pas pris en charge si une application utilise également le mot clé de chaîne de connexion `Context Connection`.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-124">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>

<span data-ttu-id="a4fe6-125">L'appel d'une méthode `async` n'alloue aucun thread supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-125">Calling an `async` method does not allocate any additional threads.</span></span> <span data-ttu-id="a4fe6-126">Elle peut utiliser le thread de terminaison d'E/S existant brièvement à la fin.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-126">It may use the existing I/O completion thread briefly at the end.</span></span>

<span data-ttu-id="a4fe6-127">Les méthodes suivantes ont été ajoutées dans .NET Framework 4,5 pour prendre en charge la programmation asynchrone :</span><span class="sxs-lookup"><span data-stu-id="a4fe6-127">The following methods were added in .NET Framework 4.5 to support asynchronous programming:</span></span>

- <xref:System.Data.Common.DbConnection.OpenAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteDbDataReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbDataReader.GetFieldValueAsync%2A>

- <xref:System.Data.Common.DbDataReader.IsDBNullAsync%2A>

- <xref:System.Data.Common.DbDataReader.NextResultAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbDataReader.ReadAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlConnection.OpenAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteXmlReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlDataReader.NextResultAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlDataReader.ReadAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>

 <span data-ttu-id="a4fe6-128">D’autres membres asynchrones ont été ajoutés pour prendre en charge la [prise en charge du streaming SqlClient](sqlclient-streaming-support.md).</span><span class="sxs-lookup"><span data-stu-id="a4fe6-128">Other asynchronous members were added to support [SqlClient Streaming Support](sqlclient-streaming-support.md).</span></span>

> [!TIP]
> <span data-ttu-id="a4fe6-129">Les nouvelles méthodes asynchrones ne requièrent pas `Asynchronous Processing=true` dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-129">The new asynchronous methods don't require `Asynchronous Processing=true` in the connection string.</span></span>

### <a name="synchronous-to-asynchronous-connection-open"></a><span data-ttu-id="a4fe6-130">Ouverture de connexion synchrone à asynchrone</span><span class="sxs-lookup"><span data-stu-id="a4fe6-130">Synchronous to Asynchronous Connection Open</span></span>

<span data-ttu-id="a4fe6-131">Vous pouvez mettre à niveau une application existante afin d’utiliser la nouvelle fonctionnalité asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-131">You can upgrade an existing application to use the new asynchronous feature.</span></span> <span data-ttu-id="a4fe6-132">Par exemple, supposons qu'une application possède un algorithme de connexion synchrone et bloque le thread d'interface utilisateur chaque fois qu'elle se connecte à la base de données et, une fois connectée, l'application appelle une procédure stockée qui signale d'autres utilisateurs que celui qui vient de se connecter.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-132">For example, assume an application has a synchronous connection algorithm and blocks the UI thread every time it connects to the database and, once connected, the application calls a stored procedure that signals other users of the one who just signed in.</span></span>

```csharp
using SqlConnection conn = new SqlConnection("…");
{
   conn.Open();
   using (SqlCommand cmd = new SqlCommand("StoredProcedure_Logon", conn))
   {
      cmd.ExecuteNonQuery();
   }
}
```

<span data-ttu-id="a4fe6-133">Une fois converti pour utiliser la nouvelle fonctionnalité asynchrone, le programme a l'apparence suivante :</span><span class="sxs-lookup"><span data-stu-id="a4fe6-133">When converted to use the new asynchronous functionality, the program would look like:</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;

class A {

   static async Task<int> Method(SqlConnection conn, SqlCommand cmd) {
      await conn.OpenAsync();
      await cmd.ExecuteNonQueryAsync();
      return 1;
   }

   public static void Main() {
      using (SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI")) {
         SqlCommand command = new SqlCommand("select top 2 * from orders", conn);

         int result = A.Method(conn, command).Result;

         SqlDataReader reader = command.ExecuteReader();
         while (reader.Read())
            Console.WriteLine(reader[0]);
      }
   }
}
```

### <a name="adding-the-new-asynchronous-feature-in-an-existing-application-mixing-old-and-new-patterns"></a><span data-ttu-id="a4fe6-134">Ajout des nouvelles fonctionnalités asynchrones dans une application existante (combinant les modèles anciens et nouveaux)</span><span class="sxs-lookup"><span data-stu-id="a4fe6-134">Adding the New Asynchronous Feature in an Existing Application (Mixing Old and New Patterns)</span></span>

<span data-ttu-id="a4fe6-135">Il est également possible d'ajouter la nouvelle fonction asynchrone (SqlConnection::OpenAsync) sans modifier la logique asynchrone existante.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-135">It is also possible to add new asynchronous capability (SqlConnection::OpenAsync) without changing the existing asynchronous logic.</span></span> <span data-ttu-id="a4fe6-136">Par exemple, si d'une application utilise actuellement :</span><span class="sxs-lookup"><span data-stu-id="a4fe6-136">For example, if an application currently uses:</span></span>

```csharp
AsyncCallback productList = new AsyncCallback(ProductList);
SqlConnection conn = new SqlConnection("…");
conn.Open();
SqlCommand cmd = new SqlCommand("SELECT * FROM [Current Product List]", conn);
IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);
```

<span data-ttu-id="a4fe6-137">Vous pouvez commencer à utiliser le nouveau modèle asynchrone sans modifier considérablement l'algorithme existant.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-137">You can begin to use the new asynchronous pattern without substantially changing the existing algorithm.</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;

class A {
   static void ProductList(IAsyncResult result) { }

   public static void Main() {
      // AsyncCallback productList = new AsyncCallback(ProductList);
      // SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");
      // conn.Open();
      // SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);
      // IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);

      AsyncCallback productList = new AsyncCallback(ProductList);
      SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");
      conn.OpenAsync().ContinueWith((task) => {
         SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);
         IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);
      }, TaskContinuationOptions.OnlyOnRanToCompletion);
   }
}
```

### <a name="using-the-base-provider-model-and-the-new-asynchronous-feature"></a><span data-ttu-id="a4fe6-138">Utilisation du modèle de fournisseur de base et de la nouvelle fonctionnalité asynchrone</span><span class="sxs-lookup"><span data-stu-id="a4fe6-138">Using the Base Provider Model and the New Asynchronous Feature</span></span>

<span data-ttu-id="a4fe6-139">Vous devrez peut-être créer un outil qui peut se connecter à différentes bases de données et exécuter des requêtes.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-139">You may need to create a tool that is able to connect to different databases and execute queries.</span></span> <span data-ttu-id="a4fe6-140">Vous pouvez utiliser le modèle de fournisseur de base et la nouvelle fonctionnalité asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-140">You can use the base provider model and the new asynchronous feature.</span></span>

<span data-ttu-id="a4fe6-141">Microsoft Distributed Transaction Controller (MSDTC) doit être activé sur le serveur pour utiliser des transactions distribuées.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-141">The Microsoft Distributed Transaction Controller (MSDTC) must be enabled on the server to use distributed transactions.</span></span> <span data-ttu-id="a4fe6-142">Pour plus d’informations sur la façon d’activer MSDTC, consultez [Comment activer MSDTC sur un serveur Web](/previous-versions/commerce-server/dd327979(v=cs.90)).</span><span class="sxs-lookup"><span data-stu-id="a4fe6-142">For information on how to enable MSDTC, see [How to Enable MSDTC on a Web Server](/previous-versions/commerce-server/dd327979(v=cs.90)).</span></span>

```csharp
using System;
using System.Data.Common;
using System.Data.SqlClient;
using System.Threading.Tasks;

class A {
   static async Task PerformDBOperationsUsingProviderModel(string connectionString, string providerName) {
      DbProviderFactory factory = DbProviderFactories.GetFactory(providerName);
      using (DbConnection connection = factory.CreateConnection()) {
         connection.ConnectionString = connectionString;
         await connection.OpenAsync();

         DbCommand command = connection.CreateCommand();
         command.CommandText = "SELECT * FROM AUTHORS";

         using (DbDataReader reader = await command.ExecuteReaderAsync()) {
            while (await reader.ReadAsync()) {
               for (int i = 0; i < reader.FieldCount; i++) {
                  // Process each column as appropriate
                  object obj = await reader.GetFieldValueAsync<object>(i);
                  Console.WriteLine(obj);
               }
            }
         }
      }
   }

   public static void Main()
   {
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();
       // replace these with your own values
       builder.DataSource = "your_server";
       builder.InitialCatalog = "pubs";
       builder.IntegratedSecurity = true;
       string provider = "System.Data.SqlClient";

       Task task = PerformDBOperationsUsingProviderModel(builder.ConnectionString, provider);
       task.Wait();
   }
}
```

### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="a4fe6-143">Utilisation de transactions SQL et de la nouvelle fonctionnalité asynchrone</span><span class="sxs-lookup"><span data-stu-id="a4fe6-143">Using SQL Transactions and the New Asynchronous Feature</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;

class Program {
   static void Main() {
      string connectionString =
          "Persist Security Info=False;Integrated Security=SSPI;database=Northwind;server=(local)";
      Task task = ExecuteSqlTransaction(connectionString);
      task.Wait();
   }

   static async Task ExecuteSqlTransaction(string connectionString) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         await connection.OpenAsync();

         SqlCommand command = connection.CreateCommand();
         SqlTransaction transaction = null;

         // Start a local transaction.
         transaction = await Task.Run<SqlTransaction>(
             () => connection.BeginTransaction("SampleTransaction")
             );

         // Must assign both transaction object and connection
         // to Command object for a pending local transaction
         command.Connection = connection;
         command.Transaction = transaction;

         try {
            command.CommandText =
                "Insert into Region (RegionID, RegionDescription) VALUES (555, 'Description')";
            await command.ExecuteNonQueryAsync();

            command.CommandText =
                "Insert into Region (RegionID, RegionDescription) VALUES (556, 'Description')";
            await command.ExecuteNonQueryAsync();

            // Attempt to commit the transaction.
            await Task.Run(() => transaction.Commit());
            Console.WriteLine("Both records are written to database.");
         }
         catch (Exception ex) {
            Console.WriteLine("Commit Exception Type: {0}", ex.GetType());
            Console.WriteLine("  Message: {0}", ex.Message);

            // Attempt to roll back the transaction.
            try {
               transaction.Rollback();
            }
            catch (Exception ex2) {
               // This catch block will handle any errors that may have occurred
               // on the server that would cause the rollback to fail, such as
               // a closed connection.
               Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());
               Console.WriteLine("  Message: {0}", ex2.Message);
            }
         }
      }
   }
}
```

### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="a4fe6-144">Utilisation de transactions SQL et de la nouvelle fonctionnalité asynchrone</span><span class="sxs-lookup"><span data-stu-id="a4fe6-144">Using SQL Transactions and the New Asynchronous Feature</span></span>

<span data-ttu-id="a4fe6-145">Dans une application d’entreprise, vous devrez peut-être ajouter des transactions distribuées dans certains scénarios, pour activer les transactions entre plusieurs serveurs de base de données.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-145">In an enterprise application, you may need to add distributed transactions in some scenarios, to enable transactions between multiple database servers.</span></span> <span data-ttu-id="a4fe6-146">Vous pouvez utiliser l’espace de noms System.Transactions et enregistrer une transaction distribuée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4fe6-146">You can use the System.Transactions namespace and enlist a distributed transaction, as follows:</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Transactions;

class Program {
   public static void Main()
   {
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();
       // replace these with your own values
       builder.DataSource = "your_server";
       builder.InitialCatalog = "your_data_source";
       builder.IntegratedSecurity = true;

       Task task = ExecuteDistributedTransaction(builder.ConnectionString, builder.ConnectionString);
       task.Wait();
   }

   static async Task ExecuteDistributedTransaction(string connectionString1, string connectionString2) {
      using (SqlConnection connection1 = new SqlConnection(connectionString1))
      using (SqlConnection connection2 = new SqlConnection(connectionString2)) {
         using (CommittableTransaction transaction = new CommittableTransaction()) {
            await connection1.OpenAsync();
            connection1.EnlistTransaction(transaction);

            await connection2.OpenAsync();
            connection2.EnlistTransaction(transaction);

            try {
               SqlCommand command1 = connection1.CreateCommand();
               command1.CommandText = "Insert into RegionTable1 (RegionID, RegionDescription) VALUES (100, 'Description')";
               await command1.ExecuteNonQueryAsync();

               SqlCommand command2 = connection2.CreateCommand();
               command2.CommandText = "Insert into RegionTable2 (RegionID, RegionDescription) VALUES (100, 'Description')";
               await command2.ExecuteNonQueryAsync();

               transaction.Commit();
            }
            catch (Exception ex) {
               Console.WriteLine("Exception Type: {0}", ex.GetType());
               Console.WriteLine("  Message: {0}", ex.Message);

               try {
                  transaction.Rollback();
               }
               catch (Exception ex2) {
                  Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());
                  Console.WriteLine("  Message: {0}", ex2.Message);
               }
            }
         }
      }
   }
}
```

### <a name="cancelling-an-asynchronous-operation"></a><span data-ttu-id="a4fe6-147">Annulation d'une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="a4fe6-147">Cancelling an Asynchronous Operation</span></span>

<span data-ttu-id="a4fe6-148">Vous pouvez annuler une requête asynchrone à l'aide de <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-148">You can cancel an asynchronous request by using the <xref:System.Threading.CancellationToken>.</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading;
using System.Threading.Tasks;

namespace Samples {
   class CancellationSample {
      public static void Main(string[] args) {
         CancellationTokenSource source = new CancellationTokenSource();
         source.CancelAfter(2000); // give up after 2 seconds
         try {
            Task result = CancellingAsynchronousOperations(source.Token);
            result.Wait();
         }
         catch (AggregateException exception) {
            if (exception.InnerException is SqlException) {
               Console.WriteLine("Operation canceled");
            }
            else {
               throw;
            }
         }
      }

      static async Task CancellingAsynchronousOperations(CancellationToken cancellationToken) {
         using (SqlConnection connection = new SqlConnection("Server=(local);Integrated Security=true")) {
            await connection.OpenAsync(cancellationToken);

            SqlCommand command = new SqlCommand("WAITFOR DELAY '00:10:00'", connection);
            await command.ExecuteNonQueryAsync(cancellationToken);
         }
      }
   }
}
```

### <a name="asynchronous-operations-with-sqlbulkcopy"></a><span data-ttu-id="a4fe6-149">Opérations asynchrones avec SqlBulkCopy</span><span class="sxs-lookup"><span data-stu-id="a4fe6-149">Asynchronous Operations with SqlBulkCopy</span></span>

<span data-ttu-id="a4fe6-150">Des fonctions asynchrones ont également été ajoutées à <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> avec <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-150">Asynchronous capabilities were also added to <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> with <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Data;
using System.Data.Odbc;
using System.Data.SqlClient;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;

namespace SqlBulkCopyAsyncCodeSample {
   class Program {
      static string selectStatement = "SELECT * FROM [pubs].[dbo].[titles]";
      static string createDestTableStatement =
          @"CREATE TABLE {0} (
            [title_id] [varchar](6) NOT NULL,
            [title] [varchar](80) NOT NULL,
            [type] [char](12) NOT NULL,
            [pub_id] [char](4) NULL,
            [price] [money] NULL,
            [advance] [money] NULL,
            [royalty] [int] NULL,
            [ytd_sales] [int] NULL,
            [notes] [varchar](200) NULL,
            [pubdate] [datetime] NOT NULL)";

      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"
      // static string connectionString = @"Server=(localdb)\V11.0;Database=Demo";
      static string connectionString = @"Server=(local);Database=Demo;Integrated Security=true";

      // static string odbcConnectionString = @"Driver={SQL Server};Server=(localdb)\V11.0;UID=oledb;Pwd=1Password!;Database=Demo";
      static string odbcConnectionString = @"Driver={SQL Server};Server=(local);Database=Demo;Integrated Security=true";

      // static string marsConnectionString = @"Server=(localdb)\V11.0;Database=Demo;MultipleActiveResultSets=true;";
      static string marsConnectionString = @"Server=(local);Database=Demo;MultipleActiveResultSets=true;Integrated Security=true";

      // Replace the Server name with your actual sql azure server name and User ID/Password
      static string azureConnectionString = @"Server=SqlAzure;User ID=myUserID;Password=myPassword;Database=Demo";

      static void Main(string[] args) {
         SynchronousSqlBulkCopy();
         AsyncSqlBulkCopy().Wait();
         MixSyncAsyncSqlBulkCopy().Wait();
         AsyncSqlBulkCopyNotifyAfter().Wait();
         AsyncSqlBulkCopyDataRows().Wait();
         // AsyncSqlBulkCopySqlServerToSqlAzure().Wait();
         // AsyncSqlBulkCopyCancel().Wait();
         AsyncSqlBulkCopyMARS().Wait();
      }

      // 3.1.1 Synchronous bulk copy in .NET 4.5
      private static void SynchronousSqlBulkCopy() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            conn.Open();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               cmd.ExecuteNonQuery();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  bcp.WriteToServer(dt);
               }
            }
         }

      }

      // 3.1.2 Asynchronous bulk copy in .NET 4.5
      private static async Task AsyncSqlBulkCopy() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               await cmd.ExecuteNonQueryAsync();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  await bcp.WriteToServerAsync(dt);
               }
            }
         }
      }

      // 3.2 Add new Async.NET capabilities in an existing application (Mixing synchronous and asynchronous calls)
      private static async Task MixSyncAsyncSqlBulkCopy() {
         using (OdbcConnection odbcconn = new OdbcConnection(odbcConnectionString)) {
            odbcconn.Open();
            using (OdbcCommand odbccmd = new OdbcCommand(selectStatement, odbcconn)) {
               using (OdbcDataReader odbcreader = odbccmd.ExecuteReader()) {
                  using (SqlConnection conn = new SqlConnection(connectionString)) {
                     await conn.OpenAsync();
                     string temptable = "temptable";//"[#" + Guid.NewGuid().ToString("N") + "]";
                     SqlCommand createCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), conn);
                     await createCmd.ExecuteNonQueryAsync();
                     using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                        bcp.DestinationTableName = temptable;
                        await bcp.WriteToServerAsync(odbcreader);
                     }
                  }
               }
            }
         }
      }

      // 3.3 Using the NotifyAfter property
      private static async Task AsyncSqlBulkCopyNotifyAfter() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               await cmd.ExecuteNonQueryAsync();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  bcp.NotifyAfter = 5;
                  bcp.SqlRowsCopied += new SqlRowsCopiedEventHandler(OnSqlRowsCopied);
                  await bcp.WriteToServerAsync(dt);
               }
            }
         }
      }

      private static void OnSqlRowsCopied(object sender, SqlRowsCopiedEventArgs e) {
         Console.WriteLine("Copied {0} so far...", e.RowsCopied);
      }

      // 3.4 Using the new SqlBulkCopy Async.NET capabilities with DataRow[]
      private static async Task AsyncSqlBulkCopyDataRows() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);
               DataRow[] rows = dt.Select();

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               await cmd.ExecuteNonQueryAsync();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  await bcp.WriteToServerAsync(rows);
               }
            }
         }
      }

      // 3.5 Copying data from SQL Server to SQL Azure in .NET 4.5
      //private static async Task AsyncSqlBulkCopySqlServerToSqlAzure() {
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {
      //      await srcConn.OpenAsync();
      //      await destConn.OpenAsync();
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatement, srcConn)) {
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync()) {
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {
      //               await destCmd.ExecuteNonQueryAsync();
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {
      //                  bcp.DestinationTableName = temptable;
      //                  await bcp.WriteToServerAsync(reader);
      //               }
      //            }
      //         }
      //      }
      //   }
      //}

      // 3.6 Cancelling an Asynchronous Operation to SQL Azure
      //private static async Task AsyncSqlBulkCopyCancel() {
      //   CancellationTokenSource cts = new CancellationTokenSource();
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {
      //      await srcConn.OpenAsync(cts.Token);
      //      await destConn.OpenAsync(cts.Token);
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatement, srcConn)) {
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync(cts.Token)) {
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {
      //               await destCmd.ExecuteNonQueryAsync(cts.Token);
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {
      //                  bcp.DestinationTableName = temptable;
      //                  await bcp.WriteToServerAsync(reader, cts.Token);
      //                  //Cancel Async SqlBulCopy Operation after 200 ms
      //                  cts.CancelAfter(200);
      //               }
      //            }
      //         }
      //      }
      //   }
      //}

      // 3.7 Using Async.Net and MARS
      private static async Task AsyncSqlBulkCopyMARS() {
         using (SqlConnection marsConn = new SqlConnection(marsConnectionString)) {
            await marsConn.OpenAsync();

            SqlCommand titlesCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[titles]", marsConn);
            SqlCommand authorsCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[authors]", marsConn);
            //With MARS we can have multiple active results sets on the same connection
            using (SqlDataReader titlesReader = await titlesCmd.ExecuteReaderAsync())
            using (SqlDataReader authorsReader = await authorsCmd.ExecuteReaderAsync()) {
               await authorsReader.ReadAsync();

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               using (SqlConnection destConn = new SqlConnection(connectionString)) {
                  await destConn.OpenAsync();
                  using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {
                     await destCmd.ExecuteNonQueryAsync();
                     using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {
                        bcp.DestinationTableName = temptable;
                        await bcp.WriteToServerAsync(titlesReader);
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="asynchronously-using-multiple-commands-with-mars"></a><span data-ttu-id="a4fe6-151">Utilisation asynchrone de plusieurs commandes avec MARS</span><span class="sxs-lookup"><span data-stu-id="a4fe6-151">Asynchronously Using Multiple Commands with MARS</span></span>

<span data-ttu-id="a4fe6-152">L’exemple ouvre une connexion unique à la base de données **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-152">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="a4fe6-153">À l’aide d’un objet <xref:System.Data.SqlClient.SqlCommand>, un <xref:System.Data.SqlClient.SqlDataReader> est créé.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-153">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="a4fe6-154">À mesure que le lecteur est utilisé, un deuxième <xref:System.Data.SqlClient.SqlDataReader> est ouvert, en utilisant les données du premier <xref:System.Data.SqlClient.SqlDataReader> comme entrée de la clause WHERE pour le deuxième lecteur.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-154">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>

> [!NOTE]
> <span data-ttu-id="a4fe6-155">L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-155">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="a4fe6-156">La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-156">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="a4fe6-157">Modifiez la chaîne de connexion en fonction des besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-157">Modify the connection string as necessary for your environment.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.Threading.Tasks;

class Class1 {
   static void Main() {
      Task task = MultipleCommands();
      task.Wait();
   }

   static async Task MultipleCommands() {
      // By default, MARS is disabled when connecting to a MARS-enabled.
      // It must be enabled in the connection string.
      string connectionString = GetConnectionString();

      int vendorID;
      SqlDataReader productReader = null;
      string vendorSQL =
        "SELECT VendorId, Name FROM Purchasing.Vendor";
      string productSQL =
        "SELECT Production.Product.Name FROM Production.Product " +
        "INNER JOIN Purchasing.ProductVendor " +
        "ON Production.Product.ProductID = " +
        "Purchasing.ProductVendor.ProductID " +
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId";

      using (SqlConnection awConnection =
        new SqlConnection(connectionString)) {
         SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);
         SqlCommand productCmd =
           new SqlCommand(productSQL, awConnection);

         productCmd.Parameters.Add("@VendorId", SqlDbType.Int);

         await awConnection.OpenAsync();
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {
            while (await vendorReader.ReadAsync()) {
               Console.WriteLine(vendorReader["Name"]);

               vendorID = (int)vendorReader["VendorId"];

               productCmd.Parameters["@VendorId"].Value = vendorID;
               // The following line of code requires a MARS-enabled connection.
               productReader = await productCmd.ExecuteReaderAsync();
               using (productReader) {
                  while (await productReader.ReadAsync()) {
                     Console.WriteLine("  " +
                       productReader["Name"].ToString());
                  }
               }
            }
         }
      }
   }

   private static string GetConnectionString() {
      // To avoid storing the connection string in your code, you can retrieve it from a configuration file.
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";
   }
}
```

## <a name="asynchronously-reading-and-updating-data-with-mars"></a><span data-ttu-id="a4fe6-158">Lecture et mise à jour des données asynchrones avec MARS</span><span class="sxs-lookup"><span data-stu-id="a4fe6-158">Asynchronously Reading and Updating Data with MARS</span></span>

<span data-ttu-id="a4fe6-159">MARS permet l’utilisation d’une connexion pour les opérations de lecture et les opérations DML (Data Manipulation Language) avec plusieurs opérations en attente.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-159">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="a4fe6-160">Cette fonctionnalité évite à une application de traiter les erreurs de connexion occupée.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-160">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="a4fe6-161">En outre, MARS peut remplacer l’utilisateur des curseurs côté serveur, qui consomme généralement davantage de ressources.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-161">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="a4fe6-162">Pour finir, comme plusieurs opérations peuvent opérer sur une seule connexion, elles peuvent partager le même contexte de transaction, en éliminant la nécessité d’utiliser les procédures stockées **système sp_getbindtoken** et **sp_bindsession**.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-162">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>

<span data-ttu-id="a4fe6-163">L’application Console suivante montre comment utiliser deux objets <xref:System.Data.SqlClient.SqlDataReader> avec trois objets <xref:System.Data.SqlClient.SqlCommand> et un objet <xref:System.Data.SqlClient.SqlConnection> unique avec MARS activé.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-163">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="a4fe6-164">Le premier objet de commande récupère une liste de fournisseurs dont le niveau de solvabilité est 5.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-164">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="a4fe6-165">Le deuxième objet de commande utilise l’ID de fournisseur fournie par un <xref:System.Data.SqlClient.SqlDataReader> pour charger le deuxième <xref:System.Data.SqlClient.SqlDataReader> avec tous les produits du fournisseur en question.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-165">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="a4fe6-166">Chaque enregistrement de produit est visité par le deuxième <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-166">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="a4fe6-167">Un calcul est effectué afin de déterminer ce que doit être le nouveau **OnOrderQty**.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-167">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="a4fe6-168">Le troisième objet de commande est ensuite utilisé pour mettre à jour la table **ProductVendor** avec la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-168">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="a4fe6-169">Tout ce processus entier se déroule au sein d’une seule transaction, qui est restaurée à la fin.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-169">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>

> [!NOTE]
> <span data-ttu-id="a4fe6-170">L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-170">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="a4fe6-171">La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-171">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="a4fe6-172">Modifiez la chaîne de connexion en fonction des besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a4fe6-172">Modify the connection string as necessary for your environment.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Data;
using System.Data.SqlClient;
using System.Threading.Tasks;

class Program {
   static void Main() {
      Task task = ReadingAndUpdatingData();
      task.Wait();
   }

   static async Task ReadingAndUpdatingData() {
      // By default, MARS is disabled when connecting to a MARS-enabled host.
      // It must be enabled in the connection string.
      string connectionString = GetConnectionString();

      SqlTransaction updateTx = null;
      SqlCommand vendorCmd = null;
      SqlCommand prodVendCmd = null;
      SqlCommand updateCmd = null;

      SqlDataReader prodVendReader = null;

      int vendorID = 0;
      int productID = 0;
      int minOrderQty = 0;
      int maxOrderQty = 0;
      int onOrderQty = 0;
      int recordsUpdated = 0;
      int totalRecordsUpdated = 0;

      string vendorSQL =
          "SELECT VendorID, Name FROM Purchasing.Vendor " +
          "WHERE CreditRating = 5";
      string prodVendSQL =
          "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +
          "FROM Purchasing.ProductVendor " +
          "WHERE VendorID = @VendorID";
      string updateSQL =
          "UPDATE Purchasing.ProductVendor " +
          "SET OnOrderQty = @OrderQty " +
          "WHERE ProductID = @ProductID AND VendorID = @VendorID";

      using (SqlConnection awConnection =
        new SqlConnection(connectionString)) {
         await awConnection.OpenAsync();
         updateTx = await Task.Run(() => awConnection.BeginTransaction());

         vendorCmd = new SqlCommand(vendorSQL, awConnection);
         vendorCmd.Transaction = updateTx;

         prodVendCmd = new SqlCommand(prodVendSQL, awConnection);
         prodVendCmd.Transaction = updateTx;
         prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);

         updateCmd = new SqlCommand(updateSQL, awConnection);
         updateCmd.Transaction = updateTx;
         updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);
         updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);
         updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);

         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {
            while (await vendorReader.ReadAsync()) {
               Console.WriteLine(vendorReader["Name"]);

               vendorID = (int)vendorReader["VendorID"];
               prodVendCmd.Parameters["@VendorID"].Value = vendorID;
               prodVendReader = await prodVendCmd.ExecuteReaderAsync();

               using (prodVendReader) {
                  while (await prodVendReader.ReadAsync()) {
                     productID = (int)prodVendReader["ProductID"];

                     if (prodVendReader["OnOrderQty"] == DBNull.Value) {
                        minOrderQty = (int)prodVendReader["MinOrderQty"];
                        onOrderQty = minOrderQty;
                     }
                     else {
                        maxOrderQty = (int)prodVendReader["MaxOrderQty"];
                        onOrderQty = (int)(maxOrderQty / 2);
                     }

                     updateCmd.Parameters["@OrderQty"].Value = onOrderQty;
                     updateCmd.Parameters["@ProductID"].Value = productID;
                     updateCmd.Parameters["@VendorID"].Value = vendorID;

                     recordsUpdated = await updateCmd.ExecuteNonQueryAsync();
                     totalRecordsUpdated += recordsUpdated;
                  }
               }
            }
         }
         Console.WriteLine("Total Records Updated: ", totalRecordsUpdated.ToString());
         await Task.Run(() => updateTx.Rollback());
         Console.WriteLine("Transaction Rolled Back");
      }
   }

   private static string GetConnectionString() {
      // To avoid storing the connection string in your code, you can retrieve it from a configuration file.
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";
   }
}
```

## <a name="see-also"></a><span data-ttu-id="a4fe6-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4fe6-173">See also</span></span>

- [<span data-ttu-id="a4fe6-174">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a4fe6-174">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
