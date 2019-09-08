---
title: Création d'un DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 3e1c31dac458594eee70ddd99469aca7cf63b848
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785476"
---
# <a name="creating-a-dataview"></a>Création d'un DataView
Il existe deux façons de créer un objet <xref:System.Data.DataView>. Vous pouvez utiliser le constructeur **DataView** , ou vous pouvez créer une référence à la <xref:System.Data.DataTable.DefaultView%2A> propriété de <xref:System.Data.DataTable>. Le constructeur **DataView** peut être vide, ou il peut accepter soit un **DataTable** comme argument unique, soit un **DataTable** avec des critères de filtre, des critères de tri et un filtre d’état de ligne. Pour plus d’informations sur les arguments supplémentaires disponibles pour une utilisation avec le **DataView**, consultez [Tri et filtrage des données](sorting-and-filtering-data.md).  
  
 Étant donné que l’index d’un **DataView** est construit à la fois lors de la création du **DataView** et lorsque l’une des propriétés **sort**, **RowFilter**ou **RowStateFilter** est modifiée, vous obtenez des performances optimales en fournissant les ordre de tri ou critères de filtrage en tant qu’arguments de constructeur lorsque vous créez le **DataView**. La création d’un **DataView** sans spécifier de critère de tri ou de filtre et la définition ultérieure des propriétés **sort**, **RowFilter**ou **RowStateFilter** entraînent la génération ultérieure de l’index au moins deux fois : une fois quand le **DataView** est créé, puis à nouveau lorsque l’une des propriétés de tri ou de filtre est modifiée.  
  
 Notez que si vous créez un **DataView** à l’aide du constructeur qui ne prend aucun argument, vous ne pourrez pas utiliser le **DataView** tant que vous n’aurez pas défini la propriété de **table** .  
  
 L’exemple de code suivant montre comment créer un **DataView** à l’aide du constructeur **DataView** . Un **RowFilter**, une colonne de **Tri** et un **DataViewRowState** sont fournis avec le **DataTable**.  
  
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
  
 L’exemple de code suivant montre comment obtenir une référence au **DataView** par défaut d’un **DataTable** à l’aide de la propriété **DefaultView** de la table.  
  
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
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
