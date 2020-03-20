---
title: Ajout de données à un DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 02d7f94259cc56513be404c5539ca7015d5f3533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151531"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="9c94f-102">Ajout de données à un DataTable</span><span class="sxs-lookup"><span data-stu-id="9c94f-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="9c94f-103">Après avoir créé un objet <xref:System.Data.DataTable> et défini sa structure à l'aide de colonnes et de contraintes, vous pouvez ajouter de nouvelles lignes de données à la table.</span><span class="sxs-lookup"><span data-stu-id="9c94f-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="9c94f-104">Pour ajouter une nouvelle ligne, déclarez une nouvelle variable comme type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="9c94f-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="9c94f-105">Un nouvel objet **DataRow** est <xref:System.Data.DataTable.NewRow%2A> retourné lorsque vous appelez la méthode.</span><span class="sxs-lookup"><span data-stu-id="9c94f-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="9c94f-106">Le **DataTable** crée ensuite l’objet **DataRow** en fonction de <xref:System.Data.DataColumnCollection>la structure de la table, tel que défini par le .</span><span class="sxs-lookup"><span data-stu-id="9c94f-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="9c94f-107">L’exemple suivant montre comment créer une nouvelle ligne en appelant la méthode **NewRow.**</span><span class="sxs-lookup"><span data-stu-id="9c94f-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="9c94f-108">Vous pouvez ensuite manipuler la ligne ajoutée en utilisant un index ou le nom de colonne, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9c94f-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="9c94f-109">Une fois que les données sont **Add** insérées dans la nouvelle <xref:System.Data.DataRowCollection>ligne, la méthode Add est utilisée pour ajouter la ligne au , indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9c94f-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="9c94f-110">Vous pouvez également appeler la méthode **Add** pour ajouter une nouvelle ligne <xref:System.Object>en passant dans un tableau de valeurs, tapé comme , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9c94f-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="9c94f-111">En passant un tableau de valeurs, tapé comme **objet,** à la méthode **Add** crée une nouvelle ligne à l’intérieur de la table et définit ses valeurs de colonne aux valeurs dans le tableau d’objets.</span><span class="sxs-lookup"><span data-stu-id="9c94f-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="9c94f-112">Notez que les valeurs du tableau correspondent de façon séquentielle aux colonnes, en fonction de leur ordre d'apparition dans la table.</span><span class="sxs-lookup"><span data-stu-id="9c94f-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="9c94f-113">L’exemple suivant ajoute 10 lignes à la table **des clients** nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="9c94f-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c94f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c94f-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="9c94f-115">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="9c94f-115">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="9c94f-116">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9c94f-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
