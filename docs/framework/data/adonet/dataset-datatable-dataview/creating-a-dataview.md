---
title: Création d'un DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151336"
---
# <a name="creating-a-dataview"></a>Création d'un DataView
Il existe deux façons de créer un objet <xref:System.Data.DataView>. Vous pouvez utiliser le constructeur **DataView,** ou vous <xref:System.Data.DataTable.DefaultView%2A> pouvez <xref:System.Data.DataTable>créer une référence à la propriété de la . Le constructeur **DataView** peut être vide, soit il peut prendre soit un **DataTable** comme un seul argument, ou un **DataTable** avec des critères de filtre, des critères de tri, et un filtre d’état de ligne. Pour plus d’informations sur les arguments supplémentaires disponibles pour une utilisation avec le **DataView**, voir [Les données de tri et de filtrage](sorting-and-filtering-data.md).  
  
 Parce que l’index d’un **DataView** est construit à la fois lorsque le **DataView** est créé, et lorsque l’une des propriétés **Sort**, **RowFilter**, ou **RowStateFilter** sont modifiées, vous obtenez les meilleures performances en fournissant n’importe quel ordre de tri initial ou des critères de filtrage comme arguments constructeurs lorsque vous créez le **DataView**. La création **d’un DataView** sans spécifier les critères de tri ou de filtre, puis la définition des propriétés **Sort,** **RowFilter**, ou **RowStateFilter** provoque plus tard l’index à être construit au moins deux fois: une fois lorsque le **DataView** est créé, et encore une fois lorsque l’une des propriétés de type ou de filtre sont modifiées.  
  
 Notez que si vous créez un **DataView** à l’aide du constructeur qui ne prend aucun argument, vous ne serez pas en mesure d’utiliser le **DataView** jusqu’à ce que vous avez défini la propriété **Table.**  
  
 L’exemple de code suivant montre comment créer un **DataView** à l’aide du constructeur **DataView.** A **RowFilter**, **Sort** column, et **DataViewRowState** sont fournis avec le **DataTable**.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 L’exemple de code suivant montre comment obtenir une référence à la **DataView** par défaut d’un **DataTable** utilisant la propriété **DefaultView** de la table.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [Tri et filtre de données](sorting-and-filtering-data.md)
- [DataTables](datatables.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
