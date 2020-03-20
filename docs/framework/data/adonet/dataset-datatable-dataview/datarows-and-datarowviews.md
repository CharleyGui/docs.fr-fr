---
title: DataRows et DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 14e7e1ccb051410c351e49afee9f2d6809264833
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151297"
---
# <a name="datarows-and-datarowviews"></a>DataRows et DataRowViews
Un objet <xref:System.Data.DataView> expose une collection énumérable d’objets <xref:System.Data.DataRowView>. Les objets **DataRowView** exposent les valeurs comme des tableaux d’objets qui sont indexés par le nom ou la référence ordinaire de la colonne dans le tableau sous-jacent. Vous pouvez <xref:System.Data.DataRow> accéder à celui qui est exposé <xref:System.Data.DataRowView.Row%2A> par le **DataRowView** en utilisant la propriété de la **DataRowView**.  
  
 Lorsque vous affichez les valeurs en <xref:System.Data.DataView.RowStateFilter%2A> utilisant un **DataRowView**, la propriété de **dataView** détermine quelle version de ligne de la **DataRow** sous-jacente est exposée. Pour plus d’informations sur l’accès à différentes versions de ligne à l’aide d’un **DataRow**, voir [Row States et Row Versions](row-states-and-row-versions.md).  
  
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
