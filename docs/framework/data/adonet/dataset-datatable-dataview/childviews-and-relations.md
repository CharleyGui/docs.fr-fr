---
title: ChildView et relations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d475d356-6abb-4701-8fd1-2906fb93dfba
ms.openlocfilehash: 74b2de7a9ee62ae42a932c94261cf425d6a94808
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203733"
---
# <a name="childviews-and-relations"></a><span data-ttu-id="489d3-102">ChildView et relations</span><span class="sxs-lookup"><span data-stu-id="489d3-102">ChildViews and Relations</span></span>

<span data-ttu-id="489d3-103">S'il existe une relation entre différentes tables d'un objet <xref:System.Data.DataSet>, vous pouvez créer un objet <xref:System.Data.DataView> contenant des lignes de la table enfant connexe à l'aide de la méthode <xref:System.Data.DataRowView.CreateChildView%2A> de l'objet <xref:System.Data.DataRowView> pour les lignes de la table parente.</span><span class="sxs-lookup"><span data-stu-id="489d3-103">If a relationship exists between tables in a <xref:System.Data.DataSet>, you can create a <xref:System.Data.DataView> containing rows from the related child table by using the <xref:System.Data.DataRowView.CreateChildView%2A> method of the <xref:System.Data.DataRowView> for the rows in the parent table.</span></span> <span data-ttu-id="489d3-104">Par exemple, le code suivant affiche les **catégories** et leurs **produits** associés par ordre alphabétique, triés par **CategoryName** et **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="489d3-104">For example, the following code displays **Categories** and their related **Products** in alphabetical order sorted by **CategoryName** and **ProductName**.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
Dim prodTable As DataTable = catDS.Tables("Products")  
  
' Create a relation between the Categories and Products tables.  
Dim relation As DataRelation = catDS.Relations.Add("CatProdRel", _  
  catTable.Columns("CategoryID"), _  
  prodTable.Columns("CategoryID"))  
  
' Create DataViews for the Categories and Products tables.  
Dim catView As DataView = New DataView(catTable, "", _  
  "CategoryName", DataViewRowState.CurrentRows)  
Dim prodView As DataView  
  
' Iterate through the Categories table.  
Dim catDRV, prodDRV As DataRowView  
  
For Each catDRV In catView  
  Console.WriteLine(catDRV("CategoryName"))  
  
  ' Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation)  
  prodView.Sort = "ProductName"  
  
  For Each prodDRV In prodView  
    Console.WriteLine(vbTab & prodDRV("ProductName"))  
  Next  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
DataTable prodTable = catDS.Tables["Products"];  
  
// Create a relation between the Categories and Products tables.  
DataRelation relation = catDS.Relations.Add("CatProdRel",
  catTable.Columns["CategoryID"],  
                                                            prodTable.Columns["CategoryID"]);  
  
// Create DataViews for the Categories and Products tables.  
DataView catView = new DataView(catTable, "", "CategoryName",
  DataViewRowState.CurrentRows);  
DataView prodView;  
  
// Iterate through the Categories table.  
foreach (DataRowView catDRV in catView)  
{  
  Console.WriteLine(catDRV["CategoryName"]);  
  
  // Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation);  
  prodView.Sort = "ProductName";  
  
  foreach (DataRowView prodDRV in prodView)  
    Console.WriteLine("\t" + prodDRV["ProductName"]);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="489d3-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="489d3-105">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="489d3-106">DataViews</span><span class="sxs-lookup"><span data-stu-id="489d3-106">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="489d3-107">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="489d3-107">ADO.NET Overview</span></span>](../ado-net-overview.md)
