---
title: DataRows et DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: bce90c1d310178e66da7c758c6df2cd357199c8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153285"
---
# <a name="datarows-and-datarowviews"></a>DataRows et DataRowViews

Un objet <xref:System.Data.DataView> expose une collection énumérable d’objets <xref:System.Data.DataRowView>. Les objets **DataRowView** exposent des valeurs en tant que tableaux d’objets indexés par le nom ou la référence ordinale de la colonne dans la table sous-jacente. Vous pouvez accéder au <xref:System.Data.DataRow> qui est exposé par le **DataRowView** à l’aide <xref:System.Data.DataRowView.Row%2A> de la propriété du **DataRowView**.  
  
 Lorsque vous affichez des valeurs à l’aide d’un **DataRowView**, la <xref:System.Data.DataView.RowStateFilter%2A> propriété du **DataView** détermine la version de ligne du **DataRow** sous-jacent qui est exposée. Pour plus d’informations sur l’accès à différentes versions de ligne à l’aide d’un **DataRow**, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).  
  
 L'exemple de code suivant affiche toutes les valeurs actuelles et d'origine d'une table.  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
