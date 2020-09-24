---
title: Ajout de données à un DataTable
description: Reportez-vous à cet exemple de code pour ajouter de nouvelles lignes de données à une table dans ADO.NET, après avoir créé un DataTable et défini sa structure à l’aide de colonnes et de contraintes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: aac2d90cc57a4af823c42f8c7eb2adcd43c63caf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164816"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="8f8f9-103">Ajout de données à un DataTable</span><span class="sxs-lookup"><span data-stu-id="8f8f9-103">Adding Data to a DataTable</span></span>

<span data-ttu-id="8f8f9-104">Après avoir créé un objet <xref:System.Data.DataTable> et défini sa structure à l'aide de colonnes et de contraintes, vous pouvez ajouter de nouvelles lignes de données à la table.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-104">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="8f8f9-105">Pour ajouter une nouvelle ligne, déclarez une nouvelle variable comme type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-105">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="8f8f9-106">Un nouvel objet **DataRow** est retourné lorsque vous appelez la <xref:System.Data.DataTable.NewRow%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-106">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="8f8f9-107">Le **DataTable** crée ensuite l’objet **DataRow** en fonction de la structure de la table, comme défini par <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="8f8f9-107">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="8f8f9-108">L’exemple suivant montre comment créer une nouvelle ligne en appelant la méthode **NewRow** .</span><span class="sxs-lookup"><span data-stu-id="8f8f9-108">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="8f8f9-109">Vous pouvez ensuite manipuler la ligne ajoutée en utilisant un index ou le nom de colonne, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-109">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="8f8f9-110">Une fois que les données sont insérées dans la nouvelle ligne, la méthode **Add** est utilisée pour ajouter la ligne à <xref:System.Data.DataRowCollection> , comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-110">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="8f8f9-111">Vous pouvez également appeler la méthode **Add** pour ajouter une nouvelle ligne en passant un tableau de valeurs, de type <xref:System.Object> , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-111">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="8f8f9-112">Le passage d’un tableau de valeurs, typé en tant qu' **objet**, à la méthode **Add** crée une nouvelle ligne à l’intérieur de la table et définit ses valeurs de colonne avec les valeurs du tableau d’objets.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-112">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="8f8f9-113">Notez que les valeurs du tableau correspondent de façon séquentielle aux colonnes, en fonction de leur ordre d'apparition dans la table.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-113">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="8f8f9-114">L’exemple suivant ajoute 10 lignes à la table **Customers** nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="8f8f9-114">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f8f9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f8f9-115">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="8f8f9-116">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="8f8f9-116">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="8f8f9-117">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8f8f9-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
