---
title: Modifications de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 4fdb19e7fa014bf4a7c924b1fbae53fa44de6e3c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153259"
---
# <a name="datatable-edits"></a>Modifications de DataTable

Lorsque vous modifiez les valeurs de colonne d'un objet <xref:System.Data.DataRow>, les modifications sont immédiatement placées dans l'état actuel de la ligne. <xref:System.Data.DataRowState>Est ensuite défini sur **modifié**, et les modifications sont acceptées ou rejetées à l' <xref:System.Data.DataRow.AcceptChanges%2A> aide <xref:System.Data.DataRow.RejectChanges%2A> des méthodes ou du **DataRow**. Le **DataRow** fournit également trois méthodes que vous pouvez utiliser pour suspendre l’état de la ligne pendant que vous la modifiez. Ces méthodes sont <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> et <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Lorsque vous modifiez directement les valeurs de colonne dans un **DataRow** , **DataRow** gère les valeurs de colonne à l’aide des versions de ligne **actuelles**, **par défaut**et **d’origine** . En plus de ces versions de ligne, les méthodes **BeginEdit**, **EndEdit**et **CancelEdit** utilisent une quatrième version de ligne : **Proposed**. Pour plus d’informations sur les versions de ligne, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).  
  
 La version de ligne **proposée** existe pendant une opération de modification qui commence par appeler **BeginEdit** et qui se termine à l’aide de **EndEdit** ou **CancelEdit,** ou en appelant **AcceptChanges** ou **RejectChanges**.  
  
 Pendant l’opération de modification, vous pouvez appliquer la logique de validation à des colonnes individuelles en évaluant le **ProposedValue** dans l’événement **ColumnChanged** du **DataTable**. L’événement **ColumnChanged** contient des **DataColumnChangeEventArgs** qui maintiennent une référence à la colonne qui change et à **ProposedValue**. Après avoir évalué la valeur proposée, vous pouvez la modifier ou annuler la modification. Lorsque la modification est terminée, la ligne passe de l’état **proposé** .  
  
 Vous pouvez confirmer les modifications en appelant **EndEdit**, ou vous pouvez les annuler en appelant **CancelEdit**. Notez que si **EndEdit** confirme vos modifications, le **DataSet** n’accepte pas réellement les modifications tant que **AcceptChanges** n’est pas appelé. Notez également que si vous appelez **AcceptChanges** avant de mettre fin à la modification avec **EndEdit** ou **CancelEdit**, la modification est terminée et les valeurs de ligne **proposées** sont acceptées pour les versions de ligne **actuelles** et **d’origine** . De la même manière, l’appel de **RejectChanges** met fin à la modification et ignore les versions de ligne **actuelles** et **proposées** . L’appel de **EndEdit** ou **CancelEdit** après l’appel à **AcceptChanges** ou **RejectChanges** n’a aucun effet, car la modification est déjà terminée.  
  
 L’exemple suivant montre comment utiliser **BeginEdit** avec **EndEdit** et **CancelEdit**. L’exemple vérifie également le **ProposedValue** dans l’événement **ColumnChanged** et décide s’il faut annuler la modification.  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [Manipulation des données dans un DataTable](manipulating-data-in-a-datatable.md)
- [Gestion des événements de DataTable](handling-datatable-events.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
