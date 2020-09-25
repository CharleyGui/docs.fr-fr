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
# <a name="handling-dataadapter-events"></a>Gestion des événements DataAdapter

<xref:System.Data.Common.DataAdapter> ADO.NET expose trois événements que vous pouvez utiliser pour répondre aux modifications apportées aux données au niveau de la source de données. Le tableau ci-dessous répertorie les événements `DataAdapter`.  
  
|Événement|Description|  
|-----------|-----------------|  
|`RowUpdating`|Une opération UPDATE, INSERT ou DELETE sur une ligne (par un appel à l'une des méthodes `Update`) est sur le point de commencer.|  
|`RowUpdated`|Une opération UPDATE, INSERT ou DELETE sur une ligne (par un appel à l'une des méthodes `Update`) est terminée.|  
|`FillError`|Une erreur est survenue pendant une opération `Fill`.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating et RowUpdated  

 `RowUpdating` est déclenché avant le traitement d'une mise à jour d'une ligne de l'objet <xref:System.Data.DataSet> au niveau de la source de données. `RowUpdated` est déclenché après le traitement d'une mise à jour d'une ligne de l'objet `DataSet` au niveau de la source de données. En conséquence, vous pouvez utiliser `RowUpdating` pour modifier le comportement de la mise à jour avant qu'elle ne survienne, pour fournir une gestion supplémentaire lors d'une mise à jour, pour conserver une référence à une ligne mise à jour, pour annuler la mise à jour en cours et la programmer pour un traitement par lots à traiter ultérieurement, etc. `RowUpdated` est utile pour réagir aux erreurs et aux exceptions qui surviennent pendant la mise à jour. Vous pouvez ajouter des informations d'erreur au `DataSet`, ainsi qu'une logique pour les nouvelles tentatives et ainsi de suite.  
  
 Les arguments <xref:System.Data.Common.RowUpdatingEventArgs> et <xref:System.Data.Common.RowUpdatedEventArgs> passés aux événements `RowUpdating` et `RowUpdated` comprennent les élément suivants : une propriété `Command` qui référence l’objet `Command` utilisé pour effectuer la mise à jour ; une propriété `Row` qui référence l’objet `DataRow` contenant les informations mises à jour ; une propriété `StatementType` pour le type de mise à jour effectuée ; le `TableMapping`, le cas échéant ; et le `Status` de l’opération.  
  
 Vous pouvez utiliser la propriété `Status` pour déterminer si une erreur est survenue pendant l'opération et éventuellement contrôler les actions sur les lignes actuelles et qui en résultent. Lorsque l'événement se produit, la propriété `Status` est égale à `Continue` ou `ErrorsOccurred`. Le tableau suivant présente les valeurs que vous pouvez affecter à la propriété `Status` afin de contrôler les actions ultérieures pendant la mise à jour.  
  
|Statut|Description|  
|------------|-----------------|  
|`Continue`|Continuer l'opération de mise à jour.|  
|`ErrorsOccurred`|Abandonner l'opération de mise à jour et lever une exception.|  
|`SkipCurrentRow`|Ignorer la ligne actuelle et continuer l'opération de mise à jour.|  
|`SkipAllRemainingRows`|Abandonner l'opération de mise à jour mais ne pas lever d'exception.|  
  
 L'affectation de la valeur `Status` à la propriété `ErrorsOccurred` entraîne la levée d'une exception. Vous pouvez contrôler l'exception levée en affectant la propriété `Errors` à l'exception souhaitée. L'utilisation de l'une des autres valeurs pour `Status` évite la levée d'une exception.  
  
 Vous pouvez aussi utiliser la propriété `ContinueUpdateOnError` pour gérer les erreurs des lignes mises à jour. Si `DataAdapter.ContinueUpdateOnError` a la valeur `true`, lorsqu'une mise à jour de ligne entraîne la levée d'une exception, le texte de celle-ci est placé dans les informations `RowError` de la ligne particulière et le traitement continue sans lever d'exception. Vous pouvez ainsi répondre aux erreurs lorsque `Update` est terminé, contrairement à l'événement `RowUpdated`, qui vous permet d'y répondre au moment de l'erreur.  
  
 L'exemple de code suivant montre comment ajouter et supprimer les gestionnaires d'événements. Le gestionnaire d'événements `RowUpdating` écrit un journal de tous les enregistrements supprimés avec un horodatage. Le `RowUpdated` Gestionnaire d’événements ajoute des informations d’erreur à la `RowError` propriété de la ligne dans le `DataSet` , supprime l’exception et continue le traitement (en miroir le comportement de `ContinueUpdateOnError`  =  `true` ).  
  
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
  
## <a name="fillerror"></a>FillError  

 Le `DataAdapter` émet l'événement `FillError` en cas d'erreur pendant une opération `Fill`. Ce type d'erreur se produit habituellement lorsque les données ajoutées dans la ligne n'ont pas pu être converties en type .NET Framework sans perte de précision.  
  
 En cas d'erreur pendant une opération `Fill`, la ligne actuelle n'est pas ajoutée au `DataTable`. L'événement `FillError` vous permet de résoudre l'erreur et d'ajouter la ligne, ou d'ignorer la ligne exclue et de poursuivre l'opération `Fill`.  
  
 Le `FillErrorEventArgs` passé à l'événement `FillError` peut contenir plusieurs propriétés qui vous permettent de répondre aux erreurs et de les résoudre. Le tableau suivant présente les propriétés de l'objet `FillErrorEventArgs`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`Errors`|`Exception` survenue.|  
|`DataTable`|Objet `DataTable` en cours de remplissage au moment de l'erreur.|  
|`Values`|Tableau d'objets contenant les valeurs de la ligne qui était ajoutée au moment de l'erreur. Les références ordinales du tableau `Values` correspondent à celles des colonnes de la ligne ajoutée. Par exemple, `Values[0]` est la valeur qui a été ajoutée comme première colonne de la ligne.|  
|`Continue`|Vous permet de choisir la levée ou non d'une exception. L'affectation de la valeur `Continue` à la propriété `false` stoppe l'opération `Fill` en cours et une exception est levée. L'affectation de la valeur `Continue` à `true` poursuit l'opération `Fill` en dépit de l'erreur.|  
  
 L'exemple de code suivant ajoute l'événement `FillError` du `DataAdapter` à un gestionnaire d'événements. Dans le code d’événement `FillError`, l’exemple détermine s’il y a une possibilité de perte de précision, donnant ainsi l’opportunité de répondre à l’exception.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Gestion des événements de DataSet](./dataset-datatable-dataview/handling-dataset-events.md)
- [Gestion des événements de DataTable](./dataset-datatable-dataview/handling-datatable-events.md)
- [Événements](../../../standard/events/index.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
