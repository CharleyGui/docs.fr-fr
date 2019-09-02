---
title: Suppression de DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 46109ee1781b8b509df87b4203c51a55b9f596ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205105"
---
# <a name="datarow-deletion"></a><span data-ttu-id="14808-102">Suppression de DataRow</span><span class="sxs-lookup"><span data-stu-id="14808-102">DataRow Deletion</span></span>
<span data-ttu-id="14808-103">Il existe deux méthodes que vous pouvez utiliser pour supprimer <xref:System.Data.DataRow> un objet d' <xref:System.Data.DataTable> un objet: la méthode **Remove** de <xref:System.Data.DataRowCollection> l’objet et la <xref:System.Data.DataRow.Delete%2A> méthode de l’objet **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="14808-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="14808-104">Tandis <xref:System.Data.DataRowCollection.Remove%2A> que la méthode supprime un **DataRow** du **DataRowCollection**, la <xref:System.Data.DataRow.Delete%2A> méthode marque uniquement la ligne pour suppression.</span><span class="sxs-lookup"><span data-stu-id="14808-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="14808-105">La suppression réelle se produit lorsque l’application appelle la méthode **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="14808-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="14808-106">En utilisant <xref:System.Data.DataRow.Delete%2A>, vous pouvez vérifier par programme les lignes marquées pour suppression avant de les supprimer.</span><span class="sxs-lookup"><span data-stu-id="14808-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="14808-107">Lorsqu'une ligne est marquée pour suppression, sa propriété <xref:System.Data.DataRow.RowState%2A> prend la valeur <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="14808-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="14808-108">Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne doivent être appelées dans une boucle foreach lors de l'itération au sein d'un objet <xref:System.Data.DataRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="14808-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="14808-109">Ni <xref:System.Data.DataRow.Delete%2A> ni <xref:System.Data.DataRowCollection.Remove%2A> ne modifient l'état de la collection.</span><span class="sxs-lookup"><span data-stu-id="14808-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="14808-110">Lorsque vous utilisez <xref:System.Data.DataSet> un objet ou un **DataTable** conjointement avec un **DataAdapter** et une source de données relationnelle, utilisez la méthode **Delete** de **DataRow** pour supprimer la ligne.</span><span class="sxs-lookup"><span data-stu-id="14808-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="14808-111">La méthode **Delete** marque la ligne comme étant **supprimée** dans le **DataSet** ou le **DataTable** , mais ne la supprime pas.</span><span class="sxs-lookup"><span data-stu-id="14808-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="14808-112">Au lieu de cela, lorsque le **DataAdapter** rencontre une ligne marquéecomme Deleted, il exécute sa méthode **DeleteCommand** pour supprimer la ligne au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="14808-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="14808-113">La ligne peut ensuite être supprimée définitivement à l’aide de la méthode **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="14808-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="14808-114">Si vous utilisez **Remove** pour supprimer la ligne, la ligne est entièrement supprimée de la table, mais le **DataAdapter** ne supprime pas la ligne au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="14808-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="14808-115">La méthode **Remove** du **DataRowCollection** prend un **DataRow** comme argument et le supprime de la collection, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="14808-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="14808-116">En revanche, l’exemple suivant montre comment appeler la méthode **Delete** sur un **DataRow** pour changer son **RowState** en **Deleted**.</span><span class="sxs-lookup"><span data-stu-id="14808-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="14808-117">Si une ligne est marquée pour suppression et que vous appelez la méthode **AcceptChanges** de l’objet **DataTable** , la ligne est supprimée de la **table DataTable**.</span><span class="sxs-lookup"><span data-stu-id="14808-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="14808-118">En revanche, si vous appelez **RejectChanges**, le **RowState** de la ligne revient à ce qu’il était avant d’être marqué comme **supprimé**.</span><span class="sxs-lookup"><span data-stu-id="14808-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14808-119">Si le **RowState** d’un **DataRow** est **ajouté**, ce qui signifie qu’il vient d’être ajouté à la table et qu’il est alors marqué comme **supprimé**, il est supprimé de la table.</span><span class="sxs-lookup"><span data-stu-id="14808-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14808-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14808-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="14808-121">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="14808-121">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="14808-122">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="14808-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
