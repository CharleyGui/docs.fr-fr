---
title: AcceptChanges et RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: c537fa808fc6ba4c740e71bfd70fe9cd1f3bd31a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785562"
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges et RejectChanges
Après avoir vérifié l’exactitude des modifications apportées aux données <xref:System.Data.DataTable>dans un, vous pouvez accepter les modifications <xref:System.Data.DataRow.AcceptChanges%2A> à l’aide <xref:System.Data.DataRow>de la méthode <xref:System.Data.DataSet>de, <xref:System.Data.DataTable>ou, qui définira les valeurs de ligne **actuelles** sur  **Les valeurs d’origine** et définissent la propriété **RowState** sur **Unchanged**. L’acceptation ou le rejet des modifications efface toutes les informations **RowError** et affecte la **valeur false**à la propriété **HasErrors** . L'acceptation ou le rejet des modifications peut également affecter la mise à jour des données dans la source de données. Pour plus d’informations, consultez [mise à jour des sources de données avec les DataAdapters](../updating-data-sources-with-dataadapters.md).  
  
 S’il existe des contraintes de clé étrangère sur le **DataTable**, les modifications acceptées ou rejetées à l’aide de **AcceptChanges** et **RejectChanges** sont propagées aux lignes enfants du **DataRow** en fonction de  **ForeignKeyConstraint. AcceptRejectRule**. Pour plus d’informations, consultez [contraintes de DataTable](datatable-constraints.md).  
  
 L'exemple suivant vérifie les lignes ayant des erreurs, résout, le cas échéant, les erreurs et rejette les lignes dans lesquelles les erreurs ne peuvent pas être résolues. Notez que, pour les erreurs résolues, la valeur **RowError** est réinitialisée à une chaîne vide, ce qui entraîne la définition de la propriété **HasErrors** sur **false**. Lorsque toutes les lignes contenant des erreurs ont été résolues ou rejetées, **AcceptChanges** est appelé pour accepter toutes les modifications pour l’ensemble du **DataTable**.  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Manipulation des données dans un DataTable](manipulating-data-in-a-datatable.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
