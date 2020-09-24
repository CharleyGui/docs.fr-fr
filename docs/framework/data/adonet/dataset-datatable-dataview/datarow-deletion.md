---
title: Suppression de DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 2092d7319a398bbdeaef764d677818f78ddf9de9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153350"
---
# <a name="datarow-deletion"></a>Suppression de DataRow

Il existe deux méthodes que vous pouvez utiliser pour supprimer un <xref:System.Data.DataRow> objet d’un <xref:System.Data.DataTable> objet : la méthode **Remove** de l' <xref:System.Data.DataRowCollection> objet et la <xref:System.Data.DataRow.Delete%2A> méthode de l’objet **DataRow** . Tandis que la <xref:System.Data.DataRowCollection.Remove%2A> méthode supprime un **DataRow** du **DataRowCollection**, la <xref:System.Data.DataRow.Delete%2A> méthode marque uniquement la ligne pour suppression. La suppression réelle se produit lorsque l’application appelle la méthode **AcceptChanges** . En utilisant <xref:System.Data.DataRow.Delete%2A>, vous pouvez vérifier par programme les lignes marquées pour suppression avant de les supprimer. Lorsqu'une ligne est marquée pour suppression, sa propriété <xref:System.Data.DataRow.RowState%2A> prend la valeur <xref:System.Data.DataRow.Delete%2A>.  
  
 Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne doivent être appelées dans une boucle foreach lors de l'itération au sein d'un objet <xref:System.Data.DataRowCollection>. Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne modifient l'état de la collection.  
  
 Lorsque vous utilisez un objet <xref:System.Data.DataSet> ou un **DataTable** conjointement avec un **DataAdapter** et une source de données relationnelle, utilisez la méthode **Delete** de **DataRow** pour supprimer la ligne. La méthode **Delete** marque la ligne comme étant **supprimée** dans le **DataSet** ou le **DataTable** , mais ne la supprime pas. Au lieu de cela, lorsque le **DataAdapter** rencontre une ligne marquée comme **Deleted**, il exécute sa méthode **DeleteCommand** pour supprimer la ligne au niveau de la source de données. La ligne peut ensuite être supprimée définitivement à l’aide de la méthode **AcceptChanges** . Si vous utilisez **Remove** pour supprimer la ligne, la ligne est entièrement supprimée de la table, mais le **DataAdapter** ne supprime pas la ligne au niveau de la source de données.  
  
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
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
