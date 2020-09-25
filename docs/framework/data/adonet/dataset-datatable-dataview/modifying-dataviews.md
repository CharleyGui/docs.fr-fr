---
title: Modification des DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 8e3a3f92fe8ecc94a041fbcb1540bae18a41dbef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203681"
---
# <a name="modifying-dataviews"></a>Modification des DataViews

Vous pouvez utiliser l'objet <xref:System.Data.DataView> pour ajouter, supprimer ou modifier des lignes de données dans la table sous-jacente. La possibilité d’utiliser le **DataView** pour modifier les données dans la table sous-jacente est contrôlée par la définition de l’une des trois propriétés booléennes du **DataView**. Ces propriétés sont <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> et <xref:System.Data.DataView.AllowDelete%2A>. Elles ont la valeur **true** par défaut.  
  
 Si **AllowNew** a la **valeur true**, vous pouvez utiliser la <xref:System.Data.DataView.AddNew%2A> méthode du **DataView** pour créer un nouveau <xref:System.Data.DataRowView> . Notez qu’une nouvelle ligne n’est pas réellement ajoutée au sous-jacent <xref:System.Data.DataTable> tant que la <xref:System.Data.DataRowView.EndEdit%2A> méthode du **DataRowView** n’a pas été appelée. Si la <xref:System.Data.DataRowView.CancelEdit%2A> méthode du **DataRowView** est appelée, la nouvelle ligne est ignorée. Notez également que vous ne pouvez modifier qu’un seul **DataRowView** à la fois. Si vous appelez la méthode **AddNew** ou **BeginEdit** du **DataRowView** alors qu’une ligne en attente existe, la méthode **EndEdit** est implicitement appelée sur la ligne en attente. Lorsque la méthode **EndEdit** est appelée, les modifications sont appliquées au **DataTable** sous-jacent et peuvent être validées ou refusées ultérieurement à l’aide des méthodes **AcceptChanges** ou **RejectChanges** de l’objet **DataTable**, **DataSet**ou **DataRow** . Si **AllowNew** a la **valeur false**, une exception est levée si vous appelez la méthode **AddNew** du **DataRowView**.  
  
 Si **AllowEdit** a la **valeur true**, vous pouvez modifier le contenu d’un **DataRow** via le **DataRowView**. Vous pouvez confirmer les modifications apportées à la ligne sous-jacente à l’aide de **DataRowView. EndEdit** ou refuser les modifications à l’aide de **DataRowView. CancelEdit**. Notez que vous ne pouvez modifier qu'une seule ligne à la fois. Si vous appelez les méthodes **AddNew** ou **BeginEdit** du **DataRowView** alors qu’une ligne en attente existe, la méthode **EndEdit** est implicitement appelée sur la ligne en attente. Lorsque la méthode **EndEdit** est appelée, les modifications proposées sont placées dans la version de ligne **actuelle** du **DataRow** sous-jacent et peuvent être validées ou rejetées ultérieurement à l’aide des méthodes **AcceptChanges** ou **RejectChanges** de l’objet **DataTable**, **DataSet**ou **DataRow** . Si **AllowEdit** a la valeur **false**, une exception est levée si vous tentez de modifier une valeur dans le **DataView**.  
  
 Lorsqu’un **DataRowView** existant est en cours de modification, les événements du **DataTable** sous-jacent sont toujours déclenchés avec les modifications proposées. Notez que si vous appelez **EndEdit** ou **CancelEdit** sur le **DataRow**sous-jacent, les modifications en attente seront appliquées ou annulées, que la méthode **EndEdit** ou **CancelEdit** soit appelée sur le **DataRowView**ou non.  
  
 Si **AllowDelete** a la **valeur true**, vous pouvez supprimer des lignes du **DataView** à l’aide de la méthode **Delete** de l’objet **DataView** ou **DataRowView** , et les lignes sont supprimées du **DataTable**sous-jacent. Vous pouvez par la suite valider ou refuser les suppressions à l’aide de **AcceptChanges** ou de **RejectChanges** respectivement. Si **AllowDelete** a la **valeur false**, une exception est levée si vous appelez la méthode **Delete** du **DataView** ou **DataRowView**.  
  
 L’exemple de code suivant désactive l’utilisation du **DataView** pour supprimer des lignes et ajoute une nouvelle ligne à la table sous-jacente à l’aide du **DataView**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
