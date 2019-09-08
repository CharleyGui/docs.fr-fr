---
title: Informations sur l'erreur de ligne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 5ede6e2cd52ad55f8c35a42d137044dd1ceea400
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785956"
---
# <a name="row-error-information"></a><span data-ttu-id="4fc90-102">Informations sur l'erreur de ligne</span><span class="sxs-lookup"><span data-stu-id="4fc90-102">Row Error Information</span></span>
<span data-ttu-id="4fc90-103">Pour éviter d'avoir à répondre chaque fois qu'une erreur de ligne se produit pendant que vous modifiez des valeurs dans un objet <xref:System.Data.DataTable>, vous pouvez ajouter les informations d'erreur à la ligne pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="4fc90-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="4fc90-104">L'objet <xref:System.Data.DataRow> fournit une propriété <xref:System.Data.DataRow.RowError%2A> sur chaque ligne à cette fin.</span><span class="sxs-lookup"><span data-stu-id="4fc90-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="4fc90-105">L’ajout de données à la propriété **RowError** d’un **DataRow** affecte la <xref:System.Data.DataRow.HasErrors%2A> **valeur true**à la propriété du **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="4fc90-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="4fc90-106">Si le **DataRow** fait partie d’un **DataTable**et que **DataRow. HasErrors** a la **valeur true**, la propriété **DataTable. HasErrors** a également la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="4fc90-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="4fc90-107">Cela s’applique également au **jeu de données** auquel le **DataTable** appartient.</span><span class="sxs-lookup"><span data-stu-id="4fc90-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="4fc90-108">Lors du test des erreurs, vous pouvez vérifier la propriété **HasErrors** pour déterminer si des informations d’erreur ont été ajoutées à des lignes.</span><span class="sxs-lookup"><span data-stu-id="4fc90-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="4fc90-109">Si **HasErrors** a la **valeur true**, vous pouvez <xref:System.Data.DataTable.GetErrors%2A> utiliser la méthode de l’objet **DataTable** pour retourner et examiner uniquement les lignes comportant des erreurs, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4fc90-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fc90-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fc90-110">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="4fc90-111">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="4fc90-111">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="4fc90-112">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4fc90-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
