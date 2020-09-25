---
title: États des lignes et versions des lignes
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 1b80ae78fad22989f99fb1e992d4978a192e0c66
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204526"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="2eaa3-102">États des lignes et versions des lignes</span><span class="sxs-lookup"><span data-stu-id="2eaa3-102">Row States and Row Versions</span></span>

<span data-ttu-id="2eaa3-103">ADO.NET gère les lignes des tables à l'aide des états et des versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="2eaa3-104">Un état de ligne indique le statut d'une ligne ; les versions de ligne conservent les valeurs stockées dans une ligne pendant leur modification, notamment les valeurs actuelles, d'origine et par défaut.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="2eaa3-105">Par exemple, une fois qu'une modification a été apportée à une colonne dans une ligne, la ligne possède un état de ligne `Modified` et deux versions de ligne : `Current`, qui contient les valeurs de ligne actuelles et `Original`, qui renferme les valeurs de ligne avant la modification de la colonne.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="2eaa3-106">Chaque objet <xref:System.Data.DataRow> a la propriété <xref:System.Data.DataRow.RowState%2A> que vous pouvez examiner pour déterminer l'état actuel de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="2eaa3-107">Le tableau suivant fournit une brève description de chacune des valeurs d'énumération `RowState`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="2eaa3-108">Valeur RowState</span><span class="sxs-lookup"><span data-stu-id="2eaa3-108">RowState value</span></span>|<span data-ttu-id="2eaa3-109">Description</span><span class="sxs-lookup"><span data-stu-id="2eaa3-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="2eaa3-110">Aucune modification n'a été apportée depuis le dernier appel à `AcceptChanges` ou depuis la création de la ligne par `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="2eaa3-111">La ligne a été ajoutée à la table mais la `AcceptChanges` n'a pas été appelé.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="2eaa3-112">Certains éléments de la ligne ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="2eaa3-113">La ligne a été supprimée d'une table et `AcceptChanges` n'a pas été appelé.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="2eaa3-114">La ligne ne fait partie d'aucun `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="2eaa3-115">Le `RowState` d'une ligne nouvellement créée prend la valeur `Detached`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="2eaa3-116">Une fois le `DataRow` ajouté au `DataRowCollection` à l'aide de l'appel à la méthode `Add`, la propriété `RowState` prend la valeur `Added`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="2eaa3-117">`Detached` est également défini pour une ligne qui a été supprimée d'un `DataRowCollection` à l'aide de la méthode `Remove` ou par la méthode `Delete` suivie de la méthode `AcceptChanges`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="2eaa3-118">Lorsque `AcceptChanges` est appelé sur un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou sur un <xref:System.Data.DataRow>, toutes les lignes avec un état de ligne `Deleted` sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="2eaa3-119">Un état de ligne `Unchanged` est attribué aux autres lignes et les valeurs de la version de ligne `Original` sont remplacées par celles de la version de ligne `Current`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="2eaa3-120">Lorsque `RejectChanges` est appelé, toutes les lignes avec un état de ligne `Added` sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="2eaa3-121">Un état de ligne `Unchanged` est attribué aux autres lignes et les valeurs de la version de ligne `Current` sont remplacées par celles de la version de ligne `Original`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="2eaa3-122">Vous pouvez afficher les différentes versions de ligne d'une ligne en passant un paramètre <xref:System.Data.DataRowVersion> avec la référence de colonne, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="2eaa3-123">Le tableau suivant fournit une brève description de chacune des valeurs d'énumération `DataRowVersion`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="2eaa3-124">Valeur DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="2eaa3-124">DataRowVersion value</span></span>|<span data-ttu-id="2eaa3-125">Description</span><span class="sxs-lookup"><span data-stu-id="2eaa3-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="2eaa3-126">Les valeurs actuelles de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-126">The current values for the row.</span></span> <span data-ttu-id="2eaa3-127">Cette version de ligne n'existe pas pour les lignes ayant un `RowState``Deleted`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="2eaa3-128">Version de ligne par défaut d'une ligne particulière.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-128">The default row version for a particular row.</span></span> <span data-ttu-id="2eaa3-129">La version de ligne par défaut d'une ligne `Added`, `Modified` ou `Deleted` est `Current`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="2eaa3-130">La version de ligne par défaut d'une ligne `Detached` est `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="2eaa3-131">Les valeurs d'origine de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-131">The original values for the row.</span></span> <span data-ttu-id="2eaa3-132">Cette version de ligne n'existe pas pour les lignes ayant un `RowState``Added`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="2eaa3-133">Les valeurs proposées de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-133">The proposed values for the row.</span></span> <span data-ttu-id="2eaa3-134">Cette version de ligne existe pendant une opération de modification sur une ligne ou pour une ligne qui ne fait pas partie d'un `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="2eaa3-135">Vous pouvez vérifier si un `DataRow` possède une version de ligne particulière en appelant la méthode <xref:System.Data.DataRow.HasVersion%2A> et en transmettant un `DataRowVersion` comme argument.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="2eaa3-136">Par exemple, `DataRow.HasVersion(DataRowVersion.Original)` retournera la valeur `false` pour des lignes qui ont été ajoutées avant l'appel à la méthode `AcceptChanges`.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="2eaa3-137">L'exemple de code suivant affiche les valeurs dans toutes les lignes supprimées d'une table.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="2eaa3-138">Les lignes `Deleted` n'ont pas de version de ligne `Current`, vous devez donc passer `DataRowVersion.Original` lors de l'accès aux valeurs de colonne.</span><span class="sxs-lookup"><span data-stu-id="2eaa3-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2eaa3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2eaa3-139">See also</span></span>

- [<span data-ttu-id="2eaa3-140">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="2eaa3-140">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="2eaa3-141">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="2eaa3-141">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="2eaa3-142">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="2eaa3-142">DataAdapters and DataReaders</span></span>](../dataadapters-and-datareaders.md)
- [<span data-ttu-id="2eaa3-143">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2eaa3-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
