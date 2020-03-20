---
title: Modifications de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151258"
---
# <a name="datatable-edits"></a>Modifications de DataTable
Lorsque vous modifiez les valeurs de colonne d'un objet <xref:System.Data.DataRow>, les modifications sont immédiatement placées dans l'état actuel de la ligne. Le <xref:System.Data.DataRowState> est ensuite réglé sur **modifié**, et <xref:System.Data.DataRow.AcceptChanges%2A> les <xref:System.Data.DataRow.RejectChanges%2A> modifications sont acceptées ou rejetées en utilisant le ou les méthodes de la **DataRow**. Le **DataRow** fournit également trois méthodes que vous pouvez utiliser pour suspendre l’état de la ligne pendant que vous l’éditez. Ces méthodes sont <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> et <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Lorsque vous modifiez directement les valeurs de colonne dans un **DataRow,** **dataRow** gère les valeurs de colonnes à l’aide des versions **actuelles,** **par défaut**et **lignes d’origine.** En plus de ces versions de ligne, les méthodes **BeginEdit**, **EndEdit**et **CancelEdit** utilisent une version de quatrième rangée : **Proposed**. Pour plus d’informations sur les versions de ligne, voir [Row States et Row Versions](row-states-and-row-versions.md).  
  
 La version de ligne **proposée** existe au cours d’une opération de modification qui commence par appeler **BeginEdit** et qui se termine soit en utilisant **EndEdit** ou **CancelEdit,** ou en appelant **AcceptChanges** ou **RejectChanges**.  
  
 Pendant l’opération de modification, vous pouvez appliquer la logique de validation à des colonnes individuelles en évaluant la **Proposition dans** l’événement **ColumnChanged** de la **Table de données**. **L’événement ColumnChanged** détient **DataColumnChangeEventArgs** qui gardent une référence à la colonne qui change et à la **Proposition .** Après avoir évalué la valeur proposée, vous pouvez la modifier ou annuler la modification. Lorsque l’édition est terminée, la ligne sort de l’état **proposé.**  
  
 Vous pouvez confirmer les modifications en appelant **EndEdit**, ou vous pouvez les annuler en appelant **CancelEdit**. Notez que si **EndEdit** confirme vos modifications, le **DataSet** n’accepte pas réellement les modifications jusqu’à ce qu’AcceptChanges soit appelé. **AcceptChanges** Notez également que si vous appelez **AcceptChanges** avant d’avoir terminé le montage avec **EndEdit** ou **CancelEdit**, le montage est terminé et les valeurs de ligne **proposées** sont acceptées pour les versions de ligne **actuelle** et **originale.** De la même manière, appeler **RejectChanges** met fin à l’édition et rejette les versions de ligne **actuelles** et **proposées.** Appeler **EndEdit** ou **CancelEdit** après avoir appelé **AcceptChanges** ou **RejectChanges** n’a aucun effet parce que le montage a déjà pris fin.  
  
 L’exemple suivant montre comment utiliser **BeginEdit** avec **EndEdit** et **CancelEdit**. L’exemple vérifie également la **proposition dans** l’événement **ColumnChanged** et décide d’annuler ou non la modification.  
  
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
