---
title: Gestion des événements DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a2c2dc71cc9e5c445fd05534dad5ad47fd66f436
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194724"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="4b446-102">Gestion des événements DataAdapter</span><span class="sxs-lookup"><span data-stu-id="4b446-102">Handling DataAdapter Events</span></span>

<span data-ttu-id="4b446-103"><xref:System.Data.Common.DataAdapter> ADO.NET expose trois événements que vous pouvez utiliser pour répondre aux modifications apportées aux données au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="4b446-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="4b446-104">Le tableau ci-dessous répertorie les événements `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="4b446-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="4b446-105">Événement</span><span class="sxs-lookup"><span data-stu-id="4b446-105">Event</span></span>|<span data-ttu-id="4b446-106">Description</span><span class="sxs-lookup"><span data-stu-id="4b446-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="4b446-107">Une opération UPDATE, INSERT ou DELETE sur une ligne (par un appel à l'une des méthodes `Update`) est sur le point de commencer.</span><span class="sxs-lookup"><span data-stu-id="4b446-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="4b446-108">Une opération UPDATE, INSERT ou DELETE sur une ligne (par un appel à l'une des méthodes `Update`) est terminée.</span><span class="sxs-lookup"><span data-stu-id="4b446-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="4b446-109">Une erreur est survenue pendant une opération `Fill`.</span><span class="sxs-lookup"><span data-stu-id="4b446-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="4b446-110">RowUpdating et RowUpdated</span><span class="sxs-lookup"><span data-stu-id="4b446-110">RowUpdating and RowUpdated</span></span>  

 <span data-ttu-id="4b446-111">`RowUpdating` est déclenché avant le traitement d'une mise à jour d'une ligne de l'objet <xref:System.Data.DataSet> au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="4b446-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="4b446-112">`RowUpdated` est déclenché après le traitement d'une mise à jour d'une ligne de l'objet `DataSet` au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="4b446-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="4b446-113">En conséquence, vous pouvez utiliser `RowUpdating` pour modifier le comportement de la mise à jour avant qu'elle ne survienne, pour fournir une gestion supplémentaire lors d'une mise à jour, pour conserver une référence à une ligne mise à jour, pour annuler la mise à jour en cours et la programmer pour un traitement par lots à traiter ultérieurement, etc.</span><span class="sxs-lookup"><span data-stu-id="4b446-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="4b446-114">`RowUpdated` est utile pour réagir aux erreurs et aux exceptions qui surviennent pendant la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b446-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="4b446-115">Vous pouvez ajouter des informations d'erreur au `DataSet`, ainsi qu'une logique pour les nouvelles tentatives et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="4b446-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="4b446-116">Les arguments <xref:System.Data.Common.RowUpdatingEventArgs> et <xref:System.Data.Common.RowUpdatedEventArgs> passés aux événements `RowUpdating` et `RowUpdated` comprennent les élément suivants : une propriété `Command` qui référence l’objet `Command` utilisé pour effectuer la mise à jour ; une propriété `Row` qui référence l’objet `DataRow` contenant les informations mises à jour ; une propriété `StatementType` pour le type de mise à jour effectuée ; le `TableMapping`, le cas échéant ; et le `Status` de l’opération.</span><span class="sxs-lookup"><span data-stu-id="4b446-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="4b446-117">Vous pouvez utiliser la propriété `Status` pour déterminer si une erreur est survenue pendant l'opération et éventuellement contrôler les actions sur les lignes actuelles et qui en résultent.</span><span class="sxs-lookup"><span data-stu-id="4b446-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="4b446-118">Lorsque l'événement se produit, la propriété `Status` est égale à `Continue` ou `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="4b446-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="4b446-119">Le tableau suivant présente les valeurs que vous pouvez affecter à la propriété `Status` afin de contrôler les actions ultérieures pendant la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b446-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="4b446-120">Statut</span><span class="sxs-lookup"><span data-stu-id="4b446-120">Status</span></span>|<span data-ttu-id="4b446-121">Description</span><span class="sxs-lookup"><span data-stu-id="4b446-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="4b446-122">Continuer l'opération de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b446-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="4b446-123">Abandonner l'opération de mise à jour et lever une exception.</span><span class="sxs-lookup"><span data-stu-id="4b446-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="4b446-124">Ignorer la ligne actuelle et continuer l'opération de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b446-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="4b446-125">Abandonner l'opération de mise à jour mais ne pas lever d'exception.</span><span class="sxs-lookup"><span data-stu-id="4b446-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="4b446-126">L'affectation de la valeur `Status` à la propriété `ErrorsOccurred` entraîne la levée d'une exception.</span><span class="sxs-lookup"><span data-stu-id="4b446-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="4b446-127">Vous pouvez contrôler l'exception levée en affectant la propriété `Errors` à l'exception souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4b446-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="4b446-128">L'utilisation de l'une des autres valeurs pour `Status` évite la levée d'une exception.</span><span class="sxs-lookup"><span data-stu-id="4b446-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="4b446-129">Vous pouvez aussi utiliser la propriété `ContinueUpdateOnError` pour gérer les erreurs des lignes mises à jour.</span><span class="sxs-lookup"><span data-stu-id="4b446-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="4b446-130">Si `DataAdapter.ContinueUpdateOnError` a la valeur `true`, lorsqu'une mise à jour de ligne entraîne la levée d'une exception, le texte de celle-ci est placé dans les informations `RowError` de la ligne particulière et le traitement continue sans lever d'exception.</span><span class="sxs-lookup"><span data-stu-id="4b446-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="4b446-131">Vous pouvez ainsi répondre aux erreurs lorsque `Update` est terminé, contrairement à l'événement `RowUpdated`, qui vous permet d'y répondre au moment de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="4b446-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="4b446-132">L'exemple de code suivant montre comment ajouter et supprimer les gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="4b446-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="4b446-133">Le gestionnaire d'événements `RowUpdating` écrit un journal de tous les enregistrements supprimés avec un horodatage.</span><span class="sxs-lookup"><span data-stu-id="4b446-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="4b446-134">Le `RowUpdated` Gestionnaire d’événements ajoute des informations d’erreur à la `RowError` propriété de la ligne dans le `DataSet` , supprime l’exception et continue le traitement (en miroir le comportement de `ContinueUpdateOnError`  =  `true` ).</span><span class="sxs-lookup"><span data-stu-id="4b446-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="4b446-135">FillError</span><span class="sxs-lookup"><span data-stu-id="4b446-135">FillError</span></span>  

 <span data-ttu-id="4b446-136">Le `DataAdapter` émet l'événement `FillError` en cas d'erreur pendant une opération `Fill`.</span><span class="sxs-lookup"><span data-stu-id="4b446-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="4b446-137">Ce type d'erreur se produit habituellement lorsque les données ajoutées dans la ligne n'ont pas pu être converties en type .NET Framework sans perte de précision.</span><span class="sxs-lookup"><span data-stu-id="4b446-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="4b446-138">En cas d'erreur pendant une opération `Fill`, la ligne actuelle n'est pas ajoutée au `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="4b446-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="4b446-139">L'événement `FillError` vous permet de résoudre l'erreur et d'ajouter la ligne, ou d'ignorer la ligne exclue et de poursuivre l'opération `Fill`.</span><span class="sxs-lookup"><span data-stu-id="4b446-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="4b446-140">Le `FillErrorEventArgs` passé à l'événement `FillError` peut contenir plusieurs propriétés qui vous permettent de répondre aux erreurs et de les résoudre.</span><span class="sxs-lookup"><span data-stu-id="4b446-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="4b446-141">Le tableau suivant présente les propriétés de l'objet `FillErrorEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="4b446-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="4b446-142">Propriété</span><span class="sxs-lookup"><span data-stu-id="4b446-142">Property</span></span>|<span data-ttu-id="4b446-143">Description</span><span class="sxs-lookup"><span data-stu-id="4b446-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="4b446-144">`Exception` survenue.</span><span class="sxs-lookup"><span data-stu-id="4b446-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="4b446-145">Objet `DataTable` en cours de remplissage au moment de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="4b446-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="4b446-146">Tableau d'objets contenant les valeurs de la ligne qui était ajoutée au moment de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="4b446-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="4b446-147">Les références ordinales du tableau `Values` correspondent à celles des colonnes de la ligne ajoutée.</span><span class="sxs-lookup"><span data-stu-id="4b446-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="4b446-148">Par exemple, `Values[0]` est la valeur qui a été ajoutée comme première colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="4b446-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="4b446-149">Vous permet de choisir la levée ou non d'une exception.</span><span class="sxs-lookup"><span data-stu-id="4b446-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="4b446-150">L'affectation de la valeur `Continue` à la propriété `false` stoppe l'opération `Fill` en cours et une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="4b446-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="4b446-151">L'affectation de la valeur `Continue` à `true` poursuit l'opération `Fill` en dépit de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="4b446-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="4b446-152">L'exemple de code suivant ajoute l'événement `FillError` du `DataAdapter` à un gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="4b446-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="4b446-153">Dans le code d’événement `FillError`, l’exemple détermine s’il y a une possibilité de perte de précision, donnant ainsi l’opportunité de répondre à l’exception.</span><span class="sxs-lookup"><span data-stu-id="4b446-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b446-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b446-154">See also</span></span>

- [<span data-ttu-id="4b446-155">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="4b446-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="4b446-156">Gestion des événements de DataSet</span><span class="sxs-lookup"><span data-stu-id="4b446-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="4b446-157">Gestion des événements de DataTable</span><span class="sxs-lookup"><span data-stu-id="4b446-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="4b446-158">Événements</span><span class="sxs-lookup"><span data-stu-id="4b446-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="4b446-159">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4b446-159">ADO.NET Overview</span></span>](ado-net-overview.md)
