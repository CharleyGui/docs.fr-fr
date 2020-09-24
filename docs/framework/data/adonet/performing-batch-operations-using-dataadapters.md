---
title: Exécution d'opérations en lot à l'aide des DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 9dd6abb91b3549e3bc8b4ae84cbb227171512ecb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177421"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="e39c1-102">Exécution d'opérations en lot à l'aide des DataAdapter</span><span class="sxs-lookup"><span data-stu-id="e39c1-102">Performing Batch Operations Using DataAdapters</span></span>

<span data-ttu-id="e39c1-103">La prise en charge des lots dans ADO.NET permet à un objet <xref:System.Data.Common.DataAdapter> de grouper des opérations INSERT, UPDATE et DELETE à partir d'un objet <xref:System.Data.DataSet> ou d'un objet <xref:System.Data.DataTable> pour le serveur, au lieu d'envoyer les opérations successivement.</span><span class="sxs-lookup"><span data-stu-id="e39c1-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="e39c1-104">La réduction du nombre d'allers-retours vers le serveur entraîne généralement des gains de performances importants.</span><span class="sxs-lookup"><span data-stu-id="e39c1-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="e39c1-105">Les mises à jour par lots sont prises en charge pour les fournisseurs de données .NET pour SQL Server (<xref:System.Data.SqlClient>) et Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="e39c1-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="e39c1-106">Lors de la mise à jour d'une base de données avec les modifications d'un objet <xref:System.Data.DataSet> dans les versions précédentes d'ADO.NET, la méthode `Update` d'un objet `DataAdapter` apportait des mises à jour à la base de données ligne après ligne.</span><span class="sxs-lookup"><span data-stu-id="e39c1-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="e39c1-107">Comme elle effectuait une itération dans les lignes de l'objet <xref:System.Data.DataTable> spécifié, elle examinait chaque objet <xref:System.Data.DataRow> pour voir s'il avait été modifié.</span><span class="sxs-lookup"><span data-stu-id="e39c1-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="e39c1-108">Si la ligne avait été modifiée, elle appelait `UpdateCommand`, `InsertCommand` ou `DeleteCommand` en fonction de la valeur de la propriété <xref:System.Data.DataRow.RowState%2A> de cette ligne.</span><span class="sxs-lookup"><span data-stu-id="e39c1-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="e39c1-109">Chaque mise à jour de ligne impliquait un aller-retour sur le réseau vers la base de données.</span><span class="sxs-lookup"><span data-stu-id="e39c1-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="e39c1-110">À partir d'ADO.NET 2.0, <xref:System.Data.Common.DbDataAdapter> expose une propriété <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="e39c1-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="e39c1-111">L'affection d'une valeur entière positive à la propriété `UpdateBatchSize` a pour effet d'envoyer les mises à jour de la base de données sous la forme de lots de la taille spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e39c1-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="e39c1-112">Par exemple, l'affectation de la valeur 10 à la propriété `UpdateBatchSize` groupe 10 instructions distinctes avant de les soumettre en tant que lot.</span><span class="sxs-lookup"><span data-stu-id="e39c1-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="e39c1-113">Avec la valeur 0, l'objet `UpdateBatchSize` utilise la taille de lot la plus grande que le serveur peut gérer.</span><span class="sxs-lookup"><span data-stu-id="e39c1-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="e39c1-114">La valeur 1 désactive les mises à jour par lots car les lignes sont envoyées les unes après les autres.</span><span class="sxs-lookup"><span data-stu-id="e39c1-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="e39c1-115">L'exécution d'un lot très volumineux peut réduire les performances.</span><span class="sxs-lookup"><span data-stu-id="e39c1-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="e39c1-116">Vous devez donc tester le paramètre de taille de lot optimal avant d'implémenter votre application.</span><span class="sxs-lookup"><span data-stu-id="e39c1-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="e39c1-117">Utilisation de la propriété UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="e39c1-117">Using the UpdateBatchSize Property</span></span>  

 <span data-ttu-id="e39c1-118">Lorsque les mises à jour par lots sont activées, la valeur <xref:System.Data.IDbCommand.UpdatedRowSource%2A> ou `UpdateCommand` doit être affectée à la propriété `InsertCommand` de `DeleteCommand`, <xref:System.Data.UpdateRowSource.None> et <xref:System.Data.UpdateRowSource.OutputParameters> du DataAdapter.</span><span class="sxs-lookup"><span data-stu-id="e39c1-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="e39c1-119">Lors de l'exécution d'une mise à jour par lots, les valeurs <xref:System.Data.IDbCommand.UpdatedRowSource%2A> ou <xref:System.Data.UpdateRowSource.FirstReturnedRecord> de la propriété <xref:System.Data.UpdateRowSource.Both> de la commande ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="e39c1-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="e39c1-120">La procédure suivante illustre l'utilisation de la propriété `UpdateBatchSize`.</span><span class="sxs-lookup"><span data-stu-id="e39c1-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="e39c1-121">La procédure accepte deux arguments, un <xref:System.Data.DataSet> objet qui contient des colonnes représentant les champs **ProductCategoryID** et **Name** dans la table **production. ProductCategory** et un entier représentant la taille du lot (le nombre de lignes dans le lot).</span><span class="sxs-lookup"><span data-stu-id="e39c1-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="e39c1-122">Le code crée un nouvel objet <xref:System.Data.SqlClient.SqlDataAdapter>, en définissant ses propriétés <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> et <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="e39c1-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="e39c1-123">Le code est basé sur l'hypothèse que l'objet <xref:System.Data.DataSet> comporte des lignes modifiées.</span><span class="sxs-lookup"><span data-stu-id="e39c1-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="e39c1-124">Il définit la propriété `UpdateBatchSize` et effectue la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="e39c1-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="e39c1-125">Gestion des événements et des erreurs liés aux mises à jour par lots.</span><span class="sxs-lookup"><span data-stu-id="e39c1-125">Handling Batch Update-Related Events and Errors</span></span>  

 <span data-ttu-id="e39c1-126">Le **DataAdapter** comporte deux événements liés à Update : **RowUpdating** et **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="e39c1-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="e39c1-127">Dans les versions précédentes d'ADO.NET, en cas de désactivation du traitement par lots, chacun de ces événements était généré une fois pour chaque ligne traitée.</span><span class="sxs-lookup"><span data-stu-id="e39c1-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="e39c1-128">**RowUpdating** est généré avant la mise à jour, et **RowUpdated** est généré une fois la mise à jour de la base de données terminée.</span><span class="sxs-lookup"><span data-stu-id="e39c1-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="e39c1-129">Changements de comportement d'événement avec les mises à jour par lots</span><span class="sxs-lookup"><span data-stu-id="e39c1-129">Event Behavior Changes with Batch Updates</span></span>  

 <span data-ttu-id="e39c1-130">Lorsque le traitement par lots est activé, plusieurs lignes sont mises à jour en une seule opération de base de données.</span><span class="sxs-lookup"><span data-stu-id="e39c1-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="e39c1-131">Par conséquent, un seul événement `RowUpdated` se produit pour chaque lot, tandis que l'événement `RowUpdating` se produit pour chaque ligne traitée.</span><span class="sxs-lookup"><span data-stu-id="e39c1-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="e39c1-132">Lorsque le traitement par lots est désactivé, les deux événements sont déclenchés avec un entrelacement de un à un où un événement `RowUpdating` et un événement `RowUpdated` se déclenchent pour une ligne, puis un événement `RowUpdating` et un événement `RowUpdated` se déclenchent pour la ligne suivante, jusqu'à ce que toutes les lignes aient été traitées.</span><span class="sxs-lookup"><span data-stu-id="e39c1-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="e39c1-133">Accès aux lignes mises à jour</span><span class="sxs-lookup"><span data-stu-id="e39c1-133">Accessing Updated Rows</span></span>  

 <span data-ttu-id="e39c1-134">Lorsque le traitement par lots est désactivé, la ligne mise à jour est accessible à l'aide de la propriété <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> de la classe <xref:System.Data.Common.RowUpdatedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e39c1-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="e39c1-135">Lorsque le traitement par lots est activé, un simple événement `RowUpdated` est généré pour plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="e39c1-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="e39c1-136">C'est pourquoi la valeur de la propriété `Row` pour chaque ligne est null.</span><span class="sxs-lookup"><span data-stu-id="e39c1-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="e39c1-137">Des événements `RowUpdating` sont encore générés pour chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="e39c1-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="e39c1-138">La méthode <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> de la classe <xref:System.Data.Common.RowUpdatedEventArgs> permet d'accéder aux lignes traitées en copiant les références aux lignes dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="e39c1-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="e39c1-139">Si aucune ligne n'est traitée, `CopyToRows` lève une exception <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="e39c1-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="e39c1-140">Utilisez la propriété <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> pour retourner le nombre de lignes traitées avant d'appeler la méthode <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="e39c1-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="e39c1-141">Gestion des erreurs de données</span><span class="sxs-lookup"><span data-stu-id="e39c1-141">Handling Data Errors</span></span>  

 <span data-ttu-id="e39c1-142">L'exécution par lots a le même effet que l'exécution des instructions individuelles.</span><span class="sxs-lookup"><span data-stu-id="e39c1-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="e39c1-143">Les instructions sont exécutées dans l'ordre où elles ont été ajoutées au lot.</span><span class="sxs-lookup"><span data-stu-id="e39c1-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="e39c1-144">Les erreurs sont gérées de la même manière, que le mode de traitement par lots soit activé ou non.</span><span class="sxs-lookup"><span data-stu-id="e39c1-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="e39c1-145">Chaque ligne est traitée séparément.</span><span class="sxs-lookup"><span data-stu-id="e39c1-145">Each row is processed separately.</span></span> <span data-ttu-id="e39c1-146">Seules les lignes traitées avec succès dans la base de données sont mises à jour dans l'objet <xref:System.Data.DataRow> correspondant à l'objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="e39c1-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="e39c1-147">Le fournisseur de données et le serveur de base de données principal déterminent les constructions SQL prises en charge pour l'exécution par lots.</span><span class="sxs-lookup"><span data-stu-id="e39c1-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="e39c1-148">Une exception peut être levée si une instruction non prise en charge est soumise pour exécution.</span><span class="sxs-lookup"><span data-stu-id="e39c1-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39c1-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e39c1-149">See also</span></span>

- [<span data-ttu-id="e39c1-150">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="e39c1-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="e39c1-151">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="e39c1-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="e39c1-152">Gestion des événements DataAdapter</span><span class="sxs-lookup"><span data-stu-id="e39c1-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="e39c1-153">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e39c1-153">ADO.NET Overview</span></span>](ado-net-overview.md)
