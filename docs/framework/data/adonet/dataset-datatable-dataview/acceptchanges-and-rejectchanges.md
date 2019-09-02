---
title: AcceptChanges et RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: a8589b157bc2579a03d856b73802abc9a4b42855
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204078"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="da2fe-102">AcceptChanges et RejectChanges</span><span class="sxs-lookup"><span data-stu-id="da2fe-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="da2fe-103">Après avoir vérifié l’exactitude des modifications apportées aux données <xref:System.Data.DataTable>dans un, vous pouvez accepter les modifications <xref:System.Data.DataRow.AcceptChanges%2A> à l’aide <xref:System.Data.DataRow>de la méthode <xref:System.Data.DataSet>de, <xref:System.Data.DataTable>ou, qui définira les valeurs de ligne **actuelles** sur  **Les valeurs d’origine** et définissent la propriété **RowState** sur Unchanged.</span><span class="sxs-lookup"><span data-stu-id="da2fe-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="da2fe-104">L’acceptation ou le rejet des modifications efface toutes les informations **RowError** et affecte la **valeur false**à la propriété **HasErrors** .</span><span class="sxs-lookup"><span data-stu-id="da2fe-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="da2fe-105">L'acceptation ou le rejet des modifications peut également affecter la mise à jour des données dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="da2fe-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="da2fe-106">Pour plus d’informations, consultez [mise à jour des sources de données avec les DataAdapters](../updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="da2fe-106">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="da2fe-107">S’il existe des contraintes de clé étrangère sur le **DataTable**, les modifications acceptées ou rejetées à l’aide de **AcceptChanges** et **RejectChanges** sont propagées aux lignes enfants du **DataRow** en fonction de  **ForeignKeyConstraint. AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="da2fe-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="da2fe-108">Pour plus d’informations, consultez [contraintes de DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="da2fe-108">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="da2fe-109">L'exemple suivant vérifie les lignes ayant des erreurs, résout, le cas échéant, les erreurs et rejette les lignes dans lesquelles les erreurs ne peuvent pas être résolues.</span><span class="sxs-lookup"><span data-stu-id="da2fe-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="da2fe-110">Notez que, pour les erreurs résolues, la valeur **RowError** est réinitialisée à une chaîne vide, ce qui entraîne la définition de la propriété **HasErrors** sur **false**.</span><span class="sxs-lookup"><span data-stu-id="da2fe-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="da2fe-111">Lorsque toutes les lignes contenant des erreurs ont été résolues ou rejetées, **AcceptChanges** est appelé pour accepter toutes les modifications pour l’ensemble du **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="da2fe-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a><span data-ttu-id="da2fe-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da2fe-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="da2fe-113">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="da2fe-113">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="da2fe-114">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="da2fe-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
