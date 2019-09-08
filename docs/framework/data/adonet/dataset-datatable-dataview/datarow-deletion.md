---
title: Suppression de DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 3f48339539f08bbc1c2c15035741375bd9ade553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784721"
---
# <a name="datarow-deletion"></a>Suppression de DataRow
Il existe deux méthodes que vous pouvez utiliser pour supprimer <xref:System.Data.DataRow> un objet d' <xref:System.Data.DataTable> un objet : la méthode **Remove** de <xref:System.Data.DataRowCollection> l’objet et la <xref:System.Data.DataRow.Delete%2A> méthode de l’objet **DataRow** . Tandis <xref:System.Data.DataRowCollection.Remove%2A> que la méthode supprime un **DataRow** du **DataRowCollection**, la <xref:System.Data.DataRow.Delete%2A> méthode marque uniquement la ligne pour suppression. La suppression réelle se produit lorsque l’application appelle la méthode **AcceptChanges** . En utilisant <xref:System.Data.DataRow.Delete%2A>, vous pouvez vérifier par programme les lignes marquées pour suppression avant de les supprimer. Lorsqu'une ligne est marquée pour suppression, sa propriété <xref:System.Data.DataRow.RowState%2A> prend la valeur <xref:System.Data.DataRow.Delete%2A>.  
  
 Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne doivent être appelées dans une boucle foreach lors de l'itération au sein d'un objet <xref:System.Data.DataRowCollection>. Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne modifient l'état de la collection.  
  
 Lorsque vous utilisez <xref:System.Data.DataSet> un objet ou un **DataTable** conjointement avec un **DataAdapter** et une source de données relationnelle, utilisez la méthode **Delete** de **DataRow** pour supprimer la ligne. La méthode **Delete** marque la ligne comme étant **supprimée** dans le **DataSet** ou le **DataTable** , mais ne la supprime pas. Au lieu de cela, lorsque le **DataAdapter** rencontre une ligne marquée comme **Deleted**, il exécute sa méthode **DeleteCommand** pour supprimer la ligne au niveau de la source de données. La ligne peut ensuite être supprimée définitivement à l’aide de la méthode **AcceptChanges** . Si vous utilisez **Remove** pour supprimer la ligne, la ligne est entièrement supprimée de la table, mais le **DataAdapter** ne supprime pas la ligne au niveau de la source de données.  
  
 La méthode **Remove** du **DataRowCollection** prend un **DataRow** comme argument et le supprime de la collection, comme illustré dans l’exemple suivant.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 En revanche, l’exemple suivant montre comment appeler la méthode **Delete** sur un **DataRow** pour changer son **RowState** en **Deleted**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Si une ligne est marquée pour suppression et que vous appelez la méthode **AcceptChanges** de l’objet **DataTable** , la ligne est supprimée de la **table DataTable**. En revanche, si vous appelez **RejectChanges**, le **RowState** de la ligne revient à ce qu’il était avant d’être marqué comme **supprimé**.  
  
> [!NOTE]
> Si le **RowState** d’un **DataRow** est **ajouté**, ce qui signifie qu’il vient d’être ajouté à la table et qu’il est alors marqué comme **supprimé**, il est supprimé de la table.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Manipulation des données dans un DataTable](manipulating-data-in-a-datatable.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
